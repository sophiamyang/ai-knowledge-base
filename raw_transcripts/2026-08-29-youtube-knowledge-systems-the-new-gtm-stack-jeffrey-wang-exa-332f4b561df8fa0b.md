---
id: "332f4b561df8fa0b"
title: "Knowledge Systems: The New GTM Stack — Jeffrey Wang, Exa raw transcript"
aliases:
  - "Knowledge Systems: The New GTM Stack — Jeffrey Wang, Exa raw transcript"
  - "Knowledge Systems: The New GTM Stack — Jeffrey Wang, Exa"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=6pbQgnJ9Voc"
origin: "https://www.youtube.com/watch?v=6pbQgnJ9Voc"
type: "raw-transcript"
created: "2026-08-29"
---

# Knowledge Systems: The New GTM Stack — Jeffrey Wang, Exa Raw Transcript

Hey everybody, I'm Jeff. I guess I was introduced, but I'm the co-founder of Exa.
And today going to give a talk on turning go-to-market into an AI engineering problem in the spirit of this AI engineering fair.
And just a quick show of hands just to like understand the audience, like raise your hand if you're technical.
Okay, great. Okay, so I kind of oriented this talk around like go-to-market as presented to to engineers, so I'm happy I did that.
Cool. So first, just to like ground the ground like what what Exa is, cuz it's sort of relevant inside of this presentation.
Exa's a Exa's a search engine for agents.
Think like agents are really smart, but they don't have access to the web.
We're like this web MCP, web tool that agents can access.
We power Cursor, we power Cognition, we power a lot of the AI ecosystem at this point.
And before we start, I also just want to like talk about, you know, especially to a technical audience, like why should you even care?
Like why should you care about go-to-market?
I guess this audience cares about go-to-market cuz you chose to go to this go-to-market talk.
But I think there's this like funny narrative right now which is like people are like, oh like, product is the only thing that matters, or distribution is the only thing that matters.
And there's all sorts of like Twitter flame wars like, like, oh, is Clay going to succeed because they're really good at distribution, but they're like what what the heck is their product?
And then and other people are like, oh the like the the product needs to be super good cuz agents, you know, agents shop for the product, so they'll shop the for the best product.
And so my view and my experience in the last few years is that you just kind of have to do both.
Like I think you have to get product right and you have to get go-to-market right.
Like you've got to build the thing. It's got to be good.
And then you got to get it into people's hands.
If you don't do both things, then you don't have a company.
So that's kind of my view on the matter.
And I would say like a really funny thing also is like as a technical person, when you start a company or you start some sort of project, like very much so the bias is like, hey, I'm going to just build the thing, I'm going to make it really, really freaking good, right?
Like that's kind of like the bias you have as like an engineer.
That's the bias we had when we started Exa, and we were like honestly pretty bad at go-to-market.
Like we were [laughter] we were not doing enough marketing, we were not doing enough sales.
But I think the cool thing about a about go-to-market particularly in 2026 is you can treat go-to-market like an engineering problem, and particularly an AI engineering problem.
And so I think that's like a super exciting thing.
Like it's like more fun for engineers than ever to do go-to-market cuz you can automate things, you can you can do so much as one person and etc.
Also, I want to make this interactive.
If if anybody has questions at any point, please please ask cuz I'm aware there's a lot of talks and I don't want to bore you.
Cool. So cool.
So so the hypothesis I have is if you're an engineer or or if you're anyone, you can treat go-to-market like an engineering problem.
So first, I guess like what is what do go-to-market teams do?
So I have like a laundry list of things here of things that go-to-market teams do.
But here are a few, like one is you got to research like your customer, right?
You got to research your targets.
You have to find out information about your about targets.
You have to find the right people at particular companies.
You have to build POCs.
There's like a just a ton of stuff you have to do, right?
So, you know, I'm not going to not going to list everything here, but like what is the grand unifying theme?
Well, go-to-market is a data problem, all right?
So you have all you have this like entire world of of of what your product does, and then in this entire world of like all your potential customers, and you're just trying to like learn and figure out what your world looks like.
And so this is my this is my proposal.
It's a data problem, and we have to solve it from a data perspective.
Cool. So, okay, so what is the data that is relevant?
I propose that you need basically a live model of your world that agents can act on.
And so what does that mean?
Okay, well, one is you have a ton of internal data, right?
There's all this information that you know about your customers, about people that are at your company, data about how people use the product.
That's like internal data that you know.
And then there's all sorts of external data, right?
Like there's over 60 million companies in the world, and there's like billions of people, like over a billion that are on LinkedIn, for example, and all sorts of stuff are is is is like happening every day, right?
Like there's all this news.
And so when you're building like this data go-to-market system, it's important to keep in mind just like all the different sources that exist and and and and are available to your agents.
And cool. So I'm going to like go through, hopefully, pretty fast just all the different components of what we've built at Exa.
And just for like context, I've been really passionate about this for a long time.
So like Exa was launched in the middle of 2023, and so we were post-GPT-4, and GPT-4 was really incredible cuz it could actually, even then, even though it's way worse than like Febo or whatever, like it could actually just automate entire parts of go-to-market.
And so from the beginning, I've been thinking about our go-to-market from from a very, very AI agent-first perspective.
And so we're going to go over two interfaces that we have that help us, and then two agents.
Cool.
Cool. Okay, the first is what we call our ICP dashboard.
And the ICP dashboard is an product that we have internally that answers the question like, what is our world?
Like what is the world of customers and use cases that we care about?
And what we actually do is we go ahead and use Exa, and again, Exa is this like arbitrarily powerful search engine for AIs essentially, and we just classify basically like every possible company that is inside of our total addressable market.
And I kind of blurred out some of the details on like how much money we make from each category and stuff like that.
But yeah, we have like categories like model providers, AI coding platforms, like say Cursor, go-to-market intelligence tools, and this makes up our TAM, and we have an understanding of literally like almost every company with in those segments.
And then for each of those companies, we can deep-dive, right?
So here's the example of SpaceX.
We can see how much annual spend we could anticipate them to have and then all this like metadata about the company.
So we have a list of all the companies and then a ton of data about each company.
How do we do this?
Again, we're able to do this because Exa is this search engine.
We take the internet, we crawl it, we train we train embeddings to do web search really well.
And so basically from a technical perspective, you can think about Exa as like embeddings over the internet.
And when you have embeddings over the internet, you have this like arbitrarily powerful semantic filtering and slicing and dicing of any type of data that you want.
And so we use that to generate these this like gigantic list of potential ICPs.
Cool. Next, we have a tool we call RequestLens.
RequestLens, what is RequestLens?
Well, it's basically a system where anytime something significant happens with any of our customers, we're alerted.
Someone signed up, someone used a ton of searches, someone stopped using searches, someone showed up that we really, really care about.
All these things are signals that we are notified about and that our team can act on.
Cool. So those are the two interfaces that we have, and then I'll go over two types of agents that we have.
So one is coding agents.
So our go-to-market team is crazy [laughter] crazy, crazy deep on agents.
So like like our our our engineering team uses a lot of agents, but our go-to-market team is like like you could look you could look at some of their like Devin spend and like other agent spend, it's really freaking high.
And that's because everybody on our go-to-market team is constantly asking agents about our customers.
We have like like account executives that build demos for our customers.
Like it's just this crazy ecosystem where we have like maybe a dozen different agents inside of our Slack, and anybody can use any of them, they all have access to tons and tons of our internal data, and yeah, anytime we want to dig deeper on an account, anytime we want to make a demo, etc., we depend heavily on agents.
Cool. And then I want to talk about another really cool agent that I'm pretty proud of.
We call it Jeffbot, or I call it Jeffbot.
Jeffbot is an AI clone of myself as much as possible.
So what is it?
Well, basically, this winter break, I'm sure a lot of you spent that break playing with Opus 4.5, and I was no different.
So I was in Puerto No, I was in Mexico.
I was in Mexico, and I was I had a week off, and so my goal with that weekend with Opus 4.5 was to just try to make a digital clone of myself.
And so I did things like analyze like 760 of my emails to figure out what my email voice is.
Like, oh, I use 18 words on average per email, and I like to end emails with "best" and not "sincerely," like all all that type of stuff, right?
So I made like a like a voice for myself.
And then I also made a decision-making framework.
So I made like a decision-making framework where I analyzed hundreds of decisions I've made in the past, and I I analyzed them, and then I created evals.
So I actually created evals from those decisions and calibrated this agent system to behave like myself.
And then finally, I gave it like read and write access to all the data that I personally have.
And there's a cool advantage to this because like I basically have access to every single system at the company [laughter] cuz I'm in the the the nice seat of of having that.
And so like, yeah, this thing has access to like everything.
And basically what happens is anybody at the company can use Jeffbot to create drafts of Slack messages that are basically like answers or decisions that are made.
And this is a huge, great thing, like the go-to-market team uses it to like draft emails, for example.
Cool. All right, so those those
