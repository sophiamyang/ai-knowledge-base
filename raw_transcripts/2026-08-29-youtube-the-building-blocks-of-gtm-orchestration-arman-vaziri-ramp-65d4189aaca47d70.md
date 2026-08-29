---
id: "65d4189aaca47d70"
title: "The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp raw transcript"
aliases:
  - "The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp raw transcript"
  - "The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=VjEP0xqTUI0"
origin: "https://www.youtube.com/watch?v=VjEP0xqTUI0"
type: "raw-transcript"
created: "2026-08-29"
---

# The Building Blocks of GTM Orchestration — Arman Vaziri, Ramp Raw Transcript

Yeah, really appreciate everybody showing up.
As mentioned, my name's Arman.
I lead our product and sales-led growth engineering teams at Ramp.
And today I'm going to talk to you about the building blocks of go-to-market orchestration.
And to kick it off, like what do I mean by go-to-market orchestration?
Effectively, like what we're building towards is the ability to just describe a motion, right?
Whether it's like playbooks or experiments or like evergreen campaigns that you want to run.
And how those get like distributed across the channels through which you actually execute your go-to-market, right?
Whether it's outbound or ads or web or whatever.
We want the ability to kind of describe this and automate that output.
And this really started a few years ago where we kind of noticed that there's a ton of great ideas.
You know, like everybody across product and data and engineering and go-to-market have like really good ideas for things that they want to do.
And the bottleneck is kind of like everything after that, right?
How do you go pull an audience to go and target?
How do you go and convince a bunch of people to like abide by whatever strategy that you've come up with, or playbooks, or enablement materials?
And we wanted to try to aim to reduce that coordination cost.
So there's parts of this where we could see it as like an engineering problem, even like a few years ago.
Just go and create like a consistent data substrate.
Go and like federate that across the different systems through which you run your go-to-market.
And obviously, in the last few years, agents have really like deepened our ability to go and like push the level of automation that you can do on behalf of operators, like as close as possible to those points of execution.
So like, really specifically, I'm a golfer.
Suppose I want to offer golfers at East Coast construction companies an incentive to like try Ramp, talk to sales, whatever.
And we want to be able to go and spin up an audience of golfers at East Coast construction companies.
Spin up like an incentive.
Let's go offer like some Pro V1 golf balls to these people.
Go create like outbound sequences, generate the copy, generate creative for paid ads and for web.
Maybe show some in-app notifications for your customers.
And do all of that seamlessly by just describing the intent, right?
And probably more than just this one sentence.
So a few years ago, we kind of identified a few fundamental challenges here.
As was previously mentioned, the necessary data for this was just messy, inconsistent across systems, right?
Everybody's operating off of a different source of truth.
And that makes it like effectively impossible to go and distribute some coordinated action across these different go-to-market teams and channels.
The next is that like reps were just buried in busywork, right?
Even if like you have the best intentions, "I want to go and like run this campaign.
I want your help doing it."
The reality is that like our sales teams are in back-to-back-to-back-to-back meetings all day.
They're outbounding.
They're selling.
And the operational burden of like doing everything in between sales was just really high, which made kind of like really scaling out experimentation and creativity challenging.
And similar to that, just the coordination and distribution are expensive, right?
If you're like have this idea, "I'm going to go write this like proposal, this enablement material.
I'm going to go try to like convince a bunch of people to go and use all this."
That's just like a really challenging thing to do on any like pace that's not on the order of like months.
So over the last few years, we've been trying to solve this problem from the ground up, right?
How can we start with that ingestion and consistency problem and data quality, which is just like, you know, on the road map every quarter.
How can we then go build those vertical efficiency and growth levers, saving people time in like managing operations and execution, as well as like how can we improve conversion rates, make people more performant by being able to kind of scale some of these more like informed and personalized and creative strategies?
And then how can we extend this horizontally, right?
Teams have very common workflows at some level, right?
Everybody wants to outbound.
Everybody has meetings.
How can we go take the patterns that we built for one team and start to just mirror it to others?
And now, kind of where we're at is like this distribution and coordination problem, right?
How can you go and execute across multiple channels simultaneously through just like the description of intent?
So yeah, I'll get into the building blocks.
Really broadly, go-to-market agents are complicated.
In order to do this effectively, right, your agents have to understand pretty much the entirety of your company, how you go to market, why products are useful, how to kind of like segment your buyers, your prospects, your customers, from people who have like never heard about you and you have like no information on them and they have no information on you, all the way to like customers who are actively using your products who have like a totally different set of problems that you have to work with.
And to just start to get a little technical here, we started with like this consistent data foundation problem.
And if you're looking at this and you're like, that looks like a CDP.
Yeah, you're right.
We effectively went and built an internal customer data platform at Ramp where we're effectively doing your very traditional things.
We're going to take CRM data, product data, enrichment data, web data, buying signals, you know, whether it's things that are internally modeled, like I don't know, we think that this customer has a high propensity to attach to procurement or treasury, all the way to things that are like external signals, like funding announcements, as well as like interaction data, right?
Emails, meetings, calls, page views.
And on the signal side of this, right, we have some set of real-time events that are coming in, things like emails.
You can go and pipe them onto a Kafka topic, consume them, and then funnel them back into both like we have like a Postgres database that backs all this.
It enables us to maintain like transactional guarantees, referential integrity between the entities that exist and the different entities that exist, right, between your CRM, between your product, between third parties, and attribute everything to the right level of detail, which we found to be like a pretty important problem, as well as all the associated metadata around capturing like where did this come from?
When did it, you know, come in?
As well as starting to embed a lot of this data, right?
So much sales data is just inherently unstructured, right?
You have like call transcripts.
You have emails.
You have notes.
And the ability to kind of search across that is really valuable.
We have a set of online batch jobs, which are really just calling a lot of APIs for the most part.
Ramp's addressable market is pretty much like the entire US and now expanding internationally.
So being able to kind of like precompute, preprocess, pre-ingest like all this enrichment data about who we can sell to and who we're already selling to is really important for us.
And then, as previously mentioned, a ton of work has gone into the offline piece of this with DBT, Snowflake, pulling everything into our warehouse, doing a lot of offline batch compute, and then piping that in via reverse CTL back into the same layer.
Next, more tactically, the way we tend to approach these problems is solve for one team first, then scale horizontally.
As I mentioned before, you have like a very overlapping set of problems that exist, right?
Everybody wants to do automated outbound.
Everybody wants to prepare for meetings, whereas certain teams may have like problems or like things that they do that are isolated to them, like QBR generation.
And to get into an example, like one of the things that we shipped is like pre-meeting briefs, right?
For AMs, AMs are like account account managers.
They kind of manage the customer relationships that exist, trying to ensure that customers are using Ramp as best as possible.
And there's a lot of like important context that goes into like a meeting, right?
It's like, what are we talking about?
Who are we meeting with?
What is the AM trying to do, like what are the product usage information, what are the account vitals, what's the agenda that we want to tackle?
And similarly, like what is the customer trying to do, right?
Do they have open tickets that they're trying to address?
Did they like email us saying that there was like a specific thing they're trying to talk about?
And how can we pull this together for AM so that they can go in prepared and kind of manage the operational piece of just being in back-to-back-to-back meetings all day?
Again, technically, the place to start with this is obviously if we're trying to generate a pre-meeting brief, we need to know when these meetings are so we can pipe in meeting events, do some hydration, map things like attendee emails, meeting titles back to the accounts that we're meeting with.
This is like a sneaky hard problem at Ramp because you have the same emails that can work on behalf of multiple businesses.
So it's kind of like a fuzzy match, and we can go and persist that.
So that way, every downstream consumer of like, "Hey, I care about this meeting," doesn't have to go and like recompute this from the ground up.
And also as mentioned in the previous talk, we've also built a system around durable execution, right?
That's pretty agnostic to the trigger that comes in.
Everything is represented as a durable thread built around Temporal representing each tool call and model call as an activity.
That way if, you know, like a worker goes out for some reason, it can resume execution from where it left off, pulling together all the state that it had accumulated at that point in time instead of starting back from like the beginning of the thread and trying to reprocess everything, which would be very inefficient and slow.
There's also like great out-of-the-box capabilities for things like config-scoped tool calls.
Different agents are going to have access to different sets of tools, which give them access to different information, different integrations, and different skills that might be necessary to actually perform the work.
And similarly, there's things like human-in-the-loop tooling to just pause execution, get input, resume.
And then getting to the unstructured piece of this, as I mentioned, like unstructured information is probably like the most valuable thing you're sitting on within your warehouse, or your notes, or wherever you store this today.
So we have some set of real-time data coming in, meeting transcripts, emails.
We have some set of like batch jobs that are kind of pulling in like enablement materials, product knowledge, playbooks, chunking them, embedding them, putting them in Turbopuffer.
And it allows you to kind of, or allows agents to go and search like, "What do I care about?
What am I trying to answer right now?"
and doing some combination of like a vector search, attribute search, keyword search in order to pull information scoped to like a specific account, for example, without having to pull in like the full raw corpus into agent context, which would also be very inefficient, very expensive.
And similarly, we've gone and built a skill library to allow people to customize their agents, right?
Getting back to the meeting brief example, different people have different formats that they care about.
They have different information that they care about.
And allowing them to kind of represent that in text, giving that to the agent to pull it together has been like very valuable for getting adoption.
And putting all this together, you get an operational background agent, right?
You have like every night we're going to go and generate these things, fan out a set of agents that are going to go and compute per account meeting prep, which gives, or which used some set of tools giving them access to like that online CDP in Postgres I had mentioned, the vector database, meeting prep skills that we own at a system level, as well as like custom instructions that users are providing themselves.
And getting into the extending the blocks, the goal is for these foundations to speed up the next thing, right?
Meetings are super important.
We want to be able to generate things like post-meeting follow-ups and things like automatic CRM updates, right?
Which can pull in the transcript and say like, "Hey, we discussed this potential expansion opportunity.
Let me go and pre-fill all the information needed to create that opportunity.
Get a thumbs-up from a rep, and just make it happen."
And similarly, we want to extend it horizontally to other teams, right, which is mainly an exercise of creating specific skills, data integrations, and like just data ingestion itself, where we can say like, "Okay, email, call transcript embeddings, custom instructions, generalizable.
But if we're building this for AEs who are hand- handling like pre-sales opportunities, we need to go and focus more on like third-party data instead of a bunch of product data that we have already."
And that needs to be incorporated into our customer data platform.
The skills need to go and reference kind of like a different set of information that we have on the people that we're trying to sell to.
And similarly, we've built this in a way where employees have access to the same tools and skills that are being used for the background agents that we're creating, right?
We set up a what we call like our GTM MCP.
And this is basically just like a window into the same exact tools that we've set up for these background agents.
So that way, the things that we build are just kind of automatically federated out to people who want to go and build their own agents.
They want to go chat with the information that we're setting up and build their own automations.
And they're building a ton of them.
This is just like a glimpse into some of the analytics that we've done taking the reasoning generated by the MCP tool calls, you know, that we've that are being executed remotely.
And this compounds because like when people go and build their own thing and they go and connect to our MCP, they're basically telling us like, "Here's a problem that I have.
Here's how I'm trying to solve this problem."
And we can go and work with them to be like, "Okay, we can just go and productionize this, distribute this to everybody who probably has similar problems."
And they give us the prompts, and the skills, and the like, you know, even applications that they're vibe coding, to just like really simplify our ability to just go and productionize like these use cases.
So now you're probably wondering, what about that golf example that I had mentioned at the beginning, the orchestration problem?
The the point that I'm trying to convey by talking about all these specific things that we're doing is that these vertical builds that we're creating are the foundation of like multi-team, multi-channel, like distribution.
If we want to be able to say like, "Here's a playbook.
Here's how you sell procurement.
Here's how you sell to construction."
Or, "Here are like wacky experiment ideas that we have," like offering Pro V1s to golfers, which is actually like It works really well.
We need to be able to say like take in that corpus of information of things that people are trying to do, and federate that out through the background agents that are actually creating these artifacts that people are like using to operationalize like go-to-market and execute.
So for my Pro V1 golf example, the goal is to funnel this into Ramp Revenue, the internal application that we have built, and go and like effectively like funnel this into some of these vertical solutions that we've created, right?
So you can say like, for SDRs, we want to go and create an audience of here are the golfers that we want to send things to.
We can go and generate like personalized copy and sequences that they can go and send.
Maybe we want to go and create web landing pages and spin up the images and the creative that will point these email sequences to.
And we can do all that through just like the description of like, "Here's my intent."
Get the people who own these channels to review them and sign off.
And really allow us to just like move a lot quicker in how we ship and like scale creatively across all these different go-to-market channels.
So the goal of this is to ship faster, ship safer, scale our teams, become more efficient.
And with these campaigns, we can go and execute them across like multiple channels with consistent audience targeting.
Agents can go and hold context on multiple things that are like options, right?
We can go and execute this campaign or that campaign or that experiment, and balance the like traditional multi-armed bandit problem of like exploring like new possibilities versus like being safe and like going into just known returns.
And then we can build in guardrails as well to go and effectively like manage compliance rules, rules of engagement, being context-aware, making sure we're not doing the same thing over and over again.
And yeah, just do this on behalf of everybody.
And those are the building blocks of go-to-market orchestration.
Thank you, everybody.
We have probably time for one question.
Hey, there we go.
Hey.
So, just curious, how would you approach building something like this for a smaller company, or for a company that's that's just getting started?
Yeah.
I think a few people before have like mentioned something similar, but I would go and like find the very specific use cases that you can build automation around, and just like solve really specific problems that exist first.
Like three years ago, there was two of us, and we were building like automated outbound, right?
So like we were just trying to figure out like how can we go and use GPT-3.5 and like put personalized copy into some sequences and go and like pull data from wherever to go and generate that.
And by doing these things and solving these problems, you get like a really good understanding of how this works, how it could extend to other teams.
And solving like real problems as you go, the reality is that like you can't spend like a year going and building like some really complicated system architecture that like is perfect.
So you have to like piece together the vertical solutions, and then stick them together.
