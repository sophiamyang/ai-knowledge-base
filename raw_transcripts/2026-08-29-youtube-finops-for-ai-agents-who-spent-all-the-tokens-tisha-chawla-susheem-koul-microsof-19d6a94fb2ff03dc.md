---
id: "19d6a94fb2ff03dc"
title: "FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft raw transcript"
aliases:
  - "FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft raw transcript"
  - "FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=GJX19pNhmSw"
origin: "https://www.youtube.com/watch?v=GJX19pNhmSw"
type: "raw-transcript"
created: "2026-08-29"
---

# FinOps for AI Agents: Who Spent All the Tokens? — Tisha Chawla & Susheem Koul, Microsoft Raw Transcript

Okay, good morning everyone.
So, I'm Tisha, and I have Susheem with me as my co-presenter.
All right, so we'll be talking about the most expensive question in AI today.
I think a lot of you would have come across the scenario that, you know, when you opened an AI bill like through your agentic workflows, you couldn't actually trace back where that bill was actually coming from, right?
And and I don't think that's the problem right now because right now the industry is valuing, you know, token maxing, that is like spending the most amount of tokens for exploration, for all of those purposes.
And people are proud to call themselves token billionaires, and I think that's all right.
But this talk is, you know, the shift from token maxing to value maxing.
You know, how do we get there?
And we'll talk about it from this question, who spent all the tokens?
And if anybody has spent all the tokens, there has to be value associated with this, right?
And that is the talk about.

All right, now in order to minimize the gap, you know, from token maxing to value maxing, we'll kind of see we'll observe the patterns which the like the existing like the past software evolution eras had.
Like for instance, when we talk about the SaaS era, the interface was UI, and the control was in the form of usage caps, right?
Like the seat limits or tier-based policies.
Now, when we moved on to the cloud era, the control surface again changed.
The model became pay-as-you-go, and the control moved like in the form of auto-provisioning and, you know, auto-scaling policies.
Now we are in the agentic era, right?
And now how the cost is calculated here is in the form of model calls, right?
Like how like the code calls your model.
But what we've observed is that there isn't a proper control plane in place for that.
Like we do have control plane in place for in place as model gateways where there are hard caps, or there is model routing to downgrade the model, but the part like the where the code, you know, calls the model, that is what we'll be talking about today.
And we also, you know, see like in the last year, we've seen a lot of unbounded consumption happening.
Like if you've read the news, there was news about the like the AI budget for Uber getting exhausted within four months, and there were companies whose like who ran into, you know, like hundreds of millions of dollars within just months or days, and like there were a lot of like other news in place as well where like these runaway loops led to a very like massive increase in the cost, and there wasn't proper mechanisms to control it.

So, when we see all of this, the first thing that comes to our mind is, is there a tool, or is there a product to save us?
But we'll instead talk about the first principles of how, you know, we can design a system which is actually true enough to solve the problem from the very root.
So for that, let's like dive onto the principles.
First of all, let's talk about token being the unit of cost.
Right, we are charged in terms of token.
So, the now we have to see value also in terms of token, right?
Next, we all know that cost is created at the LLM like the model call boundary.
So, that is what we'll have to track.
And if we don't have proper attribution, like if we don't know what agent, what run made that particular call, we we can't, you know, control it, right?
We we just know the like the broad picture of what went wrong, but we don't we can't, you know, trace it back or narrow it down.
So that is why attribution is a very important element to have.
And like once you know which particular run or which particular agent is actually, you know, attributing to the cost, you should have proper policies in place to actually stop it.
Like let's take an example that if you have a, you know, a loop which is, you know, running very excessively and which is not required, or, you know, if your context is growing very out of range, you should have in-place policies which can like solve that particular thing there and there instead of halting that.
And if and as the last resort only, a like a halting or a should happen from a budget cap.
So these are the first principles.
Now let's see how we can, you know, define an ideal platform on top of that from these principles which we talked about.

All right, so one thing which is very important and which matters here is that when we talk about like the existing frameworks for TokenOps or for token management, most of them are at the like basically monitor the model request.
They like they are like model gateways which will, you know, basically do like model routing or hard budget capping.
But what we need right now is something which, you know, like monitors you at the run instead.
Like if you see, we need something which can control the loop between like the agent call, between the tool and the agent.
Something, you know, which can see or control the the spawning of multiple sub-agents happening from the one main agent or like something which can control the growing of context.
So like that is the need of the hour, right?
And that is what we need.
So for all of this, we like kind of are proposing a platform which, first of all, has a cumulative budget across like the like the attribution runs which happened and then where enforcement actually happens in call path rather than, you know, a separate thing.
Like for example, if something goes wrong, if your like if your context is just growing heavily, then like in-place compaction should happen, or like in-place caching, or something like that should happen.
And after that, if like after basically exhausting the list of all in-place policies, only like the the budget cap halt should happen at the very last.
So that is something which we are proposing.
But if we look at the landscape today, if you see the like the tools like this LiteLLM, Portkey, Cloudflare, all of those, they happen at again the request level, right?
Like if you see, like halting is there, routing is there for some of those, but all of this again is at the request, and you can't control the cost at the request layer at the model layer, right?
So this is the missing piece which is, you know, the basically navigating it at the, you know, the model the agent run layer.

So for that, we have TokenOps, which is a, you know, a run-aware token governance for AI agents.
And this is the architecture for that.
So, first of all, one thing I would want to highlight is the like the intentional design decision we took here was an out-of-bound plane.
So it doesn't interfere with your code at all.
So, if you see here, that out-of-the-band plane has three modules which I'll be talking about.
The first one being instrumentation.
It is a common observability layer where, you know, you'll like have like the basic telemetry, the OpenTelemetry, the cost in microns, and like the like the like enrichment layer, and basically the attribution, like what caused that like particular run.
And then there is, obviously, accounting where you'll basically accumulate it in a kind of a ledger.
Like the total runs which are happening.
And finally, we have this enforce layer which has two main purposes.
One is steering it through the policies which we've defined, which I think Susheem will cover later.
And then we have halt in place as the, you know, final like like final thing if, you know, your budget is getting exhausted.
So yeah, that is there.
Now when we again look at the landscape, this kind of will solve a lot of problems which kind of happened when we like look at the previous tools, the products there, because it is at happening at run, and it is, you know, helping you solve the problem from the very root by steering it in place.
All right, so with this, I would like to hand it over to Susheem for the demo.
Yeah.

Oh yeah. Now I think I should be audible.
Everyone in the back can hear me?
All right, perfect.
So yeah, we have established the principles behind TokenOps till now, right?
Now let's shift gears, talk about the design part of it, and maybe get into the code and eventual demo, right?
So, what I have behind me on the screen is the like bird's-eye view of what TokenOps looks like today.
It's it's three layers.
We'll go left to right and top to bottom.
So on the leftmost, you have your own agent runtime which you're trying to instrument and kind of manage the cost for, right?
The middle layer is what we're calling the bridge that basically shuffles data between your agent and the control plane.
And the control plane is where the mind of the system lies, right?
So let's talk about the bridge layer very briefly.
If we go from top to bottom, you have the attribution on top.
So, what we're trying to do here is every agent run that you do, it's attributed to some user dimensions.
So the idea is everything that you do, every run of the agent is accounted to some usability or some usage.
This comes in handy later. We'll talk about it.
The second part, which is the boundary annotation that you see, this is pretty much the heart and soul of this middle layer.
So the idea behind the boundary annotation is that you take any method—it doesn't matter what framework you're using. You might be using, let's say LangChain, LangSmith, whatever—if you have a method, you can annotate it with boundary.
What this annotation is going to do is it's going to do two things.
First, it's going to track the input and the output, and it's going to flight that up to the control layer and record it there as a ledger entry.
Now this will be annotated with the further agent run ID and the other attributes and so on.
The second thing the boundary annotation does is it acts as a channel through which the control plane can push actions down to the agent.
This is where the intel intelligence lies.
So, we do not have a single directional highway.
We want the control plane to be able to tweak the behavior of the agent on the fly to ensure that we are able to squeeze in more runs inside our budget cap, right?
Now let's say the control plane pushes down an action.
Let's take a small example.
Let's say you have a RAG retrieval tool which is generating like 20 chunks every retrieval for every call, and that's eating up eating up your budget.
And let's say the LLM is not even using the chunks that are after five because they're just not relevant, right? They're sorted by relevance.
So let's say the control plane observes this, and it wants to limit the output to just five chunks.
So it can push down an action, but that action has to be received by boundary and then has to be executed by something.
That is where the third node, the governor node, comes in.
The governor knows what actions are allowed on your agent by you as a developer, and it receives those actions from the control plane and knows how to apply it in a non-destructive way.
So, that's the first three.
The fourth one, wrap the wrap complete, is essentially just a helper method.
So, as we know, most of the agent providers or the model providers, they provide objects rather than methods for their LLMs, right?
So wrap complete is just another way of applying boundary on objects rather than methods.
Let's shift right to the control plane.
On the control plane, the first layer is the segment.
Now, this is where the attribution that we talked about earlier comes into picture.
So, any dimensions that you float from the attribution layer, let's say you have a preview agent that you share with everyone in this room, and your agent is floating a dimension saying that cohort is AI 2026, right?
So you can create a segment, which is a cohort of users which is based on this tag, like dimension being AI 2026, right?
And you can apply your budgets at this cohort level.
So you don't necessarily have to restrict everything at an agent level or a run level.
You can do you can do rollups. You can do fine-grain or coarse-grain control, right?
So, that's the segmentation part of it.
Ledger, as I mentioned, is just one agent run, all the traces in one place.
Then you have budgets. Budgets are basically just the static thresholds that work across a time window against a particular segment or an agent run.
And then you have actions.
So on the actions part, we have broadly two flavors.
First is the halt-type actions, which basically just kill your agent if it exceeds a budget.
The second part, where we are adding value, is the steer-type actions.
So here we do not kill the agent.
Instead, we try to steer the behavior of the agent or the components of the agent to try and fit that particular run within the allotted budget, right?
And then the policies layer is where it all comes together.
You basically group the budgets, the actions, and then set your policies against certain segments or agent runs, and that is where it executes, right?

So moving on, what changes in your code?
That is the boundary annotation that we just talked about.
As Tisha mentioned earlier, this is all out of band, so you do not have to change your code. You just have to apply the annotation on the methods that you have.
This boundary annotation will take care of floating all the information up to the control plane.
And the control plane lies in your own tenant, so you do not need to worry about any data leaks or anything.
Then if I talk about the governor, so for the governor, you just have to create an instance. You just have to pass it your own configs.
These configs will basically declare what sort of actions are allowed for those agents, right?
So that your control plane cannot just willy-nilly do any random things on your app on your agents.

So, before we move on to the demo, I'll just briefly touch upon the test bench that we're going to use today.
So it's a simple two-agent workflow.
We have a research agent which has access to a search tool.
You give it a question. It's allowed to look up on the web as many times as it wants, and once it knows that it has all the data, it passes the findings onto the second agent, which is a summarizer, which create is creates a research report, right?
So with that out of the way, let's just quickly walk over to the demo.

So for the demo, we have three different scenarios that we're going to talk about.
For the first one, we're going to run the TokenOps in what we call preview mode.
So, in preview mode, what happens is that all the policies run as is, but the enforcement doesn't happen.
So if you see, we ran a particular run over here, which completed, but we did not see any sort of failures here.
The policies executed, but the actions that were associated with those policies were not allowed to be executed.
So we're just going to load the dashboard screen here.
Yeah. So this is the governance output.
Governance is off. The run completed.
But in the dashboard, you can see the policies have executed.
So you can see the cost budget, the cost guard, and so on, right?
So this was the first scenario.
For the second scenario, what we're going to do is we're going to turn on the governance now.
While that is happening, I just want to touch upon why this is important.
So if you want to like include this product into your production agents, you want to have a safe environment or a safe way to firstly put it in your production environment, test the guardrails, tweak the guardrails, see what the policies are doing, and then finalize the thresholds, right?
So this is the second one, where we have now enforced the governance, and you can see in the dashboard that the precall cost cap has exceeded.
So you had a budget allotted for this run, but the agent exceeded the budget, and it was killed immediately.
So that's the simple circuit breaker sort of a methodology.
So this is the halt behavior.
And now let's see the steer behavior, which is the which is where we are trying to add value to this entire cost management scenario.
So this time we're going to run the the second prompt.
The budget allotted for this one is slightly higher, but it's still not high enough for the agent to complete in time.
So what instead happens is there is something called cost guard which kicks in.
This cost guard, it takes into account two things.
First, how much of your allotted budget have you consumed?
Second, what is the velocity at which you are consuming tokens?
Now based on these two things, if it predicts that you're going to run out of your tokens or your allotted budget by the end of the run, it's going to inject something into your system instructions.
That something could be as simple as, "Hey, you are running running out of budget, so make sure that the LLM outputs are more succinct or more summarized," right?
So that is the way we are doing the steering.

Now this was a very simple test bench to show you like how this works on a like working code.
We have also benchmarked it on a couple of open source repos.
So we have benchmarked it on browser-use as well as MetaGPT.
We ran it across multiple iterations, across stress tests, across simple scenarios, hard scenarios, and everything.
And the results we see are the average spend goes down by almost 78% with TokenOps enabled with the full policy suite that we have today.
On the completion part, when we compare it with throttling, just simple throttling, your simple throttling is going to kill your agent runs, no matter what, right?
So with the reduced average spend, what you get is you get an uplift in that completion percentage from 67% to roughly 96%.
So that is the value add that TokenOps is doing here.

Now this is the policy catalog that we run this benchmark against. This is what we support today.
We kind of researched what are the different failure modes that are there today out in the wild and tried to cover most of them here.
So you have things across spend management, you have things across context management like context compaction, tool output reduction, you have things across loop detection and progress detection and stuff like that.
So this is the entire set of policies that we support.
And at the bottom, you can see the actions.
So as I mentioned earlier, we have two flavors.
You have the the the halt-type actions and then the steer-type actions.
So for the steer, we can do allow, mutate, inject, and so on.
And for the halt, it can be a simple kill.
But this is not the end state that we envision for this.
The end state is we have a lot of data, right?
We have a ledger that is continuously being updated.
So what we want to try is we want to try a self-learning module within the TokenOps plane, within the control plane, which can look at this ledger and ask this question, "Hey, why or what is the failure mode that I'm still not able to catch?"
And then based on that, it can do two things.
One is it can enhance. It can generate new policies on the fly based on the missing or the still runaway costs.
Or it can refine the existing parameters for the existing policies that are there so that the runaway costs are managed more effectively in the future.

So with that, I think that is all we have for you guys today.
Thank you so much for your time.
And you can scan this QR code. That's the public wiki.
We are updating it almost regularly.
So you can scan this and stay up to date.
And Tisha and I are around, so if you guys have any questions, or if you want to discuss more about it, just let us know.
That's it.
Thank you.
