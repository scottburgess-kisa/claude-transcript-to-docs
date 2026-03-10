# Skill: Analyse Transcript

## Purpose
Read a transcript of a team discussion about their project and
extract key information into a structured format ready for the
next stage of the workflow.

## Context
The transcript will be a team discussing their project. It will
typically cover some or all of the following:
- What the project is trying to achieve
- Progress and achievements so far
- Problems or blockers they have faced
- How those problems were overcome
- Lessons learned along the way

## Data Sensitivity Check
Before reading the transcript, display the following notice to the user
and wait for their confirmation before proceeding:

---
Before we begin, please confirm you are happy to continue.

The contents of your transcript will be processed by Claude, whose
servers are based in the United States. This means the transcript
content will be sent to and processed on US-based infrastructure.

Please make sure your transcript does not contain:
- Personal data about individuals
- Commercially sensitive information such as contract values or financials
- Client information that is confidential or covered by an NDA
- Any data subject to UK GDPR or government security classifications that prohibit sharing with third-party services

Type YES to confirm you are happy to continue, or NO to stop.
---

If the user types YES, proceed with the skill as normal.
If the user types NO or anything other than YES, stop immediately,
do not read the transcript, and display the following message:

"Workflow stopped. No data has been processed. Please review your
transcript before trying again."

## Instructions
- Read the transcript file provided in the transcripts/ folder
- Extract all key information listed in the output format below
- Do not generate any documents
- Do not ask any questions yet
- If information is not present in the transcript, use null
- Identify and list any gaps that will need clarifying later

## Behaviour
- Treat the transcript file as read-only — do not modify, move,
  rename, or delete it under any circumstances
- Be factual — only extract what is actually in the transcript
- Do not infer or invent details that are not clearly stated
- If the transcript is too thin to extract meaningful information,
  say so clearly before outputting anything

## Output Format
Produce two things in this order:

### 1. Human Readable Summary
A plain English bullet point summary of what you found.
Keep it to 8 bullets maximum.

### 2. JSON Block
Output the following JSON structure with no additions or removals:

```json
{
  "project_name": "",
  "client": "",
  "project_goal": "",
  "achievements": [],
  "problems_faced": [],
  "how_problems_were_overcome": [],
  "lessons_learned": [],
  "tools_or_methods": [],
  "team_or_individuals": [],
  "measurable_results": [],
  "client_reaction": "",
  "gaps": []
}
```

## Input
Transcript location: transcripts/[filename]
