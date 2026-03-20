# Workflow: Transcript to Documents

## Purpose
This workflow takes a project transcript and transforms it into 
polished output documents through a series of structured stages.
Each stage builds on the last, passing enriched data forward.

## Overview
Stage 1 — Analyse the transcript
Stage 2 — Document selection
Stage 3 — Targeted clarify and enrich
Stage 4 — Parallel document generation
Stage 5 — Review and finalise outputs

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

## Stage 2 — Document Selection

### Instructions
1. Load the JSON from: working/analyse-output.json

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
   before moving to Stage 3.

---

## Stage 3 — Targeted Clarify and Enrich

### Instructions
1. Load the JSON from: working/analyse-output.json

2. Run the clarify skill with the user's document selection:
   Follow all instructions in: skills/clarify/SKILL.md

   IMPORTANT: Pass the user's selected documents from Stage 2
   to the clarify skill so it only asks questions relevant
   to the documents they want to generate.

   Selected documents should be passed as:
   [list of selected documents from Stage 2]

3. The clarify skill will ask targeted questions only for
   the selected document types and produce an enriched
   JSON that includes all information needed for generation.

4. Save the enriched JSON output to:
   working/clarify-output.json

5. Move to Stage 4.

---

## Stage 4 — Parallel Document Generation

### Instructions
1. Load the JSON from: working/clarify-output.json

2. Check the `selected_documents` field to see which documents
   the user requested in Stage 2.

3. For EACH selected document, create an agent using the Agent tool.
   Create ALL agents in a SINGLE message for parallel execution:

   **If "blog" is in selected_documents:**
   ```
   Agent tool with:
   - description: "Generate blog post"
   - prompt: "Load working/clarify-output.json and follow all instructions in skills/generate-blog/SKILL.md. Save the blog post to outputs/blog-post.md"
   - run_in_background: true
   ```

   **If "slack" is in selected_documents:**
   ```
   Agent tool with:
   - description: "Generate slack update"
   - prompt: "Load working/clarify-output.json and follow all instructions in skills/generate-slack/SKILL.md. Save the slack post to outputs/slack-post.md"
   - run_in_background: true
   ```

   **If "success story" is in selected_documents:**
   ```
   Agent tool with:
   - description: "Generate success story"
   - prompt: "Load working/clarify-output.json and follow all instructions in skills/generate-success-story/SKILL.md. Save the success story to outputs/success-story.md"
   - run_in_background: true
   ```

   CRITICAL: Use multiple Agent tool calls in a single message
   to achieve true parallel execution. Each agent runs autonomously
   and requires no user interaction.

4. You will be automatically notified when each agent completes.
   Wait for ALL agents to finish before proceeding.

5. Once all agents complete, verify the outputs exist:
   - Check outputs/blog-post.md (if blog was selected)
   - Check outputs/slack-post.md (if slack was selected)
   - Check outputs/success-story.md (if success story was selected)

6. If any outputs are missing, report which agent failed
   and suggest running that skill manually.

7. Display this summary to the user:

---
✅ Generation complete! Here is what was created:

[List each document that was successfully generated with its output location]

Moving to Stage 5 for document review and finalization.
---

### Error Handling
If an agent fails:
- Continue with other agents (don't stop the entire process)
- Report which document failed to generate
- Suggest manual execution of the failed skill as backup
- Still display results for successful generations

---

## Stage 5 — Review and Finalise Outputs

### Instructions
1. Load the JSON from: working/clarify-output.json

2. Run the review-outputs skill:
   Follow all instructions in: skills/review-outputs/SKILL.md

3. The review skill will:
   - Display each generated document for user review
   - Ask document-specific review questions
   - Handle any requested revisions
   - Update files with approved changes

4. Once the user has reviewed and finalised all documents,
   the workflow is complete.

### Review Process
- Each document is reviewed individually
- User can request changes, revisions, or approve as-is
- Files are updated in real-time during the review
- Process continues until all documents are finalised

### Benefits of the Review Stage
- Quality control after autonomous generation
- User maintains final approval over all content
- Opportunity to refine tone, details, or messaging
- Ensures outputs meet specific requirements

## File Structure Reference
transcripts/    — input transcript files go here (read-only, do not modify or delete)
working/        — intermediate JSON files (do not edit)
outputs/        — final generated documents (reviewed and finalised)
skills/         — skill files for each stage including review-outputs

## Notes
- Do not skip stages — each stage feeds the next
- The working/ folder is managed automatically
  by the workflow — do not edit files there manually
- Stage 4 uses parallel agent execution for faster generation
  — all selected documents are created simultaneously
- Stage 5 provides structured review and revision of all outputs
  — ensuring quality control and user satisfaction
- If something goes wrong at any stage, the JSON
  files in working/ can be inspected to diagnose issues
- Files in the transcripts/ folder are read-only inputs —
  never modify, move, rename, or delete them at any stage
