---
id: "b15d3a7b59b448e1"
title: "AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack raw transcript"
aliases:
  - "AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack raw transcript"
  - "AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=M05vON8i0aI"
origin: "https://www.youtube.com/watch?v=M05vON8i0aI"
type: "raw-transcript"
created: "2026-08-29"
---

# AI-Native Organisations Run on Skills: How to Structure and Scale Them — Imad Touil, QuantumBlack Raw Transcript

Thank you for joining me today.
My name is Imad Touil, I'm a Distinguished Engineer at QuantumBlack.
And today's talk, I want to really cover the how AI-native organisations runs on skills.
But before I really get started, I just want to do like a quick exercise of show of hands.
Can you raise your hand if you have already created and using skills?
Amazing.
Now, can you keep your hand up if you are using it and sharing it within your teams?
Great.
Now, keep your hands up if you have governed, maintained skills across your organization?
Amazing. I see few hands.
But that is what this talk is about.
Today, I'm really looking to break down why this is really critical, how it's important, and how actually you can adopt it across the organization.
But before I get started, what I really want to cover is actually the agentic software stack.
So the agentic software stack has two loops.
So the first loop is all you know, right, is the coding agent, or the coding agent harness, right?
And there's you have some core components: you will have your context manager, the tool and MCPs, memories and states, and skills loader, right?
But then there's an outer loop, which is your workflows, right?
Those have skills, sub-agents, MCP servers that you use, and some hooks sometimes you need them.
To have this running properly, you will need some enablement components at the bottom.
So what you will have is an environment sandbox, you will have your MCP gateway to manage and simplify all of the MCP tools across your organization, a model gateway to, again, manage and optimize for all of your LLMs, either like, you know, open source like running locally or frontier models, and also a graph knowledge graph that abstracts your IT core systems, your codebase, your skills registry, and at the end the workflow marketplace.
And then you have your context layer, right?
The context layer will bring all of what is needed to get the task done.
So this is the project's instructions, think about it as the CLAUDE.md file, the agents.md file, your tools and MCPs schema is actually to understand which tool to use and when, your memory, right, conversation history with the end user, the human is in the loop, and finally the retrieved contents that you can pull from either like files, your codebase, etc.
Now, what I want to really focus on today is the workflow, right?
And I think this is where we kind of like think is kind of a pretty simple workflow in day-to-day when you're trying to actually create an end-to-end product software delivery lifecycle in the organization.
In reality, we all have seen the four steps: specify to define what you want to build, the design or plan to plan you know what what's are you looking to build, then you go to the tasks, we break it down into tasks, and then finally you start implementing, right?
I think this looks familiar.
I think this how most of our coding agents actually are kind of shaped today.
In reality, that is not how it is composed and at scale when you look at the organization complexity.
This is just one step in the journey.
This is like building a product increment.
When you really look at the overall end-to-end lifecycle of something that a business want to build to capture the value out of it all the way to ship it to the client, you will start first of all by defining your product strategy: what to build and how to build it, right?
You set the define the the success metrics, you identify and you break down your plan roadmap for your products.
And to do this, you may need a lot of of insights, right?
So then you do like your market research, you do competitive analysis, you bring this as an input with some customer interviews.
Then you go to the discovery side, right?
So then you start discovering, okay, now I understand what to build, I'm going to break this down into like some problem statements, find the solution, validate the solution, and then probably like experiments, and then create user stories.
And before we start building, in reality, actually you need to prepare your data, right?
In some cases, you will need actually to clean up your data catalog that will support the build of your products, or maybe adjust some of the endpoints connection integration to your core systems that will help you actually build your products.
And this is where the data product delivery comes, so you build your data pipeline, you validate your data quality, and you put your catalog your catalog data assets ready for development.
Then we kind of like go back to the product increment.
That is where where we start.
But then building a product in every organization that I have been serving for the past 18 years in my career, I can see that in one organization you will find like different SDLCs kind of like, you know, scattered across the organization.
Some of it is actually for a mobile application, other is a different department, so different platform.
Some of it is internal platform that is for your employees, other is actually customer-facing.
So it is not like a one workflow that can actually build anything you want for your organization.
When you figure out like what to build and how to build it, you need to run it.
Then we come to the platform engineering ops, right?
That is again when you have your provisioned infrastructure, thinking about how you you build your your infrastructure as code modules, etc.
And then you launch your product.
And the moment you launch it, then you start kind of like the journey of optimizing the performance of your products, trying to look forward like any incidents to resolve.
And then you start the loop again, right?
So at scale, when you look at really building a digital platform, not like a very simple products that you can, you know, solo build and deploy, the landscape is way complex that is expected.
And what you're looking at here is literally like probably 10-20% of what is it, and it's really different from organization to organization.
Now going back to the the the stack, right?
When you look at the workflows, there's like four core components.
The first one is hooks.
MCP servers and sub-agents, those are kind of like given, but it doesn't really bring the right kind of like structured value to your workflows, right?
That's why skills is one of the critical components in your workflows.
Hooks basically what it does, it just kind of like pre kind of like trigger events to to do something along your workflow.
The MCP servers, we all know that, you know, you made in an MCP tool, but tell me like, who actually build a lot of MCPs?
We just use MCPs tools that is actually provided by the tool that we used to use before, right?
So you don't really own those.
The sub-agents is just to minimize the context window.
We just delegate to sub-agent to execute a specific task with is needed.
So at the end of the day, you will find all of your know-how is actually at the skills level, and if you don't have the right structure of your skills, then you're not really having a deterministic workflow.
And one thing to mention is workflows, think about them as harness blueprints that actually shape the behavior of your coding harness, for example, in the runtime.
Now looking at the rise of skills adoption, right?
So just 8 months ago, Anthropic published the first article about skills, right?
Two months later, we had the standard, an open standard that is adopted and starts a lot of agent harnesses starts adopting this new standard.
Around February this year, we have seen most of the actually agents adopt this, even though you don't see them, right?
If you pay attention when the the the agent is thinking, you can see that it's pulling skills as he's going and doing the task.
The other indication here that you need to pay attention to is actually the number of skills that were created, right?
This is just like literally a snapshot that I did across some public GitHub repos, some public skills registries, right?
There's way more than this publicly and within your organizations, right?
So the the the creation of skills and the demand is rising, but we need to understand why.
In the latest SkillsBench, comparing the latest models against like, you know, running the same task against software engineering and cybersecurity without skills, it did well, right, cuz what that's what is expected and is going to continue to be improving day after day, right?
But then when we applied skills that are more deterministic, the outcome was clearly higher than than without it.
Now if you think about now like how like the anatomy of skills and how you actually design and implement skills in your organization, this is not like a new problem that we are trying to solve here, right?
We have solved this with the microservice kind of movements, right?
So microservices need to have all of these design principles, right?
This is like a software kind of like, you know, problem that we used to solve.
Is it's similar: so skills need to be reusable, right?
Need to be modular, need to be like you can discover your skills, so if you are sitting in one team and you need a skills, you actually can automatically discover and tap to the skills.
It's portable, that you can actually use skills across workflows, but also you can use skills across harnesses.
Again, everyone adopted the same standard.
So if I'm having a skill on Claude Code and I want to move it to Cursor, it's going to just work.
Specialized skills, that is where the value.
You should not build like a one skill like a monolith again.
It should be specialized to define one tasks specifically.
Composable: skills need to be designed in a way that actually can compose, so you don't have duplication across your skills when you're trying to run them that's conflicts with each other.
Consistent: that is actually what one of the key items of skills is actually consistency and deterministic.
And finally cost-efficient.
And for cost, I can go for an another hour talk, but it's basically the skills comes to solve a key problem around the context window, right?
It's actually putting with the progressive disclosure pattern the right skills, the right amount of skills in the right time to solve the right problem, and that's reduce the token usage.
This define a new units, right, that makes your know-how in your organization executable, portable, and cheap.
On the right-hand side, just a very simple example of data retention policy, right?
When it's come to regulation, you need to understand and make sure to instruct your agents while you're manipulating, for example, your customer data, you should make sure that this data is manipulated according to the regulation, right?
And that bring me to the next example.
On the left-hand side, you can see that there's like a think about like a a catalog of skills.
And in the right-hand side is your harness, and the output is on the right-hand side, right?
So the composable skills at the regulation level, you have the skill that I just showed earlier, which is the retention policy, but you will need disclosure standards, you will need the GDPR rules that need to be respected, you will need the filing templates, right?
So all of this kind of think about it as like defining how any data, any feature that is built across your web, mobile, like you know different applications across your organizations, is really respecting these rules.
And this gets pulled automatically by on the runtime by the regulatory disclosure review workflow.
And the outcome is expected: it's deterministic, you have an audit, an audit reports that you can actually store, you have specific identification of if there is anything to improve, and that there's kind of like loop back to improve your your codebase.
However, if we don't govern skills, we will start creating a new class of technical debts, right?
First of all, you will find out that you are having a lot of duplication in your organization.
So if teams are not collaborating and everyone is, think about it, using the same technology stack, the same infrastructure, you for sure building the same skills over and over again without sharing them.
Quality: if you don't test and make sure that you're maintaining and you're validating your skills, not like against your task, but also against the latest models that comes, right, then the quality start degrading over time.
You should be able to discover your skills.
In in reality, without a governance, you cannot really discover it.
Think about it as the the backstage, the IDP, right?
It's it's come to solve a problem where, okay, I need to understand who owns this microservice back in the days, right?
I don't need to talk to anyone, I just need to tap into the service catalog and immediately find who actually own it.
That is brings ownership part.
If you don't have an owner, then no one will be able to maintain, scale those skills.
Composability is not something that comes by default.
You need to have a governance way to to align what to build and how to design it is thinking about the domain-driven approach that we have been taking also for for many years, right?
It's similar to how you shape your skills catalog.
Security: again, some of all of us like we experiment with public skills, right?
But when you think about it, some skills may have some prompt injection, and skills actually does have scripts because that's is the deterministic parts of it, because you can run a specific script for a specific task.
So if you don't have, again, a pipeline that check your security, you may be pulling something that is insecure.
And permissions: not every skills is actually something that anyone in the organization should access.
Some skills may have some business logic that is very sensitive, right?
So the access control is is also crucial at this stage.
Now how to bring this to your organization?
First of all, you need to allow at the individual level to create, test, improve, and use those skills.
Again, it shouldn't be random, it should be structured way.
There's a different tools out there, you just need to decide which tool actually you want to agree on, and you use that mechanism at the individual level.
The moment you create a skills, you need to be sharing this with your team, right?
Your team starts collaborating to improve these skills, and think about it, you're building the same technology stack, building the same products, so it's going to evolve really quickly.
But then you move on to a very critical points, which is the centralized platform.
That is where all of what I have been covering so far come to play.
You need a centralized platform that have a catalog with metadata in it that actually can discover skills, and could be searchable, you can have an MCP that's actually plugged to this catalog, search for this skill, and a CLI to pull the skills back to your either your IDE if you're locally or to your sandbox in your factory.
Then you have the dependencies, so you need to understand the dependencies between the skills as well.
You have the versioning and and lifecycle, so you understand which version of the skills is actually the latest, and a very good example when I'm using, for example, building a a functionality, I can the agent automatically capture that there is a latest version of that skill and pull it, right?
So this versioning help also to pull the the the right latest changes from the skills registry.
Access control, again as I said, if you don't know who is accessing what, that is a huge gap, and finally evaluation and observability.
And then all of this is actually play around a governance, and this is where technology stop solving the problem, right?
So you've figured out all of this, all good.
Now who's going to govern this?
And that is where you know it really depend how your organization is structured today.
That is where you should have your architects, your engineering leads, infra leads, etc., and cyber leads actually sitting down, owning parts of those domains and making sure that these skills when it gets updated is actually according to the policy that you want to adhere within your organization and drive this change.
And finally, when you get this right, what you will have, you would have at the organization level all of your teams pulling from one centralized place high-quality skills, executing them, and pulling them back to to the centralized platform if it is improved.
Now what I want to bring this, cuz it's a little bit of a unclear view, so what I created, I created a simulation, right?
So think about this: this is your organization today, right?
And what I have here, I have just a random teams.
I have 15 teams created, 5 to 12 like per team, you have skills per engineers, contribution, you have the average skills utilization, kind of like on average like how much time skills are being pulled, percentage of duplication across the team kind of as a ratio, and the skills quality and security ratio.
Now, if I run this across 6 months, what's really happening, and think about it, this is already happening within your organization, is teams are creating and using the skills, right?
But we don't have visibility.
And skills, again, they're tightly coupled to your productivity uplift.
If, for example, the example that I shared earlier on the regulation, if we don't have a skill about the regulation, that is someone is vibe coding back and forth and trying to figure out exactly how to steer the agent to implement it properly, right?
That is burning more tokens from one side cost-wise, but also the productivity is spending more time rather than getting it in one shot the right answer.
And the quality and security is similar.
If you don't have clear you know skills defined and maintained, you will have a low quality in your implementation, because then is up to the human to to decide this, and different the you know maturity from team to team, you can see the difference.
And that is why, for example, if I look just randomly at this this is like, you can see the productivity of these teams, kind of a medium, right?
If I look at this one, is a is a bit of like, I don't know, it's low, medium productivity, quality, and security also a medium, but when it came to the cost is really high.
Okay.
Now, let's actually say, okay, how this looks like if I governed all of the my skills in my in my organizations?
What's going to happen is, of course, some of them will split, right?
And this is reality.
It's going to be perfect as we expect.
But at least what you will see, you will see actually some common ground across all of your teams.
The moment you govern, you publish one skill, the next engineer trying to build a new skill, the coding agent harness will identify this skill that is already available and pull it, right?
So you you almost solve all of the issues that that I covered about governance.
And one last point is, when it came to skills, is just one component of your workflows, as I said, right?
So that doesn't mean if you've figured out skills, that's it, you're good.
No, you need to apply the same kind of like approach and solution for your whole workflows, and you may think to apply this again.
If you think about it like if you have a a centralized platform that has all of your workflows, right?
From one side, you're centralizing the workflows, which is also having the skills, but also if the next engineer came and want to, I don't know, like provision infrastructure, they can tap into a workflow and peel that workflow with the required skills and run it and test it.
Again, if it's something need to be improved in the workflow, you can easily push it back to to the centralized platform for your organization to use.
Now, before I wrap up, what I want to leave you with is this is just the start the beginning.
You see like this just we're talking about 6 to 8 months.
What's coming next and I would invite you to already explore is skills registry, right?
You should have one, if not already.
And the good news is all of the players that's been solving the IDP problem like internal developer portal, they already starts centralizing this capability, right?
So if you don't have it today, maybe in a couple of months you will see it coming.
But also there's a lot of tools that's actually solving this specific problem.
Second is skills evaluation.
There's still kind of like a discussion on what is the right approach to to you know to to evaluate skills.
The easy thing that I found so far very valuable is actually test like you you lint static tests your or evaluate your skills against the Anthropic best practices, right?
If the skill is not invoked properly, if the skill is not structured properly, there's high chance that it's not going to be high quality.
And finally is auto-evolving.
And again, this is what everyone kind of like is is the next hype right now, like, yeah, I can create like a an a closed loop that can evolve automatically my skills.
So what, right?
If you automatically starts this machine, the impact will be way more than it is today, because what I shared earlier, is going to be just maintaining and auto-evolving skills without that governance in place that's actually put the guardrails for your organization.
And at this points, I will leave you here.
Thank you so much for your listening, and looking forward, if you have any question, I will be in the leadership lounge, feel free to grab me.
Thank you so much.
