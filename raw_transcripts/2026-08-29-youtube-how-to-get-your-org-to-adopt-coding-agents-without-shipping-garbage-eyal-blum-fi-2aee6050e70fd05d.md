---
id: "2aee6050e70fd05d"
title: "How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma raw transcript"
aliases:
  - "How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma raw transcript"
  - "How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=5Bn0xro2ol8"
origin: "https://www.youtube.com/watch?v=5Bn0xro2ol8"
type: "raw-transcript"
created: "2026-08-29"
---

# How to Get Your Org to Adopt Coding Agents (Without Shipping Garbage) — Eyal Blum, Figma Raw Transcript

Good afternoon.
My name is Eyal Blum.
I am a software engineer at Figma.
And in my talk today, we're going to talk about how we've adopted or are adopting agent into our workflow at Figma,
while maintaining a high-quality of our code base.
So, as you may know, Figma is the browser-based editor where design and engineering, and now AI agent, collaborate together to ship code.
Figma has pivoted very strongly from being a traditional tool to an AI-first tool.
But in this talk, I'm not going to talk about our product. I'm going to talk more about our internal organization and how our engineering org has been adopting AI agents.
What we've found internally is, both for organizations, companies, and individuals, there's kind of a three-act
process of AI adoption.
You start with picking up something, whether it was a lot of the people in this room who have been using AI, are very AI pilled, and have been using AI for a while, and they picked up something, and got some simple things to work very well,
10x faster.
Then you start applying those same practices to bigger problems, and the AI fails pretty badly at that, gives you bad stuff,
lots of bugs,
and the trust that you built breaks down.
And then from that point, you start building the real skill, which is learning how to use AI correctly, and put the right guard rails, and the right prompting, and the right context, and all the stuff that we've been talking all day about here in all the talks, in order to actually build a real scale.
And one thing that is happening internally as we adopt,
whether between teams or individuals,
the adoption is uneven.
We have teams that are very AI forward and have already transformed their entire workflows, and then we have teams that are
still experimenting in the earlier acts and or have lost confidence, and they all need to work together in order to ship our product.
So they need to coexist in the organization, and we need to find a way to support them and while bringing on
everybody along for the journey, and getting everybody to the third act of the story.
Aside from that main friction point, we have also noticed other friction points that happened
as we adopt AI.
One thing that we've heard a lot from developers and managers have been noticing is the reduced developer agency causes
engineers to lose some of their job satisfaction.
So if a lot of people used to take a lot of pride and enjoyment in writing code and getting into the flow,
and a lot of people feel like that's been lost, or they're losing a lot of that element and getting into more of a prompt cycle where they just wait on output from AI and then speak to the AI. That's like not as much fun as they used to have and then we're getting burnout.
We've noticed another interesting thing is actually our best engineer, the one that hold all the context in their brain,
they end up getting a lot of the burden.
And what ends up happening is they know where all the pitfalls are.
They are
holding together with like their mental duct tape all the places
that agents are not working well, and they're preventing all the really bad stuff from coming in, or they have all the institutional context that have never written down in their head, and they get so much burden and become bottlenecks and gets really frustrated. So they're actually
end up being slowest to adapt because they see all the problems
firsthand.
That's another big issue that we've seen.
And this one I'm sure everybody can resonate.
I'm sure everybody here will resonate
that all of a sudden, all the design docs,
and all the Slack messages, and all the emails have gotten three or four times as long, and we've gotten two or three times as many emails.
And they say basically as much as they did before.
So
the communication has gotten quite inefficient, and some of the markers of like what is high-quality and important things versus not so much high-quality
has become challenging to navigate.
So I'm going to spend the next few minutes talking about some of the lessons that we've learned and how we've been trying to apply this. This is a journey we have not come up with the other end, but we've seen some really interesting progress
along a lot of these lines.
I think this a lot of the speakers here have touched upon this, but investing in verification is probably the highest-value thing we can do in our codebase.
Anytime that we can left-shift anything in our workflow from a human needing to do it to an agent being able to verify it.
So, for example,
when Playwright MCP came out, instead of having humans navigate the code, now the agent can explore the code.
That was a big win unlock for productivity in a lot of our teams.
That's really, that's always a big win for us.
The other thing is
it even better if when you find something that the agent has found to be useful,
take the time to take that and encode into the deterministic flow,
a deterministic flow that can be easily repeated, and it's saved on tokens, and save on time for the, and then it also you also know that
you're using the the LLM when it needs to reason. But when you have something that is already
known and basically can be encoded into tests, spending that time
always always pays dividends.
And another tip, if you tell your skills or your agent to write the code that you're writing,
like the red-to-green
the TDD style,
it almost always gives you better results, because you set a goal, then you tell the agent to strive toward that goal,
it will almost always give you better results than writing the code and then writing the test afterwards, because then it will
fit the test to the code rather than fit the code to pass the verification criteria.
This is a testing pyramid that the classic testing pyramid from the previous
just when you think about the testing themselves, which you had the end-to-end tests and then the integration test and the unit tests.
This is very similar.
Move as much as you can down to the deterministic analysis, whether it's linting, the compiler,
the unit test themselves.
Whatever that can't be covered easily, you can have agent do reviews on it based on criteria. So,
architectural standards that have been easily encoded into the codebase, you can move into the agent.
And then only at the very top, you need to have some sort of human review, which is usually around the functionality, and this is the right thing to build.
That only leave the humans to do what the humans need to actually be involved in.
Another really important thing is the planning
versus prompting. This is really ties into the giving agency back to developers and finding a replacement to the craft of writing code.
Spending a lot of time writing the plan and then
sending it off to the agent basically as a as an implementation that can be done automatically is something that we find to
really
kind of reintroduce the joy of building back into the process.
So it's not uncommon to spend a week
writing a very detailed plan, making all the decision, flushing it out, iterating, sending it out to teammates to review.
And then only when it's ready, and you've flushed out all the decisions, you can send it to the agent. The agent will
send it back to you when it's implemented.
And that has been really successful also in accelerating and also
really restoring some of the joy into the development process.
So what makes a good plan?
Really important to start with the why at the top. It really helps prevent an agent drift. If you have like a bold, big section of Kind of like when you write a design doc, you want to have the executive summary,
put that in there for the agent. Otherwise, they'll start drifting over time and make sure that the agent don't go back and change that because they feel like it.
So always start with the why.
Make sure that your plan can be broken down
into small parts that can each be verified independently.
And my personal
way of knowing what is a good size is, would I want to review that the PR that will correspond to that part? If it's going to be too big for me to want to review in one sitting, if kind of like the test is
I'm going to get need to get a cup of coffee before I read this,
that means it's too big, and I'm going to want to have it broken down into pieces.
And then
I make sure that each part can be validated independently, because what I don't want to have is
have
five stages, and then the first one is written but not validated, and then everything else is is built on top of a faulty assumption. So having kind of a validation gate or an exception criteria for each phase
really helps
make the plan
resilient to drift.
And there's all kinds of techniques of how to manage the context and
doing a a software factory on top of that, but once you have the plan, you can use whatever loop you want, or whatever workflow you want,
in order to implement it.
This is a screenshot that I randomly picked of a plan, but this is what I usually look for, the executive summary at the top, the phases, break it down, and then each one of them I would go into lots of details so that I can just feed it into a sub-agent, and the sub-agent can independently work on that and not have to worry about it.
That's there are other workflows that would work, or other structures to the plan. I find that
part of the things that's great about AI workflows is that everybody can set up the thing that works best for them. Uh-oh.
No, thank you.
Everybody can very easily set up their workflow that work exactly for them. So there's
diminishing returning trying to centralize everybody on one thing, but as long as it works for their flow, and other people can
iterate with them, I find that it generally works very well.
This is just an example, kind of a brag of like this is could be a result for a plan.
There are probably 20 PRs here. Some of them would be maybe 10 lines, and some of them would be 100 lines, but probably nothing bigger than that, and that allows us to This is in the pre-AI world, this plan, I probably worked on it
for a week. I aligned with other with three other teams for another week on that, and then I just sent it to an agent to implement overnight, and it came back. This is probably from two plans, not one, but
it's it's basically six weeks of of coding work just
that only took one week. So that's where
I get a 5x speed up. If I include the review cycle in the end as we always have to remember.
Moving on from planning,
back to the issue that we had with the skeptics and the people who are burdened with the most work, make sure that you
bring them in and take their feedback really seriously.
They're skeptic because they're seeing the the where you're lacking validation, where your tools fail.
So
their feedback is basically the roadmap of how to improve your agent interacting with the codebase.
So just make sure to bring them in rather than trying to
figure out how to make them use AI, just let's have them
be in charge of the roadmap to
make AI safe
in your organization, and they will come along once they see that that the improvements that they're making are actually making their life better.
And as you can see, they'll not be shy about telling you what you need to fix. This is
less than an hour of sitting with a bunch of people, and
this is the result of brainstorms.
Another thing that's been really helpful with my team specifically, and we're working to adopt it
in the broader organization as well,
is to make sure that you have an attention-aware communication.
In the age of AI, human attention is a scarce resource. I think I've heard it for multiple talks and a lot of people have noticed have come to the same conclusion. You can't get more human attention. So where you spend your time and what you're reading
is really becomes really important.
So since it's such a scarce resource,
marking what was generated by AI versus what was written by human is really helpful to know how much time you need to spend reading this, and how much slop can you expect in this part of the communication.
And that kind of building a new culture around that cell of communication really helps.
So, for example,
team the team that I work with, we've decided that we always
every PR description will start with something like that, something that I wrote by hand, could be very short, that describe what this is include, and what this is doing, and then the AI description is going to come after that, which is I will probably read it, I will probably edit it to remove some wrong things, but I didn't write every line here, so they should
be more suspicious, and they should pay more attention to what I wrote in the top and that should override it.
Thing like that in Slack, in email,
just like leaning into the fact that everybody knows that you're using AI to to craft your communication, but just don't be shy about telling them what you should read and what you they should pay less attention to.
And I remember
early on, maybe
like earlier in this year,
I tried to I
had some senior engineers in our org that had kind of were very much AI skeptics, and I tried to reach out to them to see what was the problem, what was going on. I'd say I tried to run an analysis on some of the PR comments that you've run, and obviously
I used AI to do that.
And then I didn't distinguish very clearly what I wrote versus what they what AI generated,
and they got very upset.
They're like, "Why are you sending? I did not expect somebody
that I respect this much to send me something that's clearly this sloppy." And then, like, I
immediately like, I apologize, I realize I should have marked it clearly and marked my intention. Like, this is what I wrote.
This is what the AI wrote, and I need your feedback on that because I don't have the context to know if it's sloppy or not. And that's what I'm asking you for. So
lessons like that, and change the culture is just as important as some of the engineering challenges that
we've been facing.
Another thing that's really helpful around the adoption is
as you progress through adoption, there's a lot of very fancy tools and a lot of very fancy workflow that we've we've been implementing,
but one of the really effective thing is just letting people use AI where they're at. So
it helps It really helps normalize the the use of AI for everyday tasks, and it helps reduce the friction.
And really one of the most powerful thing is being able to tag an agent
in a Slack message with somebody and say, "Can you just do this for me?"
And have the agents close the loop in the thread.
That that's kind of thing is really powerful. And then you can go on top of that and have all this thing automated and build all kinds of fancy things. But if you have in a conversation with somebody who's not fully bought in and then
you can tag it in a non like non-passive-aggressive way,
you can tag it and say, "Let's try to see if the agent can get it this time."
And they close the loop, and if it's a good experience, that's really helps people try it out on their own
in other cases.
And our journey continues. We're still learning, even though we're shipping AI externally, our AI adoption,
we're experimenting with with so many things all the time. Our automation story is not fully there yet. We're still trying to figure out when we should use, how we can use cloud agent effectively, given all the dependencies that we have for some of our build systems.
So we are continuing to learn. It's a culture shift, it's an engineering shift, and
I don't know about you, but
for I've been I've been working in the Valley for the last 15 years, and this is the biggest change by orders of magnitude of everything that I've seen in term culture and technology.
So we're all here together, and we're all figuring it out,
and that's that's what I want to talk to you today. Thank you.
