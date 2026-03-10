# Workflow: Transcript to Documents

## Purpose
This workflow takes a project transcript and transforms it into 
polished output documents through a series of structured stages.
Each stage builds on the last, passing enriched data forward.

## Overview
Stage 1 — Analyse the transcript
Stage 2 — Clarify and enrich
Stage 3 — Confidence check and document selection
Stage 4 — Generate chosen documents

---

## Stage 1 — Analyse Transcript

### Instructions
1. Ask the user for the transcript filename:
   "What is the name of your transcript file? 
   It should be in the transcripts/ folder."

2. Run the analyse-transcript skill:
   Follow all instructions in: 
   skills/analyse-transcript/SKILL.md

3. Save the JSON output to:
   working/analyse-output.json

4. Display the human readable summary to the user.

5. Ask the user:
   "Does this summary look accurate? 
   Reply yes to continue or tell me anything that 
   needs correcting before we move on."

6. If the user requests corrections, update the JSON 
   in working/analyse-output.json accordingly and 
   display the corrected summary.

7. Once the user confirms, move to Stage 2.

---

## Stage 2 — Clarify and Enrich

### Instructions
1. Load the JSON from: working/analyse-output.json

2. Run the clarify skill:
   Follow all instructions in: skills/clarify/SKILL.md

3. Once all questions are answered and the enriched 
   JSON is produced, save it to:
   working/clarify-output.json

4. Move to Stage 3.

---

## Stage 3 — Confidence Check and Document Selection

### Instructions
1. Load the JSON from: working/clarify-output.json

2. Review the JSON and assess confidence for each 
   output document using the criteria below.

### Confidence Criteria

**Blog Post**
- High — achievements, lessons_learned and project_goal 
  are all populated with good detail
- Medium — most fields populated but some thin or missing
- Low — key fields empty or very sparse

**Slack Update**
- High — achievements, measurable_results and 
  slack_update.call_to_action are all populated
- Medium — achievements present but results or 
  call to action are thin
- Low — little detail available or sensitivities 
  not resolved

**Success Story**
- High — measurable_results, problems_faced, 
  how_problems_were_overcome and outcome all populated
- Medium — some results available but story feels incomplete
- Low — insufficient results or narrative detail

3. Present the confidence ratings to the user in this format:

---
Here is my confidence in each document based on 
what we have gathered:

📝 Blog Post — [High / Medium / Low] confidence
   [One sentence explaining why]
   [One sentence noting any gaps that might affect quality]

💬 Slack Update — [High / Medium / Low] confidence
   [One sentence explaining why]
   [One sentence noting any gaps that might affect quality]

🏆 Success Story — [High / Medium / Low] confidence
   [One sentence explaining why]
   [One sentence noting any gaps that might affect quality]

Which documents would you like to generate?
Reply with one or more: blog, slack, success story
Or reply "all" to generate everything.
---

4. Wait for the user to confirm their selection 
   before moving to Stage 4.

---

## Stage 4 — Generate Documents

### Instructions
1. Load the JSON from: working/clarify-output.json

2. For each document the user has selected, run the 
   corresponding skill in this order:

   Blog Post →
   Follow all instructions in: 
   skills/generate-blog/SKILL.md
   Save output to: outputs/blog-post.md

   Slack Update →
   Follow all instructions in: 
   skills/generate-slack/SKILL.md
   Save output to: outputs/slack-post.md

   Success Story →
   Follow all instructions in: 
   skills/generate-success-story/SKILL.md
   Save output to: outputs/success-story.md

3. Run each selected skill one at a time.
   Complete the revision loop for each document 
   before moving to the next.

4. Once all selected documents are complete, 
   display this summary to the user:

---
✅ All done! Here is what was generated:

[List each document generated with its output location]

Your files are saved in the outputs/ folder.
To start again with a new transcript, drop it in 
the transcripts/ folder and run this workflow again.
---

## File Structure Reference
transcripts/    — input transcript files go here (read-only, do not modify or delete)
working/        — intermediate JSON files (do not edit)
outputs/        — final generated documents
skills/         — skill files for each stage

## Notes
- Do not skip stages — each stage feeds the next
- The working/ folder is managed automatically 
  by the workflow — do not edit files there manually
- If something goes wrong at any stage, the JSON
  files in working/ can be inspected to diagnose issues
- Files in the transcripts/ folder are read-only inputs —
  never modify, move, rename, or delete them at any stage
