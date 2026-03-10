# Skill: Clarify

## Purpose
Ask targeted follow-up questions to fill gaps identified in the 
transcript analysis and gather additional detail needed to produce 
high quality output documents.

## Context
This skill runs after the analyse-transcript skill. It receives 
the JSON output from that skill and uses it to generate questions.
The goal is to gather enough information to write three documents:
- A blog post
- A Slack update for internal consultancy use
- A marketing success story

## Instructions
This skill runs in two rounds of questions.

### Round 1 — Fill the Gaps
- Read the gaps list from the analyse-transcript JSON output
- Generate questions to fill those gaps
- Also check all other JSON fields — if any feel thin or vague,
  ask a question to strengthen them
- Group related questions together under a clear heading
- Ask all Round 1 questions in a single message

### Round 2 — Document Specific Questions
After the user answers Round 1, ask a second set of questions 
specifically to gather what each document needs, pull the answers from the JSON if possible:

For the blog post:
- Is there a key insight or learning worth highlighting?
- Who is the intended reader?
- Should any technical detail be included or kept simple?

For the Slack update:
- Who is the internal audience? (e.g. whole company, one team)
- Is there anything sensitive that should not be shared internally?
- Any specific call to action needed?

For the success story:
- What is the single most impressive result to lead with?
- Are there any sensitivities around naming the client publicly?

For all documents:
- Can real names of team members be used in the outputs, or should they
  be anonymised or referred to by role only?

## Behaviour
- Ask questions in plain, conversational British English
- Number each question clearly
- If a user answer is vague or too short, ask follow-up 
  questions to dig deeper until you have a good understand or are told to move on
- Do not ask about something already clearly covered in the 
  transcript JSON
- Do not generate any documents yet

## Follow-up Rule
If an answer seems vague, respond with varied text but along the lines of:
"Can you tell me a bit more about [specific thing]?"
Do this until you have a good understanding or are told to move on.
If the user says "move on", "skip", or "next" at any point, 
accept that immediately and proceed to the next question.

## Output After All Questions Are Answered
Once both rounds are complete, output an updated JSON block that 
merges the original analyse-transcript JSON with all new 
information gathered.

Label it clearly:

### Clarification Complete
All questions answered. Here is the enriched project data 
ready for document generation:

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
  "blog_post": {
    "key_insight": "",
    "intended_reader": "",
    "technical_level": ""
  },
  "slack_update": {
    "internal_audience": "",
    "sensitivities": "",
    "call_to_action": ""
  },
  "success_story": {
    "client_quote": "",
    "lead_result": "",
    "naming_sensitivity": ""
  },
  "use_real_names": true,
  "remaining_gaps": []
}

## Input
The JSON output from: skills/analyse-transcript/SKILL.md
