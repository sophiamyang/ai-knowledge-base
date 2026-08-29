---
id: "14e64dc354c183e0"
title: "GTM Engineering: The Technical Bits — Everett Berry, Clay raw transcript"
aliases:
  - "GTM Engineering: The Technical Bits — Everett Berry, Clay raw transcript"
  - "GTM Engineering: The Technical Bits — Everett Berry, Clay"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=UhCY231d0FQ"
origin: "https://www.youtube.com/watch?v=UhCY231d0FQ"
type: "raw-transcript"
created: "2026-08-29"
---

# GTM Engineering: The Technical Bits — Everett Berry, Clay Raw Transcript

Okay, good morning, everyone. I'm stoked to kick things off this morning.
Today's talk is going to start off with just a brief look at GTM engineering and what it is. And then, I'm going to get into kind of the areas that I consider to be the most technically interesting and challenging within the space.
So, GTME is pretty new. It's arisen out of a couple factors, but one of the main motivating ones is that GTM teams have kind of realized that it is now possible to ship as fast as a product and engineering team.
And so, the best GTM teams that I work with are generally pushing changes to their GTM structure almost at the same cadence that an engineering team might be doing releases.
And so at Clay, what that looks like is something like this, where every two weeks we are pushing new data to our teams. We are pushing new automations, we're of course running new campaigns, and we're constantly iterating on the things that we're shipping, and trying to keep pace with the speed that is that our engineering team is working at.
So, to do this, you need a couple fundamentals in place. And in my view, GTM engineering at its heart is really about removing the constraints that have historically stopped GTM teams from shipping at speed using technology.
And the role itself has exploded. So, I would venture to say that most advanced GTM teams are now hiring GTM engineers or looking for this role. And in my opinion, it's one of the first roles that actually is an index on the advances that we're making in AI.
And so, as models have become more powerful, GTM engineers have gained more leverage within their organization and become more valuable. And we've seen tremendous growth in this role.
So, I kind of break it down into four areas, and what I hope to do with this talk is kind of lightning round go through some of the technical problems and solutions that I see for this. If you're not familiar with Clay, we are obviously building infrastructure that kind of attacks these areas. But this is not meant to be a sales pitch. It's more meant to be if you're an engineer or a GTM engineer that's working on these things, some ways to think about how to structure it. And then, if you're a founder in the space, some of the interesting problems that I think are worth tackling.
So, the first is data. And more than most teams within a company, data is the lifeblood of GTM.
And the core goal that I think we're trying to accomplish with our data is to create a perfect virtual copy of the market: the ideal customers, the accounts, the contacts that you're going after.
So, most teams start out with something that looks like this: You have accounts, which are the companies that you're targeting, and contacts, which are the people that you're going after.
The problem, though, that makes this challenging is that accounts, at least, exist in a state of constant change.
As an organization, a company might be getting acquired, it might be splitting up new offices, it might be launching new products, so the company itself is always changing.
In addition, you as the GTM team are doing things that company that it's making it change, as well. So, you're marketing at them, you're selling towards them, you're trying to book meetings. That's changing the state of the account. And then also, the company itself is hiring people and firing people and doing things that provide signals for you.
So as GTM engineers, we need to manage all of this state within our accounts, and we don't have all the data that we need to do this kind of right off the bat.
So, this is what an example from Clay's CRM looks like. You can see I have a ton of fields that are simply telling me what state this account is in: whether they're a customer or not, whether they're expanding or churning, how big they are, how well they're scoring. And so, one of the fundamental things that we need to do is make sure that our records are updated so that we can actively accurately action on what's happening here.
And so as, you know, in a brand-new CRM or a or a CRM that I'm going into, the first thing that I am doing is actually filling up the account with relevant contacts, and then I'm layering in third-party information that is going to help me figure out which accounts to target and which ones are in in market. Primarily, I'm looking at the account hierarchy, the firmographics that describe how big the company is and so forth, the technographics that describe what technology they're using, and then I'm trying to create signals on top of those accounts that are going to allow me to go after that that company.
And so because there's a lot of third-party data involved here, we need to actually go out and source and procure that data.
And within GTM, there's literally hundreds of vendors that you can turn to to to get the data that you need, but none of those vendors is going to have a complete picture of all the information you you desire. And so, the key technique here is called waterfalling. This is where I'm going to actually go and look into multiple providers to try to fill in all the information that I need.
If you see here, if I was just using Forager to get phone numbers for this this set of countries, I'd only get halfway there. So instead, what I need to do is layer on all of these other providers, and that's not only true for phone numbers, but for most the other data points that we care about within GTM. And so, either you or the vendor that you're using needs to run evals against these data providers in order to obtain the most accurate information.
And so, not only do I need to sync in third-party information to my data layer, I also need to incorporate first-party information, and I need to keep that constantly up to date.
It's also incredibly expensive to update data all the time, especially if you're purchasing it. So, I can't just update all the fields, I need to kind of selectively choose which fields to update.
And not only am I pulling information from various sources, but if I'm running a signals program, information that I need is getting pushed to me all the time, as well.
And because I'm using multiple third-party sources, the actual representation of a single account in those different sources is going to be different, so I need to resolve the entities in between them.
And so, a great data layer will tackle all of these things and allow me to kind of move on to the more interesting work. But without this, it's really, really hard to execute automated GTM plays.
So, the next piece that I need to get right is orchestration.
And this occurs because within go-to-market, there are literally dozens of tools that most teams are using. So, I might have a sequencer, or a dialer, or a bunch of places where my reps are living or my field marketing is living.
And in most cases, the view of the world that those tools have is different depending on where you look. And so, orchestration in my view is really the active keeping all of that up to date.
And so, what happens to our data model then is I'm on top of my enrich information, I'm sending emails and calling into my contacts, the account is generating events that I need to keep track of, and I now need a system to actually plug all of this into my data layer.
And so, most teams are going to have something that looks like this as their basic stack: CRM, data warehouse, sequencer, a dialer, a notetaker for call recording, and some chat interface like Slack.
However, I usually see like 10, or 20, or 30 tools that actually these teams are interfacing with. And orchestration needs to kind of keep that information up to date.
The problem with orchestration is all of these different systems have different data needs. So, some systems need kind of like real-time updates one record at a time, other systems are going to need hundreds of thousands of records, maybe updated once a day.
I might need to schedule updates on a monthly or weekly basis depending on the data I'm using. Some data points like employee count change all the time, other data points like headquarters location change very rarely.
And I'm not going to be making updates to all the fields at the same time, so I need logic within these systems that helps with that. I also need to be able to take a single system that I'm working with and actually fan its information out to multiple different systems. And because I end up with this kind of distributed setup, I also have failures that are happening all the time. So, this turns into a fairly complex data engineering problem that we need to resolve.
A classic example of this is when I'm working with these different systems, usually, they are not fully orchestrated, which means that one system is talking to each other while I'm trying to talk to both of those systems at the same time.
So, for example, if you have a Salesforce connected to Outreach or a sequencer, usually that CRM and that sequencer are syncing independently of your orchestration system. And so, if you create contacts in your CRM, you actually need to wait for that contact to sync to the sequencer before you can then take action on it. This creates some difficult problems where you actually need to introduce things like weights and loops to check if information is ready.
So, at Clay, we've iterated on this problem quite a bit, and we've ended up in a place where we are basically taking a graph-based view of the orchestration problem with a series of general-purpose nodes that are executing various things.
And so, we have nodes that run agents, nodes that make tool calls, nodes that handle our conditional logic, nodes that run code, and then nodes that run effectively this MapReduce system to fan out the information and bring it back.
And so, a great orchestration layer will handle all of these, and whether you buy it or build it, I think this is like fundamentally the the kind of modern way to set this up.
Here's an example of this in in Clay, and again, you can use other tools for this. But basically, I'm going to have some sort of event that kicks off my orchestration, some trigger or some schedule. I'm going to then talk to a couple of different systems, I'm going to combine that information back together, and then I'm going to push it out to different interfaces that my reps are using.
Okay, so now that I have a data layer setup and I have my everything orchestrated, I now have this system which is starting to look a lot more complex.
And if you spend a lot of time in go-to-market, I think this is actually like one of the simplest views of what is happening with an account, where I have multiple signals that are occurring, I have data that needs to be updated, I have actions that my agents or reps are taking, and then I have meetings that are happening and feedback that's occurring.
And so, the state of the world today is that we are relying on sales reps in a lot of cases to manually sort through this. But one of the great advances in the last year or so is that we can now use agents to take care of all of this context.
However, if you use agents, you actually run into some of the same problems that you are dealing with if you just use LLMs.
So in GTM, in particular, we are trying to build very long-running agents, agents that run over a course of weeks or months that keep track of the state of an account throughout a deal cycle.
We also have a high bar for error because a lot of the results of our GTM work is customer communication, and getting that wrong can have disastrous consequences.
And then finally, the agents are often doing unstructured work and pushing that into systems that are highly structured like a CRM. And so, the the mapping of what the agent is producing is is super important.
So, the architecture that we've landed on for this that I think is most powerful is an agent that exists for each account and maintains a persistent state of that account.
It's always going to execute and because it's executing over a course of weeks or months, it's often going to be dormant for most of the time that it's available. So, we need to use smart triggers or a heartbeat or something to wake it up.
And then when it wakes up, it needs to kind of ingest the current context of the account from our data layer and our orchestration layer.
And because the agent is making decisions for us, in many cases, automatically, we need to allow for feedback on the agent, as well.
The cutting edge of doing this is the learning phase, where as the agent works on an account or a series of accounts, it updates its own view of what's working.
Today in GTM, this is not fully solved yet, and in fact, the continual learning effort and the next best action suggestions are kind of one of the cutting-edge problems that that we're working on.
So, here's a look at a kind of a basic agent. You can see here that I'm pulling in information from a couple different sources, I'm using reasoning steps here, and then critically, I'm also updating different values in my CRM that are just for the agents.
So, I always recommend separating the fields that agents are updating from the fields that deterministic systems are updating or that people are updating.
And to look at a full view of an agent, this is a closed lost reawaken agent, so you can see it's talking to Gong, email, CRM, and my data warehouse. And so, it's pulling together multiple pieces of information.
And this agent is triggered on a time basis. So, if if we lose an account, we're not going to kind of like immediately go after that account again, we're going to wait for a little bit of time in order to in order to attack it again. So, there's a number of kind of timing and context issues that we have to address when we're building agents for GTM.
The last step that that is important here is the actual execution step.
So, now that we have a data layer that contains the perfect copy of the virtual world, we have an orchestrated system that's sharing context with all of our systems, we have agents that are making decisions and reasoning about what to do, we actually need to get in front of customers and execute our messaging.
Unfortunately, messaging and execution is one of the hardest problems in GTM engineering.
Here's a look at some of the email open and reply rates over time.
Generally, what we observe is that cold email works less and less well as the years go on. This is a trend that's been true forever.
To look at a snapshot of this, if you look at the far left here, I actually think these are pretty elevated rates for some of these, but the relative differences between these channels is correct. So, you know, LinkedIn can be three to four times more effective than cold email, cold calling and cold email are roughly the same.
And then on the right here, this is a series of statistics from Smartlead. This is across, I think, 20 million emails.
And so, you can see we've got somewhere between 0.5% and 1% reply rates.
So, what that means is, of course, if we've got 100 contacts that were sequencing, maybe one of them will reply.
And so, that really raises the stakes for agentic execution within GTM because if your agents are doing the wrong things, then you're missing out on the margin, which is where most GTM teams are are having success.
The other thing with execution is you have to solve some very human problems. So, for example, do you email on behalf of the rep, or do you let the agent do the emailing?
If you email on behalf of the rep, what that means is like everett@clay.com is actually reaching out directly to customers.
But if I do that in the wrong way or I don't get the replies that I need, that then means that my overall domain reputation is going to suffer for for my company.
So, a common technique then is to use multiple domains to get in touch with customers. But then if I do that, I actually need to find a way to route responses on that domain back to my main domain so my reps can process it.
And that's just email. There's also multichannel outreach, which is tricky, as well, because you then have to, for example, if you get a call connection and a meeting booked on your call sequence, you then need to suppress your email sequence, and maybe unenroll someone from a lifecycle marketing campaign.
So, the coordination of the execution of all of this is also a hard problem and also something that we can use agents to to help resolve.
So, here's a look at one way that that we're tackling this. This is a setup for a kind of rep proxied view, where we have a bunch of rep inboxes that are connected to our sequencer, and we're actually sending that on behalf of reps.
But like I said, we do this for kind of a portion of our accounts. For many of our of our accounts, we actually use multiple domains to go after them, and then we have to tackle the routing problem.
So, that was kind of a lightning review of what I consider to be some of the like harder problems within GTM engineering.
I think if you get these pieces right, you can end up in a place where you're providing the technical foundation for growth that is helping your company achieve incredible results.
Um, but I think a lot of teams actually overlook some of the harder pieces here and and don't necessarily design around some of the constraints that they have to deal with.
So, that's my talk. You can see me on LinkedIn. There's a URL there, and looks like I have about 90 seconds for questions if anyone wants to ask anything.
Any any questions for Everett?
Raise your hand, I can Okay.
Just uh curious as to what your um biggest challenge is figuring out these new um changes within the org?
I think one of the harder problems is probably the interface between the human and the agent.
Like I said, I think the most powerful use of agents within GTM is to act as the reasoning and decision layer for a lot of tasks that a sales rep was previously doing.
And so, you run into a lot of instances where the rep might think that they should do something different, or the rep might not know that the agent did something.
So, because ultimately, a human still needs to get on a call with a prospect, coordinating the connection between what the automated systems are doing and what the what the human sales rep is doing and making that work well, I think is probably one of the hardest problems.
Okay, well, oh yeah, one more.
I have a question, so GTM engineers are fundamentally software developers that have this knowledge. And my other question is that this is mainly for outbound, or inbound as well is included in this practice?
For everything, yeah. So, like the orchestration problem is pretty acute in inbound. You have to get the routing right, you have to qualify the account properly, there's usually historical contacts on inbound that comes in that needs to be needs to be understood. So, yeah, this I think GTM engineering covers covers all of GTM.
And if you want to chat with me more about this, I'll just be right outside, but I will hand it to the next speaker now. Thank you.
