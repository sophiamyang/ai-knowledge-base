---
id: "9642ca6ea29ef8ca"
title: "Agent Frameworks Considered Harmful — Rémi Louf, .txt raw transcript"
aliases:
  - "Agent Frameworks Considered Harmful — Rémi Louf, .txt raw transcript"
  - "Agent Frameworks Considered Harmful — Rémi Louf, .txt"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=KHudyx5wW3U"
origin: "https://www.youtube.com/watch?v=KHudyx5wW3U"
type: "raw-transcript"
created: "2026-08-29"
---

# Agent Frameworks Considered Harmful — Rémi Louf, .txt Raw Transcript

Hi everyone.
So, originally I thought I was going to give a very technical talk, but I saw I was in the leadership track,
which I'm not sure what it means, but I was like, "Okay, I'm going to do half high-level and half technical."
So, it's more a story about what I,
you know, what I did in January because in around December,
um agents kind of became really good.
Uh you know, there was a step function, something happened.
Uh I think it was Opus 4.6.
And that's when I realized, and I work in AI, where I was like, "Okay, this thing is really happening."
And so I took 2 weeks out.
I took 2 weeks away.
So, I'm the CEO of ddotxt.ai,
uh you know, which is 15 people company.
I just told my CTO. I was like, "Okay, I'm just going to go away for 2 weeks, and I'm just going to dive in this thing, and try to understand what we can get out of it
and how good it is."
And so the story is, you know,
it is a story of me scratching my own itch for 2 weeks and trying to figure out how we can use, actually use agents, and what are good primitives to build agents, and whether, you know, it already exists.
Um this was a really clickbait title, but actually, it turns out to be a good title even for this talk.
Um so what you can see here on the left, the castle is my office.
Uh that's true. I do rent an office in that castle.
And the small thing with an arrow uh that you can see is like this robot mower, which kind of works unattended all day, every day.
Uh it just does its stuff
in the background without anyone having to use a remote control or think about it or anything.
And I kind of wanted the same thing for my morning because my mornings are always the same thing, the first couple hours.
It's browse market news, review of like Linear, could be Jira, my CRM,
and also, I like to walk for an hour, about an hour in the morning, and then the next hour is spent trying to process the really long voice note that, you know, was recorded while walking.
And you know,
all I wanted was my morning briefing with my coffee.
And that's kind of what we've been told for a couple of years that what the future would be.
Um, but then when you really start working with it, even if you're not
coding, all you get is a TUI today.
Uh, so it's amazing. You can code.
You can actually, you know, I started doing things that were not coding in it.
They're great for this.
Uh, agents are great for this.
It's kind of the equivalent of having a robot like a tractor mower that you still have to stay on, even if it's driving by itself, right?
It's kind of very frustrating because you have to It can do many things,
but you still have to be on.
And so, of course, the labs didn't stop there,
and they came up with apps,
uh which I call basically SSH with vibes.
That's great.
But in this situation,
when that came up, I was like, "Woah, that's awesome.
I don't have to use like a term like SSH on my phone anymore. Codex is great."
However, I noticed I just started, you know, and I was on my walk, and I was just instructing the agent to do things while I was walking, and so I wasn't thinking, you know, very clearly anymore.
I just started running agents on my phone during my morning walk.
And this is not great because this is the equivalent of this
is you're kind of midway.
Uh you know, it's not the tractor that you have to stay on. It can actually do something without you being right next to it,
but you still have this remote control that you know, you kind of have to change the trajectory every now and then.
Uh that's useful.
It's kind of absurd uh when you think about it.
And actually, when you look at people
like on their phone all the time, just screen this, it's kind of absurd, and it's clearly transitional.
Like surely we're not It's not It's not going to stop there.
Um and so, I did a very dumb thing as a CEO, which is I started coding.
Uh don't tell my board.
And I started to build the dumbest thing that could possibly work.
And of course, it became a really, a crazy rabbit hole.
Uh the repo is there if you want to take a look at it.
The code is not amazing,
uh but it works.
Um so the first thing is that
you know, I started using frameworks.
Uh I mean they're great frameworks, and I'm not going to name any frameworks because they're all good in their own way, and they all have flaws in their own way, which is fine.
Uh, but I spent all my time actually editing the prompt within the code, and I was like, "This is actually not very useful."
So, I'm like everyone here. I hate YAML,
uh, like the next guy.
But I still found that this was actually a lot easier to start implementing agents without code.
Uh, you can version it. You can diff it.
Uh, you can review in the PR.
Um, but it's just and it's just so easy.
You can just, you know, write your file, you drop it in a folder,
and then it just magically appears once you have the runtime, and it just magically works.
Um and you know,
then I needed like my market watch to run every morning while I'm, you know, while I'm walking in the fields.
And for that, we have things that you know, uh have been around for a while, which is cron jobs.
Uh and schedules
specify, you know, when the agents need to be run.
And also, we'll see, it's very important later,
uh, they publish uh,
they publish events.
And, you know, Markdown and cron, obviously, you know, it's much more complicated than that under the hood, but the interface is this.
You don't write code,
and that's the whole product so far.
And honestly, it just mostly worked at this point.
I'll I'll come back on "mostly" uh later.
And so this is actually a real picture of my one of my morning walks.
And so what I do is I
record voice notes while I'm walking.
Uh, but cron, you know, cron jobs I mean people would use cron jobs for this because that's what's available in Codex today,
but they're not ideal
because they cover when,
but this is just one point in time. It doesn't cover "because this happened."
And, you know, things that happen in our system,
like automatically, when you drop the voice note now in the system, it will emit an event,
and an agent will react to that event.
And it's the same thing when you have a new email, a new entry in the CRM,
I mean anything, a new PR that's open, a new PR that's merged, et cetera. It just reacts to events.
It's not just a cron job.
And that and that means that, you know,
agent, so the voice note processor, it's just, you know, not a cron job, but here you have accepts and returns.
So, it just declared what it accepts
and what it returns as an event.
And here it accepts a voice note, transcribes it, turn it into durable notes on the right,
and it emits a new event,
and for that, it uses structured outputs, so I'll come back to this.
And, you know, now we finally have the future we were promised because
that voice note agent emits a voice note processed,
and then I have my daily brief agent that actually will take the output of the cron job, will take the output of the voice note agents, and recreate
my daily brief, which is posted as a Slack message. So, the slack.message.post event is actually uh
is actually uh, like, um
a process actually subscribes to this and emits,
uh, and sends a Slack message to me.
It's actually This is a real This is a real thing. It's working. I can show you after
on my phone.
And you know,
there are frameworks are going to sell you the fact that you need graphs for this in code.
Uh, you do not need graph uh in this case. All you need is events.
You have no edges to maintain. Agents simply subscribe to events.
Anyone can come in and edit this.
You don't need to yeah, you don't need to know how to code. You just need to know what events exist in the system.
Fan-in and fan-out are free. No code, and it's just drop a file, and the topology emerges
whatever the log says happened.
And, you know,
then of course I,
I tried to run it. So, the first version took about
I mean you know, I cheated. I cheated. I used uh I used Codex,
and it took about like a day to write like the first thing
uh out of my week. But, of course, I tried it, and it broke.
Uh, so these are real examples actually.
The dates? No, but it's real examples.
It's like the first day,
daily brief was posted to Slack twice.
Um On Wednesday, one of my voice notes completely vanished.
And then, you know, towards the end of the week, I I kind of like played with the prompts all week, and the market brief was garbage.
But I didn't version uh
I didn't version my changes,
and I couldn't remember actually what I changed in the prompt that made the thing
completely useless.
Now, if there are distributed or ex-distributed engineers in the room,
you probably know this shopping list already.
Uh, there is nothing new under the sun.
And, you know,
each failure, so each of these failure modes that you found,
actually led to building one piece of what turned out to be a runtime.
So, the lost note actually turned into a log. I just wanted everything
to be saved forever so that I could go back to it and look into uh into what happened.
The duplicates, it was because I was not following, you know, it did several attempts, and I was not following them. I didn't have a proper queue, I was not counting the attempts,
etcetera, etcetera.
And then, uh probably the most interesting part is the lost prompt. I got into a really deep rabbit hole in there,
and I just ended up uh building a content like a content-addressed system for this.
Uh, content-addressed system, you can think of Git. Uh, you can think of Nix and any other build system.
And, you know, that was And I didn't do this because I wanted to design a runtime. I mean, by that point, I still just wanted my agents to work.
And I also like the distraction.
Uh, and I just paid off debt as it appeared, like errors as they appeared.
Uh I I hope my board won't see this talk.
Uh so the log,
the log is the system's memory.
Uh nothing is lost, and everything is observed.
Uh you can, you know, you only have one append-only events table. On the left, it's a real command-line uh
like command, `zeta events`, and you get all the events.
They are causally linked as well, like you know which event triggered which event,
which happens to be super useful when you're debugging,
and you know, even with three, four agents, you start having like major debugging headaches, so that was super super helpful.
Um And everything is queryable,
which again for debugging.
The second thing is, you know,
okay, we have a log, so we can trace back things, etc.
But it's still really hard to know what went into the, like what went to the model, what prompt was sent to the model again.
Because what you see when you're using Codex is kind of a lie.
Like you kind of have like a live chat session with the model, and so you tend to think that, "Oh, that's what the model saw,
and you know, that's exactly so I can understand what happened." The truth is
that's not exactly what the model saw.
Um there are many reasons for that. One is I mean compaction, obviously, is a big is a big thing, but also,
you know, there are just quirks. Also, you know, OpenAI doesn't share, or and Anthropic for that matter, don't share the thinking with you, the thinking traces. So, you have no idea.
I mean, kind of have an idea of what went in, but not completely either.
And so, you need something different.
Uh you need something different,
and that was the big rabbit hole,
which is trying to find a way, or build a system, where you can trace back to what the model saw internally.
And so, what I did was basically built, I mean,
nothing new, this is basically how a build system works.
Uh, so you have different parts for a prompt.
You'll have your system prompt,
you'll have a description of your first skill, of your second skill, then you have the description of your tools,
you'll have your user message, which is the question to the model.
Each one of those is stored and addressed,
and you know, stored somewhere
as a identifier, which is a hash.
And so, when we build a prompt, instead of building a piece of I mean, before rendering the text, we actually represent the prompt as a list of these uh of these hashes.
And so,
what that means is that down the line, when I have a model answer, which by the way is also stored in the same way,
we can trace back to the prompt very easily, and then from that prompt, we can know exactly what went into the model's context,
which actually matters a lot. I mean, it matters a lot for debugging,
but it also matters I mean, it makes compaction a lot easier. You're just manipulating a graph, right? You're not manipulating strings.
It's just a lot easier, and it makes KV cache management a lot easier as well indirectly.
And, but I think that when, you know,
I guess probably
the main advantage at when you use that at scale is really auditability.
It's like you can know exactly what happened
with that agent and why it returned what it returned.
And so, you know,
I'm just going to go pretty pretty quickly over this.
Uh, what you get once you have this graph
is you get diffs. Like, you can say, "Okay, what changed between these two runs?"
Like, what which components changed? Was it just my message?
Did I like give the model a different skill? Did I give it a different tool?
So, you can just yeah, you can just run this function, and it will show you, you know, the difference between the runs. So, here you have,
you know, three components that were identical.
There's one which is, you know, the user message changed,
and then you had all these other messages that were actually, you know, that were continuing it's continuation of a single session.
Uh, then you have another thing for free, which is replays.
Uh, replays turned out to be really useful for me
because
after a while, I mean, when I saw the cost ramp up, like the thing when you have observability is that you do realize that costs increase very quickly. I wanted to try with open source models, and so I wanted to rebuild old requests for to eval and see if I got the same thing out, if I got something satisfactory, if I need to change anything.
And
turns out that once you have,
uh you know, this content-addressing system, you can rebuild the request from the graph, and you can just replay it exactly the same. And you can, you know, resend. You can use a different model,
uh you can use a different request if you want. You can uh you can change it, and so
yeah, you get actually a lot of things I mean for free. You need to implement the thing.
Um and so, this is kind of different
um from what you find I mean, what I found when I started doing this. It might be different today because it was a couple of months ago.
Is that out there you had a lot of libraries. So, it's just frameworks, and frameworks just call code.
Uh your agents live inside their abstractions,
um and I don't like analogies with, you know, operating system. Okay, everyone has used that analogy, but okay, let's say a kernel like runs processes,
and your agent kind of is a process. It doesn't matter what it does actually,
uh but the system can schedule it. It's built to isolate it. It can isolate it and journals it with the log,
and the agent definition, so the Markdown, is userland. Like you don't need to use it with that system if you don't want to. Actually, you have a front end that doesn't use this Markdown,
uh this Markdown format at all.
And, okay, here's a very important point,
and, you know, that's kind of a takeaway, and it's also what justifies me working on this because disclaimer, structured outputs is our specialty. We've been working on this for 3 years,
and it just ended up being a big dogfooding project. And the reason why I did this
at the beginning was not because I absolutely wanted to use our software. I didn't necessarily want to,
you know, fork llama.cpp to add our software, etc. It's just because Anthropic was terrible at structured outputs, and so like 20% of my events were wrong and were rejected by the system.
So, that's why I ended up doing this.
And the goal, you know, the job of the kernel is actually to make bad actions impossible,
not just unlikely. And so, you have this two boundaries with the between agents and the external world. The first one is
typed tool calls, the tool calls.
Uh you don't want uh, you know, you don't want to call tools that don't exist, etcetera, etcetera.
And also the boundary with other agents, which is typed events.
And this is non-negotiable, I found. Like you can get a lot of errors just from this.
Uh, I wrote a really long blog post about this.
Uh, it's if you follow the QR code, you'll find it.
And yeah.
And the result of that is actually deployed it
uh within the company after I built this, and now today after a month of deploying it,
we have 20 agents on the left
that are not just contributed by technical people, by the way.
Uh, which is kind of what Markdown uh what Markdown gives you.
And then on the right is, you know,
we deploy it. It's called the intranet. There's the briefs. There's a bunch of I mean, there's a bunch of things, as you can as you can see.
Kind of like a few, you know, as a conclusion, a few lessons.
Uh the first one is that well executed, background agents are really magical.
Uh they feel like this, you know, robot mower that I had at the beginning is I really just sit down when I come back,
and I have this morning brief that is probably even better than what I would have had just doing it manually.
And it just appears in my inbox every day and processes my, you know, random thoughts.
Uh the difficulties that you meet doing this kind of thing, it's just good old engineering problems.
I mean, there's really nothing new under the sun when it comes to orchestrating these things.
It's just good old software orchestration.
Uh, open source models are there.
Uh, they're good enough. I replaced, so I don't have any third-party APIs anymore. Now, I just use open source models.
And even on my laptop, I use a local model.
Uh, so it's good enough for what I do with it.
For coding, I don't know, but for what I do with this, it's good enough.
The infra category is definitely unsettled.
Uh, I tried a few things before I started building myself,
and I would advise that today
like definitely start building before you buy.
Uh, so if you're a small company,
if you're a tech CEO, it's kind of an advantage because you can just do this without, you know, tasking engineers to do this and get them off track,
but I would definitely try to build before I buy just to know exactly what I need
and, you know, the limitations of what exists.
Uh, also, I will say that to people building uh
frameworks for this, is please eat your own dog food.
Uh, sometimes it's pretty clear that
people are building, you know, agent orchestration frameworks, etc., but not eating their own dog food, so please do.
And the other thing is I'm really glad I took these 2 weeks off to play with the field because that completely changed I mean, that changed the trajectory of the company. I know we're in an AI company.
We should be in it, etc., but you know, business is such that you always think about the next thing, the next thing, the next thing, the next thing,
and it's the same everywhere, but what I'm urging you to do is to stop
and actually immerse yourself in this, and try to see how useful it can be for your company.
Uh so you can steal the code.
Uh it's not a product that we sell, and we don't intend to sell this.
Uh you can read our blog as well.
Uh so I haven't explained uh this yet, but I will publish something about it.
And thank you for your attention.
