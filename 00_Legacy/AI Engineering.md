### [[Mastering Claude Code]]
### [[AI Fluency]]

### Agents are models using tools in a loop

> You're not thinking "how do I write this function." You're thinking "**what's the optimal path through this problem space**." The skill isn't implementation anymore. The skill is _steering_.

![[Host with MCP Client.png]]
- How does MCP can give context efficiently? (eg. not search all news for today)
- MCP is the new standard for building APIs—and it works very differently from traditional ones?

- MCP server primitives?
	- resources, tools, prompts
	- [ ] prompts - prompts!?
	- [ ] tools - they perform actions like POST
	- [ ] resource - any structure data source, the server wants to make accessible to the LLM client, like GET

![[There are two built-in MCP transports.png]]
- when to use STDIO transport?
	- [ ] building command line tools
	- [ ] implementing local integrations
	- [ ] needing simple process communication
	- [ ] working with shell scripts

- SSE?
	- [ ] uses HTTP POST for client to server and _optional_ Server Sent Events streams for server to client comm

- When to use SSE?
	- [ ] building web-based integrations
	- [ ] needing client-server communication over HTTP
	- [ ] requiring stateful sessions
	- [ ] supporting multiple concurrent clients
	- [ ] implementing resumable connections


![[Choosing a chunk size.png]]
Optimize for smaller size without losing context.