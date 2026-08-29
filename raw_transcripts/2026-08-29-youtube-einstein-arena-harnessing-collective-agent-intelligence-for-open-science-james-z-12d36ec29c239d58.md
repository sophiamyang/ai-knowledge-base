---
id: "12d36ec29c239d58"
title: "Einstein Arena: Harnessing Collective Agent Intelligence for Open Science — James Zou, Together AI raw transcript"
aliases:
  - "Einstein Arena: Harnessing Collective Agent Intelligence for Open Science — James Zou, Together AI raw transcript"
  - "Einstein Arena: Harnessing Collective Agent Intelligence for Open Science — James Zou, Together AI"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=mMNkdYnIVC4"
origin: "https://www.youtube.com/watch?v=mMNkdYnIVC4"
type: "raw-transcript"
created: "2026-08-29"
---

# Einstein Arena: Harnessing Collective Agent Intelligence for Open Science — James Zou, Together AI Raw Transcript

All right, uh, I think we'll go ahead and get started with the, with the presentation.
Uh, so my name is James Zou. I am, uh,
going to explain some of the work we're doing
with together.ai, and it's also in collaboration with Stanford,
around designing and optimizing environments for AI agents to enable these agents to make
new kinds of scientific discoveries.
All right.
So, so I guess the current paradigm of how people often are using or deploying AI agents is often involves designing workflows
that sort of tells the agents, uh, you know, what to do, right,
or how the agents should work.
And it's typically done through a series of steps, or prompts, tools, instructions.
In contrast, the way we imagine an environment is that the environment should really specify
not how the agent should work, but really where the agent should work,
right, and the environment then should provide a set of incentives and infrastructure for the agents,
and, uh, guardrails and resources so that the agent can then flexibly work within that environment.
Right. And our thesis here is that, you know, as agents become more and more powerful,
right, if we try to design workflows, it often can limit the capabilities and creativity of the agents,
whereas if we properly design the environment, this can enable a lot more
creativity and capabilities and intelligence for the agents to naturally emerge.
This is why I think we want to try to shift away from designing workflows and harness this towards designing environments.
So what I want to do today is to give a few examples of how we design environments for agents.
And in particular also show how they're able to then with, with having the right environment is able to actually solve some really interesting and innovative problems.
So the first example I want to share is the system that we, uh, environment that we created called the EinsteinArena.
It's sort of like the one of the first environments that enables
AI agents to be able to collaborate in the wild and to compete
to really solve open-ended scientific problems.
So we designed this EinsteinArena to be really agent-native. Right, so that means that, uh, it's very easy for agents to just read the skill stock on our, on our arena and then be able to access that arena.
And, uh, it's actually also designed so that it's intentionally very hard for humans to enter the arena, right. So you actually have to solve a little puzzle to prove that you are an AI agent in order to participate in this arena.
But any agent in the world can openly and freely participate on the arena.
And once the agent actually enters into the EinsteinArena, this is what they'll see, right. They will actually see a list of curated problems.
Each of these problems is actually a problem that we curated. So it's a scientifically interesting problem.
And we curated these problems so that, first, there's actually an existing community of human researchers that are interested in these problems.
So these are important problems for human scientists.
And second is that for each of these problems, we can actually create a well-defined and determinis- deterministic verifier to assess the quality of the solutions to each of these problems.
And I'll give some examples in a couple of slides.
So, so the agents can actually decide which of these problems they're interested in once they log on to the arena, right. So if they entered into a particular problem space,
this is what they'll see, right. They'll see some description that precisely explains what is the problem.
We have a discussion forum where the agents, uh, can communicate. So almost like a social network where the agents can actually communicate and talk to each other
and ask for help or give recommendations.
Um,
and we also have a leaderboard. This is where the agent can actually see each other's solutions, right. So in any in, in, and anytime they want, the agents can actually submit a solution to one of these problems.
And because we have this verifier, we can actually then determine what is the quality of that solution and provide a score in real time.
So this leaderboard then is be constantly updated in real time,
and the agents can also see how other agents are doing on this problem,
and they can also see other agents' solutions and download those solutions.
So there's both a collaboration dynamics and also a competition dynamics in this arena, right. They can collaborate and ask each other questions and help in the discussion forum, but agents are also competing with each other. In that way, I think it also sort of simulate how human researchers can compete and also collaborate to solve interesting problems.
So we launched this EinsteinArena environment, uh, earlier this year, I think in March.
And within a few weeks, it's already, we're very impressed and very surprised that the agents were actually able to already discover
new solutions to, uh, 11 problems that sort of the best solutions that have ever been found, right. So that means that the solutions actually discovered by the agents on EinsteinArena were better than any previous human solutions or any solutions that required using more specialized AI tools.
So I'll just give you an example of one such solutions, or one such problem,
which is called, uh, the Kissing Number Problem.
So this is actually a very famous problem, been around for hundreds of years. Uh, so for example, Isaac Newton was already working on some versions of this Kissing Number Problem, and it's actually relatively easy to state.
Right, so the Kissing Number Problem basically asks that
what is the maximum number of spheres that you can place around the central sphere
so that these additional spheres do not overlap each other?
So for example, in one dimensions, right, so around the central sphere, I can place one sphere to the left, one sphere to the right without overlap, so the kissing number in one dimension is easy to compute, it's just two.
In two dimensions, it's also easy to show that you can just, at most, place six spheres, right, so case kissing number in two dimensions is six.
But it turns out that in higher dimensions,
it actually becomes really hard to compute what's the maximum number of non-overlapping spheres,
and the kissing number problem in higher dimensions is actually open, right, as not been, uh, is, is not clear what is the the optimal number.
And so scientists, uh, have been trying to work on this problem for the last several centuries.
And in particular, right, so the kissing number problem in 11 dimensions has attracted a lot of interest for various reasons.
So this is actually sort of the progression of the solutions in 11 dimensions.
So in, you know, 1980s, right, so it's best known that there you can place 440 spheres, right, in 11 dimensions without overlap.
And in, uh, I think 19,
uh,
So, yeah. So, so in in 1980, there was a big advance that the first for the first time showed that you can actually just construct with 582 spheres in 11 dimensions without overlap.
Uh, and then it sort of stuck there for about 40 years, right, until 2022,
where a mathematician was able to publish a new advance, right, uh, a breakthrough that's able to improve that to 592 spheres.
And then there's another breakthrough from DeepMind the following year that advances that to 593 spheres.
But with on the EinsteinArena, by having these agents able to collaborate actively, right, in the wild,
within a few days, they're actually able to construct a new solution
that shows that for the first time you can create 604 spheres in 11 dimensions that do not overlap.
And this is not just a problem that's of mathematical interest, because it turns out that
the more of these you can of spheres you can place in higher dimensions without overlap, that actually creates, you know, better coding systems, including ways of like doing error correction codes for information transfer.
Right, so this actually is, by creating these better constructions, it also leads to these better engineering algorithms.
And in this case, actually, the collaborations among these agents
is really critical for making these advance, right. So these are, this is a sort of problem
where not a single agent was able to solve by itself, right, not, you know, GPT-5.5 or Claude models, they can't really solve the problem by itself.
So the collaboration among multiple agents is really critical.
And here, we're actually able to show that there's like this, uh, sort of a lineage trace of how the agents are able to collaborate
and then basically take each other's solutions and refine that and further optimize it to arrive at this breakthrough.
And you can also see some of these interactions and discussions on EinsteinArena,
right, where, uh, here's an example where, you know, one agent actually, uh, was asking other agents, you know, "Have you tried," you know, "some of these approaches,"
um, "with, uh, these SDP approaches?" And then the other agents show that, "Yes, we have tried these approaches, and here are some of the things that we've found."
Right, so the information sharing on the forums on the arena is actually really important to help the agents to arrive at this solution together.
So in addition to solving these interesting scientific problems,
right, we've also been using platforms like the EinsteinArena, uh, to help to improve, uh, you know, uh, machine learning in AI itself.
Right, so here's one example where we're actually used these agents to basically help us to create better kernels
for and to speed up those kernels.
Right, and here, we use the same environment, right, where the agents can compete and also can collaborate, and they see this leaderboard.
And we basically change the back end instead of trying to verify the solutions to this mathematics problem,
here, we're basically try to, uh, you know, we'll compile and benchmark and test and verify the quality and the speed of the individual kernels,
right, and then we'll provide the feedback to the agents in real time in the form of these leaderboards.
In this kernel settings, we also found it to be quite useful to have different agents with different personas,
right, and these different personas actually corresponds to different, uh, roles and priors that agents can actually have.
So for example, we'll have one agent that looks at tends to look at more of the profiling, another agent that tends to look at more of the memory consumptions,
a third agent that looks at, you know, the precision, the tensor computations.
And these agents can and then across different personas, they can able to collaborate and then compete on the arena to speed up the kernels.
And in this case, right, here, the agents were also able to collaborate, and lead to really quite substantial speedups, uh, including sometimes over two 2x twofold speedups in some of these production kernels.
So here I'm just showing you a few examples where for things like paged attention,
uh, and these are sort of for specific shapes, but we also have generalized this to many different shapes and different, uh, hardware types, right, where we're actually seeing that we're getting up to sometimes over 2x speedup in these kernels.
And, uh, compared to the previous state of art kernels for these problems.
And these improved kernels created, designed by the agents are actually already used in in production at Together AI.
So in the last few minutes, I want to show like a second example of a kind of an environment that we created
as a way to, uh, train and to create better data scientist agents.
Right, so we call this DSGym, which stands for Data Science Gym,
which is sort of like a unified environment that we created for both for evaluating and also for training data science agents
to solve complex data science problems.
So here in this DSGym environment, we also curated and created a unified list of different datasets and tasks.
Right, so these datasets can combine, uh, spans across many different settings.
And the agents are then able to interact with these different datasets that we have through like a unified, uh, interface and through code execution.
In the DSGym environment, we also provide a unified infrastructure
for the agents. So for example, the agents can actually spin up many different Docker containers to test their data science algorithms and to run them in parallel.
So in the process of actually creating the datasets and tasks for the DSGym environment,
so we initially actually wanted to incorporate some of the existing data science benchmarks that have been used to evaluate agents,
but we actually quickly realized that many of the existing widely used benchmarks actually have many problems.
And one big problem is that they're actually very vulnerable to shortcuts. By shortcut I mean here is that, uh, you know, here where I'm showing sort of three different common popular data science benchmarks,
right, and then in green here basically shows like the performance of the agents on these benchmarks.
Uh, but the red bar also shows how well they're able to, what fraction of the benchmark the agents can actually solve without actually using the datasets themselves, right, so just by reasoning or by, you know, uh, doing other shortcuts without actually, actually working with the underlying datasets.
And across many of these different benchmarks, right, sometimes up to 20% to 50% of the tasks can be solved without actually looking at any of the underlying data,
which I think is really a significant problem with many of the existing benchmarks.
So to address that, we actually carefully curated our our own benchmarks, right, for both for scientific analysis, and also for predictive modeling.
So for scientific analysis and discovery, the way we did this is that we actually went through recently published papers
and then carefully curated data and also tasks from those papers, and then we also had human scientists and experts to review each of those tasks.
And for predictive modeling, the way we did this is actually go through all the different Kaggle competitions
to look for some of the recent Kaggle competitions that are still open, uh, and where also you have high quality datasets and also high quality, uh, evaluations.
Then we curated those into the DSGym as a kind of task for evaluating how well models agents can actually build predictive models.
So all together in the DSGym, we actually have created, uh, over a thousand different tasks. They span across
uh, dozens of different scientific domains,
uh, ranging from biology to physics to economics.
It also involves many different data types and data modalities.
So this actually makes it very easy for us to evaluate different models, both open and closed-source models.
And one thing we found is that the existing models, even the frontier models,
often are only still achieves like less than 50% accuracy performance on the DSGym tasks, right, so these are definitely not saturated benchmarks.
We can also use DSGym as sort of like a training factory to improve these open-source models.
Right, so one thing we did here is to actually generate in DSGym actually the gym itself will actually create all these execution-verified trajectories, which means these are trajectories generated by the agents that have been verified through the through, uh, through, uh, actually executing the code from the agents.
Right, so by generating these execution-verified trajectories, then we are able to like fine-tune sort of small open-source models
that actually now achieves sort of the that are sort of the best-in-class, uh, open-source models in terms of solving these kind of data science tasks, right. And these models are small enough that you can actually run them locally on your laptops, on your computers.
So just to summarize the this part with the data science gym, right, so we with DSGym, we created this unified execution layer so people can actually run and all these different tasks across dozens of different tasks across many different domains.
We've carefully verified that there are no shortcuts in these tasks, which has been sort of a common challenge with existing data science benchmarks.
And we also enable in the DSGym a way to generate synthetic data so that you can easily use that to, uh, improve and to train your own data science agents.
So just to summarize the presentation, um, I think the main takeaway here
is that I think we're in seeing this interesting progression us in terms of how we build different AI systems.
Right, so the in the past, people have been building these AI systems mostly by designing individual models or individual tools.
And currently, there's a lot of focus on creating, designing agents, or harnesses and workflows around agents.
But what our research shows is that I think we're really moving towards the next stage
where, rather than trying to design workflows or physics or specific agents,
what we really want to do is to design environments,
which is a set of infrastructure and incentives that in that motivates the agents to actually solve more and more challenging problems.
And with appropriate designs, these environments can actually in unlock much more creativity and collective intelligence from the agents
that's, um, that's limited by the existing workflows.
And here are some of the references for the papers that we published that describes these in more detail.
So thank you very much.
