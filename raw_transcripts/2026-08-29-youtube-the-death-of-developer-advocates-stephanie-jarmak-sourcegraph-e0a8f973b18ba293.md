---
id: "e0a8f973b18ba293"
title: "The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph raw transcript"
aliases:
  - "The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph raw transcript"
  - "The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=Lrw0jqBNaw0"
origin: "https://www.youtube.com/watch?v=Lrw0jqBNaw0"
type: "raw-transcript"
created: "2026-08-29"
---

# The Death of Developer Advocates — Stephanie Jarmak, Sourcegraph Raw Transcript

Hi, everyone. Sorry for the start with technical difficulties and all of that.

We made it to the end of this track. Super exciting.

Thank you, everybody, for sticking it out this long.

Um, are there any developer advocates or DevRel people in the audience? Raise your hand.

Yeah? Okay. So, did you come to, like, throw tomatoes at me? Because I'm talking about the death now.

Okay. So, it's not going to be all doom and gloom like that.

Um, a bit of, like, backstory in this.

Um, I'm a research scientist. So, last year, I was an astronomer,

and I just sort of like wound up—I didn't know what GTM was or any of that. Just sort of wound up in this.

Um, and I submitted like a bunch of boring, science-y, eval talks that were unceremoniously, I assumed, thrown into the trash for this conference.

But my manager, who is a developer advocate,

he put in, you know, "The Death of Developer Advocates", which is, you know, appropriately buzzwordy and hype-y, and so, so that was great.

But his title is developer advocate, so it didn't really necessarily make as much sense

for him to be coming up here and giving his eulogy.

So we brainstormed like maybe I would dress up as like a robot and like maul him and attack him on the stage or something like that.

Um, but then it just logistically it was going to be hard to do that.

So, he just went on vacation.

So, I'm here as the agent advocate to talk about this sort of like new role, and

try to advocate for it, and convince all of you that we should all be agent advocates to help

in this new era.

So, zooming out a little bit, and going back in time a bit, because I was trying to talk about developer advocates to somebody at the conference yesterday, and their eyes, like, glazed over. They had no idea what I was talking about.

So, just to sort of talk about what this thing is that I'm saying is dead.

So, back in the '80s, right, it was called like software evangelism,

where one would go forth and speak the good word of the product, and bring it out there.

Then, fast-forward to the 2010s or so, that's when developer advocacy started to become a thing,

where now instead of having this single trajectory of the communication pathway, now it's a feedback loop, and a two-way street where you have these people with very deep empathy for developers, who understand them and speak their language,

and could understand what their needs were, and then bring that back to the product.

And then, these developers, right, fast-forward even more, they have so much influence within their company, and basically become these like kings makers.

And so, developer experience became a very important aspect of the go-to-market sort of strategy.

Um, but now, in 2026,

developers are no longer working alone, and what it means to be a developer is

completely changing.

And so, our role, right, as developer advocates, developer and developer relations, we're relating to developers. And so, as the role of developers fundamentally changing,

so must then does the role of the developer advocate.

So, in this slide, I'm just kind of talking about the other users, right? So what's happening with DevRel outside of the agent?

So most of the talk is going to be talking about the agent as a user.

But, I also just did want to bring up, right, that engineers, they're becoming like these orchestrators of these fleets of agents, babysitters, and whatnot

of these things.

And their job, like all of the job postings and whatnot, these languages continuously changing, right? They're expected to have this AI fluency.

And at the same time, there's also, you know, people like me, like non-engineers, right?

I was a research scientist. I had like zero commits on GitHub last year, and now I have 12,000, and I'm like an open-source maintainer for multi-agent orchestration framework.

Like, we have so much like capability now with all of these agents, and now anybody with these agents can use dev tools, essentially.

So, you have this whole other persona in ICP to potentially be relating to, and having empathy with when you're they're using your product.

So, let's talk about now this whole new user that we have in the form of an agent.

So, an agent is somewhat unique, right, in the sense that it is both the user of your tool in a very similar way to the developer.

It's going out reading your docs, but it's just reading them differently, because it's a machine.

You know, it's calling the API. It's It has its own frustrations with how it's encountering errors, and recovering from them, right?

But then, it's also a recommender of your tools. But somewhat similar, right, to developers in the way that they are also recommenders of your tools in a more organic, bottom-up way.

So, the whole, you know, basis for DevRel, right, is to encourage that bottom-up adoption.

But now, the adoption, the recommendation system, a lot of it's being driven by the agent itself, that is either, you know, maybe servicing your product directly through like ChatGPT, or Claude, like directly in a Q&A sort of environment.

Or, it's as we had heard like in some of the previous talks where the speaker asked folks like, "How many of you have just let your agent install a library for you?"

And like there were many hands went up, right?

So, there's this like recommender of tools where basically it's just installing these like frameworks and things directly and embedding them into the workflow, and sort of working with the developer in that taste.

So, I know it's late for numbers. You don't have to read them

or anything like that.

So, I have a couple different concrete examples for measuring these seats, right, as I am a data science scientist nerd person.

So, one of my first projects when I was working on this,

when I became an agent advocate, was to build a benchmark called CodeScaleBench.

And so, I developed hundreds of tasks that were reflective of the software development lifecycle.

And it basically unleashed these agents with and without our product's tooling.

So, I work at Sourcegraph and we have a code navigation MCP tool.

And the point of that was to understand, okay, how is our tool helping the agent do the work that it's, you know, going to be doing?

And when it isn't working well, why isn't it working well, so that we can then go in and actually fix that.

So, I have thousands and thousands of these traces.

And how as we have heard in like the previous talks, like now we have these amazing logs of data for like these really tight feedback loops where you can see exactly where it's breaking down, and then go in and fix it.

So, this one specific example here was when I was looking at how it was like using a read tool.

And the model had these expectations based off of its like biases from how it from its training data of what it expected for a particular command that would be available within the tool.

And there's nothing in our description that would have like led it to believe otherwise.

So, it tried to use like read line instead of start line or something like that, and then it ended up failing.

But then, at least the error told it why it failed. So, it was like, "Okay, that that was a good part of it." So, it was able to fix itself.

But then, it's burning, right, an entire turn just failing when you could just go in and fix that aspect of like how it's interacting with the tool.

And this is really important, right, to gather that feedback and understand the friction that like now your new agent user is having with your tool.

Because it's a way that different organizations are going to be evaluating your tool, right, in terms of not just is it working well, but like how many tokens is the agent dealing with to work with your tool, and how fast is it?

So, this is, you know, really an important aspect of the role to measure how these users are using it.

The other side of it is like the recommendation layer, right? So the GEO instead of SEO, so the generative engine optimization.

And I didn't mention it before, but in the previous slide,

I had a GitHub repo. Like, there's two different toy projects that I put together.

At the end of the talk, there's like a QR code with a link that you can send your agent to to like have access to all this.

So, don't worry about like taking screenshots or anything. All of all of the data will be released to you.

So, anyway, back to this.

I set up a little experiment, right, to see how these different chatbots, and agents, and whatnot were recommending our product, or like mentioning it at all.

And so, there's a, you know, process to that, because you you want to understand like what is your ICP actually doing when you would want your product to be surfaced.

So, there was a bit of a gap that I found.

If I had designed some of these prompts around somebody who like was actively shopping for this sort of code intelligence sort of tooling and doing a comparative sort of thing,

then our product was ending up being recommended like 65% of the time.

But, what I found was the arguably like the more typical use case and where we'd want to be showing up for people when they're encountering a specific pain or have a specific need where our product could serve them better,

zero mentions, right?

So, in this particular instance,

I put in a prompt that was like, "We keep breaking downstream services when we change shared libraries, because we can't see all the consumers."

And you know, our one part of our product is being able to have this observability layer to like see across all the repo.

So, we'd want a some level of like attribution or recognition from from an agent to say, "Hey, you could use something like this."

But instead, it said, "Uh, you could just have your developers make a wiki page," or something.

But, what this, you know, we wouldn't know that without running these sorts of experiments and getting this sort of data.

So, what this leads to is like then you can have a hypothesis of, "Okay, maybe the messaging that we're putting out there isn't attributing some of these pains and use cases clearly enough for the agents to be picking it up."

So, we have like a content campaign in the works to make changes to our website, and then we can directly measure whether that has like an actual lift.

And not necessarily in the form of like anything that was baked into the training data, but then how the agents that are using those like web search tool calls, how they are then interpreting the information about your product.

So, you know, there are just some different ways that you could think about guiding the agent to help support like the surfacing, the discoverability of your product, and this user finding it at their moment of need, right?

So, for example,

this whole field is moving so fast.

So, I mean, training data is like always going to be stale.

Actually, in the GEO pilot study that I did, the data that I was showing there, that was using Claude Sonnet 4.

It's very old, obviously. And I just today this afternoon ran it with 4.6 thinking that, "Okay, surely it's going to it's going to be better. It's going to know like improved information about our product."

But, so in the previous model, it kept pitching Cody, which was like one of our older products.

But, if I When I ran it again, it it pitched Cody even more, right?

Because like now you have all of these like old models like outputting content that then is like compounding in the internet. So you have to figure out like how to bury all of that noise with your true signal.

And the way that some folks are working on that is, as we've heard from other people, like these LLMs.txt sort of pages, right?

So, you have more authoritative sources of truth that you're hoping to direct the agent to.

But, they still need to be using the tools and using real-time information and provenance to be able to give accurate answers about your product.

You also want to give like the agent something to quote, right? That they they want to bring something that they can really sell to the to the user, right?

So, you want current examples, and keep everything up-to-date.

Like even if your stuff hasn't changed in 2 years, which would be shocking,

even if it hasn't, like keep everything up-to-date and fresh, because that, you know, part of that is how they how have their relevance algorithm.

And they also really, really like charts, and FAQs, and things like that.

And you also want to make sure your product is where the agents are, right?

You're going to market. So, go go to agent market, right?

So, make sure you're in the marketplace, in the MCP registries, everywhere that you would expect an agent to be able to easily find you.

And also make sure that, you know, that whole you reduce as much friction as possible for an agent or and developer to go from finding out about your tool to embedding it in their workflow.

Because if an agent realizes your tool requires like three different demos, and emailing sales reps, and stuff, they're never going to say, "Hey, user, like here's what you should do. But FYI, you're going to have to do all this other stuff." It's just not going to happen.

And then, also make sure that you are covering that those pains, right?

Because that's how a user is going to be more like in their time of need, right?

That's going to be the best opportunity for your product and your service, right, to be surfaced to them.

And so, you want to make sure that there's enough content out there on the internet for the agent to like be aware of that and make those connections for you.

And so, right, there's this like ongoing question of what even the heck is DevRel, and advocacy, and now now this agent advocacy thing, right?

It's like, where does it fit? Where does it go?

Like, is it engineering? Is it product? Is it marketing?

It's like, yeah, yes, yes. It's all of those things.

And with the rise of agents, it hasn't gotten any clearer, right? Those seams haven't gotten any clearer.

If anything, though, everybody's role across the organization has gotten fuzzier.

So, that actually helps in a lot of ways.

And but you can sort of split it up and think about it in terms of like these different flavors, right?

And you can mix and match depending on whatever skills and abilities various employees have within your organization, and whatever the product needs at a given time.

So, you have like the engineering flavor, right?

And those are folks that are partnering directly with the engineering team to make these interfaces for how the agent is talking to your product, like through the MCP server, and building out these evals and the instrumentation.

Then, you have the product flavor. So, those are folks that are going to own the end-to-end agentic experience, right?

And so, translating these evals to bring it to the product team, and like having the agent experience rubrics, and how they're encountering all that content.

And then, you have the marketing flavor, right? And that should be the folks that are really owning that pipe gen, and how the agents are like entering the funnel and finding out about your product, and then bringing the developers along with them by surfacing those recommendations.

So, I know I, you know, said "the death", right, of developer advocates.

Um, but the core, right, of DevRel still holds.

It's just you have a change in your audience.

So, it's still extremely important to do enablement, right?

It's just the type of enablement is a bit different.

You're educating developers now who are have a completely different type of job, where they're orchestrating these fleets of agents.

And you're also educating agents, right?

So you're having to put out content that is machine-readable, has like agent-friendly APIs, all of these things that make it as easy as possible to use your product both for human developers, and for the agents that they're using.

And community is also more important than ever.

Right? Having that human-to-human connection, where developers can come,

and bring their agents also into the loop, right?

So, that's another component that needs to be considered when you're building these different communities.

Because there's all these questions, right, of privacy, and like data concern as well.

If people are like bringing their Claudes and whatnot like into the Discord, and they're like recording all of the conversations and everything, like this is just like a new thing that you have to think of as a community builder.

And then, there's the feedback loop. So, you're still responsible for bringing the voice of the developer who's using the agents back to the organization.

But then, you can also basically spin up like thousands of these agents to perform experiments on them, experiments that you can't really like do as easily with the developers who don't want to maybe talk to you that much.

And then, credibility, right?

So, you need to be earning credibility both from human developers,

so like don't like not using Claude slop at them, right?

And tell your AEs to stop that as well. Nobody Everybody knows what it is, and nobody likes it.

And but then credibility like actually Claude loves its own slop for whatever reason.

So, there's a bias, right, from the agents of their own content.

So, whenever you're making like agent-facing content, as long as it's structured, you can have as many em dashes and whatevers as it wants.

But, it's just a completely different sort of credibility landscape, humans versus agents.

So, what I'm advocating for here, right, is like building out a curb cut.

So, curb cuts were built for wheelchairs, like built for a specific user to use them.

Um, but now, everybody, you know, benefits from that, right? Anybody with wheels, right, strollers, and suitcases, and all of those things.

So, my argument is that by serving the agents, the human path gets clearer, too.

There's just, you know, there's one more user in the room now, but they're still serving the human on the other end, and we're all working together on this.

So, for, you know, DevRel, one quick thing that you could do like right away is point a coding agent at your docs, and then looking through that transcript, and start developing your agent experience report.

And then, if you're more on the GTM side,

start like developing some of these experiments with the GEO, putting together those prompts, and looking at the mentions versus recommendations.

And I made this whole talk agent-legible, right?

So, there's a QR code there as well as a couple different toy repos that have some templates for you to get started.

And that's it.
