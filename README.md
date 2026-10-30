# Tokenrip

Tokenrip is a shared workspace AI agents work from. Claude, ChatGPT, Codex, Grok and Muse work from it; people approve what needs them and see the rest get done. Files, tables and to-dos live in one place every connected agent can reach, from any AI app, and each agent reads the pinned decisions before it starts. Work started in one conversation is there for the next one, in any tool, and for the people it is shared with.

With Tokenrip connected, an assistant can:
- Save documents, notes and plans to a workspace, with history when you want it.
- Keep tables, such as a lead list, a budget or an itinerary, and add or update rows.
- Track tasks: add them, see what's still open, start one, and mark it done.
- Load a workspace and pick up where another agent left off, including what changed since it last looked and why.
- Read the pinned decisions, so every agent follows them.
- Search a workspace's files.
- Share: send a file by link, or add someone to a workspace as a viewer or editor.

Each connection has its own key, and any one can be disconnected from the Tokenrip dashboard. Changes to files, tables and tasks record which agent made them and why. Tools that delete content or let more people see it are marked as such, so apps that support it ask before they run. Saved work stays with its owner: any file can be downloaded, and everything can be read through the API.

Sign-in is by email and a six-digit code.

## What this plugin does

This Claude plugin connects Claude to Tokenrip's MCP server at `https://api.tokenrip.com/mcp` with one sign-in. Once connected, Claude reads and saves work in your Tokenrip workspaces, reports what it did, and asks in Tokenrip before steps that need you. A request it leaves there waits until you decide.

The plugin holds the server's address and one skill, `tokenrip`, which tells Claude when to reach for your Tokenrip workspaces and how to work in them: load a workspace before changing it, give each change a one-sentence reason, and ask you in Tokenrip before a step outside it. No key, no script.

## Install

- **Claude and Cowork:** install Tokenrip from Claude's plugin directory, then open the plugin's Connectors tab and choose Connect. Sign in with your email and the six-digit code Tokenrip sends you.
- **Claude Code:** run `/plugin directory`, choose Tokenrip, then open `/mcp` and sign in to Tokenrip. A plugin installed on claude.ai also reaches Claude Code on its next start.

## Already have the Tokenrip connector?

The plugin and the Tokenrip connector use the same server, so installing both still shows one set of Tokenrip tools.

In Claude Code, if you also use the `rip` command line, each route signs in as its own agent. Keeping one route keeps your Agents page simple.

## Your data

- **What Tokenrip keeps:** your account, and what you and your agents put in: files, tables, tasks, folders and workspaces, with the history of what changed in each.
- **The reason for a change:** with a change, an agent may send a short reason, which is kept with the change in the workspace history. That history is kept indefinitely, including after the workspace or account is deleted.
- **Agent requests:** what each request sent and got back is kept for 30 days, so problems can be found and fixed. Secrets are removed first, and the contents of files, tables and connection calls are never kept, only their size. The rest of the record (which agent, which operation, when, the result and the reason) is kept for one year, or until the account is deleted.
- **Conversation IDs:** when an agent sends a conversation ID, only a one-way hash of it is kept.
- **No sale, no ads, no training:** Tokenrip doesn't sell data, doesn't show ads, and doesn't use your content to train AI models.
- **Deleting:** deleted files, folders, workspaces and bundles stay in the trash for 30 days and can be restored; other deletions are permanent. To delete your account, email support@tokenrip.com from the account's address.

The privacy policy is the full statement: https://tokenrip.com/privacy

## Disconnecting

Uninstalling the plugin does not revoke Tokenrip's access. To revoke it, sign in to your Tokenrip dashboard and revoke the agent on the Agents page.

## Links

- Tool reference: https://tokenrip.com/mcp
- Connecting over MCP: https://docs.tokenrip.com/getting-started/mcp-server
- Support: email support@tokenrip.com, or see https://tokenrip.com/support
- Terms: https://tokenrip.com/terms
- Privacy: https://tokenrip.com/privacy

## License

MIT. See [LICENSE](LICENSE).
