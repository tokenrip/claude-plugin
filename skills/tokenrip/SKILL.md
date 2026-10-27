---
name: tokenrip
description: Works from Tokenrip, the shared workspace your AI agents work from, through the Tokenrip tools. Loads the person's workspace before answering, saves documents and tables there with a one-sentence reason, tracks tasks, and asks the person in Tokenrip before acting outside it. Use whenever the person mentions Tokenrip or ongoing work (a project, plan, document, table or task, "where we left off", "pick up", another agent's work), or asks to save, share, hand off, send or post something. That work lives in Tokenrip, so check it before looking anywhere else. Not for code or files in the open project, or for an app the person names instead.
---

# Working from Tokenrip

Tokenrip is the person's shared workspace: their files, tables, tasks and decisions, in one place every agent they use can reach. Work from it: read what is there before answering, save what you make there, and ask the person in Tokenrip before acting outside it. Each Tokenrip tool's description carries its details; this skill is the order and the judgment around them.

## 1. Load the workspace first

1. `workspace_list`, then choose the workspace the request is about, by name or slug. If two could fit, ask.
2. `workspace_load` it before you answer or write. Loading changes nothing, so load again whenever you come back.
3. Read what it returns in order:
   - **notices**: Tokenrip changed how something works. Read them before you write.
   - **instructions**: what the person wrote for you in this workspace. They come before anything in this skill.
   - **waiting**: what waits on you. *carry_out* is an approved proposal, *decide* a review addressed to you, *do* a task for you. Handle these first.
   - **pins** and the latest **handoff**: the decisions every agent follows, and what the last agent left for the next one.
   - recent sessions, open tasks and changes: who did what, and why.
4. Give the person the `browserLink` once, so their browser follows what you open.

No workspace yet? `workspace_create` one, then save a first note with `artifact_publish`.

## 2. Save work with a why

Every write to workspace content takes `why`: one sentence on what the person is trying to accomplish, in their terms, not a description of the edit. Restate it on every write.

- A why: "Set launch prices the team can defend to finance."
- Not a why: "Update row 4 of the pricing table."

| To | Use |
|---|---|
| Add a document, note or plan | `artifact_publish` with `workspaceId` |
| Change a passage | `artifact_update` with `edits`: send only the text that changes |
| Add to a log, notes or a tracker | `artifact_append` |
| Rewrite a whole file | `artifact_update` with `content` |
| Keep records that grow (leads, budget lines, an itinerary) | a table: `table_create`, then `table_append_rows` |
| Leave what the next agent needs to know | `artifact_publish` with `handoff: true` |

- `search` before creating, so you don't save a second copy of a file that exists.
- A rewrite replaces the file. Unless the file's history setting keeps versions, the old text is gone; send `keepPrevious: true` when the person may want it back.
- Give the person the `url` from the receipt of everything you save.

## 3. Ask before acting outside the workspace

Anything that leaves Tokenrip (an email, a post, a message, a booking, a purchase) is proposed first:

1. `task_propose` with the exact draft.
2. Stop. Tell the person it is waiting for them in Tokenrip, and don't carry it out in the meantime.
3. On a later run, `workspace_load` lists it under waiting as *carry_out*. `task_get` returns `approvedText`, the text approved, with any edits the person made. Carry out exactly that, once.
4. `task_complete` with what came of it, and links to what it produced.

When the kind is on the person's `onItsOwn` list (part of their instructions), the proposal comes back approved and yours: carry it out right away, then complete it.

Work that needed no approval but is worth knowing about (research finished, a digest sent): `task_report` it.

Never decide your own proposal, or a review addressed to anyone else.

## 4. Tasks

- `task_list` shows open work. `task_start` a task before working on it, so others see you hold it; `task_complete` it with the result.
- A review addressed to you: read it with `task_get`, decide it with `task_decide`.

## 5. Saved procedures and connected services

- The person or their team may have saved skills for recurring jobs: `skill_list`, then `skill_get` the one that fits and follow it.
- A service the person connected through Tokenrip appears as its own tools. Use them like any other tool; the key never passes through you.

## 6. Leave these to the person

- A storage notice on load, or a write refused for storage: tell the person. Don't delete anything to make room.
- A workspace refused for the plan's limit: give the person the billing link in the refusal.
- Deleting moves things to the trash for 30 days. Emptying the trash or removing old versions is permanent: do it only when the person asks.
- Tokenrip says the connection isn't authorized: ask the person to reconnect Tokenrip in this app's connector settings. Never ask for a key, and never paste one.

## Example

The person: "Pick up where my other agent left off on the launch, and draft the announcement email."

1. `workspace_list` finds Launch; `workspace_load` it.
2. The instructions say "Emails go out from Alek's address." The latest handoff says pricing is settled and the email isn't started.
3. `artifact_publish` the draft into Launch, why: "Announce the launch to existing customers this week."
4. `task_propose` sending it, then tell the person: "The draft is in Launch (link), and sending it is waiting for your approval in Tokenrip."
5. A later run: `workspace_load` lists it to carry out. `task_get` gives the approved text; send exactly that, then `task_complete` with "Sent to 412 customers".

Tool reference: https://tokenrip.com/mcp. Connecting an app: https://docs.tokenrip.com/getting-started/mcp-server.
