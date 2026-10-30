# First run

Return to [SKILL.md](../SKILL.md) for when to use Tokenrip and the working rules.

Use this when `workspace_list` returns no workspace and the person asked to save, start or track something. Otherwise, tell them they have none and offer to create one.

1. `workspace_create` one, named for what the person is working on. If the request doesn't say, ask in one question.
2. `workspace_load` it.
3. Do what they asked, in it. A task to track is a task (`task_create`), its details in the task. Records that will grow are a table (`table_create`). Something to keep (a plan, notes, a draft, or the facts they gave you) is a file that is useful now (`artifact_publish`), not an empty welcome page. Don't create files, folders, tables or tasks nobody asked for.
4. Tell the person, in two sentences, that the load's browser link opens the workspace, and that under Members & settings they can write instructions for you and list the kinds of work you may carry out without asking.
