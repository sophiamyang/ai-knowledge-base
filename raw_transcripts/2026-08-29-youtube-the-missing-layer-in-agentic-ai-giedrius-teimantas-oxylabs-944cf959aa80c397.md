---
id: "944cf959aa80c397"
title: "The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs raw transcript"
aliases:
  - "The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs raw transcript"
  - "The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=XsvUhpnHepE"
origin: "https://www.youtube.com/watch?v=XsvUhpnHepE"
type: "raw-transcript"
created: "2026-08-29"
---

# The Missing Layer in Agentic AI — Giedrius Šteimantas, Oxylabs Raw Transcript

What a beautiful voice.

All right, thank you for coming.

Um today I'm going to talk a little bit about missing layer of agentic AI and explain a little bit about how web scraping infrastructure can actually help you.

But first,
let me talk uh a little bit about my friend's idea.

So my friend had this idea.
He build this AI chatbot
that you know, chatted with people about their style and it was supposed to help them pick out new items,
uh, as a you know, some sort of a personal shopper.

And once those items were picked out, you know, this uh this this this chatbot would
uh produce prompts
that a shopping agent would then take
and attempt to find them
online
and purchase them for uh, you know, for for for the customers.

Um this idea you know, is not new and uh it could be applicable to many scenarios, but
my friend was kind of, you know, uh he was uh he was uh he was good at building agents, uh, but uh he ran into
different problems and asked me for advice.
And when he ran it,

he he would usually you know, instead of you know, product pages or whatever, he would get
things like that.
It's uh you know, he would get Captcha'd.

And and you know, and uh
you know, of course, you know, he was uh he was doing it very very quickly, so he vibe coded the whole thing,

uh while having uh, you know, a thought about you know, infrastructure and underlying layers and how it should work, I didn't uh at all.

Uh he was using a browser automation
framework for everything and
it was
slow,

expensive,
and unreliable.

So at the end, he made a product that uh
uh that does not work
and is expensive to run.

So he asked me for help, and you know, I was a little bit reluctant at first because
uh, you know, I don't like giving out professional advice, you know, for free.
But uh, I took a look at it, and uh,
you know, I got a little curious, I have to be honest.

I noticed that he was missing something.

Um he was missing a layer,
an infrastructural layer

that would allow this agent to operate freely
on the open web.

My name is Giedrius. I I work for Oxylabs, uh where, in the past 10 years, we've helped, you know, companies
that trained large language models
uh, get their data.

And now
we use this infrastructure to help AI agents
to access
uh web
on scale
and at low cost.

And uh
before we go into this agent
and see how we can build it, I wanted to talk a little bit about the scraping industry and how we operate.

And uh
the principles
that we operate on can be summed up by
one
uh sentence,

you know, cost matters.

And the first principle is

use a browser only when you have to.

Validate content.

HTTP response 200 does not mean
that we are good to go.

Lighter content is preferred.

Websites are full of JavaScript, CSS,

HTML,
and there's a lot of bytes that do not deliver
any value whatsoever.

And today,
I will demonstrate how these principles are also applicable
when building agents
that interact with the web.

So coming back to my friend's agent, right? Let's uh
let's take a look and see how uh we could do a better job and uh making this agent run more reliably.

So, here's how my friends set it all up, you know, so four different stages:

discovery:
the agent is was supposed to find products pages
on websites where these items can be bought.

Then, a decision stage, right? And uh where an agent can decide
uh what products to buy based on, you know,
uh the the the content of these pages, so the agent has to visit them,
verify that the the stock is there, the price is right,
the the the description fits, you know, the prompt.

And once that decision is made, user is given with a choice, you know, whether to go ahead with the purchase
or, you know, reject it altogether.

The problem was that
sometimes,
and of course, we go to execution right away, then execution just making the purchase.

But the problem was that sometimes it worked
and sometimes it did not.

That was a little problematic.

So let's dissect it step by step
and see how we could build this differently
while improving performance and reducing the cost dramatically
by using this same principles from the scraping industry.

So
the first stage: discovery.

So my friend,
uh, you know, he chose to go with a predefined list of websites:
major retailers,
uh, and queried their search pages in order to find this products.

He used the browser automation tool
for that. It kind of worked, but, you know, it did have challenges. So,

their browser automation tool lacked what we call stealth, so they could, so they would get Captchas and sometimes fail to access the sites altogether.
This would break down the flow.

So a retry mechanism would have to be put in place,
making the whole process very long,
uh, you know, costly,
uh, and sometimes the sites would not be
uh accessed at all.

And also, you know,
as a result, it also became very difficult to predict the final cost per transaction.

The list of websites that my friend was checking was also deterministic, so selection of items would only be limited
to the few choices he put in.

Websites themselves were heavy on JavaScript, making the whole process very slow and costly.

And finally,
even if it worked, items ended up being unavailable at checkout
because in the discovery phase, the he
was not able to use any geolocation capabilities and a lot of e-commerce websites are
uh, you know, uh
they take your user's location into account when displaying stock,
options,
sizes, and so ever.

So, now we solve these problems at Oxylabs every day. So, when scraping, you always want
the results to appear on the first try.

And to not to use browser unless absolutely necessary.

However, for this specific discovery phase, you also want to use, to allow your agent to search the web.
Doing so with the browser is very cumbersome.

That is why I chose to use a product that we built,
especially for agents, Fast Search API.

It returns a compact JSON, which is less than 2,000 tokens per response,
has fast response times:
less than 700 milliseconds on average,

and it's uh, has a a high success rate at a predictable low price.

And most importantly, it gives your agent access to the to, you know, to many popular search engines,
that
all of this websites
have been indexed index already a long time ago.

So in the discovery phase, instead of predefined list
and the browser,
we give agent a tool to search the web: Fast Search API.

Agent formulates fan-out queries and selects the relevant URLs from search results.

Since the responses are quite small
and there's no need for complicated models,
we can have the agent run quite quickly in this stage.

Um yeah,
so

so now the agent has
searched the web and selected some relevant URLs.

It is time for those, for for the agent to visit those pages
to see what they're all about,

in order to confirm price,
stock level,
description,
product details, and so on.

With this,
we can go to into decision phase. This is where agent
selects the items we will purchase.

For this, my friend also used the browser.
He ran many browsers in parallel so it could
uh, you know, so the whole process could happen faster,
and that is not a bad thing.

He managed to get some results, however many
of the results
would end up like this.

And the result?

The agent would be left with very few choices with the majority of popular retailers being left out.

It's a good thing he did well with observability, so he actually noticed when it happened.

But
what we see when working with these types of customers is that they often
fail to detect the failure.

They end up checking only the
content size and HTTP response code
and then feeding this large HTML to an LLM.

Now, and a large language model, of course, can distinguish between valid e-shop content and a Captcha,
but we need to spend tokens in order to do that.

And when we attempt to open 10 websites,
but only three
return valid content,

but feed all of the 10 to the to the model,

it is a problem.

It means that we waste 70% of the tokens.

And that is a little crazy in my in my opinion.

So I noticed this problem as well, and my initial hunch was
compression:
was to compress the output.

And then I thought, wait,
the problem is not the compression, the problem is that the content is not valid.

We need to make sure
that the content is valid before even attempting any compression.

This will lead to more options
for the agent to choose from and fewer wasted tokens.

And then I remember rule number one of scraping:
use a browser
when you absolutely need it.

Otherwise,
look for other solutions.

So
I I tried to rebuild this stage without a browser, and I uh only by using Oxylabs Web Scraper API,

and this gave me many benefits,
uh but firstly,

only valid content was returned.
In case of Captchas or other blocks,
the request would fail with an explicit error message,
so I know not to include it when sending to a large language model.

But the success rates are quite high,
and even for
protected websites, so that wasn't that much, you know, much of a problem.

So no browser was needed, and uh
everything is a lightweight REST API.
I can run hundreds of requests in parallel
and receive content at the same time.

Also the API supports markdown, so no need to sub- submit raw HTML
uh to LLMs.
If a website is dynamic,
it runs a full browser under the hood to render the content
correctly.

And finally, it supports geolocation options, so I can localize my results
and get relevant content.

The best part,

customers only pay for successful results.

So actually, yeah.

That's
uh, that's what's, uh that's was what that's was the best thing about it: no cure, no pay.
If If the scraper fails,
there's no cost,
and it fails loudly.

So now we have all of the information to make a decision.
We present the decision to the user, and the user makes the final call.

Once it's affirmative,
we move to the last stage
of the workflow: the purchase.

So I remember what I said a couple of times about browsers, this time,
but this time is different. You This time, you absolutely
need to use
a browser.

We need to process inputs,
and the content is highly dynamic.

Now, this time, my implementation, my friend's implementation
does not differ much. We both use Playwright MCP with a browser
and a large language model.

The main problem my friend faced, however, just like in uh in the previous stages
uh using browser,
was access.

Just like in the beginning,
as he was using the browser, he was getting Captcha'd into oblivion,
make it in impossible to automate the flow.

Well, the fix was quite easy.

I just connected Oxylabs headless browser, since it supports Playwright MCP, it's just a drop-in replacement.

With this replacement, I hardened this agent with years of scraping experience

and got
proper stealth
done at the browser source-code level,

a residential proxy attached to it out of the box,

and,
most importantly in this in this case,
a geolocation capability,

so my results are localized the same way
as in the
verification stage.

So if we run it,

we actually have
a a
a a a browser
that that access the content
and can actually automate the flow by, you know, selecting the right size from the prompt,
add it to cart,
and
complete the purchase.

And boom.

We have an agent that commands
a powerful infrastructure,
hardened by years of web scraping experience.

Not only does it open the up the web,
but also saves the time
on implementation
and token cost.

And
if I can leave you with a few lessons we learned today,
was that

you know, when building agents,
use the same principles from the scraping industry.
Use the browser when you absolutely need to.

You have to validate content before feeding it to large language models.

And most importantly, fill the missing layer
with the proper infrastructure
so you can focus
on building stuff.

But remember,
cost matters.

Thank you very much.
