# Skill: Review Outputs

## Purpose
Review and refine the generated documents after parallel agent execution.
This skill provides a structured review process for each document type
and handles user-requested revisions.

## Context
This skill runs after Stage 4 (Parallel Document Generation).
It receives the list of selected documents and guides the user
through reviewing each generated output, offering the opportunity
to request changes and improvements.

## Instructions

### Step 1 — Load Document Selection
1. Load the JSON from: working/clarify-output.json
2. Read the `selected_documents` field to see which documents
   were generated in Stage 4.

### Step 2 — Review Each Generated Document
For each document in `selected_documents`, follow this process:

#### If "blog" was selected:
1. Display the contents of: outputs/blog-post.md
2. Ask these review questions:
   - Does this capture the key insights from your project?
   - Is the tone appropriate for your intended audience?
   - Are there any details missing or that should be removed?
   - Is the length appropriate?

3. If the user requests changes, make them and display the updated version.
   Continue until the user approves or says to move on.

#### If "slack" was selected:
1. Display the contents of: outputs/slack-post.md
2. Ask these review questions:
   - Does this have the right energy and tone for your team?
   - Are there any sensitivities or details that shouldn't be shared?
   - Is the call-to-action clear and appropriate?
   - Would you add or remove anything?

3. If the user requests changes, make them and display the updated version.
   Continue until the user approves or says to move on.

#### If "success story" was selected:
1. Display the contents of: outputs/success-story.md
2. Ask these review questions:
   - Does this tell a compelling narrative about your work?
   - Are the results presented clearly and impressively?
   - Is the client representation appropriate?
   - Would this appeal to your target audience?

3. If the user requests changes, make them and display the updated version.
   Continue until the user approves or says to move on.

### Step 3 — Final Summary
Once all documents have been reviewed, display this completion message:

---
🎉 **Review Complete!**

All documents have been reviewed and finalised:

[List each document with its final location, e.g.:]
- Blog Post → outputs/blog-post.md
- Slack Update → outputs/slack-post.md
- Success Story → outputs/success-story.md

Your polished documents are ready to use!

To run this workflow again with a new transcript,
drop it in the transcripts/ folder and start over.
---

## Behaviour Guidelines

### Revision Handling
- Make requested changes directly to the files
- Always display the updated content after making changes
- Be responsive to user feedback, even if it means significant rewrites
- If a user says "move on" or "next", accept the current version immediately

### Review Questions
- Ask questions conversationally, not as a formal checklist
- Focus on substance over style unless specifically asked
- Offer specific suggestions if you notice areas for improvement
- Don't ask about things the user has already addressed

### Document Display
- Show the full document content in the conversation
- Use clear formatting with headers to separate different documents
- Add document titles like "## Blog Post Review" before each document

### Length and Detail
- Keep review questions focused and actionable
- Don't overwhelm with too many questions at once
- Prioritize the most important aspects for each document type
- Allow users to request deeper review if they want it

## Follow-up Rule
If the user is happy with a document, immediately move to the next one.
If they request changes, make them, display the result, and ask:
"How does this look now? Any other changes needed?"

Continue this loop until they approve or ask to move on.

## Input
- The enriched JSON from: working/clarify-output.json (to read selected_documents)
- Generated document files from: outputs/ folder

## Output
- Updated document files in outputs/ folder (if revisions were made)
- Confirmation that all documents have been reviewed and finalised