---
id: "1202d499891d355f"
title: "AI in GTM at Notion — Flora Liu raw transcript"
aliases:
  - "AI in GTM at Notion — Flora Liu raw transcript"
  - "AI in GTM at Notion — Flora Liu"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=L4I7WgiEquo"
origin: "https://www.youtube.com/watch?v=L4I7WgiEquo"
type: "raw-transcript"
created: "2026-08-29"
---

# AI in GTM at Notion — Flora Liu Raw Transcript

Well, first of all, hi, everyone.
I'm an engineer on the product growth team at Notion, and now working on the GTM engineering team.
A year ago, I would have told you that building a GTM system was a marketing ops problem, and today I think it's one of the most interesting distributed systems problems that I've worked on.
GTM at most companies involve a spiderweb of tools, like what you see here, and they're stitched together by customer notes, proposals, contracts that are passed back and forth.
Over the last few months, a small team and myself, we've been trying to turn this spiderweb into a unified GTM system.
We're still in the midst of it, but we've learned a ton that I'd like to share with you today.
So, this isn't really a new problem.
We've been wrestling with pieces of it for years: lifecycle messaging, product recommendations, sales automations, customer data, and onboarding.
But the solutions were fragmented because the underlying technology forced them to be.
Then over the winter break, our CEO, Ivan, built spent it building a video game, and he came back convinced that software engineering could be applied to many problems that were previously unwieldy or too costly.
At the same time, our ability to execute skyrocketed with agentic technology, and the breath of problems we could solve did too.
The costly, time-consuming, and previously unsolvable spaghetti could now be sorted.
So, what we found is that GTM had become a systems problem.
That made us realize we could chip away at this holistically.
In case you don't know, Notion's platform is a collaborative brain for human and agents to think together.
Over the years, we've evolved into a context layer for your company, and AI agents can act on it.
Notion's business moves between self-serve growth and sales assist, and customers move between these two motions all the time.
The problem is that customers experience one journey, but internally, it is supported by disconnected systems that don't actually talk to each other very well.
These processes were rife with human error and put a lot of cognitive burden on our teams.
For example, sales reps are probably not the strongest at managing systems, but their strength is in sussing out human signals during the buying process.
So, every time they had to context-switch between after a call, doing research, drafting follow-up, they were spending less time with our customers and customer problems.
Most companies have separate systems for sales assist and product-led growth.
And this is actually also true for us.
Marketing run runs on one set of tools, sales on another, customer ops on a third, but all of them are looking at a customer independently and making decisions separately.
So, what we set out to build is a single decisioning system that spans self-serve growth and sales assist, and it can help the customer decide the next step so that everything is cohesive.
Our vision is for this system to be programmable, proactive, and continuous.
When we started, we were faced with some challenges.
There were so no single source of truth, so customer data was spread across Salesforce, Gong, Outreach, ZoomInfo, and many more.
Product usage lived in Snowflake.
And a decade of the most important context lived in notes in meeting docs.
Yes, our sales reps do use Notion for that, too.
Notion employees were actually actively using MCPs and their own agents to solve problems already.
But they were innovating within their own departments.
So, it was single-player mode or, you could say here, single-department mode.
Marketing built tools for tool uh marketing, sales built tools for sales, and each tool served a tiny slice of that customer journey.
And it would make it really hard to create something that was more holistic.
When we tried to automate across all of that, we hit some roadblocks.
First, data quality.
Conflicting systems of records, wrong contacts tied to different accounts, one bad mapping was enough to lose trust for sales rep.
Secondly, data latency.
Every vendor added a hop, and this lag was causing us to act on stale data, and that meant we were automating on yesterday's world.
Third, and this is a big one, structured and unstructured data.
The most important facts about a customer were left in notes, like that champion just left, or don't contact this customer again, um or they're blocked on legal.
And so these are exactly the types of notes that helped sales reps move forward and decide what to do next.
And if an automation couldn't see it or process it, it could do something catastrophically wrong.
So, our project team consisted of CX, RevOps, product, engineering, sales.
And after brainstorming together, we all kept finding the same patterns underneath that complexity.
Whoops! Oh.
Every workflow could be reduced to four questions: What do we know about the customer?
What should happen next?
How do we execute that safely?
And did it work?
That became our architecture.
So, the system has four layers:
Know: a context layer we can trust about every customer.
Decide: choose the single next-best step for them.
Third, fire act and fire a concrete action that could be a lifecycle email, um an in-app nudge, or a task handed to a rep.
And then learn: watch what happened and feed it back into the decisioning so that it's a loop.
But this architecture is mi- missing something important.
The most important part is that humans and agents are operating on the same loop.
Concretely, this means that the context needs to be displayed so that humans and agents can read and operate on it together.
So, you can see that they're working in the same system, but they might have different roles.
Agents do the repetitive work at scale, like gathering context, researching, drafting recommendations, and writing artifacts.
Humans provide the judgment, adding nuance, deciding what to do next and if a recommendation is correct, and owning the customer relationship.
We found that instead of building an AI layer on top of our business, we designed our architecture so that the agent can operate as another operator within the same system as humans.
Before we built the system, we made some choices about how we were going to implement this.
Firstly, we deliberately chose not to let an agent talk directly to a customer.
For sales-assist workflows, humans stay in the loop by default and approve anything the agents do.
The agents do the busy work.
That decision that decision also has a security dimension, too.
If a prospect fills out a Contact Sales form online, we treat that as untrusted user input.
And so trust boundaries don't break down, especially because there's an agent in the middle.
Secondly, routing and eligibility became a first-class primitive.
Eligibility used to be scattered in all over the place.
We had one check or rule in an email tool, another in sales, and we pulled that all into one place so that these rules can be consumed across our codebase, uh product, sales, engineering, and these are like customer segmentations or signal signal definitions.
And then a single classifier will route what the customer should do, and this will actually prevent double sends from our system and create very cohesive communication across.
And last but not least, we decided that it was very important to own the context layer, and we decided to rent everything else.
Since we are a lean team, we will not build our own email vendor or enrichment services like Clay.
We use Clay.
And we believe that we understood our customers the best, so we will not um give that away.
So, let's get into what we built.
The first step was to gather a consolidated view of all of our customers.
Snowflake, which is our data warehouse, is where we compute this truth.
We ingest data from all the vendors in our GTM stack to Snowflake.
We run daily transforms, and in some cases real-time, to produce a small set of modeled, versioned entities, and these are accounts, contacts, workspaces, eligibility, and facts.
And this also has clear ownership of what teams or uh tools they come from, and like timestamps.
DynamoDB is our key-value store, and it's where we compute our truth or serve our truth.
We publish a denormalized key-addressable profile that agents can quickly query in milliseconds with no joins.
We also persist agent uh persisted uh or generated artifacts, and these are research snippets, summarized notes, rolling summaries, and these unstructured data are also keyed by the same IDs so that downstream systems can read all of this in one shot.
So, this data was normalized, and, of course, we brought it into Notion so that we could work with structured and unstructured data at the same time.
So, some of the data I showed you in the boxes earlier, there's like product usage data, there's activity log from across our vendor stack, and then we also have like unstructured data that, like I mentioned, that is most important for sales context with research reports and notes.
And this turned out to be powerful for two reasons.
First, our internal GTM teams didn't need to jump between many tools anymore.
They could use Notion itself, a tool they were already using, to explore context, investigate investigate accounts, answer questions, and they could even take actions like sending to Nooks or um sending to Outreach.
This is a tool that they were very familiar with, and they didn't need to open seven tabs anymore.
Secondly, because we weren't building an AI layer, um humans, workflows, and agents could all operate on the same source of truth.
In a very literal sense, we are using Notion to grow Notion.
The next primitive we decided that we needed was a way to turn customer events into actions.
The unit here is a signal.
A signal is a single customer event that's important enough to change what should happen next for a customer.
Some are user-driven, like a customer hitting their AI limit or maybe they reached out to contact Contact Sales.
But some of them are not user-initiated at all, which are these external signal examples I listed here, like company raising funding, hiring signals, or a shift in their tech stack.
Those external signals are what allowed us to be proactive instead of reactive.
So, this is the signal service that watches the customer profile, decides whether a single action is available, decides who should own that action, and then it emits a concrete task following the architecture I described before.
And this task could be for a human or an agent.
If there's a task for a sales rep, that actually just lands in their Notion database, and they can quickly view it and act on it.
What's What's interesting about the way we build our GTM systems is that if there is no signal about a customer, the marketing component of our system kicks in.
We have a predictive engine that will recommend product features most relevant for that customer.
And it will send out lifecycle emails, and in-app nudges, or multi-channel communication to drive a customer towards adoption automatically.
So, diving deep into a small slice of what happens when we decide what action should be emitted, um this is for like the sales workflow, and we shadowed our best reps to capture something that was the most repetitive part of their job and encoded it as a durable multi-agent workflow.
Every signal becomes a workflow on Temporal, which is something we rent, and a single run will touch enrichment, web search, draft generation, and more.
Each of these is a network call that could fail or rate limit.
And so Temporal lets us focus on writing the sequential logic for our GTM use cases while it will handle the retries, dedupes, um and handling, and going back to exactly where failures left off.
And one malformed transcript can't take down the whole batch, which was really important to us.
So, an example of a cold outbound signal for us, we'll have a research sub-agent do concurrent web researches, then it'll draft like an email, and those emails uh there should be three of them, so they're scored.
And then a review agent will pick the highest scoring one and make any updates if necessary.
And this also operates on a loop, um so that the email drafts are improved.
And then when it's ready, this email draft will land in the sales task that is available for for them to act on.
Um for more reactive signals, after a follow-up call, the Gong transcript will come in.
Our agent will parse the transcript and then, um again, it will extract the critical sales MEDDPICC data: uh metrics, economic buyer, decision criteria, plan, and champion, and draft a grounded follow-up for that.
Every LLM step is traced so that we can evaluate quality and improve over time.
The third layer is what turns this automation into a system that self-improves.
Every action is a decision log, and every outcome threads back to the decision that caused it.
So, the naive version of this is a data analyst coming in and trying to understand if the output of this could be better.
The rebuilt version of this is wiring our engagement history back into the decision layer so that the system decides whether or not to continue a thread, advance to the next step, or pivot.
The system will continue to do that with the lifecycle message performance history as well.
So, these verification loops are really critical so that the system can self-heal and continuously improve.
Let's see how an agent and human work together in this shared customer view.
In the customer view, a rep can come here and see the product usage, the recent activity, and get an answer using that same data.
They used to find all of this across many different tabs, and now they can just come here each day.
The rep can ask an agent, and the agent will reply uh querying our context layer.
We can also use Notion custom agents, which are shareable across companies, to access this data context for recurring automated workflows.
In the task view, a rep starts their day with their in an already prioritized task box, and they already know how to move forward with accounts and contacts.
And then email draft for an outreach task is already pre-researched and available for them to review.
The human is still in the loop and actually adds their own judgment and taste, um and sales secret sauce, but they're no longer starting from a blank state slate.
And this does more than one help one rep be productive.
Um our goal is actually to raise the floor for the entire team.
So, a new sales rep coming in, they can learn the Notion sales process, understand what signals are important to look for, um understand which playbooks are effective, and basically know what good follow-up looks like.
Reps who can are ramping can still learn from the patterns of the strongest reps without needing every lesson to be passed down manually.
So, one of the questions that we came across along every step of the way is a classic question: Do we build or buy?
And it's very tempting and trendy to say, "Build everything."
But what we've found is that there are still key areas to build and rent access to at every single layer.
Internal agents are actually cheaper and faster to build than most people assume.
And so since we have the most data on our on our data model, uh we builded there first, and then we uh rented the generalizable parts later.
So, for us, the build versus buy is a per-layer decision.
We will not build a lot of these tools, like orchestration, email, CRM.
Um vendors do that really well.
We refuse to outsource the context layer because that's where our edge is.
A generic tool can't capture all of our esoteric data models or workflows, and we do not want that context layer to be something we can't um debug.
And so, as I mentioned before, that context layer is in Notion.
It's built off of plain markdown, a language that agents are fluent in, and we have databases and hierarchies that they can navigate easily.
At the same time, this is well-designed for human, um so this is what lets our engineers, agents, and GTM work off the same context.
And this has all the data synced across sources.
Ultimately, the reason to see if we can do all of this is to see if we could get a better throughput on deals.
It's very early for us.
We're still building this out, but the initial signs are promising.
In the last 13 weeks, we are already seeing enterprise reps have increased qualification or qualified opportunities.
And on the lifecycle marketing side, users who received context-aware recommendations were 63% more likely to take the next step.
This is the early days with a lot more features we want to build, but our thesis that a building a single system on know, decide, act, and learn seems to be right so far.
A few key takeaways um from entering entering this world as an engineer in the last 6 months is that before you build, shadow your best human.
I talked to many sales reps, and when I opened uh when they opened their computers, I saw how many tabs and tools they were navigating between.
And that was a chaos, but it was also the spec.
And so if you encode a mediocre process, you get a mediocre agent.
Start with the most legible workflow.
That's the one that's documented and repeated, and let humans stay in the loop on where there are risky possibilities.
Model GTM as primitives: entities, context, triggers, actions, eligibility rules, and the alien world becomes a system you can engineer.
Last but not least, be headless by default, design for agents as operators, and not just copilots.
If humans and agents can't read from the same substrate, you're basically building two systems that will eventually drift apart.
For us, that layer is Notion.
Right now, humans are the primary consumer of GTM data, and agents are helping at the edges.
Soon, agents will become primary, first-class consumers within the system, moving from drafting to acting within guardrails.
By creating the best context and substrate for humans and agents to collaborate together now, you're setting up your team to sprint faster.
Um yeah, and feel free to contact me if you guys want to ask more questions.
