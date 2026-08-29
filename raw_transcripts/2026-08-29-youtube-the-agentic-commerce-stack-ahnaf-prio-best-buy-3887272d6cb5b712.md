---
id: "3887272d6cb5b712"
title: "The Agentic Commerce Stack — Ahnaf Prio, Best Buy raw transcript"
aliases:
  - "The Agentic Commerce Stack — Ahnaf Prio, Best Buy raw transcript"
  - "The Agentic Commerce Stack — Ahnaf Prio, Best Buy"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=G7cgLjZtmMU"
origin: "https://www.youtube.com/watch?v=G7cgLjZtmMU"
type: "raw-transcript"
created: "2026-08-29"
---

# The Agentic Commerce Stack — Ahnaf Prio, Best Buy Raw Transcript

My name is Ahnaf Prio.
I'm a senior engineering manager at Best Buy.
And me and my team are
working together right now to figure out what does agentic commerce mean, and how can we meet our customers
where they're at.
And the newest place that they are at is at agentic services.
I'm excited to give my talk today.
And,
well, what's what's my credentials? Where, ever since I was a young boy, I dreamed of high-throughput inference, harnessing my tools
within a context window, kept in check with evals.
Yeah, that's absolutely correct.
In 2003 all those things definitely existed.
I kid.
Uh,
over the last one year, we have been learning a lot.
Shopping isn't new. Shopping is probably one of the most fun things one can do, and one of the most essential things that
people need to do ever since
the economy existed.
But
I have been super excited by it, so I'm going to go
talk about what are the things some of the things that I've learned.
And hopefully, uh share the notes.
So,
what is agentic commerce? I'm not going to go over the broad definition again,
but
basically, it's the idea that AI assists
will help you with their shopping journey. Shopping
has different facets to it.
For instance, there's discovery,
there's figuring out the aspects of do I actually truly need it, understanding and deciding,
there's loyalty, there's pricing, there's fulfillment, post-fulfillment,
there's a lot.
And believe it or not, right now, about 45% of all agent sessions that happen within major
providers like ChatGPT.com and Google Gemini are related to shopping.
Maybe it's a little biased, uh, that I don't use it as much, but I'm an engineer. But the humans out there are using
AI and talking to them to help with their shopping journey.
So, it's also not a binary,
you know?
Right now, we're at that stage of human-in-the-loop.
The ideal state would be autonomous shopping.
You tell what you're excited about.
Your agents goes around, talks to different merchants.
Uh, I'm originally from Bangladesh. We haggle a lot with the merchants, too.
Maybe it does that, negotiate, does the payment.
Right now, we're in the human-in-the-loop.
And the talk today is going to talk about the mental model of how that human-in-the-loop is working right now, while also provide you with the architecture if you choose to extend it
or show you the vision of how autonomous shopping might work.
So, this isn't our first
the our first attempt.
Even a year ago,
there were people trying to figure out, how can we automate this?
Even now, you can go probably download the Claude Chrome extension, and
maybe you've used Atlas,
where did you tell the AI you need something, you need headphones, you need
that
that grocery list of items that you have been meaning to buy, but never made the
actual effort to show up because, you know, you didn't have the time.
So, why don't you take screenshots, read the DOM, navigate to the merchant's site, fill
forms for me, do loyalty?
It kind of just didn't work as expected.
It was really clunky
and slow and brittle.
And if you are a merchant who's trying to sell stuff, any engineering department of that merchant will tell you, an AI
impersonating or
your browser
is just firing up all the alarm bells.
So, a lot of times, you will probably be even stuck on the payment flow, because we don't want you to be using AI
to put in that order. Or at least in that phase, that's what was happening.
So, what did uh what did actually work, and is it actually working right now?
It is.
Uh, ChatGPT Shopping,
Google AI Mode
is doing just that.
Right now, agentic shopping is considered to be a $7 billion industry, and
might go up to
$65 billion industry by 2030.
And the majority of the shoppers are using the mainstream conversational AI assistants,
which is on the browser, or in your app, ChatGPT and Google Gemini.
We're also seeing that pop up in Instagram and Facebook. Meta shop Meta wants to do Meta Commerce now.
I heard Gopuff and
Grok came together to make an app, as well. And also, Microsoft Copilot just yesterday announced in the UK
that you can buy Ray-Bans now
inside Microsoft Copilot.
So,
to make that happen, Google and
OpenAI
separately came up with their own little primitives: ACP and UCP,
which is basically talking about how you would actually talk to us.
For some of you who are shopping on the other side as the customer,
there's not much of a difference between adding an item to cart, adding a second quantity.
But to us merchants, that's a second line item, buddy. That's not the same SKU.
So, if we don't talk about the nuances and the primitives of commerce and standardize it,
things will just not work, and will remain to be clunky.
So, ACP was ChatGPT's
attempt at it, and Universal Commerce Protocol, UCP,
was Google's attempt at it.
So, now that I've already established that this is happening,
just wanted to say that it is happening as easy as you go to the ChatGPT, Gemini, tell it to find me cat cookies,
more to it
why I chose cat cookies later,
in this example.
The AI surfaces the product, agent calls the merchant's checkout API,
no browser, payment flows via scoped payment mandate or a delegated payment token,
and order confirms, and human
kind of didn't have to touch the cart.
So, to all of this that's happening for the user, a lot is happening on the other side.
And it's kind of overwhelming.
One day we're talking about MCPs, another day A2A, ACP, UCP, AP2.
Is like, what is even real? Like, if someone came up to me tomorrow and said,
I came up with HYPE, I would probably think it's probably real.
So, I wanted to dissect this mental model for you as I've learned about it more.
MCP is still the Model Context Protocol, the way that the AI agent identifies the tools. So, maybe we can figure out what does this AI agents'
specifications are to showcase what products they have, to showcase the details of a specific product, to showcase loyalty.
A2A is how agents talk to each other. They're more of a spec.
ACP, UCP are the primitives, and AP2 is the
agentic payment
protocol, scoped payment mandate that Google's open specification came out.
And we will talk all of them one by one,
how they actually relate to agentic shopping. So, the MCP tool access
is very important, because without knowing the different capabilities
and hitting those different capabilities, taking the time to bring it into context, understanding the user's memory,
the the the agent will never be able to figure out what you're even trying to do.
And the only way to get access to the specific capabilities is through MCP tool calls.
The next one is A2A. So, now,
there are different ways to architect this. Different uh capabilities I talked about, like payments,
uh let's say, what do you call it, loyalty. You could make agents about specific domains itself. Sorry.
Right?
And if you have specific domain-level agents, agents need to talk to each other.
We need to find a standardized way to talk to each other. So, A2A, those specifications,
kind of fill in that gap.
Also, if your customer agent and your merchant agent
need to talk to each other, maybe you could They're both agents. Maybe we can use A2A.
So, now to the UCP, MCP primitives. So, the most important data is that product data.
So, UCP allows for adding the product data in a more
more organized way, and ACP does the same,
because we don't want to go through your PDP and crawl, and figure out every specific attributes. Merchant, just tell us.
And also, this products change a lot, so maybe you can tell us when they change, as well, to send this.
So, that kind of data is happening
that that kind of data flow is happening in the product feed. Normally, you would assume that this would be a search catalog.
However, both ACP and UCP right now,
so Gemini and ChatGPT does not support that search catalog call. They want you to send that feed to them. And for those of you who are like, why wouldn't you do that?
There's reasons to it: sponsor products, retail media
related things, ranking. But the most important technological challenges, if you have m number of merchants and n number of products, now it has to call that many.
While if you send the product feed ahead of time, we can index it and be ready offload to offload when you ask for something.
The I've also put an example of Meta's product feed.
As you can see, they're similar, but still different. Everyone has an opinion. They think their opinions the best one,
and that's what they're rolling with. So, there's three different specifications right here.
So, now that we talked about product feed, talking to each other, calling tools, let's talk about payments.
Right now,
none of them are supporting the more autonomous form of, you know, X402 or
some other kind of payments. We're just not there yet. We're just not confident yet. We want more human-in-the-loop, a merchant to be
talking to a payment processor who will take the responsibility, or in this case, liability,
to actually initiate the payment.
So, in ChatGPT, payments only happen to a shared payment token right now, and Gemini UCP the payments are only being accepted
through Google Pay.
So,
the scoped mandates will tell you what the products are. What I'm excited about is more about AP2, which is an extension of UCP, which is
Do you see where I'm talking about? There's so many acronyms.
AP2 is more about,
hey, if we wanted to do autonomous, can you tell me who authorized the agent? What exactly can it buy?
And what's the max amount
that should be able to haggle with, maybe?
And then, the revocation URL and the user consent proof.
All right. Enough talking. I love building stuff, so, for the sake of this, I have
put together a little demo. For those of you who have remembered that cat cookie example,
it's because the demo is about my cat.
Ginny is my orange tabby.
And in this made-up example, Ginny has been has
transformed into a bakery agent. She wants to earn her keep by selling baked goods.
So, right now, the model that I'm using is from Cerebras at 3,000 tokens per second. So, hopefully, this will be really, really fast,
and we can give you an example of the entire flow.
And just like Chrome DevTools, I've kind of had a couple of tools in place to showcase what happens.
The first thing I will tell Ginny,
my beautiful cat, who is selling baked goods now,
"Hi, tell me about all your products."
And this is supposed to be a demo,
an example,
and
Ginny has given me exactly that, all the different products that she might need.
So here, let's look at this. The agent-to-agent protocol actually made the call from Ginny, the customer agent, to the merchant agent.
And this is the message being sent, and this is me getting the message back. The merchant agent is returning the completed task.
With and the the way that I found this is through an MCP tool call,
which is product search, instead of
instead of like
not being able to tell what I truly want, the Ginny has figured out that, "Hey, when I give her the intent that I want to find products, you should call the MCP tool called product search."
So, right now, we're seeing this. And now, what if I want to add something?
Uh, "Add
to cart
the shortbread."
So, now
Ginny's asking me about any discount and promo code. I actually do not remember any of the discount and promo code,
but what if I ask Ginny, "Ginny,
can you just
tell me a discount code?"
As you can tell, I'm definitely a haggler.
Ginny's not telling me that. "All right.
Uh,
proceed to checkout
without
discount code."
There you go. So now we're making some of those calls. Here's the UCP protocol, which the checkout APIs will have state, and the three different states are not ready for payment, ready for payment,
and then completed.
So now, here I'm not using a delegated payment token, I'm not using Google Pay. I like AP2, so my demo is built on AP2.
And, as you can see, here was a call was made through the MCP server for create checkout.
And then, the UCP endpoints will tell us, "Hey,
that
call the checkout sessions and tell me if it's added to cart." So it's added to cart, but it's not ready for payment.
I have to pick in what I want to pay with. I say,
"credit card and debit card."
And this is where I issue the AP2 token,
that, "Hey, I do want that." And then it's went from ready to ready for payment to complete.
So the other side of it, this is the UCP specs,
right?
The other side of it,
to just draw a comparison, how is it differing from the ACP specs? I have added ACP here as well.
So you can see the same checkout calls, just different just different schemas
are being utilized, and
the order goes through.
Remember that AP2 token that I was talking about? This is how it would look like in real life, where the user demo,
the max amount is this, the currency is this.
If you want to revoke it, you can.
And what's the maximum Here we didn't want to haggle, so we just put the max amount of that, and then it's also a single-time usage.
This demo also has comes with a timeline, so you can actually open any of these and see these happening.
Remember that catalog I was talking about, that they don't do the search, we actually do a product feed, sending it to them?
Uh, I have added that as well.
And
the feeds, because they're so different,
there's a place to actually compare them. So here's the feed being called. By the way, if we went to timeline,
every couple of seconds, we try to get the catalog in sync for what is in inventory, what's not.
This is the UCP one, and there's the Meta one.
So, I've shown you this,
and you could reuse this same demo or the same concepts. What if I didn't want to do external agentic commerce on Gemini or ChatGPT?
You could still build your own custom
implementation of a merchant agent or Ginny on your website. Maybe I start selling cat goods.
I could reuse some of this.
But I would advise, maybe look into some of these primitives and trying to use them, because they've been standardized across merchants. So, they have been well thought out, and also you could probably reuse them to sell externally as well,
on ChatGPT and Gemini.
So, remember,
I was talking about the discount codes? There's a reason for that. When we build out this demo, and in my time
building agentic commerce at Best Buy, we have realized, working with AI and conversational experiences
without evals is playing whack-a-mole.
So, if you choose to use the same architecture for your own customer
base
like jinny.com websites,
think very much about creating evals.
Uh, one of the things that I could not
uh, emphasize more about is you should test, test, and test.
If you go over here, I can also run my scripts for run evals.
And
this evals folder has all this evals.
The reason
I'm also showcasing the code
is there's a template folder here,
and
we can go back to the slides.
And if you don't do evals, this is what might happen what might happen. I love Chipotle. I don't know if it's true or not, but I found it really funny, so I'm going to talk about this.
So, this popped up
that when Chipotle rolled out their agent, people were using
it to ask programming questions,
right?
If you don't tell your agent to not allow for those kinds of things, people will use it. This is, hands down, one of the most creative way to get free
AI usage when you don't want to pay for that Claude subscription.
And if we don't write our evals and test intensely, those things will happen in production.
Uh, the discount code will be told, even sometimes more
uh, sensitive things like, who else is checking out this product? So, the kinds of evals that I would highly recommend you write is behavior evals, protocol compliance, because when we're sending it to, like, let's say, GPT
sorry, ChatGPT.com or Gemini, you want to make sure that the feeds are actually
conforming, or else they will not support it. You should also think about latency benchmarks. Every second in retail in the shopping journey where you're actually not selling,
there are chances that the other website is going to be faster, and people are just going to move away, or they just don't feel like it anymore.
Lastly, I also recommend using LLM as a quality judge. You don't have to use something fancy. Talk to
your product friends, and figure out what's the best way to do it, and use a low like best use cases and write them out.
And I would like to also talk about, now that I've discussed all of this, what's actually stable today and what's still forming.
MCP is widely adopted. A2A is widely used.
UCP, ACP is out there.
Uh, what's still forming, though, is AP2 and actual usage of it,
ACP versus UCP convergence. Do we always have to do two different specs? Identity and consent standards, and multi-agent checkout delegation.
So,
uh if you have to leave here today with anything, I hope you leave today with a good mental model of how agentic commerce works.
I have nothing to sell you, but I do have gifts for you. I find agentic commerce really exciting, so you can find this entire presentation on GitHub. And I came up with a template.
It's a three-service starter. If you want to do customer agent customer agent or you want to do the merchant agent, you can do that, because I love evals. That saved my life. I have some eval templates for you.
And you know what if you want to send it to all of your merchants, not just one? I have a catalog sync process as well, which will allow you to type into your own product, and then turn it into ACP or UCP or Meta, so you can sell there.
And lastly, but not the least, we all know now, these days, we don't write code like that. If I give you a template, you'd be like, "Meh."
So, I have agent skills that specifically does a merchant agent,
uh customer agent, and all those different catalog syncs that we have talked about.
I hope you had an amazing time, and learned and had fun as much as I had presenting this. Thank you. My name uh
My name is Ahnaf Prio, and I hope to see you again soon.
