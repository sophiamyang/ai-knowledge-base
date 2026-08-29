---
id: "62c354b3a301515f"
title: "How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe raw transcript"
aliases:
  - "How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe raw transcript"
  - "How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=mJqwmmOx4WA"
origin: "https://www.youtube.com/watch?v=mJqwmmOx4WA"
type: "raw-transcript"
created: "2026-08-29"
---

# How to avoid disaster when vibe-coding a billing engine — Andrew Garvin, Stripe Raw Transcript

Hi everyone.
My name is Andrew Garvin, I'm one of the co-founders of Metronome.
Metronome, if you're not familiar,
is the top platform for usage billing, which as you might imagine, is taking off right now.
Um, so much so that earlier this year, we were acquired by Stripe, in the largest deal that Stripe has ever done.
And what I'm going to show you today is a fun project that we've been cooking on with the Stripe team,
that is a demonstration of some of the things that we could work on together.
This is going to combine two very different products within Stripe.
If you haven't seen it already, I recommend looking at Stripe Projects, just open up
open that up on your phone while I'm going through this.
This is something that actually was launched literally the week that Metronome was acquired, and so as you might imagine, the velocity of development at Stripe and at Metronome is pretty high.
Basically, what Stripe Projects is, is it's an orchestrator to allow you to operate and build your business as fast as possible.
And so, in essence, what it does is it provisions a Stripe account for you, as well as backend services that you may need.
Think like Vercel, Postgres, and in this case, a Metronome billing agent, in order to launch a product quickly or an application quickly, all through the CLI.
So the demonstration that we're going to do today is a very simple demonstration of how to get set up through Stripe Projects, but you can imagine all the sorts of things that people are building on Stripe today.
One of the really cool aspects of being inside Stripe is their scale and data.
And one of the things that we've observed inside of Stripe is that the use of Stripe's CLI has exponentially increased over the course of the past 5, 6 months.
We're thinking about all of the implications of the coding agents operating systems,
which we'll get into a greater topic on later in this demonstration.
So the beginning part was the thesis for this is how to avoid disaster when vibe-coding a billing engine.
As you might imagine, being in the billing space for multiple years now, we've seen all sorts of crazy things happen,
and it's even getting crazier now that people are expecting to operate Metronome, a very complicated and deep product,
with a coding agent.
And so as a result, we are working from a developer experience standpoint to make this a more seamless experience for people, and to have them avoid disaster.
And so we're going to see in a second what that a demonstration of what that might look like, and how we're guiding things.
But just to frame it, the what's happening today in with launching agent products can go crazy and it can go sideways in all sorts of ways.
So, as just a couple of types of problems that Metronome helped solve for folks,
first, we are, for example, and have for many years now,
taken in all of the API calls to OpenAI and Anthropic, and metered that for those companies.
We worked with those companies since before they had any revenue.
And so obviously we've operated at global scale, operating a metering service with a number of different data impacts.
In addition to that, we also operate credit models.
Obviously today with usage-based pricing, it's not just about having a pay-go,
metered business model, but also all sorts of different forms of credits, commits,
sales-led discounts and offers.
And then finally, now in the in the last 6 months especially,
the impact of failures here is growing in importance,
in particular because agents can run away with spend.
And so we're thinking about how to give more controls to our customers that they can offer to theirs.
So think like, for example, having agents have a wallet
that they only they can spend from, and having controls at that level.
Okay, so that's what we're going to go into today.
Let's actually get into doing this demonstration.
You're going to see how simple it is.
So, I'm going to initialize Stripe Projects right now.
Oops.
And this is, in fact, a live demo, so you should expect all sorts of different things to happen here.
So what this is doing is again initializing Stripe Projects.
We are going to, I think the switcher...
So we've selected that we're going to use Claude here, and we have a very simple thing.
I I go around the world basically talking with companies about their business model.
It's not initialized.
Aha, I see.
All right.
Come on up.
Cool. I got it.
All right, thanks, guys.
All right, sweet.
Um, yes, let's proceed.
Cool.
All right, so our product, our project is in fact ready now.
And so I go around the world talking with companies about how to set up their businesses.
One of the things that's really top of mind right now is
replicating certain business models.
People want to get off the ground without having to think about it too deeply.
One of the key topics right now is replicating Lovable's pricing model.
And so, I'm going to
enter a prompt in natural language
that allows us to guide the Metronome billing agent and Stripe
to set up a demo account that has that
that has that element to it.
and create a demo billing engine
in Metronome
mimicking
the Lovable pricing model.
Oops. Just make sure I don't misspell that.
And so if you want to, on the side you can see you can open up Lovable's pricing, and you can see all the different elements to it.
But in particular, they have a prepaid credit auto-recharge model, which is very common in
in sort of a self-serve motion today.
So, let's get this going.
So while this is going, I want you to pay attention to a couple of things that will happen.
And in particular, if you look at the, obviously, the slide on the left, there's a couple different points that I want to hit on.
So first, again, Metronome is a very complicated and deep product,
and there's a lot of different ways to hit foot guns, etc.,
if you're not guided.
And so what we've invested in is building an extensible set of skills files
that can provide context to the agent that's implementing Metronome and working with our API.
These skills files are also portable and easy to install, so that you can use them on your own side.
And what it does is it allows us to essentially remove the friction associated with getting started.
And so here,
that, and that's very important, because you want to be able to test and work with the product and evolve over time.
You're seeing here an error code,
from a developer experience standpoint,
you know, this nothing new, but
our our perspective is to have much more
verbose and clear
errors so that the agent can self-correct.
And and so again, our developer experience teams are working on finding more failure cases like that,
and being able to help guide, especially in the initialization and setup.
One thing that's that's important here, I think keying off of the last talk that was in this room,
the goal that we have from a product development standpoint is not to have a customer operate the entire system without a human in the loop.
This is a type of system that is both business critical, has deep business logic behind it.
And so instead what we are recommending and building toward is to
use the use your coding agent as a way to accelerate your work, and get into a test mode and test environment.
And so again, what we're doing here, we're not expecting to ship into production, we're not pushing it into production.
In fact, what when we go into the Metronome environment, you'll see that basically what we've done is built a sandbox experience.
And in the Metronome context, there's what it means to sort of test your initial setup is not just that you can see a contract or something like that, or see a customer provisioned,
but also you need to see usage.
And so in on the backend here, our skills files are directing
the agent to actually flow usage into the Metronome platform so that you can see what a live
what a live customer would look like.
I'm going to do one more beat on Stripe Projects here.
I think in this case, what's happening is that Stripe Projects,
so so using Stripe CLI, it's it's engaging with Metronome, which is an external vendor here.
You can also imagine also provisioning a bunch of other applications,
and using natural language to call for those as well.
And so what again, what's nice about this is that it basically removes the friction associated with setting up a test application or a test environment.
And we again have seen a ton of
usage of this form,
and we expect to see even more.
This is sort of
like, from our perspective coming into Stripe, this is one of the things that has been really amazing is that Stripe is on the forefront of thinking about agentic commerce,
and preparing primitives for the moment that we're in right now, where, in fact, this is exactly what's happening.
Companies that are launching new
new applications and new businesses, we've seen an exponential increase in new business formation at Stripe.
And then in addition to that, an exponential increase in customers that are using Stripe and using Metronome through the coding agents themselves.
Okay.
We are almost done here, I believe.
While this is going, I I like
another sort of like thing to sit back and think about.
When I go around to product teams today, they're obviously thinking about building for agents.
But I think one of the things that's important to do is to decode what exactly does that mean.
And so I what I like about this
sort of framework for thinking about the coding agents today
is thinking about the different roles that they play.
So obviously, companies are launching agents as a product,
and therefore, that's one of the reasons why they need to have usage-based pricing model,
because if the agent can be the product and run up token a token bill, it's important for you to be able to meter on that.
What we're talking about here with the Stripe Projects CLI is the agent as a buyer.
So literally procuring their initial Stripe instance, as well as additional backend services.
That's important to basically make your services discoverable to agents that may be building an application or working in the open web.
On the Stripe side, that means both in a B2C environment, so they're working on agentic commerce, but then in the Metronome environment, we're talking about in a B2B context.
And and so there's sort of like multiple different levels to play at there.
And then finally, one of the reasons why Metronome is really taking off right now is because of the agents as a user.
And so, for example, we've been working with HubSpot for the past couple of years.
They are currently on a path to transform their entire business from a seats-based model to a credits-based model.
If you've seen some things in the news,
that's starting in in EMEA, where they have dramatically lowered their seats-based price and added on a credits-based model.
The fundamental reason behind that is because what they need to be concerned about is a world in which an agent can operate their entire system.
And in that world, essentially paying for a seat-level access to the product to perform your work is no longer important in some sense.
We've been talking about this in as sort of headlessness.
Salesforce, various others have have talked about this.
This is what Metronome is literally seeing today.
And so as like one example, last week, I was at a
I was at Andreessen's demo day, where all five of the demoing companies were sales-led agents
meant to operate platforms like SAP,
or operate
operate invoicing platforms, etc., etc.
And again, in that world, it's important for you to have a usage-based pricing model,
because you have the possibility of essentially all of the value accruing to essentially one user of your platform, which in this case would be an agent.
If you guys are thinking about pricing models, not just developing in the agentic space,
I'm a good person to talk to. I'll be out here in a second.
Some of the things that we're thinking about here are basically
not only having a credits-based model, which has been
dominant on the market since OpenAI launched their prepaid credit auto-recharge model a couple of years ago through Metronome,
but in addition to that, offering more and like more and extended offers, including in a sales-led and an enterprise environment.
And so, for example, what's happening with all the coding agents in the enterprise, think like Cognition, or Cursor, or OpenAI and Anthropic themselves,
is that they are starting to adopt more
commit structures like the CSPs have done for the past 10 years.
Think having prepaid commitments, postpaid commitments, and specific types of offers for specific types of customers.
Okay, I think that we should be good to go now.
And let's see what it looks like when we open up Metronome.
Okay.
What's up?
Aha.
Yeah.
We've done multiple different versions of this, as you might imagine.
Okay.
So, as we open this up,
pull this.
It's fun. I love all these demos where you're just looking at people logging in.
So as we open this up, so the general pane that Metronome has is an onboarding wizard meant for a human that needs to set up their environment.
We've We don't need this now because we had an agent set up this environment.
And as I come in, you're going to see some of the core Metronome primitives here.
Let's start by looking at the customer that was set up.
Again, this is for testing purposes.
Up at the top, you're seeing the customer with a certain lifetime spend.
This was auto, again, populated by, by the agent for the demo environment.
I'm immediately going to go into their invoice, and we'll come back to this in a second.
And so, what you've what you see here is a draft invoice that was created,
associated with sort of replicating the Lovable pricing model again.
So if you have this on the side, you can see all the different elements of that.
But the core aspect of Lovable's pricing model is a credits-only pricing model
where you auto-recharge on a monthly basis.
And then in addit- in addition to that, they have multiple different types of credits that are scoped to different types of usage.
Beyond the the use of those credits, then, if you go over and if you overspend, then you have an invoice at the end of the period.
So a couple of the different like concepts there that are relatively complicated to administer is the credit itself.
And so Metronome has a first-class credit object.
Here what you're seeing is that there was a create- credit created for the initial period that we're testing for.
We had usage that that draw that drew down from that entire credit balance.
And then finally, if we go back to the customer pane,
in addition to that, you can see the usage that we that we plopped in.
Obviously, in a production environment, you would be seeing this in against real usage that you have.
The core reason again to show it in this manner is to just see
what it would look like if you adopted the pricing model and then had real usage against it.
Again, I'm going to come back to the invoice.
And so here, you can click into each of these different components,
Build Credits, Plan Mode Credits, Cloud Credits, AI Gateway Credits.
This is exactly what the Lovable pricing model looks like.
And again, the way that we coached the agent to be able to do to to build this was just describing in natural language to replicate Lovable's pricing model.
There was nothing more difficult than that.
So without going into the Metronome's platform to too great an extent,
the what we just did here was we initialized
and created a Stripe instance.
We then through Stripe Projects, we also created a Metronome instance.
Then we coached the agent to be able to
build a demo instance of Metronome
that had a real pricing model live in production.
And so you could imagine basically testing then from there, the exact testing and tweaking from there exactly what you wanted before bringing that into production.
This sort of framework for thinking about development both applies to Stripe, where we are working very very hard
to make it easier to run a complicated business model and get off the ground,
but also I think it bears lessons for how we might pursue agentic development more generally outside of Stripe.
So again, think about some of the primitives primitives that we talked about here today.
Agent as a buyer, agent as your product, agent as your user, and disambiguating what the different what the different
modes and and like implications of those are.
And then in addition to that, having having ways in which we coach the agent to operate more effectively in, including in a in a difficult environment.
You could try this for yourself now.
So the easiest way to get started is with the commands that are that are listed here.
And you can see everything that is available through Stripe Projects through Stripe Projects online,
as there are a number of different providers that are onboarding every day.
So companies like Vercel,
like Hugging Face, etc.,
are basically like working in Stripe Projects environment to be able to make their own products more discoverable to agents that are operating Stripe's system.
