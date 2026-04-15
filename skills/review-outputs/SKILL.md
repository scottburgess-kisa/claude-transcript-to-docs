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
2. Read the `selected_documents` field to see which documents were generated
3. Read the `persona_selection.selected_personas` field to see which writing styles were used
4. Determine which files exist: outputs/{document-type}-{persona}.md for each combination

### Step 2 — Review Each Generated Document SEQUENTIALLY

**IMPORTANT**: Review ONE document at a time. Complete the entire review process for one document before moving to the next.

Review documents in this order: blog → slack → success story (only for documents that were actually selected).

#### Document Review Process (use for each document individually):

**For BLOG POST (if "blog" was selected):**
For each persona that was selected, review each blog post version:
1. Display ONLY the contents of: outputs/blog-post-{persona}.md
2. Add this header: "## Blog Post Review ({Persona} Style) - Please review this version"
3. Ask these review questions:
   - Does this capture the key insights from your project?
   - Is the {persona} writing style appropriate for your intended audience?
   - Are there any details missing or that should be removed?
   - Is the length appropriate?
4. WAIT for user response
5. If changes requested: make them, display updated version, ask "How does this look now?"
6. ONLY move to next persona version when user approves or says "move on"
7. Continue until all blog post persona versions are reviewed

**For SLACK UPDATE (if "slack" was selected):**
For each persona that was selected, review each slack post version:
1. Display ONLY the contents of: outputs/slack-post-{persona}.md
2. Add this header: "## Slack Update Review ({Persona} Style)"
3. Ask these review questions:
   - Does this have the right energy and tone for your team in {persona} style?
   - Are there any sensitivities or details that shouldn't be shared?
   - Is the call-to-action clear and appropriate?
   - Would you add or remove anything?
4. WAIT for user response
5. If changes requested: make them, display updated version, ask "How does this look now?"
6. ONLY move to next persona version when user approves or says "move on"
7. Continue until all slack post persona versions are reviewed

**For SUCCESS STORY (if "success story" was selected):**
For each persona that was selected, review each success story version:
1. Display ONLY the contents of: outputs/success-story-{persona}.md
2. Add this header: "## Success Story Review ({Persona} Style)"
3. Ask these review questions:
   - Does this tell a compelling narrative about your work in {persona} style?
   - Are the results presented clearly and impressively?
   - Is the client representation appropriate?
   - Would this appeal to your target audience?
4. WAIT for user response
5. If changes requested: make them, display updated version, ask "How does this look now?"
6. ONLY move to next persona version when user approves or says "move on"
7. Continue until all success story persona versions are reviewed

### Step 3 — Final Summary
Once all documents have been reviewed, display this completion message:

---
🎉 **Review Complete!**

All documents have been reviewed and finalised:

[List each document with its final location for each persona, e.g.:]
- Blog Post (Alex style) → outputs/blog-post-alex.md
- Blog Post (Sarah style) → outputs/blog-post-sarah.md
- Slack Update (Alex style) → outputs/slack-post-alex.md
- Slack Update (Sarah style) → outputs/slack-post-sarah.md
- Success Story (Jamie style) → outputs/success-story-jamie.md

Your polished documents are ready to use!

To run this workflow again with a new transcript,
drop it in the transcripts/ folder and start over.
---

### Step 4 — Cleanup Working Folder
After displaying the final summary:

1. Remove all intermediate JSON files from the working/ folder:
   - Delete working/analyse-output.json
   - Delete working/clarify-output.json
   - Remove any other files except .gitkeep

2. Confirm cleanup completed:
   "✅ Working folder cleaned - ready for next workflow run."

**IMPORTANT**: Only delete .json files from working/ folder.
Never delete files from transcripts/ or outputs/ folders.

## Behaviour Guidelines

### CRITICAL: Sequential Review Process
- **NEVER show multiple documents at once**
- **NEVER move to the next document without explicit user approval**
- Complete the entire review cycle for one document before starting the next
- If user says "looks good", "approved", "next", or "move on" → proceed to next document
- If user requests changes → make them, show result, wait for approval

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
- Show ONLY one document at a time during review
- Use clear formatting with headers like "## Blog Post Review"
- Never display multiple documents in the same response

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