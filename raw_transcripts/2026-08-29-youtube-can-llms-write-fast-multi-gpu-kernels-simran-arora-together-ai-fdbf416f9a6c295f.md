---
id: "fdbf416f9a6c295f"
title: "Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI raw transcript"
aliases:
  - "Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI raw transcript"
  - "Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=pOvWgX7IJsc"
origin: "https://www.youtube.com/watch?v=pOvWgX7IJsc"
type: "raw-transcript"
created: "2026-08-29"
---

# Can LLMs Write Fast Multi-GPU Kernels? — Simran Arora, Together AI Raw Transcript

Hi everyone, sorry, it's a bit loud in here. Was not expecting this.

I'm Simran. I'm a principal scientist at Together AI.

I previously did my PhD in the Hazy Research lab with Chris Ré at Stanford, and I'm an incoming professor at Caltech.

I lead the Frontier Performance Research team at Together, where we develop systems, frameworks, and algorithms to extract as much performance as possible out of modern AI hardware.

Today, I want to share a little bit about our contributions towards simplifying the development of multi-GPU AI kernels.

A few years ago, GPU utilization used to be limited by poor intra-GPU memory access and single GPU kernels.

But with significant investment in better kernels like FlashAttention, memory efficient architectures like from DeepSeek, sparse attentions, Mambas and so on, and better DSLs, we've sort of shifted the bottleneck to multi-GPU communication.

During this talk, I'll start by telling you a little bit about why now, why GPU networking now.

Then I'll tell you about the sort of problem space, so what are the challenges in maximizing hardware utilization and development simplicity for multi-GPU kernels?

Three, we'll talk a little bit about the fundamentals behind designing effective multi-GPU kernels.

Four, we'll look at whether frontier AI models can leverage these fundamental principles, do they understand them, can they reason about them?

You know, in theory, these models are very good at reasoning.

And then five, we'll talk through the results of these frontier models on a benchmark that we've developed called ParallelKernelBench for multi-GPU kernel generation evaluation.

Okay, before we dive into those five parts, just basic preliminaries.

So this is an NVIDIA GPU, an H100 GPU, that you can see on the screen.

I always like to help ground people in GPU kernels via looking at the hardware.

So these rainbow colored dots are processors where actual compute is happening, all of the you know parallel threads are operating within one of those colored dots.

And there's typically you know 100, 200 of them on modern AI GPUs.

Around those processors, you can see some of the memory that these processors retrieve data, so large weights, activations from.

So these rectangles between the colored dots are an L2 cache, slightly faster memory, not like a crazy large amount of it.

And then these black boxes are high-bandwidth memory.

So when you nvidia-smi and see, you know, 80 GB, 188 GB, whatever it is on your GPU, that's that memory.

A GPU is operating a highly parallel program, so multiple threads are combined together in into into larger coarse-grained units, and we schedule these threads and blocks onto these processors to perform our AI compute.

Beyond a GPU, we'll have multiple GPUs and we'll also have, you know, CPUs that have memory as well.

So to perform computation, the memory that these threads use is going to be stored in a really fast register memory that's right next to the computation units.

Simple physics, if I am pulling data from very, very close to my my compute unit, it's really fast to get to it, cuz you know that data is right next to me.

But there's not a large radius, and not a large volume of space that's close by to my my compute units, and so I don't have very much of it.

So you can see that the fastest memory here, the registers, is is you know 130 TB per second on an H100, but we don't have very much on of it.

And as we go to the further away memory, we have a lot more of it, but it takes longer to reach it.

Again, simple physics.

So in multi-GPU systems in particular, there is a hierarchy of interconnects.

So we will have something called PCIe as the channel for CPU GPU communications.

We'll have multi-GPU, or multi-node communications over InfiniBand, TCP.

And then in the—we're gonna focus mostly on the NVIDIA sphere here—in the intra-GPU regime, we'll have NVLink providing point-to-point connections between GPUs, and the NVSwitch.

NVSwitch connects all NVLink endpoints into a non-blocking fabric for full GPU-GPU communication.

And NVSwitch is exciting because it also provides support for in-network, off-device acceleration for oper- like communication primitives like multicast and reductions.

Okay, so diving in with the preliminaries in mind.

Why GPU networking now?

So, as I mentioned at the beginning, we've really put a lot of effort into making AI mo- more efficient over recent years.

Again, we have architectures that use less compute, less memory, like Mamba or sparse attentions.

We have algorithms that make AI more hardware affair a- aware like FlashAttention.

We have tools to make it easy to map AI algorithms to the hardware, like TileLang, Mojo, Triton, Gluon, ThunderKittens.

And we have new techniques to overlap execution across many AI operators very tightly, like Mega-kernels.

And we also have tools to make it easy to run on multiple vendor and silicon platforms like ThunderMittens for Apple silicon or or HipKittens for AMD, and so on.

At this point, we really believe that GPU networking offers many new and exciting opportunities for AI efficiency.

Modern AI workloads are getting very big and require kernels that span multiple you know, GPUs.

So on many production distributed training and inference workloads, communication is increasingly consuming the majority of the runtime and yields low model flop utilization at scale.

So the pace of innovation and diversity of approaches that different hardware providers are taking in their networking stacks is another reason why it's an exciting time to study you know, networking and communication.

So we can see here AMD hardware with what's called XGMI interconnects providing point-to-point links between different GPUs in a scale-up domain.

We can see here TPU in interconnects as well, so the TPU will use a 3D Torus and also have optical wraparound links.

So yet another diverse form of the topology and links.

And then, again, for NVIDIA, we'll have the in NV Switch, which integrates compute capabilities directly into the interconnect fabric, like for in-network reductions.

And then we'll have our NVLink providing up to, you know, 900 GB of unidirectional bandwidth between any two remote GPUs' high-bandwidth memory on, you know, particular generation of NVIDIA hardware.

Beyond the diversity in the networking stacks, there's also a lot of evolution in how AI workloads are adapting to take advantage of this hardware, and the diversity of types of, you know, hardware that we're we're using simultaneously for one AI workload.

So KV-cache memory in modern inference systems is going to be networked across GPU, CPU, disk, and remote machines.

Inference systems increasingly disaggregate different steps of inference across different hardware back ends, so you could run speculative decoding on some hardware, decode on different hardware, prefill on different hardware.

Hardware is also evolving to have larger scale-up domains than ever before, with, you know, 72 GPUs in a scale-up domain in in the coming chips, and NVIDIA planning on a single system in 2027 with 576 GPUs.

At the same time, to take advantage of these more intensive scale-up domains, we're getting richer primitives for fine-grained control and kernel writing over these domains.

So we have something called tensor memory acceleration, where we can provi- perform asynchronous network transfers from the device side on these GPUs.

So all of these changes are opening up new opportunities and challenges in both AI, you know, how do we build models that take advantage of these trends, and in systems.

Okay, so the problems that we're gonna go after: How do we get peak hardware utilization, and also development simplicity for these multi-GPU kernels?

So it's been very difficult to write multi-GPU kernels, and there's a lot of There are a lot of papers, a lot of systems reports that document you know challenges here.

One of the things here is it's compounded by the fact that communication hardware around GPUs has progressed a lot more slowly relative to compute and memory.

So comparing NVIDIA A100s in 2020 to B200s in 2024, BF16 tensor core speeds improved by 7.2x, while intra-node communication by just 3x and inter-node communication by just 2x.

And coming back to my points about how diverse networking is right now, things like tensor cores that run matmuls and our memory hierarchies are pretty consistent and resemble one another across diverse AI vendors and multi-silicon.

But again, as I I mentioned, the networking stack is something that is really different across vendors still.

You know, a first step as we went about all this work is to just study the baselines that are out there.

So one of the popular tools for communications is this NCCL library or RCCL on AMD that both you know companies, respectively, spend a lot of you know engineering investment into releasing to make it easy for people to do multi-GPU work.

But they're not very flexible, so they're tuned for bulk transfers, for large contiguous chunks of data transfers.

And the design really breaks down when you care about peak performance, fine-grain communication, and sort of non-trivial collectives that you want to fuse together.

So, as a result, you can achieve much higher performance by writing custom communication kernels that directly address these needs.

If we look at a naive baseline that's representative of very popular libraries in machine learning, stacking PyTorch with NCCL, we can we find that across the many problems in our ParallelKernelBench benchmark, that the majority of these simple baselines will fall below 50% of their communication-aware roofline bound.

So there's a lot of room for improvement here.

The current frameworks beyond NCCL, which is popular in like Megatron-LM, FluxFlow, Nanoflow, you know all again these systems are primarily orchestrating bulk collectives via NCCL and require synchronization before and after data transfers.

So beyond those off-the-shelf libraries, we have compilers and DSLs that exist.

So there's Triton Distributed is one of them and, you know, TileLang is another one.

We have found that it's very difficult to support the rapid pace of networking improvements within these frameworks.

So our benchmarks and our papers highlight results where Triton Distributed, originally tuned around 8- H800 GPUs, fails to adapt efficiently to other architectures like H100s.

And then the third category of how people can proceed here is to really hand tune specific AI operators one by one.

So there's a lot of popular work: DPP, Comet, RingAttention, Flux, Flash-Decoding MoE, and then several distributed GEMM kernels from CUTLASS.

And these methods achieve peak performance, but often they do not, you know Some of these methods have been designed in one precision, and it takes five or six months to scale it to another precision.

And just the scalability of this hand tuning and fine-grain kernel writing is not very effective.

So with this landscape in mind, our research question was really about whether there is a small set of principles and fundamentals that really governs multi-GPU kernel writing, and whether there are methods that can leverage those principles if they exist, to simplify the development of these kernels.

I'll briefly highlight two works here that govern like that that represent our approach.

So first, we think it's important to build our own fundamental understanding, and to manually do the work to understand it, rather than just throwing, say, an LLM at the problem.

So we spent the time to build out ParallelKittens, which is a small set of minimal primitives and patterns for multi-GPU kernels.

We use this to understand the tradeoffs of multi-GPU kernels, and to, one, write a large collection of peak performance kernels for a variety of parallelism schemes.

And this I will use to hopefully, you know, educate and bring us all on the same page on what patterns we figured out.

And then once we found that there is indeed a small set of tradeoffs governing this landscape, we were curious whether models, especially these models right now that claim to be very good at kernel writing and also reasoning, could reason about these tradeoffs when we provide them in context to actually generate a bunch of net new multi-GPU kernels for us.

Unfortunately, we found they were not very good, but we'll dive into more of that at the end.

So just the fundamental section.

This is going to be more you know educational, what are the tradeoffs that go into these kernels?

So there are three main ways to do intra-GPU data transfers.

There's the per GPU, what's called copy engine, and this is host or CPU-initiated work.

It's really good for large message transfers, so when your message size, the amount of data being transferred is really big.

And it can get to sort of like peak bandwidth on on the communication side.

In contrast, you can use device-initiated or GPU-initiated transfers via that tensor memory accelerator that I mentioned, or via register-level instructions, called in sort of their PTX lingo like LD, ST, RED, MULTIMEM.

And the TMA is really nice.

These device-initiated ones are really nice because they can saturate our NVLink bandwidth using relatively small message sizes.

And this means that they can be really nice when we're trying to do fine-grained communication, rather than sending bulk amounts of data over the links all at once, coarsely.

There are some tradeoffs here, so the copy engine is really nice because it doesn't take away or, you know, waste a lot of our precious registers that I mentioned are important for compute on the GPU.

And it doesn't also use any of those rainbow-colored dots, the processors on our GPU, allowing us to repurpose those for memory or computation on our, you know, other parts of the AI pipeline.

TMA, the second option here, consumes very few registers, which is why it's nice.

And it also can achieve high utilization using very few of our processors.

So it's a nice, a useful tool for fine-grained overlapping.

TMA does have limitations.

It can't effectively take advantage of these in-network computations that I mentioned are feasible with technologies like NVSwitch.

And the register-level instructions are really nice for being able to take advantage of, you know, those those sort of in-network reductions that NVSwitch offers.

So again, there are different tradeoffs, different functionalities that these transfer mechanisms offer, and they face different tradeoffs.

Second, beyond transfer mechanism, the tradeoff is around how to overlap compute, memory, and com- communication in GPU kernels.

So there's two main categories of schedules.

The first is intra-SM, within one of those rainbow dots, where we'll we'll have different warps or threads within that processor specialized to handle either compute or one specialized for communication concurrently.

We can dedicate you know different warps to each of these.

The challenge with this intra-SM overlapping is that the communication and computation pattern really need to like align and jive with one another.

They need to use the same data as inputs for the computation and communication.

When they don't align, you could use something like inter-SM schedules that are shown on your right here, where we'll now have each of the different rainbow-colored dots on our GPUs, those different processors, specialized to compute, com- communication, and memory.

And so this this is nice when the kernel would others otherwise need to split across resources like the register file or shared memory across these different steps in misaligned ways.

This is also really nice when it's hard to maximize NVLink traversal with intra-SM overlapping.

So I just wanted to highlight one quick example here, where each of the patterns excels in popular you know AI like kind of patterns that you'll see.

So on a GEMM plus reduced scatter here, we can see that the intra-SM overlapping scheduler it schedule is very effective.

In the GEMM plus all-reduce, we can see that the inter-SM, which again leverages the in-network reductions of NVSwitch, is very effective.

So we face these tradeoffs, and you can read more about the design decisions that go into them in our ParallelKittens paper.

And then finally, ideally abstractions should allow the developer flexibility to control how they're buffering and synchronizing between data senders and receivers.

So we encapsulated these ideas into ParallelKittens.

Again, a simple set of programming primitives and templates for these multi-GPU kernels.

ParallelKittens is used in production at Together AI, as well as our partner, you know, Cursor and other companies in the AI space.

Here's some sample code.

I won't spend too much time here, but we usually add roughly a dozen lines of code over a single GPU kernel to insert these multi-GPU primitives.

And you can see here across data, sequence, and expert parallelism, how our ParallelKittens kernels are achieving state-of-the-art results compared to strong reference baselines.

And you can check out our repo to learn more.

Okay, so we understand a little bit about the tradeoffs that underlie these multi-GPU kernels, and there's just a couple main you know ones that exist.

So can models reason through them and give us these you know kernels?

Models are getting better at reasoning today.

Do they generalize well to these problems, or are we bench-maxed on you know benchmarks of the past, which are more single GPU centric?

Models right now are showing really promising results on single GPU benchmarks, so it's a ripe time to to extend it.

In our benchmark, ParallelKernelBench, each task presents the model with an unoptimized reference implementation written in PyTorch with torch.distributed NCCL operations, and then a system topology that specifies the number of ranks and intra-node hardware configuration, and the model needs to rewrite the reference into a performant CUDA kernel that uses unified virtual addressing.

The multi-GPU problem space expands combinatorially beyond single GPU cases.

So a standard Transformer layer can be parallelized across data, sequence, tensor, context, layer, pipeline, and expert dimensions, and each composition induces a different communication pass- pattern.

So to make sure that our benchmark has high coverage over the representative types of multi-GPU problems, we created this taxonomy that you can read more about in our paper, and then picked representative problems for each part of the taxonomy.

These are all patterns that arise in real AI workloads, from inference to RL to post-training.

There are 87 problems overall, drawn from GitHub repositories that we found to be very informative, and we and like optimized library implementations and DSLs that people have written multi-GPU kernels in.

We wanted to really make sure that solving PK- this ParallelKernelBench would lead to net new, useful production kernels, rather than artificial or useless kernels.

Okay, so that's ParallelKernelBench.

How do models perform?

So we measured two Sorry that this is a bit small.

We measured two main metrics: pass@k, which is the number of correct kernels generated after k attempts; and then fast_1@k, which counts solutions that are both correct and outperform the speed of the PyTorch + NCCL baseline.

So pass@k, just correctness.

Fast_1@k is whether you're getting a 1x or higher speed up over the reference, so performance-oriented.

We found that in the zero-shot setting, the best of the frontier models we tried solves 28 out of 87 problems, and 22 of those problems are faster than the PyTorch + NCCL baseline.

If we make multiple samples, you know standard scaling up test-time compute, we can get that number from, say, like the to to 36 correct solutions, but the fast 1x performance still plateaus out at roughly 31%.

So we don't see much room from continuing to scale there as we increase the number of parallel generations.

We find that the correct once correctness is established, speed-ups naturally come from eliminating NCCL staging overhead in favor of direct NVLink loads and stores.

The success patterns here are really concentrated into familiar patterns, so collective primitives, tensor parallel GEMMs, and Ulysses-style context parallelism.

So in other words, patterns that we see heavily represented on the internet, rather than necessarily patterns that the model has used its reasoning abilities to think through.

Even the best of the model that we benchmarked here, GPT-5.5, drops off very quickly as the speed-up threshold increases.

So on the x-axis here, we're increasing the speed-up threshold over that PyTorch + NCCL baseline, and then we're showing the number of correct kernels that are faster than that baseline or this much faster than the baseline on the y-axis.

So GPT-5.5 is this orange line here, and then DeepSeek-V4-Pro is the aqua line at the bottom.

We found that there's deeper issues than CUDA syntax.

So we found that if you do multiple sampling or have the model kind of look at its errors and correct them, it can often compile the kernels.

But the models really struggle to reason through the tradeoffs that we talked about in the prior section: collective ordering, data partitioning, thinking about intra versus inter-SM scheduling, or deciding between the different transfer mechanisms.

We find that they often do not use things like the register transfer instructions or tensor memory acceleration when writing the kernels.

We wanted to try a pretty simple instantiation of something like a Claude Code coding agent.

So we took the mini SWE-agent multi-turn harness and one of the best performing models, Gemini 3 Pro, and gave it access to a local bash environment to sort of mimic the standard Claude Code setup.

We found that this could help the agent go from solving 24 problems to 35 of 87 problems, with 26 achieving over a 1x speed up over the reference.

But we found that as we scaled the amount of time, the performance plateaued as and we find that additional techniques would be required to continue seeing the scaling there.

Again, these results are discussed in more detail in our paper.

We think this is a really exciting You know, just to wrap up here, we hope that people out here can use both ParallelKittens and ParallelKernelBench.

We think that the kernels generated from solving ParallelKernelBench will lead to net new production kernels that are important bottlenecks for inference and RL right now.

They're, you know, we tried our best to make them, you know, non-artificial.

And we can already see signs of life and exciting results where people have not invested a bunch of time to handwrite a multi-GPU kernel, and we've gotten some net new interesting ones like this NeMo vocab-parallel filtering kernel, a Hyena architecture context parallelism kernel, and the SAM 3 video segmentation model IoU suppression kernel.

Just to conclude here, we're really excited about how uh Well, just talking about the lessons first off, we think there aren't that many patterns that are involved in writing intra-GPU effective kernels.

Again, encapsulated by our small set of programming primitives.

But unfortunately, models do not currently understand how to reason through these tradeoffs even when we provide them in context.

We're really excited about methods that can help attack this benchmark.

We're excited about architectures that can grow with the trends of how networking stacks are evolving, you know, larger scale-up domains, shift away from scale-out, and massive on-chip memory structures.

And we hope that, you know, we can also extend And you know, you can feel free to reach out to me at my email.

Thanks.
