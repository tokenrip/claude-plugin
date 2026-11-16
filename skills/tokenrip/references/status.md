# Report what changed

Return to [SKILL.md](../SKILL.md) for when to use Tokenrip and the working rules.

Use this when the person asks what happened, where things stand, or for a status update.

1. **Read the record.**
   - `workspace_load` lists the latest changes, newest first, each with when it happened, who made it and why; its activity cursor pages back.
   - `workspace_sessions` shows who worked on what, step by step.
   - `task_list` with status *done*, ordered by *finished*, shows what was finished, newest first; its since date counts from when a task was filed, not when it moved.
   - Each open task from `task_list` or `task_get` says who it waits on (its assignee, its reviewer or its holder; anyone when no one is named) and why (to do, to carry out an approval, to decide a review, to finish work in progress). Read that for "where does this stand" and "who is it waiting on"; `task_list` with waiting set to *me* lists what waits on you. The tasks in `workspace_load` don't carry it. A task whose agent hold ran out reads To do again.
   - `output_list` shows what went out (posts, emails, publishes), newest first, by job, agent or label, each with who approved it; `job_get` shows a job's agents and when each was last seen in the workspace, and each scheduled step's last check, who made it, and whether the step is on time or late.
   - For "since I last looked", `workspace_changes` reads the changes after your last acknowledgement, and `workspace_changes_ack` moves that position.
2. **Claim only what the record shows.** A finished task, an output or a recorded change shows work done in the period. A current status alone doesn't say when it changed, and an edit alone doesn't show progress. Where the record conflicts, say so instead of choosing the hopeful reading.
3. **Lead with what changed and what needs the person.** Carry open blockers forward, and link the files and tasks you cite.
4. **Answer in the chat.** Save the summary to the workspace only when the person asks.
