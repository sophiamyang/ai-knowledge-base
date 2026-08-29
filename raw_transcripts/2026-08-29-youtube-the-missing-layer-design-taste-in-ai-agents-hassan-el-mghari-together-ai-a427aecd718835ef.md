---
id: "a427aecd718835ef"
title: "The Missing Layer: Design Taste in AI Agents — Hassan El Mghari, Together AI raw transcript"
aliases:
  - "The Missing Layer: Design Taste in AI Agents — Hassan El Mghari, Together AI raw transcript"
  - "The Missing Layer: Design Taste in AI Agents — Hassan El Mghari, Together AI"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=7GMKdpLsxwU"
origin: "https://www.youtube.com/watch?v=7GMKdpLsxwU"
type: "raw-transcript"
created: "2026-08-29"
---

# The Missing Layer: Design Taste in AI Agents — Hassan El Mghari, Together AI Raw Transcript

All right. Hello, everybody, welcome.
My name is Hassan. I lead the developer experience team over at Together AI and I'm super excited to be here today to talk to you about how to make AI apps look good, or stop letting your agents ship ugly UIs.

I'm especially passionate about this project 'cause a big part of my job and just my personal life, I just love building a lot of these AI apps and
I'll go to the next slide.
I've been building about 10 apps a year for the last 5 years and I've been lucky enough that some of these apps have gotten, you know, millions of users that have tried them out.
And I think the number one reason for that is honestly just design and UX.
And so that's what I want to talk to you about today is how I approach design and UX in my apps as someone who's not a designer.

Well, before we move on really quick, I work at Together AI. We're an AI-native cloud platform.
We help you do three things: we help you run open-source AI models, chat models like GLM 5.2, image models like Nano Banana, audio models, vision models, we have kind of all the different modalities and all the big open-source models on our platform through our inference API.
We let you fine-tune models on your own data.
And then we also have a GPU cluster product where you can reserve H100s and B200s to train your own models or do your own inference.

So, getting into some demos, I just want to start with a couple apps that that I've built, so you get a sense of like the the type of stuff that I build.
They're usually very simple, one-page apps where I try to index on the design and some animations and things like that.
So this was like a logo creator app that I built that got about 85,000 people that that used it.
This is one called MakeComics, where it'll create a comic book from scratch, starring you as as the superhero.
And this one, actually, we actually have in person at our at the Together AI booth at this conference, where you can go and there's a little iPad and you can take a picture and and get a real comic book printed out there that you can take home.

Other stuff like, this is generating subtitles from from videos.
I upload a lot of videos to YouTube and to Twitter, and so I needed something like this and I I looked into just like generating subtitles with with open-source models.
This one had about 8,000 people that that checked it out.
You know, AI chat app for open-source models, this one's fairly straightforward.
This one is a is a website that I built to help you build five or six different variations of whatever landing page you want to build and then you can kind of choose one of them.
And then the the last one I'll show off really quickly is like an AI cloud agent where you can ask it to do things and give it a GitHub repo and it'll spin up a sandbox and actually create a PR for you from scratch.
And so this is just a an example of like some of the stuff that that that that I build and that I that I put out.
And and I think really the big takeaway here is, you know, we live in a world now where more and more AI apps are kind of slop.
You know, you can kind of look at it and within a second or two, you can kind of tell that like, uh, this this kind of looks AI-generated.
And so I think just doing a little bit of extra effort, like a little 10 to 20% after just focused on the UI, is is a really, really big competitive advantage for these things.
So, like I said, vibe-coded apps, kind of all look the same.
They have the same tells.
They have the same kind of purple gradient background in every single one.
They have italics in in headers.
They always have the scroll to explore, for some reason.
They have these pills that are all like all caps and with with spaced-out letter spacing.
They have these gradient logos.
They use a bunch of emojis.
And so it's it's the same kind of stuff, sometimes some some spacing and padding issues.
But the point is, it's it's actually just like a If you really think about it and you look at all of these AI-generated websites, you can come down, you can make a list of like 20 or 30 different things that are like, okay, this is this is what AI slop is, right? All these like random graphics.
And and so I'm going to talk about two different ways that I've tried to overcome this.
And and the first one I'm going to start with is this design skill that I built called Hallmark.
And Hallmark basically takes all of these AI slop patterns and codifies them and and tells AI models like, hey, like don't don't use these, you know?
Don't do a purple gradient.
Don't use italics in the title.
And and all of these AI slop gates is what I call them, or slop patterns.
So that's one thing it does. And then the second thing it does, which I think is really important when you're building stuff, is it gives your AI model a lot of different themes.
And so I I built a bunch of these different themes, we feed them into Hallmark, and so like when you ask Hallmark to create a a website for you, it'll use these as context.
And then that's gonna that's going to be a theme throughout this talk as well, is if like if you give AI models really, really good inspiration, they tend to perform very, very well.

And so I launched this about a month and a half I have about a month and a half ago, I have a little over 10,000 people that have tried it out so far.
These are some examples of of I've mostly indexed it on landing pages, but landing pages using Hallmark.
And so this is build a landing page for an indie podcast, and it gives you that.
And there's different skills and stuff that I'm not going to get too deep into.
But the main things I just want to I just wanted to cover are the AI slop gates and the themes.
And and those two things really they do a lot.
And so this is the announcement tweet, and and I got a a bunch of really great feedback and we're still iterating a lot to to try to make it really, really good.
But I've found this to be a a a one way that I try to avoid slop, AI slop websites.
And so this is some some more examples of Hallmark-generated pages.
This one's build a landing page for like an invoicing app, and and you can see like they don't have a lot of the same tells that you'd expect from AI-generated website.
And these also are just one-shot.
Right, this is one single prompt and you get this whole website.
And really a lot of the magic also is in kind of iterating on these things over and over and over again.
So this is this is another one.
And then like a before and after, this is a pretty good example.
This was like build a page for like a learning app for kids, and on the left is like without Hallmark, and on the right is with Hallmark.
You can see it like, you know, it's just a little bit cleaner, it's a little bit nicer.
It has more like animations, which I didn't record a video to show it, but it it just looks a little bit nicer in general.
This is another one as well.
On the left, kind of like the the classic AI-generated page with the with the gradients and and everything like that, and on the right is is with Hallmark.
You know, you can look at the one on the right and still say like, oh, well, that's not a perfect landing page.
But it does give you a much better base to start out from, right?
And then you can kind of iterate your way to something that, you know, really, really looks incredible.

And, you know, I've been indexing on this thing, but app iteration is also very important.
And I think specifically, a lot of people, I think, undervalue the importance of using smaller, faster models for these app iteration cycles.
A lot of the apps that I build now, I'll kind of start in like Codex or Claude Code to build a base, and then for iterating, I'll use usually smaller open-source model like GLM 5.2.
GLM 5.2 is amazing.
Who here has used it? Show of hands.
Okay, a few people.
So this is a model that came out two weeks ago that in my opinion was like the first open-source model that to actually be very, very good at design.
And actually we're going to play a little game here where one of these landing pages was generated by GLM 5.2, which is like a cheaper open-source model, and the other one was generated with Opus 4.8.
Raise your hand if you think GLM 5.2 is A.
Okay, four hands.
That was the GLM 5.2 one, right?
So they're almost almost indistinguishable in certain ways where the one on the left was generated with GLM 5.2.
It was created way faster, as well cuz it's just it's a smaller model, so it's inherently a lot faster.
And the one on the right, you know, cost five times as much and and was a lot slower as well.
So anyway, this is another one where the the left and the right, the left one arguably is even more AI-generated and and that's the one that that that Opus actually created, right?
So anyway, like when I say like use a cheaper model to iterate with, it still needs to be sufficiently good and and GLM 5.2 is one of those models I feel is is really, really incredible for for this kind of stuff.
So this is another example where it's very hard to tell the difference.
And and for iteration, so this is like a a a really simple website I one-shot with just that one prompt.
This is using GLM 5.2.
And you can see this does have a lot of the AI tells.
It's impressive that it actually works.
It's an image playground where you send it a prompt and you get an image.
But just with a little bit of iteration on the left—I'm not going to go through all of it—you get to a website that looks it it looks roughly similar, but it just looks a lot nicer.
And it has a much better logo and way better loading states and animations and just better spacing overall with with just a one or two follow-up prompts.
So I I think like iteration is is extremely, extremely important.

So the final part of my talk is just takeaways for like how how I approach building apps that look good as someone who's not not really a designer as well.
A lot of other people speaking on this track are are incredibly talented designers and and you should take a look at their thing.
My my objective is not necessarily to make the best designed app in the world, it's just to make apps that look and feel really good, or at least much, much better than like purely kind of AI-generated slop.
So so my my main takeaways for this: one is like getting familiar with a lot of these AI tells, right?
We went through some of the like patterns of of AI slop.
A lot of the time, you know, I sit down with people and I show them a website and they're like, 'Oh, well, that's AI-generated,' right, in two seconds.
But they can't tell me why, right?
They're like, 'Ah, that just looks AI-generated, I have no idea what it is.'
And so I I think it's it's worth understanding that like, well, yeah, it's it's purple gradient and it's this this logo and it's this thing.
And when you understand that stuff, I think it becomes a lot easier to to bake that into the apps that you build, or ask the AI models to hey, like, 'Hey, don't don't do this, or don't do that.'
So so that's that's one tip I have.
Another one that's kind of tangential is like saving your preferences in some sort of skill or Markdown file.
You can do it in AGENTS.md, you can do kind of whatever you want.
But the big thing here I think is as you build stuff, you start to build an intuition for like what you want, what you don't want.
Like you generate a website and every single time the logo looks like crap and you have to regenerate the logo, you can start to build out an AGENTS.md that has a bunch of this stuff.
Like, 'Avoid this, for the logo, do them this way, for this, do it that way.'
And and as I've gone, I've kind of built up like a substantial AGENTS.md that helps me do this.
And and to a degree, this is kind of what Hallmark is as well, right?
If you don't have your own, you can use something like like Hallmark.

This is maybe the most important one.
If you take one thing away from this talk, please give your agents references and screenshots.
I don't build anything nowadays without giving AI models a lot of inspiration.
And I kind of have this like inspiration vault for like anytime I look at like a website or an app that I really like or that I'm like, 'Wow, like this this looks amazing,' I'll just save it I'll just save it somewhere, and now I have a a really large collection of them.
And so when I'm building a new app, I usually will will be like, 'Oh, like actually, kind of I think I want this to look like a a mix of Duolingo and a mix of this app and a mix of this app.'
And I'll paste in a ton of screenshots for the AI model to look at and and the output will always be way, way, way better.
So always try to use references and and screenshots.

Longer and more specific prompts are always better.
These days, I I will just record voice notes.
And so I'll start a voice note for like 1, 2, 3 minutes, and I'll just rant and be like, 'Oh, I want to build an app that looks like this, and here's how you you should use it, and here's the type of user that's going to use it, and we have a text box here, and we have an image upload thing, and here's how it should look, and here's and here's some inspiration,' right?
And so it's usually like all my prompts now are like two or two to three paragraphs, so they're they're a lot longer prompts and and they usually do a lot better.
Like this is like a an example of a much longer prompt.
I'm not going to go through all of it, but it it just produces something that's just a little bit better, like on the at the the thing on the bottom was was kind of produced with with with this prompt.

Break things down into steps.
I think like So I just talked about make your prompts longer, but also if you're building seven different features, you probably don't want to put them all on the same prompt, right?
You probably want you can do one, you know, one or two features per prompt where you talk about them extensively.
And and usually I'll send off like the start of the app will be like a a huge prompt with a bunch of screenshots of inspiration, and then immediately I'll queue up like a bunch of other messages of like, 'Oh, we'll do this feature and do this feature, this do this feature,' and I'll kind of let it go.
So that's something that I that I've seen helps.

Cool. This is one this is the one I talked about: iterating with a cheaper open-source model can beat using closed-source models for everything.
For iteration tasks, I I've I've found they're a lot better.
I think Cursor did a great job proving this with like Composer 2.5, which is like an open-source model that they post-trained.
And it kind of feels magical using it for iteration 'cause it's so, so, so fast.
And so you'll see that in in some of these open-source models.

Cool. And then the last thing is I see people kind of trying to one-shot apps and then being like, 'Well, that's it, I'm done. You know, I'm going to post this as is.'
And it's really, really important to understand that like whatever your agent creates is just the base, right?
And it's on you to kind of like give it additional context, give it additional inspiration, and go back and forth and make the apps look and feel really good, keep them simple, and and kind of iterate that way.

Cool. That's all I got.
Thank you so much for coming.
