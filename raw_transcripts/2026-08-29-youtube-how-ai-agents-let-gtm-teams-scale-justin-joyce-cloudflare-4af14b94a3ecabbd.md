---
id: "4af14b94a3ecabbd"
title: "How AI Agents Let GTM Teams Scale — Justin Joyce, Cloudflare raw transcript"
aliases:
  - "How AI Agents Let GTM Teams Scale — Justin Joyce, Cloudflare raw transcript"
  - "How AI Agents Let GTM Teams Scale — Justin Joyce, Cloudflare"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=Qw_tC68KKes"
origin: "https://www.youtube.com/watch?v=Qw_tC68KKes"
type: "raw-transcript"
created: "2026-08-29"
---

# How AI Agents Let GTM Teams Scale — Justin Joyce, Cloudflare Raw Transcript

Well, thank you everyone for joining.
I'm hoping that you guys had a great time so far at this conference, and you guys have a lot of takeaways back, you know, to your company.
I don't know if any of you guys saw the AGI pills downstairs?
Yeah. Well, I just took some.
So, if I say any phrases about "that's the" the the gun.
What's that? What's the What's the phrase?
"That's the" burning gun, or the "smoking gun," or I start hallucinating in general, well, please snap me back.
That's probably just the AGI pills.
All right.
So, without further ado, let's get started.
My name is Justin Joyce.
I'm a Principal Sales Operations and Strategy Manager at Cloudflare.
And I work with the go-to-market team as part of the revenue operations organization, specifically on the teams that produce leads for the sales teams, as well as the customer experience team, which works on the customer experience after the sale the sales have been done.
And just a little background about me.
As Mada said, I started in sales operations and sales, and then I moved to sales to the machine learning side about the last 7 years at Grainger.
And I really wanted to do that to be able to learn how to have prescriptive analysis and prescriptive prediction so I can help the business better to make decisions and to understand, you know, what's the next step next best step.
So, 6 months ago, I had an opportunity to move back into sales operations because I really wanted to use all the skills that I had been learning from machine learning, as well as from sales operations in general.
So, what's the general problem?
The general problem is that traditional go-to-market does not scale.
There's a few facets to this.
The first facet is that, usually, teams on the back-office side, they're either doing work in Excel or Sheets at worst, building analysis each week, multiple hours a week.
And as they take on multiple projects, that gets exponentially long with how many of those analysis that they're doing.
At best, they are producing dashboards, providing information to the leadership and executive team, which, you know, meets the needs of most teams, but not all of them.
And that needs meets that needs means that, in general, not all the requirements of the go-to-market teams are met.
They're not able to really provide all the information that the teams need when they need it.
The second problem, which is more on the go-to-market side with the sales and the sales teams and the other teams that I mentioned that I support, is they have two gaps essentially.
The first gap is the context gap, meaning when a salesperson is talking to a prospect one call, and talking to a current customer in the next call, or talking in adoption conversation the call after that, they have to constantly switch context, and they have to gather information for those specific calls, which is good.
They really need to get that information to have those calls and understand how to approach the situation.
But they have to do all that work in between.
The second one was what is like to what I like to call is the expert gap, which is the gap between how your expert salesperson or expert go-to-market sales individual, how he would approach a situation, how he would talk to a prospect, how he would work on adoption call, how he would handle a customer satisfaction issue, and the between also a new salesperson or someone that's just ramping up.
So, ideally, you like everyone working at the same operational level so you have consistency in execution, consistency in messaging, of how to assess a a customer's problems and how your product can help fit that portfolio.
So, with these two problems with manual work, as well as sales people not having enough information and having the gap of having to get all the information they need and gather that, as well as not being able to execute the same level, it really creates inefficiency in the go-to-market organization.
And so, for the last 6 months or so since I've joined Cloudflare, I've been really focusing on how can I make this operation efficient from back to front, and there's a lot of great things that we've been doing at our company in general that's helped me enable that, and I really want to share some of those findings with you.
So, the framework that I'm proposing here, which I think is is is going to really be effective in as we flesh this out in the future, is a three-pillar approach.
The first pillar approach is how can we scale analysis and the ability of operations team to meet the data needs of executives, leadership, as well as be able to build applications using business context?
How can they take things that would take 2 hours to do down to 5 minutes?
Back in well, not back in January of this year, I after I join joined the company, I had built these skills, and I'd started asking questions of the data directly, and I was able to get answers immediately while doing other things.
And I saw the huge power of how, if we can scale the analysis and the operations of the teams, we can actually focus on the second part of my job, which is strategy.
The second pillar is how can is to scale insight.
There's story in the data, and how can we provide that to the team?
How can we provide that team at, you know, the weekly level, at the different levels of management?
How can we provide that information, that insight, that story to every customer that the sales teams are talking to?
And the third one, which is arguably the biggest one, is to provide self-service capabilities to the go-to-market team.
When these sales individuals, when they're talking to a customer, how can they get the expert-level information that they need to interact with that customer, and to best assess, you know, how they should approach the situation, how to handle rejections, how to upsell them, and how to handle customer satisfaction issues?
This is a huge part of what I've seen we've done at Cloudflare, and I'll share in a little bit what that looks like.
So, as it relates to scaling the analytical capability, the back-office operations, what we've done is we built role-specific skill files, which have the context of the business information, tying it to the data.
This is for both technical and non-technical users.
Technical users, you could say the ones who are building SQL and being able to data engineer a lot of solutions.
And then the non-technical people would be more individuals who are closer to the business with the sales people, who may not know how to write SQL.
And so, we have skill files that they are able to use to ask questions of the data to get answers fairly quickly while doing other tasks.
And an example here is, in those skill files, we also, through testing, we've included the types of questions that the business would ask of the data.
In this case, looking at the close date changes in opportunities, as well as changes in the amount of the opportunities, so that we can answer essentially 80% or or more of the questions, where the other 20% might be more complex, strategic questions.
And so, overall, this allows the teams to be able to embed all of the logic into these skill files and get answers fairly quickly.
So, I've seen users who do not know any SQL and essentially their requests in the past would be bottlenecked to someone who knows data and can write SQL for complex queries, be able to just ask questions of the data and get answers.
And this is very useful also for what I show later on on the third pillar, is for building skills for these go-to-market teams so that they can ask questions of their data and and get answers.
Also, in our team, we've used these same skill files to build multiple applications, when usually, you know, that is done in IT and bottlenecked in those areas.
We're able to use the semantic information about the business knowledge, as well as the columns, to be able to build these applications rather quickly.
So, this allows us to free up our time so that we can focus on strategy and enablement.
All right. For the second pillar, what I mentioned earlier, there's a story in the data, and they really shouldn't have to search for it.
What I'm showing you here is synthetic data on the right.
We have a weekly summary that goes out, which highlights how the business is doing, how they're pacing to their goals, and then highlighting trends, standouts, as well as watches.
So, this we provide this information to the business so they can, as you just, like you can open your phone now on Gemini, if you have it, and you can see your notes for the day or the things that you need to do, giving that same level of information to the go-to-market team so they can just go along their day, and if they do need to look at some of the reports or dashboards, they can to drill in, but we bring the story to them.
And I'll pull this together why I think this is really important.
You know, of course, there's a place for dashboards and standardized information, but there's a different level of adoption of the KPI metrics at any given company.
You're going to have people who love dashboards, people who are never going to look at them.
So, I think you really need to have a way to scaffold that across the business.
So, how do we do this automated analysis?
So, a big part of this is simplifying the data so that the AI agents can actually analyze the data in a very consistent and clean way.
Here, what we do is we transform that data by the dimension of time, also slice of the logical part of the business, which is manager, theater, and, finally, the metric.
Here, we have data that is wide.
You can also go from wide to long.
Our trend information that I showed you, that data is long, and then we do some preprocessing on that data to then highlight trends.
So, the the embedding of the logic of how you would filter this data to even analyze it, as well as the logical aggregations the business want to see, is all engineered upfront.
This, from my experience, this handles 80 or plus percent of the requests.
It's just getting information about the performance of the teams and how they're doing.
You can always go down to the raw data, but this last pillar, which I'll go in a minute, allows them to do that.
To be able to orchestrate this effectively and be able to rely on it, we have a multi-agent workflow where we first get the data, and then we do a first-pass draft on the data, calling our MCPs, and then the we have a second reviewer agent who checks the veracity of the data.
And then we have a third agent, which is a tone agent who, using a multi-shot prompt, is able to just craft the message and highlight the risks and opportunities equally.
And with every run, we have observability into each of the LLM calls so we can see what has passed and what is the response that is going on there.
And so, this architecture, we've tested for about 2, 3 months, and, you know, looking at every single run to see what is going wrong, and this is the the model that we had set up that is really working for us.
And we really hope to expand this beyond just what I've shown you for multiple teams, but also down to the customer level like I was just talking to you about.
The third part is the self-service model.
And what I'm showing you here is our internal tool called Cloudflare OS, which is an agentic workspace that is running on Cloudflare, where the go-to-market team can come in here.
It spins up their own compute and their own persistent environment, using Cloudflare workers, as well as durable objects, which is basically a storage, sort of like S3.
And so, the salespeople can come in here and get the data they need it when they need it.
So, some use cases that these teams are using it for is doing a forecast brief, building QBR decks, building a purchase deck on what the what customer that they're onboarding has purchased, doing account planning, general queries of the data, as well as renewal preparation, how are they going to look at what the customer has used and either upsell them or figure out how they can get them adopting their product more?
So, just a little bit more into that Cloudflare OS setup that I just showed you.
The AI agent workspace is what that screen that I was showing you, and through the the three-part piece of the skills in the lower left, which is our like expert level information, as well as the MCP connection and the AI gateway, they're able to have conversations in this agentic workspace to pull data they need, and using expert-level skills, which is curated, so that they are able to execute the jobs that they need to do when they need to do it.
And so, a little more information about the skill repository.
We have a central alias where skills are presented to the central team, curated by the go-to-market team, as well as by operations team, and then reviewed so we can make sure that we're not having a proliferation of skills, and we have an expert-level knowledge skill at every level so that they can really get all the information they need for how to approach any customer situation.
And so, just a few more images here of them using it.
Here, we have them building a prescriptive plan for their daily work.
They're asking a question.
It's they're you can see the agent is responding by looking into the MCP and starting to pull the data together.
And related to the QBR deck, here's a slide of generating a custom slide deck for a customer call.
And so, this is really I think unlocked the ability of the go-to-market teams to be able to really have all their information serviced to them.
And so, bringing it together with the three pillars that I talked about.
If you really don't have all these, I think you have issues with serving the go-to-market needs in terms of using optimizing the use of agentic systems.
With self-service, you allow them to be able to pull data when they need it, for whatever situation they need it, with the expert-level information.
The the second is by pushing the the insights to the business, you're able to surface the generalized, standardized information of how these teams are doing, and also, yeah, so so that there's no and also, so they're aligning with source of truth on performance.
And then the the third one is the scaling of the analytical team for them to be able to answer queries and build applications for the teams, which really unlocks a lot because the opportunity cost of that team being overloaded and being able to help is that the meet the needs of the go-to-market team is not met.
So, some findings and the future.
So, the first thing is skill curation is the basis for all of this agentic workforce.
If you're able to embed the knowledge of the business into the skill files, as well as these skills for the an analyst to be able to build answer questions or build applications, as well as those skills that I showed you in the Cloudflare OS, you're really able to give them the ability to use agentic systems in a more predictable and deterministic way so that they can execute evenly across the board.
The second thing is, through this whole process, the feedback loop is very important.
Just like a company would try to sell a product externally and get feedback, with these internal teams, the feedback loop is very important to be able to see is is what you're building is actually useful, what are some issues that they're having, and how can you make this work more efficiently?
And the third thing is the layering of those three pillars that I talked about.
Being able to answer questions where the team comes to you, some of the go-to-market team, that's how they like to interface with the operations team is to be able to ask questions, and then the pushing of information, and then the self-serviceability.
Through that, you're able to interweave all the needs of the team to be able to be met by this agentic-run team.
So, through all these different pillars that I talked about, we've really been able to 2x our efficiency in being able to serve the teams and as well as allowing them to be able to get the information that they need to do their job.
And some some things that I see going into the future, number one is a deeper integration with our systems that we work in.
So, for example, those QBR decks and renewal call skills, how can we set up meetings for the go-to-market team, and embed those artifacts in those meetings so they don't have to actually pull them?
We can allow them to that self-service portal to be more ad hoc and what they need, but that requires some information or some security setup, and how can we do that?
And then also, another example is getting meeting notes from those calls, which you have to set up that across the board.
So, there's some system-side thing that we have to work on there.
The second thing is harder problems around quoting and approvals and updating the CRM itself.
We use Salesforce, and we're just in the midst of building the connections and the ability for us to update Salesforce with these agentic systems.
And I see that being set up in a way that I've set up with that automated analysis, where you have multi-agent workflows to just make sure that everything is getting done right.
And the second thing is we've sort of reached the Cambrian stage of using agentic systems, which means there's an explosion of excitement and skills and finding out ways to solve anything with AI.
But I see, as we get to this fuller integration and standardization, we're going to want to come back and and and not really limit, but just figure out a really strategic approach for allowing each team to use the agentic system so that the source of truth and all the systems are aligning.
All right. Well, thank you for joining this talk, and I appreciate you, you know, coming here.
Hope you have a great conference.
