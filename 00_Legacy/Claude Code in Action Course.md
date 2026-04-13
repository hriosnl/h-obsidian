Claude is great at determining what tools to use
Claude code is a solid git assistant

### Giving Claude the best context possible [🔗](https://anthropic.skilljar.com/claude-code-in-action/303236)
- create a memory using #
- if you know the file which it needs to look into, mention it with @
- **boost Claude's intelligence**
	- use screenshot then `Ctrl + v` not Command + v in claude
	- enable Plan mode (shift+Tab x2) - breadth
		- this mode is useful when you have a task that requires wide understanding of your codebase and requires looking at different areas; requires several steps to complete
	- enable Thinking mode - depth
		- this is useful when you are focusing on a particular tricky bit of logic or troubleshooting a difficult bug
	- Short Course

![[Screenshot 2025-08-21 at 19.12.32.png|200]]

### Directing the flow of converstation 
- press ESC - contrary to my belief, this is just an interrupt not reset of context 😮
- combine ESC and memory is powerful for tasks always done improperly
- errors that are encountered are not relevant context to the main task
	- go back in time (ESC ESC)
- /compact - really useful when Claude has learned a lot about the current task and you want to maintain that knowledge for the next tasks
- /clear - when you are about to do a task unrelated to the previous one


### Custom commands [🔗](https://anthropic.skilljar.com/claude-code-in-action/303234)
To create a custom command, you need to set up a specific folder structure in your project:
1. Find the `.claude` folder in your project directory
2. Create a new directory called `commands` inside it
3. Create a new markdown file with your desired command name (like `audit.md`)
The filename becomes your command name - so `audit.md` creates the `/audit` command.

Custom commands can accept arguments using the `$ARGUMENTS` placeholder.

### MCP Servers
Allow all Playwright tools:
`{ "permissions": {
	`"allow": ["mcp__playwright"],
	`"deny": [] }
`}


### Hooks

![[hooks.png]]

**Here's the confusing part:**
1. The stdin input to your commands will change based upon the type of hook being executed (`PreToolUse`, `PostToolUse`, `Notification`, etc)
2. The `tool_input` contained in that will differ based upon the tool that was called (in the case of `PreToolUse` and `PostToolUse` hooks)


To handle this challenge, it is recommended to use a hook like this:

```javascript
"PostToolUse": [ // Or "PreToolUse" or "Stop", etc
  {
    "matcher": "*",
    "hooks": [
      {
        "type": "command",
        "command": "jq . > post-log.json"
      }
    ]
  },
]
```

Notice the provided command. It will write the input to this hook to the `post-log.json` file, which allows you to inspect exactly what would have been fed into your command! **This makes it a lot easier for you to understand what data your command should inspect.**