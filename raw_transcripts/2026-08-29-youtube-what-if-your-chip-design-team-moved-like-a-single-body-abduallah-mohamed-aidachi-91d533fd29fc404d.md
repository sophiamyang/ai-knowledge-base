---
id: "91d533fd29fc404d"
title: "What If Your Chip Design Team Moved Like a Single Body? — Abduallah Mohamed, AIDAChip raw transcript"
aliases:
  - "What If Your Chip Design Team Moved Like a Single Body? — Abduallah Mohamed, AIDAChip raw transcript"
  - "What If Your Chip Design Team Moved Like a Single Body? — Abduallah Mohamed, AIDAChip"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=0I6aoPSRzVc"
origin: "https://www.youtube.com/watch?v=0I6aoPSRzVc"
type: "raw-transcript"
created: "2026-08-29"
---

# What If Your Chip Design Team Moved Like a Single Body? — Abduallah Mohamed, AIDAChip Raw Transcript

Hello everyone.

So, I want to start with a simple question.
What if your team or your org, or company moved like a single body?
I'm Abduallah Mohamed, the VP of AI ML at Aida Chip.
And today was supposed to be Khaled with me to present this, but he's heads down with our development partner at the moment.
So I will be presenting the whole presentation for today.

So, let's go for the next slide.

So how many of you have been attending the World Cup soccer or watching some games? Oh nice, we have a couple of fans.
Yeah, it's all over the place.
And imagine for a moment, just a single moment, you are a soccer player, all right?

And if you're a soccer player, you have this intent.
The moment you go into the field, you're just going to run and score a goal.
This is what you want to do.

And for the second thing, you have this knowledge that you've been accumulated through your training the whole day,
your exercises with your coach,
and the best practices and the videos you have watched it.
And you, at the moment in the field, like the moment of truth that you are there, you combine both of that intent and knowledge,
and combine both of them, and through your nervous system, you execute to achieve your goal.

And we can call this in a sense, you are being self-aligned as a single entity by yourself.

And except the fact that a soccer team or a football team, depending where you're coming from, is not a single player. It's actually 11 players.
And on the field you are up against another team with 11 players. They're playing against you.

And at this moment, it's not about your individual skills.
It's about how your team working together win.

So in general, like the team keep changing and everything is getting harder and harder, and the teams that win, actually the team that the most aligned
in both of the both of teams.
So in short, we can say alignment beats individual skills.

Okay.

Now, what if your team is over 50 engineers or 50 players?
This is completely changes the whole scene right now.
So everyone at these days, we empower the engineers with AI tools,
AI agents, and we want to increase the productivity.
But we know from literature that the more people you have, the quadratic term of communication between them and aligning them keep growing and keep growing.
And at a specific point actually, it actually starts going declining.
Your throughput actually is not what you're getting.
It's diminishing cost.

So everyone trying to solve this linear problem of more tools and more stuff, but nobody actually is tackling the quadratic term over there.
And this is why the alignment is important. If you are able to change this quadratic term into a linear term or build a multiplayer AI system
that will solve this problem.

Okay, moving into chip design. Chip design is a different story.
If you are in software company, you have a bug in software, you can ship a batch to fix it.
You can roll out a new version.
It's most of the times doable.

But in chips, you can't do this in chips. It's hardware. Fix it on silicon has been printed.
And if you're going to do this, there is a cost actually, we call it the respin cost.
On average, between chip design companies it's about $50 million.
And for some companies, like being one month late in the market, it's a make or break for them.
And we spoke to many practitioners in the field, on average like 15 practitioner, and we found that most of them pointed towards the same problem
that we spend 70% of our time doing alignment.

Alignment to make sure that once we print the chip, nothing is there.
And one of the key words that we heard and still resonating that the most successful chip organization are not the one with the best engineers,
but they are the most aligned organization.

So how chip design today works?
We start with bottom figure, like the fragmented intent and decision. You attend a couple of meetings,
you talk about decisions, what are you going to do next?
You have the specs written everywhere, you have the Slack messages, you have emails, everything is fragmented over there.

And then we go into a second part, which is the knowledge.
Nobody updates wikis, right?
Many of us has wikis, they've been collecting dust for years.
And the code keep evolving outside the wikis, it's not over there.

And now we have the tools that you execute with, which comes with many, many frictions.
And these tools, like the data is lost over there, what input, what output, what results.
Most of the time, I've not been captured.

And what you see here is not something we came we'd like drew from our imagine. This is actually how is it today.
We draw it from inside the companies and from the backgrounds of the people we have in our team.

And what we're trying to solve here is building a multiplayer AI with a shared nervous system.
Instead of having scattered knowledge or scattered intent all over the place,
we build a living graph. We call it the system of intent.
And this living graph actually has all the constraints of the system,
has all the decisions over there,
it keep evolving.
And as an AI person actually, we don't allow the agents to touch it except with human-in-the-loop approval for specific changes.
And this thing is like the Bible of the whole system. This is where the whole org is going or whole company is going.

And the next one is the tribal-knowledge layer.
The tribal-knowledge layer, we can think about it as a memory
that keeps evolving with day-to-day usage and the knowledge base that capture all the information and documents,
and it's keep evolving from a project to project
and keep bringing the best practice over there.

And lastly, instead of having this general coding agent that everyone uses today, we have a specially designed agent
that being developed by subject-matter experts
to help the engineers doing their work.
So for example, like we have digital design agent,
analog design agent, and so on.

And by combining all of this, you will have this shared nervous system that allows you to move fast and move forward.

Okay.

So it's easy to say an idea on a slide, it's nice, everyone makes slides,
but I want to show you like a demo from what we have today
and showing the intent, knowledge, and execution.
It will be short demos,
and we'll start with the first one.

Yeah. That here. Okay, cool.

So we can see that each engineer gets a role-based AI teammate specific to their role.
They can check the knowledge base of the whole project that being contained and being growing and compounding over time.
And now they have their own intent.

And you have single place for design
where it captures all the tooling you have. It captured the results, it captures what you did
and what we gonna do next, and the analysis of everything.
So everything being contained in one place.

And here we see a human finishing their work,
this human signing off the the results of some simulation.
And the system of intent realizes, "Okay, this person is done with this. I'm going to notify the next stakeholders of what they should do."
And signal to them that they are done with this.

And now the system of intent, which is actually the nervous system or the Bible of the system, it's a graph, living graph that keep compounding with time.
We see in this example like it realized it like there's something off,
like some value out of constraints that shouldn't be there,
that might cost you $50 million actually to respend the whole chip.
And it notified the system and the notification goes
and some engineers start working on it.
And once it got it fixed, it submits again into the system and it keep evolving over there.

Okay.
Good.

So, let's say, for example, like you were working in the system,
you look at the Bible, you find, "Oh, there's something wrong about it.
I don't like this value."

And then you propose a change.
So the system of intent and the spec graph captures all the values over there,
all the stakeholders, and you start doing this modification.
And it gathered all the shared knowledge.

And then it fired a request, as you can see here.
And this request goes to an architect or an owner of the system.
The owner can approve or decline it. And the moment they approve that this is a valid change,
it actually goes and echo in the whole system.
Like everyone will know that this decision has been made,
there is that change, please revise everything over there.

Good.

Good.

So, moving to a very difficult topic here, like how we gonna evaluate our claims and measure the success of the system?

The philosophy we are using this or the philosophy toward this, we don't grade the agents,
we try to grade the alignment itself.
So we have four axes: two horizontal, two vertical.
The horizontal axes like qualitative, the vertical axes like qualitative and quantitative values,
which is typical in this domain at the moment.
And then horizontal ones, which is per component and the system end-to-end.

And if we're gonna zoom into the per component, you can measure like, "Is that agent giving you the correct output for this voltage?" Like, known values versus golden answers.
Or you can use LLM as judge and measure the golden answer versus the expert we have for this one,
which is okay. You can measure how good my memory, like is the recall state-of-art, which is the case in our thing, are we doing inference really good?

But then it comes into the harder question, which is basically, are we doing a task completion?
Like if someone uses this whole thing,
is he really completing the task he want to do?
Is he frustrated while using this? Are our agent overstepping human-in-the-loop approval or not?
Sometimes the agents goes south on that end.

And we measure also, it does does our system allow you to work concurrently on multiple tasks in parallel?
This is a success metric or success goal we have.

And the last one is token tax. We don't want to overload you once you use this with all the lovely tokens
and increase your budget.

And there is hard frontier here, like in literature now, the topic of memory or graph memory, or graph RAG, whatever the title is,
is there's around like 150 papers in this area at the moment and all of them are addressing in a nice way. You can measure the recall. There is data sets.

But there is no work in research at the moment that targets tribal memory or institution memory.
Like, what does it mean exactly? How do you measure a tribal memory success?

And also for chip design domain, it's actually even harder because there is not enough data sets
like computer vision domain. There is many data sets over there,
so there's nothing collected. So we have our own wheel ongoing with SMEs collecting this kind of data sets.

Cool.

So what broke, which actually when I attend any talk, I like to hear what broke, how you fix it?

First, agent overstepped.
In early design phases of the system, we found that an analog agent that's specifically for analog design
actually overstepping and doing RTL agent work,
which wasn't really great.
Even we tried to enforce it, but it was difficult problem.

And then another thing is, we noticed that truth has drifted.
An agent modifying something in the system
not necessarily means it modifies it everywhere it should be modified.
And that make it harder. Like we have a case specifically where one agent were modifying a parameter and updated it in one place, five other places were forgotten.

And the third one is one of my favorites is we asked the agent, "Do not write into specs. Just don't don't change the specs."
They said, "Okay,
I obey you. I'm not gonna write into specs."
But then they moved into bash, and they used sed to write into the specs. We blocked bash, we blocked sed, they said, "Okay, cool. I will use cat actually to write over the specs."
So being like a a cat chasing a mouse around to just prevent it from writing over specs.

And based on these three failures we have,
we came up with principles that we are working today.

First, we have a spec hierarchy with agent scope and file isolation to allow them only to work on this specific task or specific domain.
That solves our problem of agents stepping on each other.

Second one is, we have a single source of truth
with automatic conflict detection that is not LLM-based, but actually rule-based,
that can detect that this agent did this issue.
And we can or want to change its value and actually resonate in the whole system immediately.

And thirdly, which I think of it as an IT administration for agent,
we block at the source. Like we block from system level, not a bath level like tool by tool, but just we try to block it over there.

And the key lesson we learned here that
agents care about, like if you have your agents which are intelligent,
what matters is substrate layer that they're living in.
Like the world they're living in is more important than the agents itself.
Like what they can do, what they cannot do, what you allow and what you don't allow.

Cool.

So I'm gonna use the word "bottleneck," it's been used many times,
but actually it's bottleneck in our case.
It wasn't missing intelligence, it was missing alignment.

And a shared nervous system lets your team move like a one body,
as we see at the moment. One of the things I like hearing from our subject-matter experts that they're saying that
at the beginning of system, it's not working fine.
Now it is good.
Now I feel it's raising me. That is success for our case.
And we think that this gives you 4x leverage from our measurement at the moment.

And alignment is universal.
We building it for the hardest case, which is chip design.

So currently we're in alpha stage
with our development partners.
And the sign-ups for beta are open.
And you can actually join now, and we expect it to release it in October 26.

If you wanna
reach out us, sign up for
the beta,
just use this QR code or the link over there. Thank you, everyone.
