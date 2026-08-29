---
id: "49b44c6d74fe511d"
title: "Building GTM AI Agents: Lessons from Deploying to 6,000 Users — Sait Izmit, Snowflake raw transcript"
aliases:
  - "Building GTM AI Agents: Lessons from Deploying to 6,000 Users — Sait Izmit, Snowflake raw transcript"
  - "Building GTM AI Agents: Lessons from Deploying to 6,000 Users — Sait Izmit, Snowflake"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=DrTdD-ttjCY"
origin: "https://www.youtube.com/watch?v=DrTdD-ttjCY"
type: "raw-transcript"
created: "2026-08-29"
---

# Building GTM AI Agents: Lessons from Deploying to 6,000 Users — Sait Izmit, Snowflake Raw Transcript

Hi, everyone. So, I think I'm one of the last speakers that is standing between you and the long weekend.
So, I hope I can get your energy levels up.
Um so, I'm responsible for our internal AI tools for our sales team.
And the reason I'm here today is indeed like we launched our internal go-to-market assistant
in September last year.
It answered more than 1 million questions so far. We roughly answer 40,000 questions a week.
Um and we are the customer zero for a lot of Snowflake products. So, this is built on Snowflake CoWork.
Um and I meet a lot of customers every week. Okay, so I meet a lot of enterprises, Fortune 500 companies,
and then they're all trying to build similar things and then whole struggle. Right, so and then I end up like having this discussion with them all the time.
Like, they ask, like, "How did you guys do it?"
And then we share our best practices.
So, I will try to share some of those things with you.
Uh I'm told that I need to have some code in my presentation. I don't, but I will try to show you at least some architectural diagrams.
Just to make it more interesting for the engineering audience.
Uh but let's jump into it. Um
I think before we start, like I think I already I was watching the other presentations, like I think everyone tries to give their interpretation of like,
you know, why are we even building things for go-to-market? Okay, so this is how I explain it to family and friends.
So, let's take Snowflake, okay? So, we are a company of like, you know, close to 10,000 people.
So, if you look at that or our organization, almost half of our basically workforce is sales.
Right? And what are they responsible for?
They are responsible for revenue generation.
What do they struggle with?
And I you know I talk to a lot of customers, it's very common.
You know, everyone's data is siloed. We work with a lot of first-party data, a lot of third-party data, it's all locked down in these like SaaS tools and things like that.
And literally, we have, for example, like reps who are using 15 different tools, not because they love the UI of those tools, because every tool has a different data point, and then they end up stitching all of that together in spreadsheets and running it there, right?
Then the data is endless. Like, we have reps who are have 1,000 accounts assigned to them, 1,000 customers.
They have to stay on top of their recent news, what's happening with their consumption, did they get any support tickets recently, what was their latest earning results, everything.
There's no, not a single human on this planet can stay on top of that much data.
And then they need to do that 30 times, 40 times a day.
Right?
So, what does AI offer for them?
It offers that data democratization. No more like thousand dashboards, right? No more access to analysts, like you know.
Um it offers automation possibilities for them, right?
It frees up their inbox.
It offers tool consolidation, no longer 15 different tools that I need to work for.
And that brings productivity savings. It frees up your time, right? You can use that time on other things. It helps you become a better seller. You're more effective with your customers.
And that translates to business results. You can cover more of your book,
you know, you can have better win rates,
uh you can have shorter deal cycles, and ultimately, what everyone cares about, you can get incremental revenue,
okay? So, that's the reason why am I working for, you know, making the go-to-market organizations more effective.
But there's a catch. These are non-deterministic systems,
right?
And I run into this problem every time
with users.
I've seen many, many, many AI projects failed,
and then it fails on this principle.
User trust is earned extremely
hard, and it's lost overnight.
Right?
So, at the end, what you are doing is you are putting a free-form chat box there.
Right? And people will come in, and then they will ask any question they can think of.
If they like what they see
in the first five questions,
they come back.
If they don't like what they see, it's 10 times more effort for you to win them back, if you can ever win them back.
Right?
So, we have a saying in our team, we say, "Quality is p minus one."
Right?
And that's basically, we take that very, very seriously.
So, one of the things that we really cared about is when I first joined the team,
you know, the team had all these like data sources connected from our top dashboards, we they had a knowledge assistant built into it, and so on. We had three lines of agent instructions,
and then before I even tried the agent, I opened the spreadsheet. I took the sales process. I wrote down 150 questions.
And then the sales our engineering team was like, "What are you doing? We don't have that data in the agent."
I was like, "It doesn't matter. These are the questions your sellers are going to ask."
Right?
And then we run our test, 50% accuracy, you know, like everyone is depressed, and so on.
So, we said, "Okay, let's make sure that we don't go for coverage, but we go for quality."
Right?
We don't want to try to answer 100 questions and get them 70% right. We want to answer 50 questions, but get them 95% right,
right? Because with that, you get a first impression, good first impression, you build the trust with them,
and then rather than being in that boat of, "Oh, this thing doesn't work," people are like, "Oh, this thing is awesome. Can I get more of that?"
Right?
So, we started small, and 60% of the data we actually added after the launch, after the six, seven months post-launch.
Today, if you look into our agent,
I mean, it's not a small agent. We have 15 semantic views, 85 tables, 3,000 columns of data,
we have like five to six different MCP connections on it, you know, close to 20 skills connected to that, and so on, and so on.
Right?
So, it's a huge system that we're managing in here.
And then you cannot just launch these things to everyone, right? So, we said that, "Look, we need to do this in a controlled way," because we want to make sure that we earn that first five questions. We don't want to burn our bridges in that first five questions,
right?
So, that's why with every product we do, we do a phased launch.
The first one is a pilot. The goal of the pilot is to prove the accuracy, prove the quality,
right? You get your top, you know,
AI-native folks in the organization
who are eager to work with you, give you feedback, improve the product, make sure that you got the rough edges through that, right?
And then after a couple of weeks, you come to a point where it looks like, okay, those rough edges are more smoother now,
okay? Then you go into your beta launch. We do a 10% beta, right, with 600 people.
There you are looking at, do I truly have, basically, a minimum viable product? Is the MVP really there,
right? And what will happen is that you will start getting tons of requests, "Can you connect this data? Can you connect that data?" and everything.
And then you are looking at like, where are they actually the concentrations happening?
Because that means that if you don't get those things in, you don't truly have an MVP,
right? Then it's not gonna work for their daily workflows.
And then at that stage, you're also trying to prove, are they coming back?
Right? So, the things that we really track there
is basically like, okay, how many questions they're asking, and everything, but what is the retention rate?
So, we exited, for example, that at like more than 70% retention rate at the weekly active users were coming back.
Okay, now we're in a good place, right? We have confidence on the accuracy, we have on the confidence of the basically the coverage of the product we have, and people are coming back.
Okay, now let's go to GA, and then you launch to the GA.
Then then you have your next problem.
So, I know that this is a technical conference, but this is also where a lot of these products fail.
It's basically how do you drive change management?
So, you launch your product. You are two weeks into the launch,
and then you are here. And all your management is like disappointed or frustrated, "Why aren't people using this? Why our numbers are very low?"
Right? And I showed them this graph.
I say that only 20% of your basically organization actually tried the product.
I cannot do anything. It's not the product's fault if people are not even taking five minutes to try to try the product,
right?
If they try it, and if they don't come back, okay, that's my problem,
right? But if they don't try it, then we have another problem.
So, the first, and I've been, you know, I've seen this with many, many sales organization in my past life as well, and so on, usually it's a couple of months process.
And then you significantly invest in basically change management, in activation.
I will spend 60-70% of my time in sales meetings, giving demos, building dashboards to see which teams adapted, you know, shaming the like the managers whose team is actually doing good, getting sponsorship from sales leaders to basically like make sure that they pro- you know, they push their people to try these things, and so on.
And then ultimately, that gets your blue line up, and then your questions are start coming up.
And then your focus can shift into, okay, how do I drive more depth?
Right?
And I want to really, really emphasize this because if we hadn't done this,
we would probably be doing, you know,
half of where we are today. So, it's a very, very important part, and then as engineers, if you spend all your effort, you want to have a good product, make sure that the activation and the change management is like lined up like post-launch of the product, as well.
Now we run into another issue. Okay, you are let's say that four to six months down the run,
right?
What happens is you successfully launch the product. You are first like rock stars in the company,
right? People literally shove you on the corridor, like, "Hey, your product is awesome. We can talk to our data now. We don't need to wait on the queue to like, you know, get access to like analysts to answer our questions in every two weeks," and so on,
right?
And after a couple of months, they start coming back to you with frustrations, "Hey, I cannot do this in the product anymore,
right? I I would like to, I mean, I saw this other AI product that does this," and so on.
This is what I call the collapsing of the wow factor,
okay?
So, initially, you are cool, but then
then that becomes a habit, right? You basically change their habit, and it becomes standard for them.
Now you need to raise the bar again.
So, the journey that we usually see with the sales teams is like you start with talk to your data.
How do we get you out of those like, you know, hundreds of dashboards situation, dependency to the analyst, and then first we basically like democratize the data for you so that you can basically talk to your data.
Then the next wave comes with all the MCP connections, right, all the integrations that you are building.
Now it becomes like automate my workflows.
We literally have now sellers who are going to use our agent basically to monitor their inbox, they monitor their Slack channels, you know, keep track of all the customer questions coming about like product questions, how use the agent to draft responses that save that in Gmail, review then afterwards like send those things out, right?
Or they automate their like outreach workflows, and so on. Okay, that's great. Now I became an orchestrator,
right? I'm basically automating my more flow workflows.
Then the next thing you see start happening is teams, they get these like, you know, tool democratization, this empowerment coming to them, right?
Because historically, a lot of these go-to-market teams, they have been always in the backlog of someone, backlog of of an IT team, or like trying to get a SaaS budget to the get a vendor on board to actually like enable something.
And now all of a sudden,
they're able to build team skills.
They're able to build like, you know, the custom dashboards that are basically like fully, you know, optimized for what their team needs. Are able to like deploy applications, automations, alerts, and things like that,
right?
And then there comes the phase of hyper-personalization,
right?
Everyone is able to now like get everything personalized for them, not only for themselves, but also for their customers, with living context of customers, contacts, and things like that.
I think the main message I want to give here is
if you just do the first stage,
and if you just wait there,
you will get disrupted in a month or two.
Right?
Because now you already raised their expectations that already became a baseline,
and then they will find that another product that does better than you, and right now the switch is very easy. They're going to just switch overnight,
okay? So, you need to keep iterating, you need to keep that wow factor,
and then you cannot just rely on the fact that, you know, what I built so far is going to stay cool forever.
And the next thing is, how do you deal with basically the changing technology?
So, I talked to a lot of customers,
and then, you know, sometimes you run into these customers, big enterprises, very big brands, and then they are still trying to chase that perfect architecture.
They are trying to like test different frameworks. They are trying to see how the, you know, technology is maturing, and everything, and so on. But the thing that they don't do is they don't build, and then they don't launch, and they don't learn,
right?
All these blue boxes that you see here, those are all the things we added after the launch,
right?
When we literally first launched the agent,
it was a nine-page long agent instructions.
It was couple of Cortex Analyst tools, semantic views, it was a Cortex Search Service for our unstructured data,
and we were managing the agent instruction versions out of a Google Doc.
That's how we launched it
to 6,000 people,
right?
Then we realized like, "Okay, it's not going to work out. Let's figure out CI/CD. It's not going to work out. Let's figure out our basically eval infrastructure with all the like the unit tests, routing tests, and everything," right?
Then we start basically like coming to a point where, for example, we were creating all these like business processes and workflows. We couldn't fit them into the agent instructions anymore. And then the skills came, and we were like, "Oh, perfect! Let's build a skill library."
You know, then the MCPs came. Perfect! But now like we had to put bunch of other instructions to basically orchestrate that, we hit the limits on the agent instructions. What do we do? Okay, let's do the progressive disclosures,
right?
And then user memory comes, task scheduling comes. We want to go beyond the chat screen, and then, you know, chat interface, and start doing the Slack interface, and things like that.
If I look at the PRD and the architectural diagram we wrote in the beginning of the project,
if I compare to this architecture we have now, 80% of it doesn't match,
okay?
So, like if you look at our sprints,
like maybe 60-70% percent of the work we are doing is adding new features, improving quality, and all kind of things.
But 30-40% of the work is that we are constantly re-architecting with the new technology.
So, this is the time where like you need to get your hands dirty, you need to run with the new technology,
and then you shouldn't be like, you know, too much tied to your architecture. You should be okay to like pivot very easily
so that you can basically double on down on these like new capabilities, and things like that.
And then the longer you wait,
the more, you know, you lose towards your competition, because if your competition is doing these kind of things like three, four months ahead of you,
right? That means that they're also getting more customers.
Um last thing is
I would really, really recommend investing your logs,
okay? Because they create the basically the feedback loop.
So, first of all, technically, it's very fun, okay? So, you basically use LLMs to like classify your logs, and things like that.
As I said, like we have 1.2 million questions, we get 40,000 questions every week.
It's technically very fun, you know, how you would do that at scale without breaking the bank, and so on. You know, our data scientists love working on those things, and then they really experiment with new things.
But as a result of that, what we get
is we get a very, extremely detailed breakdown of topics and, you know, things that we are having. And I'm just showing you the top category categorization level there,
but then basically we are able to track like, you know, what kind of questions they're asking. We're able to break down each of those categories to sub-categories, you know, we're able to get like detailed example questions, this and that, and so on.
All good, but how do we use that? Then we start creating the basically the feedback loops,
right?
I know I mean, I still interview, of course, users, but now I see in real time what my feature gaps are.
I'm clearly seeing what people are asking and we're not able to answer or where we have a like a quality issue where they're swearing at the agent or like repeating their question so that we see where to improve.
For sales enablement, it's a gold mine.
Let's say that we launch a new product,
usually, you know, they would need to interview maybe 100 sellers a week to be able to understand like how basically the,
you know, the topics are changing, where there's gaps in terms of like knowledge documents, battle cards.
I see that in real time in a minute or two by just asking an LLM a question.
And then we can then, you know, connect to Confluence, we can connect the Jira, we can connect the Slack channels,
we can ingest the PRDs, and in couple of minutes, we can actually like, you know, generate battle cards, sales enablement document, and then feed it back into the agent,
right? I mean, you cannot do that kind of like a feedback loop with humans, right? So, then we can basically automate these kind of things.
Um within the sales organization, there will be different teams that are trying to connect each other, they're trying to maybe target similar accounts from different angles.
They don't know about each other. We do. We are now able to ping them, and then we are able to basically do matchmaking,
right? I'm just giving you a couple of examples.
Now, this is also one of those areas where like you start building your AI platform, you start building your architecture.
The first features are difficult to get out,
the next ones are easy, and then once you start tapping into your logs, this this like
hockey stick exponential thing actually starts happening, and it's magical.
So, if you were to take a couple of things from this talk,
like quality over coverage.
I'm very, very like religious about this.
If you go for the coverage,
you are going to shoot yourself in the foot,
okay?
Change management. A lot of engineers doesn't think about this,
right?
A lot of these AI initiatives, they don't fail because there's an issue with the technology, there's an issue with that, assuming you did the first one right, right?
So, they fail actually in activation.
So, make sure that you have a plan for that, especially in larger organizations where we are dealing with like 6,000 go-to-market users, right?
Um again, don't forget this concept of collapsing wow factor.
You cannot stay where you are. You cannot just say that, "Hey, I did an innovation. I'm going to surf that for a year."
You know, every time people are happy, you should be paranoid. You should be like, "Okay, what am I going to show them in a month or two now?
How do I basically keep that excitement going on?"
Right?
Build fast with today's tech, like don't try to invest in these like, you know, super like, you know, architectures, and have these like six, nine months of long projects, and things like that. How do you turn around these things in weeks, days, and so on?
And just be comfortable with the fact that you are constantly going to be re-architecting, that's fine,
right?
Just don't overinvest in the current architecture. Just make sure that you keep your like flexibility out there.
Um and then the feedback loops. I think that's what kind of like gives you really that like, you know, the incremental part of like that hockey stick exponential part of the thing.
Um we constantly publish like blog posts, I mean, where we kind of like try to have our, you know, learnings shared with uh our customers, and so on. Like, we have blog posts on like how we do agent instructions, how we do our structured data with semantic views,
you know, how we basically build our RAG-based like knowledge assistance,
the non-technical side of the story, like how do you drive change management, and so on. So, feel free to check those.
Um and yeah, I think that's
end of my talk.
Okay.
We have time for one question.
Okay, there you go.
Thanks for the talk. Um I don't know if you already said this, but I saw in the the the titles of the articles Snowflake Intelligence, is that an underlying context or layer that the tool or system you built was on top of, or was that the tool itself, or something else?
Yep. Snowflake Intelligence, we renamed that to Snowflake CoWork a couple of weeks ago in our Summit. That's basically our no-code agent platform
that we basically have available for our business users.
Um I mean, the advantage of that is that a lot of these tools around like, you know,
uh you know, Cortex Analyst, or Cortex Search, or Cortex Sense, a lot of those things are basically comes out of the box.
Uh we made a strategic choice for our internal thing where we said that, "Look, it is important that we bring all our data together, and we do that in Snowflake. We bring all the first-party, the third-party data, all the Salesforce data, everything, the call transcripts, and so on, all together.
And then these agents then can basically, uh basically inherit a lot of the uh role-based access controls, and so on.
And then literally, you can deploy these agents without writing a single line of code, right?
Um and then, you know, you don't need to worry about the UI. The chat UI comes out of the box, and so on.
And then we have been the customer zero of that like internally to build this ourselves, and then, you know, our customers are able to go, and then build similar things uh basically on Snowflake CoWork platform, as well. And it comes with the guardrails and things where you don't really need to worry about them going very, you know,
crazy and, you know, what data sources to do things, and so on. So, we're able to do a lot of curation.
We are able to do a lot of security guardrails in there as well.
Yeah.
Thank you.
Thank you.
