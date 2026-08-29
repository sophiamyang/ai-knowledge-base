---
id: "372032b07eecd147"
title: "AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash raw transcript"
aliases:
  - "AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash raw transcript"
  - "AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=bMjlRrWjdT0"
origin: "https://www.youtube.com/watch?v=bMjlRrWjdT0"
type: "raw-transcript"
created: "2026-08-29"
---

# AI Evals for Cross-Functional Teams — Nachiket Paranjape & Swaroop Chitlur Haridas, DoorDash Raw Transcript

Good afternoon, everyone.

Thanks for coming for a post-lunch talk. Always appreciate that.

My name is Swaroop, and here's my teammate Nachiket.

We are here on behalf of the DoorDash GenAI Platform team,

and we kind of wanted to share our evals journey.

It started as,

you know, evals is another engineering thing, but then it slowly we realized it evolved into a cross-functional effort,

and we kind of want to share our story here.

So, what is this team? This team is a GenAI platform team.

We are a horizontal team that helps all other product teams. So, product teams at DoorDash build on top of the infrastructure and the primitives that we provide.

And we see our

USP and the value that we provide is that we help product teams balance these three forces, which is accuracy, latency, and cost.

Initially, we applied this in terms of models, but if you think about it, it also applies to agents.

And the way we achieve this is we have primitives and building blocks.

So for example, we have an LLM gateway where you can easily switch between different models and try the latest and greatest.

We have an agent gateway where you can connect to tools and other agents,

and we help solve authentication, agent identity, and other things in a central place,

which our security team can bless.

Similarly, we pair the LLM gateway with open-weights models hosting.

Of course, cost is a number one concern these days.

And we kind of invested in open-weights models and have seen significant impact already.

And maybe we'll talk about that in a future conference.

The fourth pillar is evals, and that's the part that we would want to share today.

When we started talking to product teams internally at DoorDash, there were

varying,

distinct needs across teams.

We had a consumer discovery and shopping assistant team.

For those who attended Raghav's talk earlier today,

you will see the need for session-level quality judgments.

Then personalization ML, then you needed a way to scale up human judgment.

And with multi-agent systems, we needed trajectory-based evals.

Now the question is, how do you cater to all these different needs under a common platform?

And as we spoke to these teams, we realized like,

we needed to empower the people who are the domain experts.

And in our case, that was strategy and operations folks, it was product managers,

it was even labeling partners, and not only engineers.

So, we kind of started with like, okay, we have to be UI-first. And this was the guidance we had from Andy Fang, our co-founder, as well.

So we had UIs for non-engineers to contribute.

Then we kind of evolved to also being API-first so that engineers can also build and not be blocked on the central platform,

and they can build their own

systems.

And then of course, with the coding agents, now we have become workflow-first, where we kind of empower S&O and PMs to also being able to

navigate

the platform and run operations as well.

So with that context, I'll hand it off to Nachiket to talk about how we went about delivering this.

Cool.

Thanks, Swaroop.

And thanks, everyone, for joining us. I know France is playing right now, and I promise you this will be better than that.

I'm kidding.

So, as Swaroop was saying, evals is not just an engineering harness. It is a cross-functional effort across different pillars, across different

teams that actually helps us add all the domain-specific knowledge into our, into the quality of the AI itself.

So from your traces, to your datasets, from, you know, scoring mechanisms,

this is all basically a team sport. We all have to play and help improve the quality of AI.

So, going a little bit deeper into the same aspect. We have different teams at DoorDash who help us actually improve the quality of AI.

So you're going to have your strategy and operations folks who are going to set priorities, set the quality bar that you want to aim for.

You're going to have your product people who are going to translate

these requirements into rubrics, workflows. You're going to have your operations teams running

annotations. You're going to have your engineering teams like us providing APIs, telemetry,

datasets, judges, all, you know, the the cool things.

And

combining all these together is is what a recipe

is for actually making sure that you are shipping quality AI products through an evals platform.

So, we've tried to boil this down into sort of, you know, like a a continuous iteration loop.

So right from tracing, you know, having a tracing solution, viewing your sessions, your traces,

to sampling them down, your, you know, to a very small set that you actually want to look at,

annotating these with the domain-specific expertise that you bring in with the different teams I mentioned,

reviewing those,

then creating those golden datasets which are going to be, you know, your

golden datasets then that you want to measure or calibrate against,

and then of course, like, you know, monitoring this over a period of time and then, you know, rinse and repeat. Go through the whole loop again.

So this is, in our experience, has been, you know, like a good sort of continuous loop

for, you know, shipping quality AI.

At the on on the platform level, we have two surfaces.

So we have the telemetry layer where we have all our traces, our scores,

observations. That is also sort of the plane where users are able to access these traces using an MCP, using an SDK,

using our APIs. And then we have the workflow layer. This is where a lot of our StratOps, our product teams operate on the platform.

So this is where all the annotation tasks are set.

You know, this is where they review their golden datasets,

create their judges, calibrate their judges, and so on.

So, maybe today we'll go through, you know, these sort of four different modules or pillars of our platform step-by-step.

So again, first one: tracing and sampling,

which is actually capturing what your agents, what your LLMs are actually, you know, outputting, for lack of better words,

and actually viewing those.

Now, in order to

also power this whole platform, we have, I think as Swaroop mentioned, we have gone in an API-first

approach.

What that has allowed us to do is have these stable APIs that actually, you know,

and then, you know, build UIs on top of that.

So all our scores, our datasets,

these are all powered by very stable APIs that our team owns.

So all your API access,

including, you know, like an SDK access, is basically powered by this single

plane.

Again,

going back and, you know, like just refreshing your memory,

step one: capture your traces,

capture your sessions, measure your scores.

Then you want to start

almost, you know, like adding all your judgment, your context,

your domain knowledge,

and then calibrating your judges is what we have seen as the whole

life cycle.

Step two is on the annotation side.

So you obviously are capturing a lot of your agentic behavior, your sessions, your traces,

but you actually want to see what are some places where things went well and what are some places where things did not go well.

This is where you can actually titrate your, you know, and actually look inside what's actually happening

at at the session level and annotate these datasets.

And as Swaroop mentioned, we have a lot of use cases. We have We talk to multiple different teams who have

a various ways of annotating their datasets.

And it's it's almost hard for a platform team to, you know, build like a UI specific

for each use case.

And, you know, to give you an example, it's usually going to be an annotator who's going to annotate these datasets.

So the platform team is, you know, in charge of the APIs. We have a strategy and ops person who's actually deciding what to annotate, and then you have an annotator who's actually going to annotate your dataset.

So we took this approach, everybody has, you know, access to coding agents, and we actually doubled down on that API-first approach.

So, because we had these APIs, we were actually able to enable our StratOps teams to use something like a Codex or a Claude Code and vibe-code their own annotation UIs.

So, we had different use cases. I think we had a a talk from Raghav before.

We had image annotation use cases. We had some, you know, manual testing use cases.

What stood out to us was the underlying patterns were similar.

So if we are are API-first,

we can actually enable our our our partners to simply vibe-code these UIs for annotations.

So it's it's like a very simple example there,

you know, of of a vibe-coded UI. Looks pretty clean, does the job, and you get, you know, the annotation that you need.

This is basically like a menu from a restaurant. It's it's, you know, nothing crazy.

But the point I want to make here is that what helped us was to give

this workflow in the hands of the operators so that they can actually build their own vibe-coded annotation UIs.

So moving on, once you have these annotation UIs, you obviously want to, you know, calibrate your your your judge prompts. You obviously have some LLM as a judge

metric that you're tracking. You want to now start improving that with these golden datasets.

In order to do that, you know, we have a pretty simple process.

You're going to start with, you know, some judge prompt, take a look at, you know, what exactly do you want to measure from the output,

have have something simple. You're going to have your baseline scores, where you're going to simply run those LLM judges on your traces.

And then you're going to have that optimization loop.

So we use the GEPA library, which is a pretty commonly used library out there for prompt optimization.

And once, you know, the the iteration loop is complete, our partner teams are happy, they're going to then elevate that judge prompt as their LLM as a judge.

Now even while doing that, LLM as a judge as a concept, the whole prompt calibration concept,

might be straightforward to a lot of folks, but it is still like a pretty new and evolving field.

And what we wanted to do was really reduce the friction of back-and-forth with an engineering team.

So we tried to really remove all the complicated logic and make this into a self-serve UI.

So the screenshot that you actually see is what actually exists.

So, you know, like a product manager or an operator is going to come to our UI, they're going to set some of these configs on the platform,

and then actually run the calibration loop themselves. So they don't have to worry about the different settings that they need to worry about, what are the different

tweaks that they need to do. And they can actually like, you know, run a calibration loop using any model of their choice. I think in this example, I have Gemini. They can use run it using, you know, any of the Claude or the OpenAI models too.

The other important piece was actually making this reviewable.

You know, again, a lot of this

is a closed box where you can't really it's hard to see what's actually happening.

So the second piece that we built was actually giving them visualization and visibility

into what's actually happening. So, on the left, you can see we and this is like one of the good examples where we saw like a significant amount of

improvement in the judge prompt.

And we actually show the, you know, the the the previous, the original system prompt and the calibrated prompt

to our partners so that they are also able to gain that trust

as as as we build this.

Yeah, just want just wanted to add to that is this enables different configurations in different teams.

In some teams, we have seen strategy and operations folks own the prompt.

We have seen some teams where the product manager owns the prompt.

We have seen some teams where engineering owns the prompt. So this gives the flexibility for teams to design and evolve because we're all learning.

So even the org design is improving, and we are enabling that.

Yeah, that that that's a good point. I think the overall idea was to, you know, build something which is as self-serve as possible,

so that, you know,

people aren't always necessarily blocked by our team helping them out.

And then finally, you know, the quality loop in practice.

You know, as we've been going through this exercise, we've seen a lot of improvements happening to our product as well.

So, you know, for example, we Swaroop mentioned we started with the UIs, we are, you know, now API and workflow-first.

We're trying to reuse a lot of the existing infrastructure that already existed at DoorDash.

And that's helped us get a long way.

Now some of

we we've seen obviously like, you know, really good results. I think a very good result that we we do like to call out is we actually did see a lot of reduction in the spend

at per annotation cost.

As you as you all can imagine, we do have, you know, thousands of rows that need to get annotated every week,

and it can get pretty expensive at DoorDash scale.

And having this self-serve annotation platform really helped us reduce increase the velocity and reduce the cost that we were actually spending

with these annotators to to to annotate the data for us.

Obviously, this resulted in faster loops.

Teams were able to iterate faster, they were able to

you know,

calibrate their own judges in a completely self-serve way.

And thus, it has resulted us in in in moving with a very, very high velocity.

So, finally, just want to, you know, quickly touch on this slide again.

The eight steps, you know, continuous loop,

which is, you know, you you have your traces, you want to look at your traces, your sessions, you want to sample it down to a size which is which you're comfortable with,

you want to start annotating your datasets, you really want to start

making the data better with the human knowledge that exists and the domain knowledge that exists,

and then calibrate your workflows, calibrate your agents, calibrate your LLM judges

with this golden dataset,

and then repeat this whole cycle over a period of time to,

you know, to ship reliably and ship with high quality.

Yeah, we have four minutes left. Thank you once again.

I think that was the last slide. Thanks for attending. And if there's any questions, we'd be happy to hang out after the talk, or even happy to answer them now.
