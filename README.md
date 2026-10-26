# Tokenrip

The shared workspace your AI agents work from. Claude, ChatGPT, Codex, Grok and Muse work from here. You approve what needs you and see the rest get done.

## What this plugin does

Tokenrip keeps your files, lists and to-dos in one place that every agent you use can reach, from any AI app. Work started in one conversation is there for the next one, and for the people you share it with.

With Tokenrip connected, Claude can save documents, notes and plans to a workspace with version history; keep tables such as a budget or a guest list; track tasks; load a workspace and pick up where another agent left off, including what changed since it last looked; search your files; and share a file by link or add someone to a workspace.

The plugin connects Claude to Tokenrip's server at `https://api.tokenrip.com/mcp` and carries no key, no script and no instructions of its own. How to work with Tokenrip comes from the server when Claude connects. Each agent connects with its own key, and you sign in with your email and a six-digit code.

## Install

- **Claude and Cowork:** install Tokenrip from Claude's plugin directory, then open the plugin's Connectors tab and choose Connect. Sign in with your email and the six-digit code Tokenrip sends you.
- **Claude Code:** run `/plugin install tokenrip@claude-plugins-official`, then open `/mcp` and sign in to Tokenrip.
- **Grok Build:** add Tokenrip from Grok Build's plugin marketplace, which reads this same package.

## Already have the Tokenrip connector?

The plugin and the Tokenrip connector use the same server, so installing both still shows one set of Tokenrip tools.

In Claude Code, if you also use the `rip` command line, each route signs in as its own agent. Keeping one route keeps your Agents page simple.

## Your data

- **What Tokenrip keeps:** your account, and what you and your agents put in: files, tables, tasks, folders and workspaces, with the history of what changed in each.
- **The reason for a change:** with a change, an agent may send a short reason, which is kept with the change in the workspace history. That history is kept indefinitely, including after the workspace or account is deleted.
- **Agent requests:** what each request sent and got back is kept for 30 days, so problems can be found and fixed. Secrets are removed first, and the contents of files, tables and connection calls are never kept, only their size. The rest of the record (which agent, which operation, when, the result and the reason) is kept for one year, or until the account is deleted.
- **Conversation IDs:** when an agent sends a conversation ID, only a one-way hash of it is kept.
- **No sale, no ads, no training:** Tokenrip doesn't sell data, doesn't show ads, and doesn't use your content to train AI models.
- **Deleting:** deleted files, folders and workspaces stay in the trash for 30 days and can be restored. To delete your account, email support@tokenrip.com from the account's address.

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
