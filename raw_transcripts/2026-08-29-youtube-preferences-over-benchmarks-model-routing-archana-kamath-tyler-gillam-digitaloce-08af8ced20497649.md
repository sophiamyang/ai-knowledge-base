---
id: "08af8ced20497649"
title: "Preferences Over Benchmarks: Model Routing — Archana Kamath & Tyler Gillam, DigitalOcean raw transcript"
aliases:
  - "Preferences Over Benchmarks: Model Routing — Archana Kamath & Tyler Gillam, DigitalOcean raw transcript"
  - "Preferences Over Benchmarks: Model Routing — Archana Kamath & Tyler Gillam, DigitalOcean"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=FvxY8oPoI8o"
origin: "https://www.youtube.com/watch?v=FvxY8oPoI8o"
type: "raw-transcript"
created: "2026-08-29"
---

# Preferences Over Benchmarks: Model Routing — Archana Kamath & Tyler Gillam, DigitalOcean Raw Transcript

Hello everyone.

So, Preferences over Benchmarks.
The talk today is about model routing and specifically why the way most people think about picking a model, which usually is chasing, you know, to the top of a benchmark, is actually the wrong instinct.

I'm Archana, VP of engineering for inference engine and AI infrastructure at DigitalOcean.
And I'll be joined by Tyler, who built parts of the router, and we'll actually do a live demo for us today.

We both work on the managed agent orchestration and inference engine products at DigitalOcean.

So, you may know DigitalOcean as Droplets, databases, and App Platform.
All of that is true.
We are also the AI-native cloud.

This is five integrated layers, starting from infrastructure all the way up to the managed agents, with the inference engine right in the middle.

And that's why we are here talking about inference router.
Routing lives in the inference engine.
And if you want to know more about our stack and the full story, please come find us at the booth.

So, everybody is reaching out for the model routing.
And let's look at three reasons why the three reasons that are breaking the one model habit for most users.

The first one I want to talk about is cost.

Spend is exploding, and even companies like Walmart, Uber, Microsoft, they are actively capping usage to control the inference bills.

The second one is fit.

One model for every task is likely an overkill.
You're essentially paying frontier rates for a work that a much smaller model will be able to handle really well.

And the third one, which for me is the most important one, is the risk.

The risk associated with one single model.
Models can go down.
And if you bet your entire product and production on one model, you have no failover when something degrades.

And model orchestration is actually the new FinOps.

As you all know, cloud cost optimization took us about 15 years for it to actually become a real good discipline and for companies to get it right.
This one actually is arriving in months and not years.
And here's the premise that I think everybody gets wrong about this.

We all think of like what is the best model for a job.
Here's the thing.
There is no single best model.
The right one depends on the actual request.

For example, if you're doing classification and labeling, a small, open model may very well work really well for you and will give you really good cost optimizations.

However, if you are running code completion inline, you will likely need really fast routing, and that is where a faster, larger routing model comes into picture.

Think about code generation and bug fixing.
You're likely good with an mid open-weight model.
Uh and again, it'll bring you like really good cost optimizations over using a frontier for something that is likely an overkill in this situation.

But then you're looking at like really accuracy-critical tasks like code review and security.
You're likely going to lean towards a frontier model.

So, essentially, what makes a model right for a request?
It's a mix that no public leaderboard can actually encode for you.

Because it's the task itself.
What are you actually trying to achieve?
What is your model trying to achieve?
The system prompts and tools around it, that is the methodology by which you're getting something done using a model.

The cost you're willing to spend.
This is a very, very important aspect.

And latency that the use case needs.
Not all use cases need the same amount of latency.
So depending on what you're trying to do, this can vary widely.
And finally, the end-user preference.
All of this is driven by what the end user really wants out of your application.

So, I'm going to welcome Tyler on to the stage so that he can actually show you the inference slide router live in action and show you how it can really help with all of these key aspects that I'm calling out here.

Testing.
All right, thank you, Archana.

Okay, so many builders have tried auto-routing before.

But the problem was that it feels like a black box.

The router makes a choice, and if that choice results in poor performance, you really have no way of improving it.
We built ours differently.
At the architecture level, which is what you can see on the screen, a request runs through our open proxy Plano and our purpose-built routing model.

Both open source.

There is no vendor lock-in, which is a key DigitalOcean value.

You describe what matters for your workload:
cost, latency, quality, preferred models,
or hard rules.
Then the router uses that context to pick the right model per request.

Because the routing model is specialized for this job, it's super fast, under 200 milliseconds, and it costs customers nothing extra.

In our evaluations, it actually is beating frontier models like the GPT-5 series models at routing tasks itself with a fraction of the latency.

So the difference is simple.
This is routing you can customize, evaluate, and improve without vendor lock-in.

So, you bring your preferences, and we honor them.
You describe the task in natural language, and set what matters:
cost, latency, and task description.
You bring your rules, and we execute them intelligently.

Layer decision-tree rules on top.
Start from presets.
Change anything you want in a single line of code.

And you validate with your own evaluations, not someone else's leaderboard.
Route, evaluate, adjust, then feed that back in.
That loop is key.

Okay, we're going to switch gears here.
We're going to do a live demo.

Bear with me here.

All right, I'm going to show you a couple things.
First, I'll show you router configuration in the UI, how to use it, and then how you can use evaluations to measure and improve your router's performance.

And then I'll show you a real router that I created inside a coding agent workflow.

So, I'm here in the cloud console, the DigitalOcean cloud console.
And you can see my routers.
We have several presets.
You can see software engineering, general writing, knowledge bases and document intelligence.

In this case, I've actually created my own, so I I customized off our preset software engineering.
Uh if we click into this, we can see that I have severed several different tasks here.

I have bug fixing, code generation, test writing, and a few others.

This also shows that you can specify more than one model per task in the bug fixing case and code generation case.

Um in the code generation, I have GLM-5.2 and GPT-5.2.

And because I really want to always route to GLM-5.2 unless it's down, I use this manual ranking option.
So it'll always go to GLM-5.2.
If GLM fails, it'll fail over to GPT-5.2.

In the bug fixing one, you can see a little bit of a different one.
In this case, I have selection policy fastest.
So, out of this model pool, if it matches to bug fixing, it'll pick whichever one's been fastest throughout the last 30 minutes.

Okay, let's do this in action a little bit.
Here's our playground, where I'll show a couple of examples side-by-side.
First, I'll start with just a simple prompt: Write a basic Fibonacci function.

And as this runs, we can see on the left, we're routing to Opus.
On the right, we're using our software engineering router that I just showed you.

And you're going to see that it picks different models on the right.
So, in this case, it matched to the code snippets task and just used the Llama 4 Maverick model that I had configured for that one.

And if we scroll down, I mean this is this is obvious, right?
This model is extremely fast and extremely cheap compared to Opus.

Now, let's say, optimize my function.

And we'll see the same thing happen.
In this case, it matched to the code performance optimization task, using GPT-5.2.
And again, it's obviously significantly faster.
If we scroll down here, we can also see that it's significantly cheaper.

We'll do one more: Write some unit tests.

Okay, and in this case, it matched to Claude 5 Sonnet on the test writing and code verification.

And again, we're going to see faster and cheaper.
So, it's a pattern.
It matches my, you know, vibe check, right?
It's still vibes, though.
How you actually prove it is working it through evaluations.

So, I have an evaluation that I ran here.

Comparing Opus on the left, or actually on the right hand side, to my router on the left hand side.

You can see that the scores, 90% for my router, 95% correctness for Opus, are very, very close.
In fact, that's pretty much within LLM as a judge uh margin of error.

But what what's really interesting is if we scroll down here, we can see that the router used significantly less tokens and was significantly faster than Opus.

Okay, let's jump into a real workflow here.
This is where the inference router really becomes impactful.
Here, I have two terminals running open-code.

On the left, I have a single-model approach using Claude Opus.
So, I have Opus set up or open-code set up with Opus.
On the right, I've configured open-code to send requests to our software engineering router that I just showed you configuring.

Um below, I kind of have this custom-built open-code where you'll be able to see live uh observability essentially.

So, let's uh go ahead and get these started.
It's just a simple feature request preloaded into here: Build me a spinning wheel app.

I'll run the same prompt in both.

And as this runs, we can focus on the bottom panels.
It'll start to to show up here.
Hopefully, we can see that on the screen.

Uh you'll be able to see token usage in real time, which models are being selected, what task those map to, and the cost accumulating live.

So, on the right, we can already see that we're starting to route to GLM-5.2 because our requests are starting to match the code generation.

And on the left, of course, we're just routing to Claude Opus.
I think open-code sometimes routes to to Haiku by itself, so that's what you see there.

And we'll notice latency, too, how quickly things start to come back.
In this case, it wants me to create a temporary directory.

So, the key difference here is that, on the left, we'll see every single request that I write goes to the same premium model.
Cost and latency is going to stay high for pretty much every single task.
On the right, the router is selecting models based on the task.

So, we're optimizing both cost and speed.

And we can see that uh our software engineering router already finished.
And if we look here, it actually matched to two models throughout.
So, let's go ahead and open this up and see how it looks.

Okay, this actually looks really solid to me.
And Opus 4.7 finished at a similar time.
Let's take a look at that.

We can compare.
I mean, this is this is a vibe check, right?
But, honestly, I would say that the software engineer routed it better, cuz this is an interesting approach that you I'm not even sure it works too well.
So, in this case, the router did a little bit better.

So, now that that step is done, you know, we get similar outputs.
But if we look here, the software engineering router has only spent 8 cents on the session.

While Opus directly has spent 25 cents.
So, we have a about a 3x in cost and very, very similar quality so far.

Let's try another another prompt here.
What what comes next in a software engineering lifecycle?
Probably write some unit tests, right?

So, we'll write this in both.

Start Opus first.
On the right, we have the router again.
And we can see that it got matched to the test writing and code verification, which picked the Claude 5 Sonnet model because that's what I configured earlier.

And we'll see the same pattern.
It's going to be significantly cheaper overall across the entire session than going straight to Opus.

So, we'll let this finish here.

Okay, and now that finished.
Let's just queue up one more.
Write some documentation in a README.

And then we can compare the total session cost.

Okay, and as this runs, we'll wait and see what it does.

Okay, it created the README.
And what if we look here, we can see that the total session cost for the router was 14 cents, while the total session cost for Opus was 44 cents.

So, at this point, we can see the cost is significantly lower.
Latency is optimized per step.

And the quality remains pretty similar across.
So, you can see as you scale this, the cost, performance really add up.

Okay.
Archana, back to you.

Thank you so much, Tyler.
And, that that was actually a live demo that we ran here, so thanks to Tyler for setting it up and taking us through that.

So, now that you've seen it work, let's look at some quick facts.

Routing decision and under 200 milliseconds per request.

It runs on a custom mixture of experts model purpose-built for routing.

Zero application code changes needed from you to get it to adopt.

And it's free and included, so you do not have to roll out your own router.

And we open source the whole routing model via Plano, so you can actually check how that looks as well.

The last thing I wanted to talk about was a bit about um routing is the foundation layer.
It's not really the destination.

And there are three things that we usually build on top of it.
The first one is evals to prove that the right model works with your use case and your tests well.

Caching, so that you can stop paying twice or more for the same answer each time.

And personalization, so that the router learns what works for your team over time.

This is a continuous improvement loop maturing over time.
That means that the more you route and evaluate, the better the router does for your workload.

So, to summarize, where does this leave you?

There is no single best model.
There's only the right model for the request.

And benchmarks will only tell you part of the story.
Your preferences will tell you the rest.

And we built the router to honor your preferences and stay open, so that you're never locked into a single stack.

And that's how teams actually build.

We are DigitalOcean, an AI-native cloud.
Come find us at the booth, and route your next workload with us.
Thank you so much for being here.
