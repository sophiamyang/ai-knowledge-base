---
id: "386fd20be2f34c8b"
title: "Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma raw transcript"
aliases:
  - "Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma raw transcript"
  - "Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma"
source: "youtube"
source_name: "AI Engineer"
content_type: ""
url: "https://www.youtube.com/watch?v=ZIYYsAzaLlA"
origin: "https://www.youtube.com/watch?v=ZIYYsAzaLlA"
type: "raw-transcript"
created: "2026-08-29"
---

# Building the Engine While Flying the Plane: Launching the Figma MCP Server — Jesse Lumarie, Figma Raw Transcript

All right. Get started?
Hi, I'm Jesse and I've been a software engineer at Figma for about three years, and I'm going to talk to you about how we built Figma's first MCP server in about three months.
And in case you don't know what it is, the Figma MCP server is a way for you to send context between production code and design, and vice versa.
Tools don't need to build a dedicated integration, they can just use our Figma MCP and they kind of get started.
So, taking you back to November 2024, long, long time ago, Anthropic released the MCP server spec, and everyone in the world of AI was sort of starting to use it and experiment with it.
But outside of Anthropic, none of the other AI agents or labs were really using it. So OpenAI, Cursor, VS Code, they didn't support it yet.
Once we got access to the feature in Cursor, however, we were able to kind of ideate and understand what it was capable of, and we got something a little bit closer to an actual product.
And that's where my story begins.
I was working on growth initiatives at the time, and I saw our internal demo, and I really wanted to use it. I thought it would be great for non-designers to kind of be able to use Figma.
I started creating actually a Figma plug-in based MCP server, and I started doing it one day a week. It was kind of my 20% project that we didn't We didn't really have 20% projects, but I I really want to work on it, so I did.
And so I got staffed with some other folks on the team. We were the MC peeps. That's a peep. It's a candy if you don't know.
They're delicious. And I I just want to be very clear.
I'm going to say I a lot and we. There was a big team behind this, so it's not just me, and they're all fantastic.
A few weeks later, after we started getting our initial architecture sorted, a new version of the spec dropped, deprecating the support type that we were going to use, which was server-sent events.
And while the MCP spec was sort of chugging along, clients were adding features and support in different paces.
Claude had early support, Claude Desktop, but Claude Code wasn't really supported with all the complete set of features.
OpenAI and VS Code didn't have support until that spec update, and then it wasn't even then VS Code didn't go out of didn't get to GA until July.
It didn't mean that all the features were implemented, either. There are lots of different pieces, and in many cases, only tools were supported.
VS Code was truly like the golden client. They eventually supported kind of all pieces of the spec.
But it was it was hard to kind of understand what you were building towards because clients supported so many different things.
But even though we didn't know exactly what the MCP server spec would be supported, we knew that it would be extremely powerful and a great product for us to to utilize, and so we started building.
And so taking a more high-level recap, about a year ago, we launched our local MCP server. And what local means, it was heavily designed for developer use cases. You kind of had to know what you were doing a little bit, and we targeted developers because they were the first to adopt AI workflows.
They would use a single prop prompt like, "Help me implement this," and the developer could pull everything that they would normally get from Figma's Dev Mode into their coding agent.
This includes things like component data, spacing, variables.
And from there, we just kept adding more and more read read tools like for FigJam, for Make, etc.
But they all share this kind of mutual goal: to make Figma context available for developers wherever they are.
So, Figma, if you don't know about Figma, Figma is a canvas.
And it's represented as a scene graph in C++. It's a graph of connected nodes not unlike the HTML DOM.
And we had a number of different ways we could represent the scene graph.
We had this internal representation, which was kind of akin to JSX or XML, effectively converting the scene graph into JSX tags and XML tags and passing those to the agent.
It was abstract and sparse, but it didn't have super rigorous fidelity.
Another option that we had internally was D2R, which is our like way of saying a React Tailwind representation.
And the reason why we had this is Figma has a Slides product, and so we already had a way of basically converting the scene graph into HTML.
If you actually copy the output of the Figma MCP today and you paste into like a simple MCP or simple HTTP server, it should be pixel-perfect.
And if it's not, file a bug.
But we had a hunch that this representation would be the best one because lots of the models were sort of RL'd on this React Tailwind type of code.
And we we had a suspicion that it would work really well.
The last one that we kind of considered was just a plain image. But back in early 2025 2025, agents weren't great at converting images directly to HTML or CSS, or sort of other languages, and so we kind of used that as an additional piece of context, not as the sole one.
And to give you what what this kind of looks like in practice: On the left here, we have a a Figma frame, and on the right, we have the React Tailwind code.
You can also see at the very top, the Image Canyon Crew Meetup link.
We also basically abstract out the images within the code, sorry, within the scene graph, and put them at the top level.
Our first attempt was just passing base64 data into the code, and that was just a terrible idea. It would just blow up the context window and was bad all around.
Don't do that.
We'd also pass an image of the current node to the agent as well. While the image by itself did not do a good job of converting to code, having the code context plus the image actually had better agentic output.
So, what do I mean by better? How did we know it was better? We tried to do evals.
And so we did some sort of very simple evals to start with a mix of quantitative and qualitative data.
From a quantitative standpoint, we we looked at: Did it use variables?
Did it use the theming we expected? Did it use the right font?
And from the qualitative side of things: Does it look good? Did it make good decisions with incomplete information?
And we spent like two hours grading an eval into an Excel spreadsheet, and we said, "We're never We're never doing that again." It was awful. Don't do evals by hand if you can help it.
We had a bunch of toy repos that we kind of created or kind of had folks create for us.
And we eventually ended up coding up a web app that sort of helped us with the evals, which made things a lot easier, at least from like a process perspective.
One interesting thing is Figma there are Figma files which we are converting. There's a lot of open-source code out there, but there's not a lot of open-source code that also has Fig files attached.
And so we had to either create our own or sort of find different ways to make automated systems.
And now we have a eval that sort of runs like hundreds of times a week. Engineers can kick this off and sort of grade against prompt changes with LLM judges, so we kind of remove the human from the loop where where we don't need it.
But having an agent translate a pixel-perfect version of code isn't enough.
I mentioned that the React Tailwind version of our output was pixel-perfect. That's really only half the story.
An enterprise doesn't care if it's pixel-perfect if it's not using its like battle-tested, accessible, and internationalized components.
At Figma, we already had this concept of Code Connect, which allows you to link design components to components in your codebase.
We needed a way to use this with our MCP server so that an engine an agent used the correct components.
For example, this beautiful button here.
This would be a perfect representation if you were to throw that into an HTML server.
But you kind of see two problems.
If you had a primary button in your codebase, you wouldn't be referencing it.
And that's not ideal if it has accessibility properties or internationalization properties.
And then second, you'd eat up the context window.
We we use Well, this happened the last time.
We use React Tailwind to basically convert things over.
But we want to make sure we do it in the sparsest way possible.
All right.
Just gonna keep vamping a bit here.
And so picture the same thing on screen, but now we have like all this React Tailwind code. It's going to then be converted into sending over basically a sparse representation of it via Code Connect.
And by connecting the user's code to the design, we're able to pass back, effectively, what is a pointer, which allows the agent to use the code component, leading to our higher fidelity implementation.
So effectively, you go from like this big, old thing of React Tailwind to the small React component that just says, "Use button component."
All right.
It's going to let you You got to reset it? Okay, cool.
Let's pause.
Oh, what was that?
All right. I can start talking a little bit about the next bit. Oh wait, you can see the school thing.
You can ask yourself how I described it well. But yeah, it's basically like a React component that you're able to then bring into your code.
Once we felt good about the serialization syntax, we started to look at what an MCP server can be.
And the MCP spec had a lot of great pieces in it, but some features weren't quite fleshed out within clients, and other features we really wished existed.
Many clients only implemented a subset of the spec, and many features were very experimental.
This is the client compatibility matrix from March 2025.
Today, for example, we expose a host of resources to an agent so that it can figure out how to use our server, as well as different help articles within Figma, whereas before, we would send that information down with like an error, for example, and the agent would have to crawl, wasting inference and sort of reasoning to sort of figure out what is actually going wrong.
One small part of the spec that was missing was server instructions. I shouldn't say missing from the spec. It was in the spec, but no clients implemented it.
And it wasn't really highlighted in the docs until Anthropic added a a nice blog post to sort of talk about it, and then some clients started adding it. And therefore, we would add additional instructions into each tool call, basically instructing the LLM how to use our server even though server descriptions weren't necessarily written out yet.
Some other features that we really, really wanted were elicitation and sampling.
Elicitation, if you haven't heard of it, is a way for you to ask the user a question, take that input, and pass it back to your server.
So here, we have it's VS Code and basically just asking, you know, "What's my name?" and you're able to take that input and pass it back to the server, which is interesting on its own.
But we thought, in combination with sampling, which is unfortunately deprecated, but it's fine because you're able to work around it, but sampling is a way of having a server query the client's LLM from from our server. In in kind of the canonical case was for small queries.
We thought it'd be really useful to combine elicitation and sampling into a single workflow.
We talked about how Code Connect improves users' workflows quite a bit and kind of makes outputs a lot better.
What we wanted to do was ask the user, "Can we map out your code codebase for Code Connections so that our MCP MCP server can link them so that the output would be better and reduce the amount of context we send?"
Unfortunately though, most of the clients didn't implement these features and didn't allow you to properly query the the agent in the context of the codebase. So for sampling, even when VS Code supported it, you could only really query it as a general agent, not specific to the codebase.
But we were able to kind of hack around it using tools.
When you got the context of a particular component, or sorry, of a particular design in Figma, if we noticed it was a component and that it wasn't code connected, we'd send down a prompt to ask the user if they'd want to map the unlinked component, component, kind of mimicking elicitation.
If the user said yes, we'd send out another prompt to have the agent scan the codebase for potential matches, mimicking sampling.
We'd then service them in a specified format, or ask the agent to do so, and then have them send it back in bulk to make a bunch of Code Connections.
The screenshot on the right is the MCP inspector, and if you haven't used it and you're developing an MCP server, you're doing yourself a disservice. It's a really great tool, and it's open source and great.
But the magic in in our case was combining these two features, because we could ask the user for permission, we can have the agent give us those suggestions, and we can map them, and in the end, the users got a better experience.
It's pretty great.
The last sort of little thing that we did was we wanted to make our output the best it could be, and we didn't necessarily know when we were starting. You know, we had our evals, but we didn't know if the React Tailwind code would be successful for other types of codebases.
And outside of the elicitation and sampling, which didn't really work as we wanted, there was no way of getting that information from the user.
So we added some optional query arguments to our tool calls for ones like get_design_context where they would send back what sort of language, what sort of framework the user might be using.
This is imperfect. Agents lie. But it was at least a signal for us to understand like, "Oh, this type of user, the Svelte user may not have had a good experience, perhaps it's because our translation layer wasn't working as well."
We have found that that works pretty well, but this was kind of our way of verifying that.
While we were working towards our first beta, we know we wanted four things: We wanted to launch quickly.
We wanted to have the highest possible bar for our security. We wanted to respect file permissions.
And we wanted to respect our pricing and packaging so we didn't have abuse vectors.
And so after the spec changed and introduced OAuth in March 2025, we had to decide whether to keep our MCP server local or sort of switch to the new remote server using streamable HTTP and kind of like work on all the OAuth problems.
We punted.
So until late March, there wasn't this off-spec to to build from, and we could easily relay off from our web app to our desktop app.
So for folks who don't know, the Figma desktop app is Electron, and so the front end of it is a web app and we basically just run figma.com in that, and then we have an IPC bridge between the two, and that sends it to our Node process that allows us to talk to the user's file system.
We then sort of exposed a a server-sent events server in Node, and that way, clients could talk directly locally.
The local story was also really great with enterprises because they kind of liked the idea of our data not being sent anywhere.
This architecture was our fastest path to getting something into the hands of users to understand product-market fit and what kind of tools and use cases folks had.
We launched the MCP server internally, and the reception was extremely honest.
We base But we we worked out a lot of the kinks and we started to get some really positive feedback in the community from from a bunch of nice folks.
But launching this part was just the beginning.
We had a lot of improvements that we wanted to make, and we immediately started working on the remote server as soon as we launched.
Clients were on different timelines, and we were still trying to figure out, you know, where we were going, but we knew we wanted to get the remote server out, so that's what we worked on.
In September, we launched the remote server. We GA'd both servers in October 2025, and then we started adding read and write capabilities.
And kind of all these things combined ended up making for Figma one of the fastest-growing products that they've ever had, which was not something we were expecting when we started working on this.
So late last year, I started working on a slightly different thing.
We started to see some research that designers really wanted to shift to writing production code in certain cases, and we didn't really have a dedicated product for this.
So I started hacking with a bunch of MCP MCP folks at an off-site, and this eventually became something called Make in your local codebase, which is kind of Figma's agentic solution for for working on on Git GitHub and and local codebases.
And the reason I bring this up is only slightly self-serving, but it relates to this this next slide.
If there's one thing you want to take away from this talk, it's that we're so early.
Like this has not been a long time. The MCP spec is only 2 years old, and we're still figuring out the best way to do things.
And then second, Figma's done a great job of letting engineers build and figure out what's next and letting them run with it run with it.
I wasn't staffed on MCP. I wasn't staffed on our Make product, but I ended up helping them be built just because I was kind of given the leeway to do so and learning a ton along the way.
That's all for my talk.
I'll be around today and tomorrow, but feel free to reach out. I'm happy to talk about MCP, Figma, and all that.
Thanks so much for your time.
