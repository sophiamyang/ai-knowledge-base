---
id: "1642996e12a276c2"
title: "Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber raw transcript"
aliases:
  - "Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber raw transcript"
  - "Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=17-YSUHo6Lk"
origin: "https://www.youtube.com/watch?v=17-YSUHo6Lk"
type: "raw-transcript"
created: "2026-08-29"
---

# Agentic SDLC at Uber — Uday Kiran Medisetty & Adam Huda, Uber Raw Transcript

Hey, uh let's get started.
Good morning everyone. I'm Uday.
I'm here with my colleague Adam.
We'll talk about our journey towards managed software factory.
And in the beginning In the first part of the talk, I'll talk about the key building blocks that we are investing in. And later, Adam's going to talk talk about how we take all of these blocks to build an end-to-end cohesive solution for our engineers.
To set some context, we have a few thousand engineers across 12 global tech sites.
Over the last year, all of the investments we made in agentic AI have led to more than 70% of our PRs now either by local or cloud agents.
And all of this led to twice the number of lines of code per engineer year-over-year.
And this extends way beyond coding, and we see it in every aspect of the engineering lifecycle today.
And we're also accelerating toil at a toil reduction at a massive pace.
Like we handled more than 250 automated migrations, cumulatively 9 million lines of code automatically for our engineers.
And before even the building blocks, um you know one All the investments we made over the last six years on moving to monorepos, moving to Bazel, all of that also laid a really solid foundation for us to accelerate this.
So, the first I'll cover all of these six building blocks, and Adam is going to talk about a specific example and show how that feature can be built end to end uh with all of these.
And all of these are in various stages of maturity and rollout within Uber, but we want to give everyone a sneak peek of what we are up to.
So, let's go to the building blocks, the six building blocks, one by one.
The first one is model gateway.
This is one of our earlier investments.
The three things that we wanted to mention ensure was no PII ever leaves our perimeter to any of the vendor by default.
And any guardrail that we add here, the latency of that is strictly bounded.
And every request that goes through this, whether it's uh and we need to be able to attribute per user, per project, and per team.
So, we have a model gateway. We made sure all of our internal use cases, our coding harnesses, our external use cases, they all go through one single OpenAI, Anthropic-compatible endpoint.
It goes through a series of middlewares. The first one is identity and authentication using SPIFFE.
We have a data anonymizer that redacts 20-plus PII types.
We have a AI Guard that has five specialized models that handles various parts of safety and policy that we want to ensure. And all of that runs under 100 milliseconds.
We also are investing in all kinds of caching and token optimization strategies at this layer.
And every request that goes through this, we are able to attribute to a specific project in our catalog.
And we can attribute per caller, per user, per team both in real time, but also in our data lake.
This enables us to create all kinds of spend tiers and guardrails in a holistic way across our portfolio.
We also use this layer for capturing audit logs, session traces, which are then plugged into our benchmarking and all kinds of self-improvement loop efforts.
And for an engineer at Uber, you take the vanilla client, you set the project ID and and we take care of everything else.
Today, we have 800-plus projects internally going through this,
cumulatively handling more than 100 million model requests per day.
This includes both the frontier models, and also open-source models, whether that is hosted in our infrastructure or some of our vendors.
The next is how do we provide tools to all of these models?
Last year when we started on this journey, we had thousands of internal APIs, but none of them are agent accessible out of the box.
And we had so many other SaaS tools, and each one of them have different way to authenticate, different way to setup, which is a lot of hassle for for everyone.
And once you end up with enough MCPs, they'll all add up to and have a massive token tax.
Similar to model gateway, we have an MCP gateway that handles whole bunch of middlewares for for engineers.
And we have an automated crawler that looks at our internal APIs
and projects all of these into MCPs with one single config change.
And we do the same thing even for our SaaS MCPs. Whether it's Google, Slack, Jira, all of this, they go through the MCP gateway.
We we host them, we do the token exchange. So for all the engineers, they go through one single entry point, one common way to install any MCPs.
This simplified a lot for all of our engineers and employees.
And then the whole bunch of token optimization strategies.
We initially had direct MCP pattern. Earlier this year, we created Omni-MCP, which is one single MCP that you install, which can discover and invoke any MCPs within the gateway.
And a couple of months ago, we projected all of this MCPs into CLI pattern so that even the response doesn't eat up in your context.
And of late, we also have a Code Mode skill which is auto-installed, which on the fly creates Python scripts to hyperoptimize some of the top MCP token consumer consuming use cases.
And all of this led to like now we have 1,000-plus MCP tools, and just with this optimization efforts, we've saved more than 40% fleet-wide savings.
So once we have the models and the tools, we need a place to run all of this.
For many years, we had DevPod, which is our cloud, remote environments.
We we we had this because we had like large monorepos with millions of lines of code, and this is how engineers work at Uber.
And now we took what we had with DevPods, and we agentified that.
Now we need some environment for agents to run for longer period of time, they need to be quick, they need to be isolated, we can install any number of them, and they need to be globally available across all of our sites.
So we have a pre-provisioned Kubernetes balloon pods. When an agent requires a new environment to run, it can take one of that which is already pre-provisioned. It has all of the repositories already snapshotted, the search index is already built. So, the agents can start working within a matter of seconds.
The next thing we noticed is the the the roles of engineers are getting blurred.
We used to offer a DevPod per language flavor for Go, Java, Android, and so on.
Now, we need agents to work across repositories, and engineers also to work across repositories.
So, we have a Mega DevPod that has all of the repositories in one one common place. And this is what we use for our autonomous coding agents now.
And even for our non-engineer employees, we are providing a simple way for them to get started with any of the agent harnesses in matter of seconds.
Then now we get to knowledge part of it.
And we jumped on this bandwagon earlier this year.
We started noticing engineers building tons of skills across many repositories.
Um, and three problems we noticed was there's a lot of duplication, same skill being built by different engineers in different repos.
And discovery and configuration was a huge hassle, and a lot of skills were of subpar quality.
So, what we built an entire lifecycle around skills. So, we have core core skills and domain-specific skills.
All of that go into a managed skills marketplace.
We have 2,500 skills there right now.
Um, and it goes through whole bunch of linter checks, automated reviews, which ensures a baseline skill quality for any skills that we have.
And we also simplified the installation and discovery, so there is one single command to discover and install any plugin in our ecosystem. And based on the engineer personas, we even auto-install some of the default skills, so the agents automatically can pick up the right skill. You don't even have to even install them.
And of late, we started working on collecting traces and comments and capturing continuous evals so that we can go give feedback back to the skill authors for skill improvements.
And this is an area of big investment for us right now.
And we have 2,500 skills, and cumulatively more than 20,000 skill executions per day across our fleet.
The next piece of knowledge is context graphs.
Uh, we we started noticing in our execution traces agents spending a lot of time even trying to find basic context, especially in our large monorepos. You need to identify where the service is located, what are the dependencies, um who owns it, what kind of patterns I need to follow.
And all of this context is gathered across scattered systems across Uber. There's 20 to 30 different systems. Each needs its own skill skills, its own MCPs to to gather the context.
And this burns tokens. This adds a lot of latency, and it creates more unpredictable outcomes.
So, we have one context graph.
We took all of the information of how Uber runs into one context graph. This has 150 unique node and edge types. We have 40 million entries there right now.
It captures all the way from how our mobile apps are built to our back end, to our data lake, all the design docs, Jira, incident, bugs, everything is connected.
And this enables agents to quickly find the right context within our ecosystem.
We are now plugging all of our skills and use cases into the graph, whether it's our on-call RCAs, whether it's the planning, or data analysis, or security scans.
And we see across all of this they we are improving the skills by a lot.
And I'm just showing a very simple example of asking a simple question of how many mobility trips in India are are cash.
This needs to understand the concepts of each of these, which tables, what kind of CTEs you need to create for the sequel. With and without graph, we see massive improvement in tokens, turns, and latency.
And we see that across any early eval that we did within our infrastructure.
And the last thing is how do we package all of this for everyone in the company to use? So, we have uh our AI assistant called Cortana. All of the things that I mentioned so far, whether it's skills, MCPs, and context graph, they're all plugged into that in every surface possible, whether it's on Slack, CLI, web.
So, anyone in the company they can ask a simple question. It can look up the context graph, invoke any skill, check any code, check any code in any codebase, and give an answer across any of these surfaces.
And now we started allowing employees to even personalize that. You can hook up your custom skills, custom prompt, and hook it up into your team Slack channel, so that it it knows all of the things about that team and works like a the that teammate.
And this this is a simple example of how you can invoke the same question before in Slack, um and may all of the employ and and more like one or more people can even collaborate on the same Slack channel.
And we have like just in the last one month, 300 unique personas created, and more than 20,000 sessions per day.
I'll now pass on to Adam, who'll talk about how we take all of this and build uh take and ship a feature end to end.
All right, thank you, Uday.
All right, as Uday said, we've got those building blocks. We're going to use those to power our software factory. So we're going to take a feature here and show it going end to end through this.
All right, first up, right, we need to have an idea. Right, a good idea probably for this moment would be something around the World Cup.
Right, would it be awesome if you were a rider and you were leaving a busy stadium, if there was a better pickup location to get you away from the crowd?
So, that's the idea.
Right, we can have our idea. We're jamming on it in Slack here.
Let's tag in Cortana. Right, that's our AI assistant to help us with that idea. Cortana, with that context graph, can help us determine whether this is a good business opportunity to go after.
So, we can go here from Slack and now open Cortana into a web interface.
And you'll see an example here of what that business research could look like.
Right, what other large-scale venue events have happened before? What are some stadiums that would make sense here?
From there, we start to think about the product requirements. Right, this should be probably just a North America rollout since that's where the stadiums are.
We can even then bring in Cortana to help us think about uh the Figma designs. We can create some initial mockups.
Right, do two variants here. We want to run an experiment, A and B. So the the button strings here are different between the two. So, let's test those two variants and see which one performs better.
Now we'll start to think a little bit about the design, and Cortana, too, can help us think about what code changes would need to happen,
right, what can we leverage that's in the app already, what screens, and what can we leverage on the back end.
Right, so this process before could take a long time. It could take weeks to get everyone aligned. Now we can compress this into a very short amount of time now, right, and get to a prototype here very quickly.
All right, so now we got to go build this. So, we we hand off from that Cortana agent to what we have at Uber. We have a Minion agent. It's a Uber's cloud coding agent solution.
All right, so you can use Minion in an interactive mode or you can run it in an autonomous mode as well. So I'm going to show you what this looks like.
Um Uday mentioned the DevPod building block, so this is powered by that DevPod, so it's got a full build environment, and it can work across repos. So we're doing back-end changes and the front-end changes here, too, as well.
We're going to see Minion kind of progress here, and it's going to stop at just creating a draft PR. It's not going to push it to CI yet.
The reason being is that we were seeing um uh that this was great for doing like toil sort of workloads, but to build more advanced like end-to-end features, we really need to be able to validate the feature first. And we want to prevent a lot of extra load coming on to CI.
So, if we can validate sooner before we push to CI, that would be a big benefit.
So, that's what we're going to see here next on validation.
Right, in the SDLC we have an inner loop, we have the outer loop, of course.
We can have these be agentified where we're shifting more checks now to happen in this inner loop.
All right, so some of the checks that initially happened that we've had there previously is like the the static analysis sort of checks.
When those are detected, now we fix those.
Well, we can shift things to happen in the inner loop, things like visual validation.
So, we can launch on a simulator with a skill, grab a screenshot from the simulator, compare it to the Figma specs.
We can also bring up the service in our back-end staging environment, compare the front end and the back-end integration together.
So, now that we've moved a um now that we've done uh that part, um we move to the outer loop where CI uh typically happens. Errors can still happen on CI, right?
Uh so self-healing CI is something that we've implemented here, where we can fix a lot of the issues that you hit on CI.
Uh code review is another thing that happens in the outer loop, but this is another thing that we've shifted. We've moved parts of code review to happen in the inner loop. Right, the outer loop code review can have a powerful model use reasoning, a skill, to do a deeper review. And then the inner loop we can have a smaller model that runs uh faster with uh with uh with the medium model.
Now, another key thing here, right, is this if this is an autonomous diff coming from Minion, we want to give a human reviewer some confidence that this diff has gone through a lot of self-improvement already, right, that it's not just testing that initial generation that happened, but all these other steps have happened. And so on the PR, you will have a table attached that says all these different checks that it went through, including the screenshots.
All right, so we got a lot more code coming through the software factory now, right? Let's talk about maintenance, right? Maintenance is even more important.
Um what we have set up now is we can actually enroll our feature or skill into um our feature or serve uh service into maintenance uh skills.
So these are uh some examples of those skills that we have:
uh feature flag cleanup. Right, we had two variants of that World Cup uh modal.
Now that the the the B variant is no longer needed, we can have that scheduled on a loop.
So, the key thing here is that this is actually a managed loop that you go to, right? We don't want
thousands of loops being sent uh set up across the company without any bounds. You have a managed surface that you go to to set up the loop. So it runs on Sunday, when we know we have better uh CI capacity available.
Uh we also don't want to overwhelm engineers that Monday morning with a bunch of extra diffs. We want to control how many diffs they're seeing on Monday as well.
Another cool key thing here is that when that ski uh skill runs and makes those diffs, those diffs will get comments, and either get landed or not landed, that's all good labeled data that we can use to improve the skill itself.
And then at a kind of monthly cadence, we're looking to see what skills can we now learn um from in our incident reviews and turn those into new maintenance skills that we can apply to all of our services.
All right, so you've seen uh these parts of the SDLC that we have agentified. There's other parts, too, like monitoring.
Now you've seen the uh building blocks that you can use to power those, and the architecture underneath them.
One of the other things that we're really thinking about now is bottlenecks.
Right, we're now we're putting more strain on our infrastructure, so we're trying to anticipate where our CI capacity needs to be, and make the right foundational investments there.
There's only so many experiments that we can feasibly run as well, so that's another bottleneck.
Then lastly, too, right, decision-making, right? It's not about, you know, can we build? We know we can probably build it now. It's more of a question of, should we build it?
All right, so that's what we have for you today. And the next talk
is going to be actually from Uber as well. And if you want to learn more about our agentic code review, uh Ameya and Will will be presenting that next in this room.
Thank you.
