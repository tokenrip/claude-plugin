# Tasks and approvals

Return to [SKILL.md](../SKILL.md) for when to use Tokenrip and the working rules.

Tasks are a workspace's work queue. Each carries two free tags the person's workflow uses: a type (what the work is, such as *article*) and a step (where it is, such as *draft* or *post*). Tokenrip never reads meaning into them; the person's instructions say what each step is.

## The task loop

- `task_start` a task, work on it, then `task_propose` it (it needs review), `task_complete` it (done) or `task_stop` it (put it down, back to To do).
- To take the next task rather than a named one, give `task_start` the workspace and, for routine work, the step the instructions name; never a type alone, which would also take approved work waiting at the next step. Nothing comes back: there is nothing to do, or a match was busy for a moment; try again later.
- A task sent back to you says in its latest round's comment what to change.
- On long work, start the task again before its lease runs out.
- Only the task's holder writes its draft files.
- Before you stop: `task_complete` what you finished, with the result and links to what it produced. For a task you hold but didn't finish, `task_update` it with how far you got and the next step, then `task_stop` it. A proposal waiting for review stays in review, where the next agent finds it.

## Proposals: asking before a step outside Tokenrip

For work in a workspace, a step that leaves Tokenrip (an email, a post, a message, a booking, a purchase, including through a service connected to Tokenrip) goes to the person as a proposal, unless they told you to do it with another app instead.

Tokenrip's own emails, such as the invite to someone the person asked you to add, belong to the Tokenrip step that sends them: they are not a step outside Tokenrip and need no proposal.

1. `task_propose` with the exact draft and a type (*email*, *post*). When the draft is files in the workspace, name them as the draft's files: the review keeps the versions you proposed. When someone else takes the next step (the instructions say who sends or posts), name that step as `then`.
2. Read the receipt. Usually it waits for review: tell the person it is waiting in Tokenrip, and don't carry it out meanwhile. When the person allowed that type of work on its own, the receipt comes back approved: carry it out now (with `then`, it moves to that step for whoever takes it instead).
3. On a later run, `task_get` shows how the review ended:
   - *approved*: the approved round's final text and files, with any edits the reviewer made, are what to carry out. Carry out exactly that, once.
   - *sent back*: the comment says what to change. Revise the draft and `task_propose` again on the same task with the same `then`: a new round doesn't carry it over.
   - *cancelled*: don't carry it out.
4. `task_complete` with what came of it and links. If carrying it out fails, say so, then propose again or `task_cancel` it.

Work that needed no approval but is worth the person knowing about (research finished, files reorganized): `task_report` it.

## Reviews, comments and assigning

- A review addressed to you: read it with `task_get`, then approve it or send it back with what to change (`task_decide`), or cancel it (`task_cancel`). Never decide your own proposal, or a review addressed to someone else.
- `comment_create` carries a question, a requested change or an answer. The task's state already shows where the work stands, so don't comment to report status.
- Work for someone else: `task_create` with an assignee (a person, or an agent as agent:<handle>, the handle from `workspace_load`) and a reviewer who decides its proposals.

## Turn a plan into tasks

1. Read the plan, then `task_list` the workspace so you don't file a task that already exists.
2. `task_create` one task per outcome someone can finish and check, titled by the outcome ("Book flights for 3 to 10 June", not "Flights"). Set an assignee only when the plan or the person names one. In the body, say which part of the plan it serves, with the plan's link.
3. Don't start the tasks unless asked. List what you filed, with links.

## Example

The person: "Pick up where my other agent left off on the launch, and draft the announcement email."

1. `workspace_list` finds Launch; `workspace_load` it. The instructions say "Emails go out from Alek's address." The pinned pricing decision settles the prices, and the open tasks show "Draft the announcement email" still To do.
2. `task_start` that task, and `artifact_publish` the draft into Launch, why: "Announce the launch to existing customers this week."
3. `task_propose` sending it as a new proposal in Launch, the draft file named as its draft, then tell the person: "The draft is in Launch (link), and sending it is waiting for your approval in Tokenrip."
4. `task_complete` the drafting task with the draft's link. The proposal stays in review for the next agent.
5. A later run: `workspace_load` lists it to carry out. `task_get` gives the approved text; send exactly that, then `task_complete` with "Sent to 412 customers". Had it been sent back ("Name the date in the subject line"), revise the draft and `task_propose` again on the same task.
