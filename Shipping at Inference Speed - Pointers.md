- and when codex comes back and hasn’t solved it in one shot, I already get suspicious
    
- The amount of software I can create is now mostly **limited by inference time and hard thinking**.
    
- And let’s be honest - most software does not require hard thinking.
    
- The simplest form is text, so by default, whatever I wanna build, it starts as CLI. Agents can call it directly and verify output - closing the loop.
    
- **These days I don’t read much code anymore.**
    
- I do know where which components are and how things are structured and how the overall system is designed, and that’s usually all that’s needed.
    

The important decisions these days are **language/ecosystem and dependencies**. My go-to languages are TypeScript for web stuff, Go for CLIs and Swift if it needs to use macOS stuff or has UI. Go wasn’t something I gave even the slightest thought even a few months ago, but eventually I played around and found that agents are really great at writing it, and its simple type system makes linting fast.


codex also allowed me to unlearn lots of charades that were necessary with Claude Code. Instead of “**plan mode**”, I simply [**start a conversation with the model**](https://x.com/steipete/status/1997412175615246603), ask a question, let it google, explore code, create a plan together, and when I’m happy with what I see, I write “build” or “write plan to docs/\*.md and build this”. Plan mode feels like a hack that was necessary for older generations of models that were not great at adhering to prompts, so we had to take away their edit tools.

Another massive win is the **knowledge cutoff date**. GPT 5.2 goes till end of August whereas Opus is stuck in mid-March - that’s about 5 months. Which is significant when you wanna use the latest available tools.

    
- Folks building Mac or iOS stuff: You don’t need Xcode much anymore. Swift’s build infra is good enough for most things these days. codex knows how to run iOS apps and how to deal with the Simulator.
    
- Sometimes it just **silently reads files for 10, 15 minutes** before starting to write any code.
    
- just say "let's discuss" as part of your prompt
    
- I simply [**start a conversation with the model**](https://x.com/steipete/status/1997412175615246603), ask a question, let it google, explore code, create a plan together, and when I’m happy with what I see, I write “build” or “write plan to docs/*.md and build this”
    
- I also wanted to give him the ability to check on my agents, and getting a **character stream** is just far more efficient than looking at images… if this will work out, we’ll see!
    
-  When you do enough agentic engineering, you develop a feeling for what’s gonna be easy and where the model likely will struggle, so often I just put in a prompt, codex will chug along for 30 minutes and I have what I need.
    
- Sometimes it takes a little fiddling or creativity, but often things are straightforward.
    
- I extensively use the **queueing feature** of codex - as I get a new idea, I add it to the pipeline.
    
- My approach to building software is very iterative. I build sth, play with it, see how it “feels”, and then get new ideas to refine it.
    
- Rarely do I have a complete picture of what I want in my head.
    
- So systems that take _the complete idea_ as input and then deliver output wouldn’t work well for me.
    
- I need to play with it, touch it, feel it, see it, that’s how I evolve it.
    
- I basically **never revert** or use checkpointing.
    
- I simply **commit to main**. 
    
- I find the added cognitive load of having to think of different states in my projects unnecessary and prefer to evolve it linearly. 
    
- I’ve already mentioned my way of planning a feature. I **cross-reference projects** all the time, esp if I know that I already solved sth somewhere else, I ask codex to look in ../project-folder and that’s usually enough for it to infer from context where to look. This is extremely useful to save on prompts. I can just write “look at ../vibetunnel and do the same for Sparkle changelogs”, because it’s already solved there and with a 99% guarantee it’ll correctly copy things over and adapt to the new project. That’s how I scaffold new projects as well.
    
- I’ve seen plenty of systems for folks wanting to refer to past sessions. Another thing I never need or use. I maintain docs for subsystems and features in a **docs folder** in each project, and use [**a script + some instructions**](https://github.com/steipete/agent-scripts/blob/main/scripts/docs-list.ts) in my global AGENTS file to force the model to read docs on certain topics. This pays off more the larger the project is, so I don’t use it everywhere, but it is of great help to keep docs up-to-date and engineer a better context for my tasks.
    
- Apropos context. I used to be really diligent to restart a session for new tasks. **With GPT 5.2** this is no longer needed. Performance is extremely good even when the context is fuller, and often it helps with speed since the model works faster when it already has loaded plenty files. Obviously that only works well when you serialize your tasks or keep the changes so far apart that two sessions don’t touch each other much. 
    
- Prompts. I used to write long, elaborate prompts with voice dictation. With codex, my **prompts gotten much shorter**, I often type again, and many times I add images, especially when iterating on UI (or text copies with CLIs). If you show the model what’s wrong, just a few words are enough to make it do what you want. Yes, I’m that person that drags in a clipped image of some UI component with “fix padding” or “redesign”, many times that either solves my issue or gets me reasonably far. I used to refer to markdown files, but with my docs:list script that’s no longer necessary.
    
- Markdowns. Many times I write “**write docs to docs/*.md**” and simply let the model pick a filename. The more obvious you design the structure for what the model is trained on, the easier your work will be. After all, I don’t design codebases to be easy to navigate for me, I engineer them so agents can work in it efficiently. Fighting the model is often a waste of time and tokens.
    
- **What’s still hard?** Picking the right dependency and framework to set on is something I invest quite some time on. Is this well-maintained? How about peer dependencies? Is it popular = will have enough world knowledge so agents have an easy time? Equally, system design. Will we communicate via web sockets? HTML? What do I put into the server and what into the client? How and which data flows where to where? Often these are things that are a bit harder to explain to a model and where research and thinking pays off.
    
- Since I manage lots of projects, often I let an agent simply run in my project folder and when I figure out a new pattern, I ask it to “**find all my recent go projects** and implement this change there too + update changelog”. 
    
- Ofc I **automate everything**. There’s a skill to register domains and change DNS. One to write good frontends. There’s a note in my AGENTS file about my tailscale network so I can just say “go to my mac studio and update xxx”.
    
- I usually work on two Macs. My MacBook Pro on the big screen, and a Jump Desktop session to my Mac Studio on another screen. Some projects are cooking there, some here. Sometimes I edit different parts of the same project on each machine and sync via git. Simpler than worktrees because drifts on main are easy to reconcile. Has the added benefit that anything that needs UI or browser automation I can move to my Studio and it won’t annoy me with popups.
    
- I used to play with slash commands, but just never found them too useful. Skills replaced some of it, and for the rest I keep writing “**commit/push**” because it takes the same time as /commit and always works.
    
- In the past I often took dedicated days to **refactor and clean up** projects, I do this much more ad-hoc now. Whenever prompts start taking too long or I see sth ugly flying by in the code stream, I’ll deal with it right away.
    
- I tried linear or other **issue trackers**, but nothing did stick. Important ideas I try right away, and everything else I’ll either remember or it wasn’t important. Of course I have public bug trackers for bugs for folks that use my open source code, but when I find a bug, I’ll immediately prompt it - much faster than writing it down and then later having to switch context back to it.
    
- Whatever you build, **start with the model and a CLI first**.
    
- My go-to model is **gpt-5.2-codex high**. Again, KISS. There’s very little benefit to xhigh other than it being far slower, and I don’t wanna spend time thinking about different modes or “ultrathink”. So pretty much everything runs on high. GPT 5.2 and codex are close enough that changing models makes no sense, so I just use that.
    
- codex config: [https://steipete.me/posts/2025/shipping-at-inference-speed#my-config](https://steipete.me/posts/2025/shipping-at-inference-speed#my-config)

