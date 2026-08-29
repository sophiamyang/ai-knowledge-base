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

Good afternoon. My name is Eyal Blum.
I am a software engineer at Figma.
And in my talk today, um, we're going to talk about how we've adopted or are adopting soft, uh, uh, agent into our workflow at Figma while maintaining a high quality for our code base.

So as you may know, Figma is the browser-based, uh, editor where design and engineering, and now AI agent, collaborate together to ship code.
And this, uh, uh, Figma has pivoted very strongly from being a traditional tool to an AI-first tool.
But in this talk I'm not going to talk about our product, I'm going to talk more about our internal organization and how our engineering org has been adopting AI agents.

And what we, uh, we've found internally is both for organizations, companies, and individuals, there's kind of a three-act process of AI adoption.
You start with picking up something, whether it was a lot of the people in this room who have been using are very AI-pilled and have been using AI for a while, and they picked up something and got some simple things to work very well, 10x faster.
Then you start applying those same practices to bigger problems, and the AI fails pretty badly at that, gives you bad stuff, lots of bugs.
And the trust that you built breaks down.
And then you from that point, you start building the real skill, which is learning how to use AI correctly and put the right guard rails and the right prompting and the right context and all this stuff that we've been talking all day about here in all the talks in order to actually build a real skill.

And one thing that, um, is happening internally as we we adopt it, um, whether teams or individuals, the adoption is uneven.
We have teams that are very AI-forward and have already transformed their entire workflows.
And then we have teams that are, um, still experimenting in the earlier acts and or have lost confidence, and they all need to work together in order to ship, uh, our product.
Um, so they need to coexist, um, in the organization, and we need to find a way to support them and while bringing on everybody along for the journey and getting everybody to the third act of the story.

Um, aside from that main friction point, we have also noticed other friction points that happened, um, as we adopt AI.
Um, one thing that we've heard a lot from developers and managers have been noticing is the reduced developer agency causes, um, engineers to lose some of their job satisfaction.
So if a lot of people used to take a lot of pride and enjoyment in writing code and going into the flow, and a lot of people feel like that's been lost, or they're losing a lot of that, uh, element, and getting into more of a prompt cycle where they just wait on output from AI and then speak to the AI, that like not as much fun as they used to have, and maybe getting burnout.

Um, we've noticed another interesting thing. It's actually our best engineer, the one that hold all the context in their brain, um, they end up getting a lot of the burden.
And what ends up happening is they they know where all the pitfalls are.
They are like holding together with with like their mental duct tape all the places that agents are not working well, and they're preventing all the really bad stuff from coming in or all they they have all the institutional context that haven't ever written down in their head, and they get so much burden and and become bottlenecks and gets really frustrated.
So they're actually and have been slowest to adapt because they see all the problems, uh, first hand.
That's another big big issue that we've seen.

And and and this one I'm sure everybody can resonate in Sorry, I'm sure everybody here will resonate.
Um, that all of a sudden all the design docs and all the Slack messages and all the emails have gotten three or four times as long, and we've gotten two or three times as many emails.
And they say basically as much as they did before.
So communication has gotten quite inefficient, and some of the markers of like what is high quality and important things versus not so much high quality, um, has become challenging to navigate.

Um, so I'm going to spend the next few minutes talking about some of the lessons that we've learned and how we've been trying to apply this.
This is a journey. We have not come out to the other end, but we've seen some really interesting progress along a lot of these lines.

Um, I think this a lot of the speakers here have touched upon this, but investing in verification is probably the highest value thing we can do in our code base.
Um, anytime that we can left, uh, left-shift anything in our workflow from a human needing to do it to an agent being able to verify it.
So for example, when, uh, Playwright, uh, MCP came out, instead of having humans navigate the code, now the agent can explore the code.
Well, that was a big win unlock for productivity in a lot of our team.
That's really, that's always a, a big win for us.
The other thing is, um, it even better if when you find something that the agent has found to be useful, take the time to take that and encode it into the deterministic flow.
Uh, deterministic flow that can be easily repeated, and it's saved on token, save on time for, and then it also, you also know that you are using the the LLM when it needs to reason.
But when you have something that is already, um, known, and basically can be encoded into a test, spending that time always, always pays dividend.
Um, and another tip, if you tell your skill or your agent to write the code that you're writing, um, like at a red to reen- to red to green at the TDD style, it almost always gives you better results because you set a goal, then you tell the agent to strive toward that goal, it will almost always give you better results than writing the code and then writing the test afterwards, because then it will fit the test to the code rather than fit the code to pass the verification criteria.

Um, this is the testing pyramid that kind of the the classic testing pyramid from the previous, um, just when you think about the testing themselves, which you had the end-to-end test, and the integration test, and the unit tests.
This is very similar.
Move as much as you can down to the the deterministic analysis, whether it's linting, the compiler, and the unit tests themselves.
Whatever that can't cover be covered easily, you can have engine agent do reviews on it based on on criteria.
So, um, architectural standards that have been easily encoded into the code base, you can move into the agent.
And then only at the very top, you need to have some sort of human review, which is usually around the functionality and this is the right thing to build.
That like only leave the humans to do what the humans need to actually be involved in.

Um, another really important thing is the planning versus prompting.
This is really ties into the giving agency back to developers and finding a replacement to the craft of writing code.
Um, spending a lot of time writing the plan and then sending it off to the agent basically as a as an implementation that can be done automatically is something that we find to really kind of uh reintroduce the joy of of building back into the process.
Um, so it's not uncommon to spend a week writing a very detailed plan, making all the decisions, flushing it out, iterating, sending it out to teammates to review.
And then only when it's red and you've flushed out all the decisions, you can send it to the agent.
The agent will, um, send it back to you when it's implemented.
Uh, that that has been really successful, also in accelerating and also, uh, really restoring some of the joy into the development process.

Uh, so what makes a good plan?
Um, really important to start with the "why" at the top.
It really helps preventing agent drift if you have like a bold big section of Kind of like when you write a design doc, you want to have the executive summary.
Put that in there for the agent, otherwise they'll start drifting over time and make sure that the agent don't go back and change that because they feel like it.
Uh, so always start with the "why".
Make sure that your plan can be broken down, uh, into small parts that can each be verified independently.
And my personal way of knowing what is a good size is, would I want to review that the PR that will correspond to that part?
If it's going to be too big for me to want to review in one sitting, it's kind of like the test is, I'm going to get need to get a cup of coffee before I read this.
That means it's too big, and then I'm going to want to have it broken down into pieces.
And then I make sure that each part can be validated independently, cuz what I don't want to have is have five stages, and then the first one is written but not validated, and then everything else is is built on top of faulty assumption.
So having kind of a validation gate or an acceptation criteria for each phase really helps, um, make the plan, uh, resilient to drift.
And and there's all kinds of techniques of how to manage the context and doing, uh, a software factory on top of that, but once you have the plan, you can use whatever loop, uh, you want, or whatever workflow you want in order to implement it.

Uh, this is a screenshot that I randomly picked of a plan, but this is what I usually look for, the executive summary at the top, the phases break it down, and then each one of them I will go into lots of details so that I can just feed it into a sub-agent, and the sub-agent can independently work on that and not have to worry about it.
Um, that's, uh, that's it.
There are other workflows that would work or other structures to the plan.
I find that part of the things that great about, uh, AI workflows is that everybody can set up the thing that works best for them.
Uh-oh.
No, thank you.
Everybody can very easily set up the workflow that works exactly for them- for them.
So there's diminishing return in trying to centralize everybody on one thing, but as long as it works for their flow, and other people can iterate with them, I find that it generally works very well.

And this is just an example, kind of a brag, of like this is, uh, could be a result for a plan.
Um, there are probably 20 PRs here.
Some of them would be maybe 10 lines and some of them would be a 100 lines, but probably nothing bigger than that.
And that allows us to This is In the pre-AI world, this plan probably worked on it for a week.
I aligned with other with three other teams for another week on that, and then I just sent it to an agent to implement overnight.
And it came back.
This is probably from two plans, not one, but it's it's basically six weeks of of coding work just, um, that only took one week.
So that's where I get a 5x uh speed up if I include the review cycle at the end, as we always have to remember.

Um, moving on from planning, uh, back to the issue that we had with the skeptics and the people who are burdened with the most work, make sure that, uh, you bring them in and take their feedback really seriously.
They're spect- skeptic because they're seeing the the where your we are lacking validation, where your tools fail.
So, um, their feedback is basically the road map of how to improve your agent, um, interacting with the code base.
So just make sure to bring them in, uh, rather than trying to, um, figure out how to make them use the AI, just this have them be in charge of the road map to make AI safe in your organization, and they will come along once they see that the that the improvements that they are making are actually making their life better.

Um, and as you can see, they will not be shy about telling you what you need to fix.
This is less than an hour of sitting with a bunch of people, and, uh, this is the result of brainstorms.

Um, another thing that's, uh, have been really helpful with uh by team specifically, and we're working to adopt it, uh, in the broader organization as well, is to make sure that you have an attention-aware communication.
In the age of AI, human attention is a scarce resource.
I think I've heard it for multiple talks, and a lot of people have noticed have come to the same conclusion.
You can't get more human attention.
So where you spend your time and what you're reading is really becomes really important.
Um, so since it's such a scarce resource, marking what was generated by AI versus what was written by a human is really helpful to know how much time you need to spend reading this and how much slop can you expect in this part of communication.
Um, and that kind of building a new culture around that style of communication really helps.
Um, so for example, um, the team the team that I work with, we've decided that we always every PR description will start with something like that, something that I wrote by hand.
It could be very short that describe what this is include, and what this is doing, and then the AI description is going to come after that, which is I will probably read it, I will probably edit it to remove uh some wrong things.
But, I didn't write every line here, so they should be more suspicious, and they should pay more attention to what I wrote in the top and that should override it.
Things like that in Slack, in email, just like leaning into the fact that everybody knows that you're using AI to to craft your communication, but just don't be shy about telling them what they should read and what you they should pay less attention to.
And I remember early on, maybe, like earlier in this year, I tried to I had some senior engineers in our org that had kind of were very much AI skeptics, and I tried to reach out to them to see what was the problem, what was going on.
And I said, I tried to run an analysis on some of the PR comments that you've run, and obviously, I used AI to do that.
And then, I didn't distinguish very clearly what I wrote versus what they what AI generated, and they got very upset.
They're like, "Why are you sending? I did not expect somebody, um, that I respect this much to send me something that's clearly this sloppy."
And then like I admit like, I apologized. I realized I should have marked it clearly and marked my intention, like, this is what I wrote.
This is what the AI wrote, and I need your feedback on that because I don't have the context to know if it is sloppy or not, and that's what I'm asking you for.
So lessons like that and change the culture is just as important as some of the engineering challenges that we've been facing.

Um, another thing that's really helpful around the adoption is, um, as you progress through adoption, there's a lot of very fancy tools and a lot of very fancy workflows that we've we've been implementing, but one of the really effective thing is just letting people use AI where they're at.
So, um, it help it really helps normalizes the the use of AI for everyday tasks, and it helps reduce the friction.
And really one of the most powerful thing is being able to tag an agent in a Slack message with somebody and say, "Can you just do this for me?"
And have the agents close the loop in the thread.
Um, that that's kind of thing is really powerful.
And then you can go on top of that and have all this thing automated and be all kind of fancy things.
But if you have in a conversation with somebody who is not fully bought in and then you can tag it in a non- like non-passive-aggressive way you can tag it and say, "Let's try it with See if the agent can get it this time."
And they close the loop, and if it's a good experience, that really helps people try it out on their own in other cases.

And our journey continues.
We're still learning, even though we're shipping AI externally.
Our AI adoption, um, we're experimenting with with so many things all the time.
Our automation story is not uh fully there yet.
We're still try- trying to figure out when we should use, how we can use cloud agent effectively given all the dependencies that we have for some of our build systems.
Um, so we are continuing to learn.
It's a culture shift. It's an engineering shift, and I don't know about you, but for I've been the I've been working in the Valley for the last 15 years, and this is the biggest change by orders of magnitude of everything that I've seen in term of culture and technology.
So, um, we're all here together, and we're all figuring it out, and that that's what I wanted to talk to you today.
Thank you.
