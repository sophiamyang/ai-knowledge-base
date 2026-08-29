---
id: "c819e4e464315097"
title: "How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth raw transcript"
aliases:
  - "How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth raw transcript"
  - "How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=V_5bn4q-vAI"
origin: "https://www.youtube.com/watch?v=V_5bn4q-vAI"
type: "raw-transcript"
created: "2026-08-29"
---

# How We Got LLMs to Recommend Our Open Source Library — Christopher Burns, Inth Raw Transcript

The talk title, we'll see if it lines up by the end of it,
but when we put this talk title in,
just be honest with you, so much changes in like three days at this point.
We'll see how it goes.
So, yeah, the whole point of it was that how I got LLMs to understand my open-source library and what I did to do it well.
Is it some kind of scientific background? Am I from a lab?
No.
My slidey clicky thing's not working.
So, I just like to say again, I'm just like you, I'm just this side of the stage.
I've just hacking hacking it together,
figuring out what is useful, what is token efficient, these kind of things.
And again, I am British, please don't think my accent makes me an expert.
So, for quick context, I'm Christopher Burns.
I'm the founder of Inth.
I created a open-source cookie banner library called c15t,
that really annoying thing on the internet,
that is me.
I spoke at Next Conf after it started taking off and it had 1.2 thousand downloads at the time. Now it's closer to 2 million.
In terms of like statistics, so we just check that, you know, this is not theoretical, this is actual something that's succeeding.
We have 3 million npm downloads,
4.5 4.5, 45% month-on-month growth,
2.8 thousand websites using as in production from Mintlify to Zer to Infisical.
And the whole concept of this talk was, it goes back to we were doing all these things to make our library more efficient,
you know, we were batting upwards compared to every other tool.
Every other tool was built for marketers and lawyers.
We were built for the developer.
So we had to make sure we had a very good developer experience.
And we had an onboarding form that said, "How did you hear about this?"
And we started to get spikes that from April 13th, you know, now it is our number one source of inbound is Claude, ChatGPT, Codex, that is ChatGPT, Gemini recommending us.
And I'd like to think of this as, you know, the iceberg.
You know, we start with the top of c15t,
and there's many, many tools that go into it from, you know, llms.txt to sitemaps to RSS feeds to robots.txts,
so many micro-optimizations that you can do from old methods of running the internet to new methods.
And how many of you have, you know, made these kind of tools?
How many of you have really, put simply, said, "Hey, agents, we need this to be done,"
and yeah, it said, "We should install this library," and you've gone, "Okay."
Raise your hands. How many people have done this?
Pretty much most people.
That's a lot of hands.
So, what's really funny is that we went from wizards installing our software to agents installing them.
And I just went through Y Combinator,
and what's really interesting is if you know who these two people are,
these are the co-founders of Stripe, the Collison brothers,
and they had a really classic saying of like a Collison brothers install,
and they would hand you their laptop and they would install Stripe.
These days, it's kind of like just a prompt.
Being in Y Combinator, we just gave people a prompt.
And really what that means is that our very good developer experience primitives are now hitting agent primitives.
So, as we was pulling all these things together, there is no one tool that fixes everything.
I like to think about these problems like, you know, Batman's utility belt:
loads of really small things targeted in different areas to get it done.
And we built all of these things into c15t because we wanted c15t to be the best developer framework in this tool.
Think of it like Stripe docs.
And as we was building more and more tools, more and more documentation websites,
we actually started abstracting these tools into a side quest that we call leadtype.
So, all of the things that we're going to talk about now are things that we have already solved with this open-source framework.
We have our friends at other developer companies implementing it and seeing similar results about how to like optimize for the agent experience.
So, again, this isn't a magic SEO tool.
It's actually a very non-sexy title, but it's a framework neutral docs pipeline.
Complex.
But really, all it basically does is take your .mdx files,
you run leadtype generate,
and it will spit out everything for, um, optimized agent experience for your websites.
And the rest of this talk is going to look a bit like a BuzzFeed, uh, list, to put simply, of these problems,
because again, not everybody knows even how to put an llms.txt on that website.
So, you know, that comes to the first problem of if your docs have hundreds of pages,
and how can it navigate them to find the right questions?
The first solution is obviously an llms.txt.
What we found in our research is that it's much better not to just generate this.
It is much better to write your llms.txt from hand.
Obviously, our tool wraps it,
but write it as you are trying to get the answers across to the LLMs.
For about 40 good lines beats 1,000 lines of noise from our testing.
And that comes to the second issue of agents don't know how to browse, they know how to fetch.
So, you then need the second part of the solution of the llms-full.
Again, think of this as a sitemap
where it takes the actual, uh, page and the links and a short, uh, description of what each page is for the LLMs to reference.
Again, most people have heard these two solutions,
but where things are starting to get very complicated and we're seeing a lot of optimizations right now,
is that HTML is expensive,
and why can't we just ship Markdown to the agents?
And we can.
And you have seen that everybody has started creating twin MDs.
So that's taking the normal website such as Next.js quick start,
and then having a .md on the end of it.
And when you load that,
it goes to the Markdown version.
But what's really important here and it's really worth noting is this line at the bottom.
If you look at all the best documentation websites: Mintlify, Vercel, c15t—pat myself on the back—
they all have this in the header.
This is saying to the agents whenever they visit the website
that there is an alternative version of this in Markdown.
Again, who actually supports it? Don't ask me.
Perplexity, some of the agents,
it's all up in the air.
And then the second thing as well is that taking the .mds,
you need to make sure that they're available through multiple methods.
So one of them is like the .md, so as you like copy it to an agent you say .md.
Another one is just taking the normal, um, link and then adding a, uh, redirect into your like your Next.js config so that if it detects an agent has the header of accepting Markdown,
instead of returning the HTML, it will return the Markdown.
And then the third one is that not all agents can append header tags,
so there's also a URL query of mode=agent.
So they're the ones that pretty much everybody knows,
and it's pretty basic internet knowledge at this point,
um,
but one of the really interesting ones is where we're going next,
and our tooling is also helping this, is that an agent can't ask your website anything.
So we need to think about the WebMCP,
and this is still very early,
but our tool is already exposing three different tools to WebMCP:
search docs, get pages, and ask docs.
Again, um, our library leadtype is pulling all of that context together
so an agent can easily ask it the right questions.
I think we'll even see a future where communication happens over email,
and there's companies in San Francisco building that today.
But this is actually the most interesting one,
and I think the most important one that anybody who has any type of developer module surface—npm modules, cargo, Python, whatever—
is that the uncomfortable truth is that coding agents are actually never visiting the website if you have a library.
They're actually visiting the node_modules.
They read the repo,
and they read the node_modules.
They they have previous stale training data,
and they're trying to work it out on what it can do from the the the compiled source.
So, again, following what people like Vercel are doing and people who are thought leaders in this industry,
is that we take the bundled Markdown documents,
and then we also put them in the node_modules
with an AGENTS.md file.
And the AGENTS.md file basically says, "If you've got a problem, if you've got a question,
all the documents are here, grep them."
And we actually see that this has surprisingly real effects.
We can see that between many different models, almost 50% token saving
on, instead of trying to search the web, find the right tools,
pulling the Markdown files from your codebase.
So if you have a library that's forever changing,
then having the node_modules built-in is a very effective solution.
This is also working without any skills,
but if you want as well, you can add skills to it to say look at the node_modules and go from there.
And again, just uh doubling down into this point,
looking at like the AGENTS.md file,
you can say like, "When working with c15t nextjs library, read the bundles, and
verify that they match and go from there."
So that's really like how we've done it.
I don't want to say this is like prescriptive, that I know the answers.
If you have documentation websites or if you have any type of Markdown,
if you're running your own blog,
you know, I've been using our package as well on our marketing website.
Every part of our marketing website also has a Markdown file.
It can be something that's used for many things.
We're currently just um, most people are just using it for documentation,
but you can literally run it and it will pull out all of these extra files.
And one of the big things was when I put this talk together,
you know, we were seeing the results that Claude was recommending,
but there was not really any like test suites yet or test harnesses on like, "Is your site agent-ready?"
And Cloudflare brought one of them out.
But my favorite
is actually one called ora.ai.
Um, this is brand new
and it tests a lot.
I'm happy to show our score of 59 because it's constantly changing.
Three weeks ago, it was a lot higher,
and again, this is a forever-changing area.
So, ora.ai, put in your website and it'll start giving you recommendations.
It's forever changing, again, we can just stay on top of it.
And yeah,
this is like one of my final slides is that the the the market,
agents, LLMs, everything is forever changing.
There is no such thing as perfection.
When I started making these slides, I got so caught up of like everyone expects me to be the expert here,
but I've just been hacking on this problem a little more than you guys have so far.
So, never get caught with being perfect.
Every small little increase really does matter.
Every small little thing you add really does matter.
Thank you so much.
You can find me on X, @burnedchris, and LinkedIn and everywhere.
I think we have time for one or two questions.
Yeah, of course.
So, if you were building um
uh we're a website agency, we work with a a lot of startups building like their own websites.
Mhm.
If you were just building a website, not necessarily like developer tool, but just a website to be found,
which of these methods like would you concentrate on if you're starting from scratch?
Yeah.
I think the most important ones, and we're starting to see this more and more,
is trying to provide a .md file for every single page.
A lot of CMSs are not built in this way,
um and we see this optimization happening more and more where,
I didn't put in the slide, but we're seeing more and more websites being visited by agents instead of real humans.
So in terms of even like trying to be proactive and token efficient,
you should provide a Markdown file if you can.
Again, a lot of CMSs are not built this way.
I actually built my own CMS.
Uh, my name is Chris and I built Chris CMS, short for Christmas.
It's a whole It's a whole thing my team wishes I never built.
But it does work, and it does bring this like token efficiency, uh, up.
So, yeah, I would say llms.txt is your first shout,
uh llms.txt full full .txt.
Second, if you if you can just do them manually,
say you're not even working on systems that have, uh, Markdown, I still recommend them.
Um, but you can always get creative with creating these, um, files on the on on the go.
