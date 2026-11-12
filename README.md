# Tokenrip

Tokenrip keeps your documents, tables and tasks in workspaces you can come back to. Save a plan in one chat and pick it up in the next, share a workspace with teammates or a client, and connect more than one assistant to the same work. Changes to files, tables and tasks record who made them and why, so whoever picks up the work next can see what happened.

With Tokenrip connected, you can ask your assistant to:
- Save documents, notes and plans to a workspace, and keep earlier versions when you want them.
- Keep tables, such as a lead list, a budget or an itinerary, and add or update rows.
- Track tasks: add them, see what's still open, start one, and mark it done.
- Hand off work: pick up a workspace where you or another assistant left off, and see what changed since the last look.
- Read the notes and decisions you pin to a workspace before starting work.
- Search a workspace's files.
- Share a file by link, or add someone to a workspace as a viewer or editor.
- Ask and answer questions with the people and assistants in a workspace, in its chat or on a task.
- Propose an email, post or other step outside the workspace, and wait for your approval before doing it.

## Install

- **Claude and Cowork:** add Tokenrip from the plugin directory, then open its Connectors tab, choose **Connect** and sign in.
- **Claude Code:** run `/plugin directory`, choose Tokenrip, then sign in from `/mcp`. A plugin added on claude.ai also reaches Claude Code on its next start.

Already use the Tokenrip connector? The plugin uses the same server, so you still see one set of Tokenrip tools.

## Try it

- What workspaces do I have in Tokenrip?
- What's left on the task list in our renovation workspace?
- Pick up where my other agent left off on the launch plan.

## What's included

- **The Tokenrip MCP server** at `https://api.tokenrip.com/mcp`. You sign in with your email and a six-digit code, and a free account is created if you don't have one.
- **The `tokenrip` skill**, which tells Claude when to use your workspaces, to say why it changed something, and to ask you before a step outside the workspace.

## Privacy

The plugin connects your assistant to Tokenrip's server at `https://api.tokenrip.com/mcp`. Your assistant sends Tokenrip what you ask it to read or save, a short reason with each change and, when the app provides one, a conversation ID, which is kept only as a one-way hash. Tokenrip keeps your workspaces, deletes what each request sent and got back after 30 days and the rest of its record after a year, never sells your data, and doesn't use your content to train AI models. Uninstalling doesn't revoke access: revoke it on the Agents page of your Tokenrip dashboard.

[Privacy policy](https://tokenrip.com/privacy) · [Terms](https://tokenrip.com/terms)

## Links

[Setup guide](https://tokenrip.com/setup) · [Docs](https://docs.tokenrip.com/getting-started/mcp-server) · [Tool reference](https://tokenrip.com/mcp) · [Support](https://tokenrip.com/support) (support@tokenrip.com)

## License

MIT. See [LICENSE](LICENSE).
