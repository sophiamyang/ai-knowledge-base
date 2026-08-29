---
id: "0abc80aa0132d614"
title: "How Anthropic Builds: Lessons from Labs — Mike Krieger, Anthropic raw transcript"
aliases:
  - "How Anthropic Builds: Lessons from Labs — Mike Krieger, Anthropic raw transcript"
  - "How Anthropic Builds: Lessons from Labs — Mike Krieger, Anthropic"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=qqrk7CtkuIw"
origin: "https://www.youtube.com/watch?v=qqrk7CtkuIw"
type: "raw-transcript"
created: "2026-08-29"
---

# How Anthropic Builds: Lessons from Labs — Mike Krieger, Anthropic Raw Transcript

Joining us on stage is the co-founder of Instagram
and a member of technical staff at Anthropic,
Mike Krieger.

How's everyone doing? I mean, good morning.

Nice.

Uh,
Mike, thank you for releasing Fable just in time for us.

[laughter]
Exactly for the conference. We timed it.

[laughter]

Um,
we're we're so glad to have you. Uh, you are,
uh, one of the preeminent builders and you're leading labs at Anthropic.
Um, how has your
model usage changed as as you've,
you know, seen
models internally grow?
Yeah, I mean, for me, it's been like both the model shift and then my role shift. So I've,
for like the first two years I was at Anthropic, I was Chief Product Officer, and then I kept seeing people build with the models,
and the FOMO just kept increasing because I was,
you know, used the models as much as possible, but, for example, on product strategy, I would write a strategy doc and then have Claude critique it, and maybe you can use a
workflow, but it's not quite the same as like building in that pure way.
And I was like spending all my weekends trying to build with it, and then I realized, "Okay, I actually just need to shift."
It's like way too interesting a time. And it's actually an interesting trend I've seen now,
like several people that were
CTOs at other places are like now joining
as ICs at Anthropic and other places.
But I made a role shift, and it was actually right around the time where we started getting sort of internal snapshots
of what became Mythos and Fable. And
what was really interesting watching
that sort of shift was,
um, that
kind of change between, "I have an idea,
I'm going to like sort of break it down in my head," much more how I would
do engineering normally, and then kind of
iterate through these different steps, to moving to much more of the paradigm of,
"I'm going to describe the goal,
like go off and work on it, and then like we can talk about what trade-offs you, you know, surface some questions along the way, but then
figure out where you landed and where we can go from there."
I find it hard. I don't know if people have this experience where, and
even Fable's only been re-enabled for a couple of days, Fable's definitely way, way smarter than me. So, sometimes it'll finish work and be like, "Here's the trade-offs I made." I'm like,
"Can you explain it to me like I'm a little
dumber than you are, because I need you to like sort of break this down for me?" But that's been one
sort of big changes, sort of moving from that
task delegation to like
express the end state and then have it go and and cook on it.

Yeah, uh, we're all learning how to delegate better.
Uh, Tariq did us a huge favor yesterday.
Uh, did we
did anyone read it in the newspaper?
Um, it's uh,
you know, that we have we have, uh,
write-ups of talks now in in like the next day's newspaper.
He said, "Be unreasonable."
In what ways, you know, have you been more ambitious
Yeah.
in your prompting?
I love that I I mean, I love that framing.
Um, we actually just hit this to like, I'm, one of the labs initiatives I have is internal products,
and, uh, somebody
was like, "Hey, it doesn't work the way I want it to,
um, and can you make some changes?" And
I realized, "Oh, I'm just going to go ask Claude to do this. Why don't you ask Claude?" And this was a non-technical person.
And so I actually think, as an industry or even as a product
team, we have to teach people to be more unreasonable
in their usage, and it's sort of
hard to imagine. I think that that uh,
if I can digress for a second on product design,
I think, right now, the like kind of first generation of AI products, we put them too much in a box and constrain their
their sort of
access to tools or kind of degrees of freedom, which means it was much harder to be unreasonable, right? When you say,
[laughter]
"Do this thing for me," and then it would be like, "Oh, I
You can't.
can't. Like, can barely,
like, I could write code, but I can't really run it, or I can kind of introspect my environment, but not really."
Um, and I think, as you see our own like
product progression, even with things like Cowork, where
like, you know, does every single like knowledge worker need a virtual machine that can write bash?
Like on the face of it, no, but then when you realize, "Oh, actually, that way it can remediate an issue where,
oh, I tried to parse a PDF using our built-in PDF parser," or I hit this yesterday,
and it was like, "Oh, I can't parse it this way. Well, okay, well, I can probably write a script that can do this as well."
Um, so I think that's it.
My most unreasonable thing though was,
uh, one of our labs projects I wrote in Python,
like near and dear to my heart, all of Instagram is in Python,
although I think they're finally converting it to
PHP now that they have, um, like
models that can do it. I know.
Oh, God.
[laughter]
Waste of tokens. Um,
and, uh, for deployment, I realized that Claude Code had like figured out a better deployment story with Bun,
and I was like, "Okay, I need to port this whole thing from Python to TypeScript."
Like as a, you know, if I put on my like 2010s engineering hat,
or even my early 20 20s, like, that's a dumb idea. Like,
who would ever port like, you know, at that point, you know, a couple hundred thousands of lines of code.
Um, but I was like, "I think this is doable now," and I basically created this dynamic workflow
set up, and over the weekend had it port the whole thing,
like verify it, double-check it, then
read both code, like this basically churn and churn and churn and churn, and then
came back Monday to a completed workflow that was
a ported version of that thing. So that probably ranks on like the more unreasonable things. Like,
yeah, just port this entire
Python codebase to TypeScript, get it working, get it deployable in,
you know, a weekend.

Yeah, I mean a lot of people are talking about the the Bun Zig to Rust
Yeah.
version.
I think a lot of people are also like, "Well, it's a compiler. It's a It's a runtime. It's got lots of tests,
easy to do.
Can you port
Instagram,
which you would know very well,
to PHP like that, like a like a product?
Yeah, I mean, I think the product side It's even,
I don't know if easy or hard, one of the things we did at Instagram, this is when Python 3 came out and we were
uh able to add type hints for the first time, and it was
people had a lot of internal conversations, like, "Are we going to run out of steam on Python?"
And my perspective is always like, "I think we can take this
way further than we think we can,
uh, but I think types are going to help us not sort of be in our own
way." And we built this thing called MonkeyType, where we basically like captured runtime
type like basically the types that were actually getting used in production,
and then mapped those back to to the types in the codebase. And I think
because of that sort of pattern, I think
there's really interesting ways in which if you're doing sort of conversion or sort of
cross-compiling
using LLMs, you can also lean on production data a lot more, or run sort of like segmented tests. I think that like
there's a lot of, uh, things you can do there. But yeah, I think it's
I mean, the sky's the limit there as well. I think the hardest part is always finding the boundary around where you can start doing it incrementally without trying to boil the whole ocean and like
swap it overnight.

Yeah, I mean, your users are your tests ultimately, and,
um,
you know, we I also read another article in the newspaper about how you could just use rollouts, and sometimes you don't really know,
uh, what you're going to need it for, but when that infrastructure exists for you to experiment and to roll things out, it enables so much.
Yeah, I mean, I always found this was advice we got. It was like we launched Instagram, and the
happened to be the first week everything melted because we didn't really know what we were doing on the back-end side of things.
[laughter]
And,
[laughter]
uh, coincidentally that week, there was like a lunch that one of our investors just scheduled
like not even for us, it was just a uh infrastructure lunch, and we ended up spending We
totally like monopolized that conversation because everybody had their own opinion about how we could fix our scaling.
Um, and like the two pieces of advice I got there is like 2010 that I will like will forever retain is like,
um, like basically like
pre-measure everything that you think you might even
remotely need because the worst thing is an outage where you're like, "Well, is this
like number normal or is it high and like
oh, I don't know because I don't have data until I just added this metric." And the other one is being like really thoughtful about knobs and feature flags. So even,
you know, early Instagram, we had like a very,
uh, simple, but really effective, like way in which we could do like ramp-ups and rollouts, and dynamic config, too, where, you know,
a lot of our runtime configurations had to be changed, you know, in a matter of seconds so that we could handle load, and being able to like do that in a first-class way was was really important. I'm seeing that definitely in in AI as well, where,
you know, we're making all sorts of different trade-offs, and having that kind of runtime configuration is super key.
Yeah.

Uh, my my favorite scaling story of Instagram, by the way, I think it's like your launch day, when you you DDOS-ed yourself with email.
[laughter]
Yes.
[laughter]
Which, uh, people should look up that story if, uh, if you haven't seen it.
Um, I wanted to go into tags,
uh, very, very major shift. Uh, it's It's how 60-something percent of your code is written today?
Yeah.
Um,
how did you square that with
everything you just said, where it's like very dynamic, like you don't actually ship one app, you ship one app with 3,000 flags.
Yeah.
And like, "Well, what are you working
