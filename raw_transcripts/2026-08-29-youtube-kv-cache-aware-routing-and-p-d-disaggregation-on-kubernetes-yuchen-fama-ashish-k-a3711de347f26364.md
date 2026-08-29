---
id: "a3711de347f26364"
title: "KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat raw transcript"
aliases:
  - "KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat raw transcript"
  - "KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=YXowceUKYJI"
origin: "https://www.youtube.com/watch?v=YXowceUKYJI"
type: "raw-transcript"
created: "2026-08-29"
---

# KV Cache-Aware Routing and P/D Disaggregation on Kubernetes — Yuchen Fama & Ashish Kamra, Red Hat Raw Transcript

All right, um,
welcome, everyone, to yet another inference talk.
I hope you have had a good conference so far.
And, um,
so,
in this session, I mean, I'm sure your people who have been in the room,
uh, must have heard these terms many times by now. So,
we're going to do a little bit more deep dive into the challenges of LLM deployments
for agentic workloads, and, um,
in this session, we'll focus specifically on KV-cache aware routing and
uh, P/D disaggregation.
Um,
and also, you know, when you when you look at public inference, uh, benchmark results, you are typically looking at very steady state, isolated, highly sanitized numbers,
and what those benchmarks actually don't show you, um,
is the chaotic reality of
multi-turn interactions, massive context fluctuations, which are
very typical of agentic workloads.
So, we'll also, uh, try to pull the curtain back on some of those complexities.
Um, by By way of introduction, uh, my name is Ashish Kamra.
I'm a senior manager of Performance Engineering at Red Hat,
and with me...
Hi, I'm Yuchen. I'm the product manager at Red Hat Inference working closely with vLLM and llm-d core maintainers, also contributor myself.
So, here is the agenda for the next 20 minutes or so. Um,
Yuchen will start with an analysis of
inference behavior in the agentic era
and some of the core characteristics and challenges.
Uh, next, we next, she will walk us through the KV cache,
um, utilization and management strategies.
I will break down the mechanics of prefill/decode disaggregation and walk you through some some results, and then Yuchen will again bring it all back together with our ongoing case study on
our favorite
open-coding model, GLM-5.2.
Um, and just a couple of uh sources from our side. If you are more interested in learning more about open-source inference, we have a free course
free course on DeepLearning.AI,
uh, by Cedric and with Andrew Ng,
um, and the other is a series of blogs on the Red Hat Developer portal on distributed inference
concepts, uh, troubleshooting, and deployment patterns.
Uh, and for those who may not be aware, since Red Hat is better known as the Linux company for enterprise
Linux and
uh, the Kubernetes company for OpenShift.
Uh, but more recently, we are also a major player in open-source AI inference
with,
uh, us being the top contributor in vLLM,
llm-d, and the KServe projects and also,
uh, having incubated GuideLLM
for benchmarking,
LLM Compressor for model quantization, and Speculators for
uh, speculative, uh, decoding models.
And we also bring it bring all of that together in a optimized Model Hub
on
Hugging Face under the Red Hat AI org.
Um, and we are also building the platform for the next wave of agentic inference workloads, and with that, I will hand over to Yuchen to, uh, walk you
through more of it.
So, we are currently, um, at this infection point, moving from the era of classic LLM inference to the agentic era.
So, when we look at the real-world agentic work- workloads such as, uh, SWE-bench and also like a traces from real-world Claude code sessions,
they fundamentally break many assumptions we made with classic LLM serving.
Uh, as you heard actually many times in previous sessions, for example, multi-turn is the new standard.
We found from a few turns all the way to 3,000 turns,
and also because agent frequently reuse the uh system prompt
and the tool definitions, we usually see super high cache hit rate,
um, often times well exceeding 90%.
Uh, another thing is input-output ratio is uh su- is massive, often times over a 100:1 ratio and even higher, and in many cases.
And on top of that, the context management is is incredibly complex due to this
high variance because we can't just simply take the average and often times we need to look at distributions and the P90 numbers, especially when you do uh capacity planning.
And also,
we observe really interesting patterns like sub-agent fan-out, which is which further complex uh complicates scheduling.
So, to help communities study um these patterns, we collaborate with uh Google. Thank you.
And also IBM, our parent company, to add uh a a trace replay tool into InferencePerf. You heard from earlier sessions
uh from Ashokan and Jason.
Um, so, yeah, feel free to check it out and the link is here.
Uh, next slide.
Oh, so transition from the class uh the characteristics um we just saw,
for agentic workloads, we are no longer chasing this um
this this raw throughput in the steady state. We often need to optimize,
uh, for example, interactive latency
and very, um, highly volatile and client-driven context,
because user and, you know, client define the prompt structure.
So, this introduce several critical challenges. First of all, KV cache management becomes super volatile because
the context is client-determined, as I said.
So,
often times we face this like, you know, frequent evictions and rewrites.
And secondly, we also need to tune um the engine, like vLLM, with upper-layer uh scheduling and routing.
It needs that coordination, such as prefix-aware routing,
especially when latency becomes a primary uh scheduling metrics rather than like a secondary or afterthought.
And, thirdly, we also need to rethink our metrics, for example, we need to measure cache throughput separately.
Why? Because on the right, it's really clear that economic stakes is very high. So, this is the uh Anthropic API pricing, you also heard from earlier sessions.
There's 10x cost difference between cache and non-cached tokens.
So, 10x difference on your um token balance sheet is is pretty serious impact on your business.
So, let's let's look at how the KV cache is um both utilized and managed in llm-d.
So, llm-d router has this really flexible um endpoint picker
plugins, we call the EPP, that can route the requests to the optimal pods and that meet the KV cache locality
and also the load criteria.
So, the EPP continue probe each pod's like VM pod metrics
to score each pod on like the running, for example, running and waiting requests.
And then the KV cache utilization also prefix uh cache availability,
and so we can schedule requests to the optimal pod with the lowest load and also highest possibility to um to uh of a cache hit.
So, um going down from uh to the KV cache management layer, actually you also heard from uh earlier session right before this.
So, for agentic sessions, when you have a hot, warm, and cold cache,
our current effort focus on, for example, um more offloading tiers
like NVMe, SSD, and also uh file systems like Ceph,
along with KV-centric store, um like a Mooncake,
and also implementing smarter and session-aware eviction policies, such as priority and also session pinning,
to ensure this really important, you know, that the context persists exactly when and where is needed.
So, I'm going to play this um video really quick. Uh, it's a It's a short demo.
I might want to stand here so I can look at it. Okay.
So,
Okay.
So, this is a example of a KV-cache-aware routing. As you see, when we send the very first request and populate the KV cache, takes roughly 3 seconds.
And when we actually look at where is, you know, the KV cache is going, there's no KV cache hit, because it's a very first turn.
And then when we have the second turn, the requests actually reuse the KV cache, because, as you see, the system prompt is the same, and this time takes about 1 seconds.
And then when you actually look at the uh pod address, exactly the same, because we did find the KV cache.
Now, going to the third turn, a new request with different system prompt, now it takes about 3 uh seconds,
and uh as you see, you know, right now and that we don't find any KV cache hit because it you can tell it's a different pod address.
And then if you just change the user prompt and keep the same system prompt, and the next turn you you reuse the KV cache and in this in this time, it takes roughly about uh 1 second.
Yeah. So, it's a pretty intuitive demo and um I'll turn it to Ashish to talk about the next slide. But before that, what that problem does it solve?
So, often times the prefix-aware routing and KV-cache routing helps you solve the TTFT problem,
and, of course, it will improve your uh your your throughput.
But often times for agentic workload, it's not just the TTFT. Your throughput is about your inter-token latency.
How do we solve that?
So, prefill/decode disaggregation is a really uh powerful technique, but there are times that work, at times it doesn't work.
So, I'll turn it to Ashish to give you a preview of um of the P/D uh disaggregation.
So, before we dive into P/D, let's just
uh look at what llm-d is. So, llm-d is a high-performance, Kubernetes-native, and actually now works on non-Kubernetes environments as well,
distributed LLM LLM inference framework hosted under the CNCF umbrella.
llm-d provides a unified intelligent control plane designed specifically for agentic era of inference workloads.
Well, Yuchen already talked about the router and the EPP at the top of the slide.
Um, the other aspects are workload APIs, such as LeaderWorkerSet and DisaggregatedSet, that orchestrates
complex multi
multi-node model execution,
and an autoscalers that monitors capacity bounds and real-time traffic mixes
to independently scale up and scale down
uh your pods depending on the system load.
So, now look Now let's look at uh prefill/decode disaggregation in detail. Um.
Uh.
Okay. So,
why does P/D exist in the first place? So, one of the most powerful patterns implemented by llm-d is prefill/decode disaggregation, and
you must have heard from some of the previous talks as well.
So, what happens is in in in a non-P/D situation, in aggregated serving, one pod is responsible for optimizing both your time to first token and your inter-token latencies.
Uh, but in P/D, prefill and decode become independently scalable inference pods.
But to understand why we actually need this, we have to look at uh the physics of LLM execution.
So, co-locating uh both prefill and decode tasks on the same GPU creates something called as phase interference.
Prefill phase is the phase that creates the KV caches for your initial prompt.
It wants high compute, it's highly bursty,
uh utilizes GPUs at uh
high FLOPS, and and thrives on large-batch parallelism to process the prompts and uh builds initial KV cache.
The decode phase, on the other hand,
is generating one token at a time and it's more memory bandwidth hungry.
It's highly latency sensitive and requires high KV cache residency.
So, in a in a in a in a traditional aggregated pod, if you if there is a sudden influx of a long prefill prompt,
it will completely stall the ongoing decode token generation process,
causing massive uh problems and jitter in user streaming latency.
So,
so, how does P/D actually work in practice in llm-d? So,
llm-d uses um
uh you know Okay, let's start with step 1. A incoming request hits the gateway router,
which dynamically evaluates cluster states using something known as the endpoint picker. Yuchen talked about
and schedules the request to use P/D disaggregation,
selecting the optimal prefill and decode workers.
The router then coordinates the transaction directly with the designated prefill worker.
The prefill worker processes the prompt, constructs the initial KV cache of the prompt,
and
outputs the standard KV transfer metadata.
Um,
and the target decode worker actually pulls the computed KV caches
um
uh across the network privily fabric, utilizing
uh the KV transfer metadata that the uh D uh prefill pod had generated.
Um.
Okay. So,
with that, yes, that's kind of how uh P/D is implemented in practice in llm-d. And next, I would like to show you some
uh experimental results on where P/D actually shines.
So, in this graph, you can see that um
uh in in in the standard aggregated deployment, which is the top red line,
uh the P99 ITL
uh hovers roughly around 900 ms, and you can you can see some fluctuations
um
up and down.
And But the the bottom blue line is the P99
uh inter-token latency on a P/D deployment, and you can see that it's drastically almost nine times better at 100 ms,
and it's also much smoother uh
than the aggregated serving.
And uh this is some of our own internal results at Red Hat. So, for a GPT-OSS-120B model, uh 16 H100s,
uh the aggregated config is uh four replicas, uh tensor parallelism 4, and the disaggregated is two prefill, two decode, all with tensor parallelism 4.
It's a highly
multi-turn workload with a 10,000-token prefix and 128 tokens
for every turn uh every turn.
So So, this is a great chart. Like, you can see at the bottommost line is a standard aggregated config that
uh is doing the default Kubernetes scheduling
and uh and and it's aggregated. So, that's kind of our baseline.
And then the middle blue line is still aggregated, but with the llm-d
uh KV-cache-aware routing, and you can almost see the gains just just based on the routing. And the red line is actually the P/D
uh
the prefill/decode config with two prefill and two decode workers.
And you can actually see that, like, it's very similar to the aggregated config at the lower concurrency regimes,
and uh even and and very similar at the higher concurrency regimes. But it's it's actually the middle part of the concurrency regime that P/D actually shines.
And and these are some of the the classic Pareto curves that we see when you actually do P/D and
and uh aggregated side by side.
So, these results are again from the GPT-OSS-120B model, 64 H100s.
Aggregated is eight replicas,
TP8, and Disagg is uh three prefill, five decode, again, TP8,
and a prefill heavy workload with like 5,000
average input sequence length and 500 output sequence length.
And you can actually see the blue line is the the P/D curve,
and the red line is the aggregated curve. And the P/D curve kind of dominates
um
uh the the aggregate curve
across the entire interactivity spectrum.
Okay. But I don't want to leave you guys that P/D is the answer to everything and it's a magic bullet, but
um it's uh it's essentially a separation phase separation trade-off and not a magic bullet.
So, we created this uh matrix to help you decide when P/D might be
uh good for you.
So,
if you're managing long contexts,
uh with high ISL/OSL ratios,
and you have if you have a large model that you're serving, that can that you can apply rich model parallelism techniques,
um you are facing that middle concurrency regime
uh that I I showed you in the previous graphs,
and and the very important part is that if you want uh strict ITL streaming requirements, like you want the you want the token generation to be uh much more smooth,
um then you want to consider P/D.
But we also saw that it requires transfer of KV caches from your prefill workers to your decode workers, so you must process an advanced uh high-speed network fabric like
uh RDMA or RoCE to support that KV cache transfer.
And if you do not have such requirements, short moderate context,
any model size,
low uh low concurrency regimes, or
uh if you have strict TTFT requirements, because you can actually tune them on an aggregate serving.
Um, and you the biggest point is like if you don't have the network fabric to support those KV cache transfers, so you might actually just want to stick with aggregated.
So, here is my key takeaway from all of this. So, architecting this complex platform requires balancing a lot of
um knobs and a highly multi-dimensional design space, all of which is supported in llm-d, as you saw.
The scheduler must support or constantly evaluate SLO targets, uh queue depths, KV cache locality metrics, P/D ratios,
and network topologies to be able to route the request to the optimal
pod,
while in while the P/D design space, you you need dynamic P/D rate matching to adapt to P/D ratios,
because, you know, you can start with a static P/D ratio, but it needs to evolve with autoscaler as the traffic changes.
Um,
and you need uh yeah, autoscaling to scale P/D pools independently,
um and constantly tweaking model parallelism techniques like tensor parallelism, data parallelism,
uh to meet your SLOs.
So, um,
I think with this, uh I will hand it over to Yuchen to anchor some of the concepts that we showed with the
real-world case study of serving the GLM-5.2 model,
uh which is uh still ongoing, as we speak.
Yes, still ongoing. You probably have seen tons of uh impressive numbers of GLM-5.2 on B200. When we talked to our customers and they usually don't have, you know, the luxury of B200, they have a lot of H200.
So, we have to figure out how to like put all the knobs together and make GLM-5.2 work really well for cluster of of H200.
So, uh we let's anchor all the concepts together. Uh, we went through, for example, the uh KV cache routing,
P/D disaggregation, we kind of call them a well-lit path in llm-d,
and also we combine with different parallelism strategies to so we can uh independently uh scale prefill pods, because for agentic workload, it's super uh long you know, like heavy prefill.
So, uh in this case, we design the prefill pool using uh up to three workers,
optimized for uh high throughput uh with deep EP.
And then for decode pool, we use uh one dedicated worker and um that's optimized for for low latency. So, we use NIXL for efficient KV transfer between the pools,
and also with uh each worker, we have the LeaderWorkerSet group
uh with TP1, DP8, and also uh EP8, uh expert parallelism 8.
So, the architecture is just highly modular, because you can uh actually scale the throughput by simply adding uh prefill workers
without reconfiguring and um the decode pool.
So, uh this highlights how llm-d effectively effectively manage the complexity of combining like TP and DP and EP at scale.
And also we found some interesting fun fact actually a couple of days ago.
Uh, BF6- BF16 KV cache actually is faster than using like FP8 uh KV cache for longer prefill.
Um, this is also like we continue to explore and found like more interesting patterns.
But, more importantly,
uh we want to kind of just show the result really quick. So, um for this uh data set, agentic workload data set, the ISL/OSL ratio is pretty high, 45:1 ratio.
Prefill is uh is really the constraint, you can tell, um with 2P even 1D, the
we have um 4x faster TTFT
and also 60 uh % more requests.
And this is continues like work in progress, so the next step is we need to also tune the upper layer scheduler,
lower TTFT, and also adding more more prefill replicas.
So, um
I know we're running out of time really quick. Uh, we we um the fundamental shift for agentic workload,
we're continuing to uh have this llm-d uh agentic north uh North Star,
uh with session graph orchestration, program-aware scheduling, uh state reuse life cycle, and also the uh agentic benchmark um
we're working on. So, you can find them uh in llm-d up upstream llm-d.
And also, you know, feel free to join the SIG group and uh and contribute, and um
this is a very last slide, so the distributed inference is not challenge every single a single company can solve alone.
We're proud to be uh building this uh future in the open alongside our incredible ecosystem collaborators: CoreWeave, Google, IBM, Nvidia,
growing list of launch partners and industry adopters.
So, if you are passionate about the future of open-source inference, we invite you to join us. We do have a booth downstairs, feel free to stop by, ask us any questions,
and uh thank you so much for your time.
