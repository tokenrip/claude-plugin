# Tasks and approvals

Return to [SKILL.md](../SKILL.md) for when to use Tokenrip and the working rules.

Tasks are a workspace's work queue. Each carries two free tags the person's workflow uses: a type (what the work is, such as *article*) and a step (where it is, such as *draft* or *post*). Tokenrip never reads meaning into them, except under a job with task definitions ([below](#jobs-and-labels)); otherwise the person's instructions say what each step is.

## The task loop

- `task_start` a task, work on it, then `task_propose` it (it needs review), `task_complete` it (done) or `task_stop` it (put it down, back to To do).
- To take the next task rather than a named one, give `task_start` the workspace and, for routine work, the step the instructions name (with your job, for a step of one of your jobs); never a type alone, which would also take approved work waiting at the next step. Nothing comes back: there is nothing to do, or a match was busy for a moment; try again later.
- A task of a job with task definitions comes with its workflow: what to do at its step and how the step ends, and the next step. Follow it.
- A task sent back to you says in its latest round's comment what to change.
- On long work, start the task again before its lease runs out.
- Only the task's holder writes its draft files.
- Before you stop: `task_complete` what you finished, with the result and links to the files it produced. For a task you hold but didn't finish, `task_update` it with how far you got and the next step, then `task_stop` it. A proposal waiting for review stays in review, where the next agent finds it.

## Proposals: asking before a step outside Tokenrip

For work in a workspace, a step that leaves Tokenrip (an email, a post, a message, a booking, a purchase, including through a service connected to Tokenrip) goes to the person as a proposal, unless they told you to do it with another app instead.

Tokenrip's own emails, such as the invite to someone the person asked you to add, belong to the Tokenrip step that sends them: they are not a step outside Tokenrip and need no proposal.

1. `task_propose` with the exact draft and a type (*email*, *post*). When the draft is files in the workspace, name them as the draft's files: the review keeps the versions you proposed. When someone else takes the next step (the instructions say who sends or posts), name that step as `then`.
2. Read the receipt. Usually it waits for review: tell the person it is waiting in Tokenrip, and don't carry it out meanwhile. When the person allowed that type of work on its own, the receipt comes back approved: carry it out now (with `then`, it moves to that step for whoever takes it instead).
3. On a later run, `task_get` shows how the review ended:
   - *approved*: the approved round's final text and files, with any edits the reviewer made, are what to carry out. Carry out exactly that, once.
   - *sent back*: the comment says what to change. Revise the draft and `task_propose` again on the same task with the same `then`: a new round doesn't carry it over.
   - *cancelled*: don't carry it out.
4. Record what went out ([below](#record-what-went-out)), then `task_complete` with what came of it. If carrying it out fails, say so, then propose again or `task_cancel` it.

Work that needed no approval but is worth the person knowing about (research finished, files reorganized): `task_report` it.

## Record what went out

Each post, email, message or publish that leaves Tokenrip gets an output: `output_record` with its kind (*x.post*, *email.reply*), who received it, its ref (the post's URL or the message id) and the task it served. On a task it takes the task's job, labels and approval. The post's URL goes in the output, not in the task's result links, which are for files the work produced.

A send that must not happen twice (a post, an email) is claimed first:

1. `output_record` with status *sending* and a key unique to this one send and where it goes: the task's id with the kind after it (*task-id:x.post*), or the id of the message you reply to. Never a key that recurs, such as a draft's id: a draft updated in place keeps its id, and one draft posted to X and to LinkedIn is two sends, each with its own key.
2. Refused with `OUTPUT_EXISTS`: the send was already claimed, and the refusal's details name that output and who recorded it, or show none when you can't see it. Either way, don't send. If it is still *sending*, another run may be sending it: tell the person rather than guess.
3. Otherwise send it, then `output_update` it to *sent* with its ref. Mark it *failed* only when you know it didn't go out (that frees the key for a retry). If you can't tell (a timeout, an error whose retry is unknown), leave it *sending* and tell the person: a retry could send it twice.

## Jobs and labels

- `workspace_load` lists your jobs right after the instructions: the standing work you do in this workspace, each with its purpose, its description, your role and your steps (the steps of its task definitions your role works, and how often to check each). A job's description says how its work is done (`job_get` reads one whole). It grants nothing: a step outside Tokenrip it asks for still goes to the person as a proposal ([above](#proposals-asking-before-a-step-outside-tokenrip)).
- A job's task definitions say what a task of the job is: the types each covers, "creating one" (what the title and brief hold, which type, where it starts) and its steps, each with who works it, how often, its instructions and whether it ends in an approval.
- **Creating a task for a job** ("create a task for founder-posts, here are my thoughts"): read the job first with `job_get`, then `task_create` with the job, the type its definition names and the brief it asks for. Tokenrip fills in the first step. A type or step that isn't the job's is refused, with the valid ones.
- **Working your step:** on each run, `task_start` with the workspace, the job and your step. Tokenrip records that you checked, even when nothing comes back, so the person sees whether each step is worked on schedule. At a step that ends in an approval, `task_propose` the work: without a then, an approval moves it to the next step, and the approve verb is the step's.
- Name the job on the tasks you file, report or propose for it (job on `task_create`, `task_report` and a new `task_propose`), so the person sees the work under it.
- Labels are the person's words for grouping work (*client:acme*). Set them on `task_create` and `task_report`, change them with `task_update`, and filter `task_list` by them. Use the labels the instructions or the task already use.

## Reviews, messages and assigning

- A review addressed to you: read it with `task_get`, then approve it or send it back with what to change (`task_decide`), or cancel it (`task_cancel`). Never decide your own proposal, or a review addressed to someone else.
- `message_post` on the task (`taskId`) asks or answers about the task; whoever reads the task reads it, and nobody is told. The task's state already shows where the work stands, so don't post to report status.
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
5. A later run: `workspace_load` lists it to carry out. `task_get` gives the approved text. `output_record` claims the send (status *sending*, the task's id with *email* after it as its key), then send exactly that, `output_update` it to *sent*, and `task_complete` with "Sent to 412 customers". Had it been sent back ("Name the date in the subject line"), revise the draft and `task_propose` again on the same task.
