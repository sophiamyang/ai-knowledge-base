---
id: "a5a09ea8091744d8"
title: "How do you diffuse AI into the real world? — Varun Shenoy, Long Lake raw transcript"
aliases:
  - "How do you diffuse AI into the real world? — Varun Shenoy, Long Lake raw transcript"
  - "How do you diffuse AI into the real world? — Varun Shenoy, Long Lake"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=B0fjR3yaZFU"
origin: "https://www.youtube.com/watch?v=B0fjR3yaZFU"
type: "raw-transcript"
created: "2026-08-29"
---

# How do you diffuse AI into the real world? — Varun Shenoy, Long Lake Raw Transcript

Hi everyone. I'm Varun.
I'm one of the cofounders at Long Lake.
And I'm excited to share a little bit about what we've been up to for the last 2 years.
It all comes back to a question all of us have asked time and time again.
The models are getting better,
but the real question is how do you actually deploy the AI into the real world?
How do you get the models to complete economically relevant tasks?
Let me start by saying everyone has seen the demo.
Think of the agent automatically booking a flight,
the agent automatically completing a ticket in some kind of customer service portal,
think of an agent completing a block of code ready to commit and go.
The reality is we've all seen this, and it feels like magic.
Two years ago, any of this would have been complete science fiction.
The capabilities are real.
Now, walk with me into a 200-person property management firm:
real people, real properties,
real dollars, real customers all across the US.
You would expect AI to show up by now,
but the reality is nothing has changed at all.
Here's the thing:
this is totally normal, and maybe, in fact, I'd argue
this is what we should expect.
This is true for every general purpose technology.
You know, take electricity, for example.
Electricity was invented in the 1880s,
and it was first demoed at Edison's Pearl Street Station Dynamo Room over in Manhattan.
This was the magic demo of its time.
The reality is it took a long time for electricity to be fully adopted.
Consider a Ford factory.
It's not enough to just have electricity.
You have to rip out the existing motors and equipment.
You have to bring in the new equipment.
You have to go and train everybody to use that very same equipment.
Here's a picture of a Ford electrified moving assembly line in 1924.
These things take time.
Diffusion of any technology takes a generation.
And since everyone here in this room today is talking about AI, I would argue
AI diffusion is perhaps the single most important problem for the next 20 years.
The models are going to keep getting better.
The big question is, how do we actually get these models to be in the real world, complete real tasks,
and make people more efficient, happier, and provide better service?
So, taking a quick step back: who are we?
We are Long Lake.
Over the last 2 years, we've raised over $3 billion from Elad Gil, General Catalyst, and Alpha Wave since our founding.
Here's the strange part:
we don't sell software.
We actually go out and acquire and partner with real services businesses in the world.
We've acquired 35 businesses across HOA and property management, architecture, HR services, and a lot more.
To give you a little bit more flavor, we have roughly a 40-person team right now, split between technology, finance, and operations.
More than half our team is part of the technology team focused on building products,
data, and deploying the core products into the field.
We're an eclectic group of folks. A bunch of ex-founders who've worked in the services before,
ex-military, folks from Palantir, Ramp, Glean,
and from the finance side, Blackstone, HIG, etc.
We are not selling them to these companies above from the outside.
We're actually deploying into these companies and figuring out how to get the technology to work.
And just to show you the scale we're playing at, we announced recently our $6.3 billion take-private of American Express Global Business Travel, the world's largest corporate travel platform.
We own these businesses,
so when the AI doesn't work, it's not their problem.
We're not the vendor.
It's our problem.
Concretely, again, we are not the vendor.
We are the operator owners,
and we work very closely with our teams within the businesses to drive real outcomes.
Now, I want to step back and get to the concrete about the how.
What are the lessons we've learned over the last 2 and 1/2 years,
and what we've learned from deploying AI into companies we've owned?
Three quick lessons:
one, how we move agents from copilots to coworkers;
two, how we leverage real-world data within these businesses.
Remember, we're seeing all of the work that's being done in these real services businesses.
There's a lot of interesting problems and solutions embedded within that.
And then, finally, perhaps the most interesting and exciting is, how do you actually get all of this technology to compound over time by learning loops in the enterprise?
And we'll get to that at the end over here.
So, starting off, from copilots to coworkers.
There's a spectrum of how much autonomy you can give an agent.
On the left here, you see a copilot. This is, you know, your simple RAG chatbot from 2 years ago.
It's very quick. You can ask a question, maybe it's integrated with some systems that can give you information back very, very quickly.
The second step is a synchronous agent.
Consider something like Claude Code, Codex, Claude Cowork.
It's real-time, there's this two-way interaction.
It's a bit more sophisticated than a copilot.
You can go let it run off for 1 to 5 minutes.
It'll call tools, maybe use skills.
It's still synchronous. You still need to step in and ask a query.
So, the next obvious rung of the ladder is the asynchronous agent.
You can come in here, still ask a query,
the agent will go off into the background, do some work, and then come back.
And what's really interesting about asynchronous agents is that the user does not have to be the one that triggers that.
You can have external triggers as well.
Maybe someone completes a certain task, and there is an async job queue that allows the async agent to pull off from and proactively offer advice to the end user.
Then, I'd argue the next step is a long-running agent.
How do you get these agents to work for hours, days, weeks, months, etc.?
I think this is currently a very core problem that a lot of the labs are focused on, as are we.
And then finally, at the end, the holy grail:
an AI coworker.
This is where most people start off.
You want a proactive partner that gets work done just alongside you.
This is what everyone wants to sell you.
But what we've learned from owning the outcomes in this business
is you have to earn the right to do more.
It's not enough to jump to the coworker immediately,
right, for for a bunch of reasons. One, for certain tasks, the models might not quite be there yet,
and two, you actually have to work with these companies in the field,
interact and iterate very, very closely so that they understand that this is the beginning of AI and you can work up the rungs over time.
I think a really unique lens to look at this problem through is that of the jagged frontier.
We all know that agents are incredibly good at writing code.
So, what does the, for example, synchronous agent for code generation look like?
This is super simple. This is just your coding agent, maybe it's Codex, Claude Code, just running on your desktop.
It has access to a file system. You collaborate with it in real time, you get instant feedback, and you iterate.
The next step is, you know, if you look at code code generation, what is the async agent?
This is also fairly straightforward and largely solved.
You take the exact same coding agent,
you wrap it in a sandbox, and you just let it go run.
It can build, it can test, and once it's done with its work, it can provide the code in the form of a PR.
One thing that's really unique about engineers is folks are incredibly good at already parallelizing their work.
It's very common place to launch 10 jobs and be comfortable with the fact that job seven
might finish before job three.
So, engineers are incredibly good at using these async agents.
Now, when we come to services, the equivalent of a synchronous agent's, what we talked about a little bit earlier, it's a coworking agent.
It's an agent that has deep context about your enterprise.
It interacts potentially with MCPs, custom tools, custom integrations,
and you can chat with it synchronously just like any of these other products.
I think this is the frontier here in the bottom right.
What does it mean to build an asynchronous agent for the services?
What does it mean to parallelize work in industries where work is traditionally done in a very, very serial manner?
This is where we spend a lot of time, and this is what I wake up every morning really excited thinking about.
You know, we've we figured out what the async and forking mechanism for code is.
You just spin up a bunch of sandboxes and do work.
What does that look like for the rest of the world?
So, here's a couple questions we think about pretty seriously:
one, you know, the models are trained on code, they want to write code, they're incredibly good at writing code,
how do we leverage these coding agents for actual knowledge work?
You know, rather than wait for the models to catch up on doing services knowledge work,
what if we just use that code knowledge and represent knowledge work as code?
Two, as I mentioned, engineers are used to parallelizing work.
How do you parallelize work that's traditionally serial?
You know, people clean out their inboxes one email by one email, not 10 emails at once.
And finally, how do you move up the ladder here, both in terms of product and user enablement?
What are the right form factors?
And I'd argue, this varies dramatically
from industry to industry.
Just because you have one way of launching an async agent for code doesn't mean that same way is going to work for architecture or property management.
The second point I want to cover today is leveraging real-world data.
We all know this.
Frontier models have learned from everything humanity has written down,
but the most valuable tasks are not on the internet.
How do you actually close the books when you're missing receipts?
How do you scope a building for construction in a blueprint, potentially collaboratively?
How do you coordinate vendors for fixing a broken roof?
All of this knowledge lives in people's heads, in 20-year-old software,
in the way that one senior person on one of these teams just knows how to do it.
How do you make this information explicit and create tasks that you can actually learn from?
So, we've constructed a little bit of a flywheel.
We get our agents to collaborate with our employees to do real work,
and this allows us to generate rich traces of data and information.
Tool calls, the hiccups, the paper cuts, everything that goes wrong with doing real work.
This, in turn, allows us to build real-world evals.
There is a ground truth here.
In the case of the roofing example, the question is, did the roof get repaired?
Did the books get closed?
And this allows us to hill climb and build better agents,
which leads to more and more impact.
And what's really exciting is it ratchets up.
Every week, our hill-climbing benchmarks
become our regression tests,
so our agents get better and better over time.
Just to drive a little bit deeper here on the traces,
there's three upshots of being able to collect these rich traces:
one, we get to generate amazing evals that are built and scored automatically,
and we're able to gather both implicit and explicit feedback.
Explicit feedback in the sense of thumbs ups and thumbs down,
maybe people provide a note telling us whether this response is good or not,
and also implicit feedback,
right? Again, we have the ground truth. Maybe there's some data that the AI generated,
and there's a real diff between that data that the AI generated and what was ultimately submitted.
That's rich information that almost no one else has.
Two, we've started post-training models internally
on all of the data that these businesses operate on
and produce, generally speaking.
This is all data that is completely out of distribution for most frontier labs.
Think of the task I showed at the beginning.
A lot of the models, a lot of the frontier models today just can't do these tasks yet,
and we're trying to post-train our own models internally to be able to do that on the rich source of data that we own.
And then finally, the actual agents themselves.
The real world is incredibly hairy and messy, and you want customization per company.
Every company does things very differently.
Customization per user.
The way each user does their work is very unique.
And customization per client.
The way you work with every client is different.
It's a services business, and you want to uphold those standards.
I love this picture
because it's the whole thing in a single image.
The the way we usually talk about LLM tasks is the top panel,
right? You just It's
It's a slope, you got a bike, but there's clear sight to success.
The reality is most work is not like that, and and you and I both know that.
There are hills and ravines.
There's death by a thousand paper cuts.
But that's what real work looks like.
That's the entire job.
The exceptions are the job.
That's That's the demo.
That's the actual job.
Now, onto the final thing I want to chat with you guys today
is learning loops within the enterprise.
I'd argue there's two hot trends everyone's talking about in 2026:
one, it's continual learning,
how do you make an agent better over time with feedback?
I think there are plenty of sessions this week on how you can use continual learning, whether it's in the prompt or in the weights.
And two, enablement.
How do you get in these enterprises and actually get them to adopt and use AI?
Traditionally speaking,
these two initiatives are owned by two separate teams,
right? The continual learning is owned by a research team, your platform engineering team, enablement's owned by growth, or deployment, or customer experience.
Usually pretty siloed. Not much interaction between the two.
We think these are part of the exact same loop.
The agent only improves if people use it,
and people only use the agent if it's worth adopting.
So, here's a little graphic of a snowball.
More usage drives continual learning, which drives a better agent, which drives more usage again.
All this to say, there's still a really big elephant in the room:
how do you get the initial usage?
I think a lot of people, you know, will use Claude Code or or give it to their whole enterprise, and expect folks to just start using it.
Everyone assumes that usage just shows up.
But as we all know, that's simply not the case. It never does,
right? Getting a 100-year-old firm to change its processes is hard.
You could have the best AI coworker on the internet or on Earth,
and if the people If the person who's closed the books for the last 20 years continues to do things the same way,
nothing changes. Nothing happens.
So, what can you actually do about it?
What you know This This seems like incredibly hard.
What What's the upshot? How do you actually get this stuff to work?
Well, I think a lot about Jensen and how he dominated the market, in his words, with extreme hardware-software co-design,
designing the chips and the software together as one system.
We look at this through the lens of extreme software-service co-design.
How do you co-design our products with the people and the processes at our businesses?
And I'd argue, this is only possible from being within, under the same roof.
We need to meet the people within these companies, both metaphorically,
for example, bringing products to their systems so that the energy required for enablement is kept low,
and also physically.
Get on a plane, show up, say hi, learn what people actually do.
You know, maybe you build a product that's natively embedded into Excel or into their ERP system,
maybe they're 3D design software, or or maybe even their Microsoft products like Outlook, Gmail, etc.
Or you show up in person, you do a lunch and learn with a bunch of folks at one of the companies,
you go to their conferences and you create cotton candy and run a stand for them,
you go mountain biking and ask them about all the difficulties that they have with their actual day-to-day jobs,
or you show up in person, one-on-one, or sometimes even two-on-one, in this case, and just show them how to use the tools,
and learn from the feedback because this is what the rest of the world really looks like.
It's not like the folks in this room or in San Francisco.
It's a lot more like this.
You cannot co-design software with a services business over Zoom or over a support ticket.
You You have to be there. You have to be in person.
And I'd argue, this is the part that actually makes it work.
In order to get AI diffusion to work,
you have to touch some grass.
Thank you so much, and I'll be around for the rest of the day if there's anything I can help with.
My email's up there.
And, yeah. Thank you.
