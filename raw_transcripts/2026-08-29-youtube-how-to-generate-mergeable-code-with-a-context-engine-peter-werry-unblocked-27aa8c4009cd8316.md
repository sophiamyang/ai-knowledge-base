---
id: "27aa8c4009cd8316"
title: "How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked raw transcript"
aliases:
  - "How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked raw transcript"
  - "How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=qdAkxLoYNI8"
origin: "https://www.youtube.com/watch?v=qdAkxLoYNI8"
type: "raw-transcript"
created: "2026-08-29"
---

# How to Generate Mergeable Code with a Context Engine — Peter Werry, Unblocked Raw Transcript

What we do at Unblocked is we build a context engine.
And I just want to do a quick sound check at the back to make sure everyone can hear me fine.
Can you guys, yeah, we're good?
Awesome.

So,
at a high level,
a context engine delivers organizational context to both your human workers and now increasingly your agents, okay?
So, why,
why is that important?
Before we go too deep on the mechanics of how a context engine works,
I just want to talk briefly about the problem.

So, what we're going to do is we're going to hop into our time machines, and we're going to travel back to the before times,
before agents.
And discuss a little bit about what we used to do as humans
before agents came into the picture.

And so, for years,
you were the context layer.
You
had to go and do things like
this.
You had to find things you were looking for,
trawled all over different data sources,
different discussions taking place.
And then through the codebase of course, try to build up tribal knowledge.
And throughout time, as your codebase progressed,
you'd be, you know, fighting incidents and things like that.
And your organization over time builds up battle scars
from all these all these different things, building code,
documenting architecture, and and dealing with outages and things like that.

But now,
we have a new problem because
as we introduce agents to the picture,
they suffer from all of these challenges except for one thing: agents are like new employees.
They reset their knowledge every time you start a new task.
Okay?
And so, you can think of an agent like an expert software engineer
who's a new employee onboarding for the first time, every time.
They have to rediscover your codebase,
how your organization builds tests,
and how they deploy software with each and every task.

Can I just put a put a show of hands for everyone that's seen this slide before by Bassim?
So, this is kind of like this is a good way to view where people are on what we call like the AI maturity curve.
Starting at the the far left,
this is kind of representative of autocomplete back in the GPT-3.5 days.
You know, remember Copilot and things like that.
And then, you know, kind of move on to using Cursor.
And then from there, you're you think you're talking about how you can start to solve the context problems.
So, some people are building organizational wikis.
Just smile if if this is kind of
bringing up memories for you.
And then, you know, all these things are great,
except that
how do you give agents access to this, and what are the compounding problems that the scaling problems as you move forward?
Well, if you give MCP and skills to your agents
to teach them how to navigate and build context,
and that's kind of where people are today, most people.
They're at the sort of stage four to five
level, okay?
And they understand that context is the bottleneck,
and they're trying to build solutions to solve it for their engineering teams.
So, looking ahead
to all the way to eight with software factories, this is kind of where the puck is going.
I'm not sure if if folks were at the keynote this morning, but
it's it's all about like delivery of context and unknown and unknowns,
and this becomes increasingly important as people start thinking about
full automation of agents.
They just can't operate without organizational context.
They get lost.

So, you know, like
that's the real problem.
Access to information
doesn't equal understanding.
I I know that folks are probably familiar with CLAUDE.md
and and
and wiki layouts and all these things.
If you attach a wiki,
it still doesn't tell the agent where the information is that it needs.
It can search for things in the wiki,
but then what happens is it'll suffer from something that
radiologists
call satisfaction of search.
So, this is a term in radiology
where you look at an X-ray,
and you're trying to find a region
that might be an indicator for cancer, okay?
And you discover like one
indicator,
and if you stop there,
you might miss other important indicators that might, you know, lead to diagnosis of even more
issues.
So, this is what happens with agents.
They don't They just They find something that they they think is correct, and then they stop.
The The other thing about agents is that they don't distill understanding.
They can look around, they can find information,
but they they don't understand how all the pieces fit together.
Because without doing that legwork ahead of time,
they don't understand how, you know, your dependencies interact with each other,
and how your architecture and sort of future planning is going to scope the work that it does next.
And so, some some people will then ask, "Well, what if we just take the entire codebase and all of our architecture documents, and just slam it into the context window?"
And then, yes, maybe like your agents will reason about everything all at once.
And in practice, that that, of course, doesn't work,
not just because you've got way more organizational context than can fit into a context window, even one that's a million tokens in size,
but it it it causes the agent to get distracted.
When you're working on a task, you want task-specific flow,
and so your agents will get distracted easily if you give them things
that cause them to look this way and that way.
And it'll just waste tokens and time.

So, in this morning's keynote,
Tariq from Claude Code mentioned unknown unknowns.
I just want to harp on that phrase again.
And it can be phrased a different way, which is finding the things that really matter.
And so,
this is what your agent can see at the top of the iceberg.
They can see the code,
and they can operate on the code.
What they don't see are things like
the
actual intent,
the team conventions, past decisions,
things that you've discussed in Slack, for example,
architecture rationale, and so on.
And that's why
your agents
need a context engine to get real work done.

So, I'm going to now
attempt a live demo, and hopefully the demo gods are kind.
So, I want to pop back up conceptually. Oops, I think I'm on the wrong tab.
We'll get to that one in a sec.
So, for now,
Sorry about that. And here we are.
So,
I'm going to ask a question as if I'm a, you know, I'm a human,
and I want to get some information about my codebase.
And, you know, the human layer hasn't gone away.
We talk about agents and their need for context, but
humans are still asking questions about the codebase, and we need that level of understanding, because, ultimately, the accountability stops with us.
When you hit merge on a PR, you need to understand what it's doing.
And you need to understand how the architecture works.
So, this question I asked here
is about an internal component of our system called the Sourcemark Engine.
And you can see that it uh is able to articulate it fairly well,
understands the architecture.
This ar- This diagram here is uh is generated, so it it this diagram doesn't exist.
It just figures it out based on the the way the code operates today, and then some proposals for future architecture.
And then, what's really important is that you show your work.
This is a trust-building thing more than anything.
But it allows people to see if
if the answer is maybe not entirely correct, then
you can in- look into the uh the knowledge base that you have and make corrections.
Increasingly, agents are doing this for you.
So now, what I want to show you is another place where humans spend their time,
which is in Slack.
And this is where a lot of the decisions get made, of course.
So, I can do something like this.
And Unblocked will sit and kind of listen for things that it thinks it can chime in on when it provides a high degree of Oh, sorry.
We went to the wrong
You guys can't see that.
Thank you, Claire.
Oh, come on down. Let's see if I can bring it up.
There we go.
Perfect.
So, I can ask questions like this in Unblocked, and if it thinks it can chime in on the answer, then it will chime in.
Otherwise, I can just
address Unblocked directly and ask the same question.
And when it thinks that it has an answer to give, then it will give an answer.
And so, we can get
quite a bit of interesting content there from Unblocked.
Thank you, Unblocked.
I'm going to switch up
and show you that the really interesting thing, which is the agents.
Okay, so
in in that question, the Sourcemark Engine, I'm not sure if people picked up, but there was a little thing at the bottom there that said, you know, there's some optimization opportunities.
So, what I did here is I went into Claude Code, and I asked it
without
using Unblocked, to
generate a plan
to optimize the Sourcemark Calculator.
And it did that.
And it happily went and you know, searched through the code, and and tried to figure out how the algorithm works, and so on.
And it it reached a conclusion.
That's great. You know, it it does a pretty good job.
But,
you know, it maybe could do a little bit better.
So, I asked that question again,
using Unblocked this time.
And it it really kind of nails the the nuances because it picks up on the
the PRs that we
where we discussed future possibilities for improvement,
some Slack conversations that we had, and
and of course, you know, Notion and architecture documents.
And it shows its work.
And this is really important, because
all of these things here, the sources, come back to Claude, and then Claude could knows exactly where to jump to next
if it needs to elaborate on that context.
And so, I just want to show you what the impact of that is.
So, if I
Oops.
Thank you.
If I pull up usage here, you can see that with Unblocked,
the total cost was, you know, sub-dollar to create the plan.
Took about a minute.
Ignore the wall clock time because I've had this open for about an hour, but
it's about a minute.
And then if I look at
the usage without Unblocked,
you can see that it's about 2 minutes,
and and and it costs more to generate all that context.
Now, the reason that happens is because it has to do more work.
It has to look around. Has to discover things.
And this compounds.
Not only does it have to do more work to discover things, it doesn't discover the right things.
So, when you get further down in your execution, it may be operating on the wrong plan or the wrong assumptions.
And then you have to go back, and you have to loop over and over again.
So, the real value of a context engine is not like the upfront cost on these short tasks, it's the compounding effect.
The The other Tariq from Sonar mentioned this in the keynote this morning.
And it's true.
Like the loops compound, and you have to be like
efficient the entire way through with your context.
I'm just going to jump back to
Safari, and I'm going to point out some really interesting things.
So, we also have a a code review agent.
And when we say
you know, organizational context, we're talking about more than just the underlying data.
We're talking about real intelligence.
So, what Unblocked does is it looks at
not like it looks at pull request data, and there are other data sources for this, and it generates a series of best practices
that help align agents to your codebase.
But we thought that this would be really helpful to surface for the review agent, as well.
So, what you can see here
is
it Unblocked chimed in, and then Richie here said, "Oh, that's cool. That's something I would say."
And and that's because that actually was something he said.
So, it surfaced the the the previous comments.
Richie's one of the senior engineers.
And we use the sort of seniority or expertise as a signal
to boost
comments that are important, okay?
So, another interesting interaction by Richie.
He
discovered that the number of code review issues that were being surfaced dropped precipitously.
And he was debugging it with Unblocked.
Got all the way to the bottom and realized what roughly what the problem was, and then asked Unblocked to fix it.
Now, this this is something that we have internally,
you know, that we're experimenting with.
So, Unblocked
can run as an agent in the cloud.
But what's really cool about this is that it has all your organizational context at its fingertips.
And the results are are pretty magical.
So, it can do things like generate this PR.
And then what you'll see here is that not only does it generate the fix,
it also is able to relate it to the all the conversations that were happening.
So, this PR was created because, and you read that context thing, it's mind-blowing.
After this PR, we switched to Claude 4.8, and it dropped a ton in issues because of the behavior is quite a bit different.
So, then it said Richie directly correlated the drop.
Now, what's this thing here? Let's click on it.
It is a Slack conversation.
So, it found the Slack conversation, correlated all of that, you know, past history back again.
And then we ended up with a with a final PR.
So, I'm going to I've got only a few minutes left.
I'm just going to close this up really quickly.
We have a a couple of open-source projects that are kind of interesting if people want to play with them.
One is the Document Query Engine.
That was something that I talked about on Monday in my workshop.
I may talk about it again tomorrow, but I just want to give folks a sense of what this thing does.
Whoops.
If you want to play with it, it's open source.
You can just download it and have a go.
It basically runs over your
GitHub repository, ingests
your your historical pull requests,
and then
synthesizes a schema based on the documents that it can sample.
And then from there, you can issue any kind of queries that you like
and get all kinds of insights out of it through the agent chat.
You can ask all kinds of questions.
And then lastly, the Engineering Social Graph.
So, this is a thing that I was talking about earlier that helps us pin down expertise and team relationships.
So, what you can see here is the sort of like the rough breakdown of our team structure at Unblocked.
As you can see, we're a fairly small team.
And so, we've got these
these clusters of people and how they relate to each other indicates a kind of
review relationships that they have.
So, these are, you know, these lines show like we review each other's code.
We can then cluster that and generate team labels for that.
Or show the coverage across your codebase.
This is really cool. You can see kind of where the holes are, where you might be lacking expert coverage.
And that's exactly what we use within the context engine itself.
All right.
One last thing.
We have, for those that want a taste of what a context engine can do, but don't want to sign up for Unblocked right away,
you can use something that we call the Context Engine Simulator,
which will
basically build up a context behind the scenes on a per-task basis,
and then use that context
to to drive the task.
It'll do it with context and without context, so that you can see what the differences might be.
This is a QR code for that if you want to just take a quick snap.
Awesome.
And I'll just land
on a quote from one of our customers.
50% fewer tokens,
faster triage,
better answers.
And that's exactly what a context engine can do.
One last shout-out before we end.
My colleague, Brandon, is giving a talk in
10 minutes
at room 2020.
He's going to speak to a in a lot more detail about some of the higher level things that context engines can do.
I'm going to run over there right after this, and I think all of you should follow me.
Awesome.
Oh, and don't forget to get a coconut.
