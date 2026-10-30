# Capture a conversation

Return to [SKILL.md](../SKILL.md) for when to use Tokenrip and the working rules.

Use this when the person asks to save, capture or write up what was discussed or decided.

1. **Find what exists.** Load the workspace, then `search` it for a file on the subject. If one exists, update it rather than starting a second file.
2. **Pick the shape,** and leave out empty sections:
   - Decision record: the context, the decision, the options considered, why, what follows from it.
   - Notes: outcomes, decisions, open questions, actions.
   - How-to: what you need first, the steps, how to check it worked.
   - Research: the question, findings with their sources, what is still unknown.
   - FAQ: each question with a direct answer.
3. **Stay faithful.** Keep what was decided apart from what was only proposed. Keep exact numbers, names and commands. Don't invent owners, dates or agreement; mark anything you added as a suggestion.
4. **Choose the write:**

   | To | Use |
   |---|---|
   | Add a document, note or plan | `artifact_publish` into the workspace |
   | Change a passage | `artifact_update` with edits: send only the text that changes |
   | Add to a log, notes or a tracker | `artifact_append` |
   | Rewrite a whole file | `artifact_update` with the full content |
   | Keep records that grow (leads, budget lines, an itinerary) | `table_create`, then `table_append_rows` |

   When the person may want the old text back, keep the previous version: unless the file keeps history, an edit replaces it.
5. **Pin only what the person decided.** A decision every agent should follow from now on: `workspace_pin` the file, or offer to.
6. **Give the person the link** from the receipt.

Don't save keys or secrets, small talk, progress notes that will be stale within the hour, or code and docs that live in a repository.
