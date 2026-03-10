# Skill: Generate Slack Post

## Purpose
Generate an energetic and celebratory internal Slack post based 
on the enriched project data gathered from the clarify skill.

## Context
This skill is part of a multi-stage content generation workflow.
It receives enriched JSON data about a project and transforms it
into a Slack post for internal consultancy updates.
The audience is colleagues who want to know what the team has 
achieved — quickly and enthusiastically.

## Pre-Generation Questions
Before generating, ask the user:

1. Who will be posting this message? The post should be written from
   their first-person perspective ("we did X", "I was impressed by Y").
   That person should not be quoted or referred to in the third person.
   Check the team_or_individuals field in the JSON and write the post
   as if it is coming from their point of view.

2. Which Slack channel or audience is this for?
   Use the internal_audience field from the JSON if populated,
   but confirm with the user before proceeding.

3. Is there anything sensitive that should not be mentioned?
   Use the sensitivities field from the JSON if populated,
   but confirm with the user before proceeding.

4. Is there a specific call to action needed?
   For example: reply with questions, join a call, read a report.
   If the JSON does not contain one, ask the user directly.

If the user is unsure about any of these, use sensible defaults 
based on the JSON and proceed.

## Tone and Style
Follow all rules in: skills/rules-style-guide.md

Additional rules for this document:
- Energetic and celebratory — this is a win worth sharing
- British English throughout
- Warm and inclusive — written for colleagues not clients
- Avoid overly formal language
- Short punchy sentences work best in Slack

## Structure and Formatting
Use the following structure:

1. Headline opener
   A single bold line that captures the win immediately
   Example: *We just helped [client] cut their reporting 
   time by 85%* 🎉

2. A short intro paragraph (2-3 sentences maximum)
   Set the scene — what was the challenge?

3. Bullet points covering key facts
   - What was done
   - How it was done
   - The results achieved
   Use relevant emojis at the start of each bullet point

4. A closing line with a call to action if applicable
   End with a plain text sign-off or a name placeholder if relevant
   Example: "Huge thanks to the team 🙌 Go give them some love!"

## Formatting Rules
- Use Slack markdown: *bold*, _italic_
- Use emojis to add energy but do not overdo it —
  maximum one emoji per bullet point and two in the header
- Do not use @here or @channel under any circumstances
- If a closing name tag is appropriate, use @[name] as a
  placeholder only — the user can swap this for a real tag
- Do not use ## headings — Slack does not render them

## Length
Default to 200-400 words.
If the user specifies shorter or longer, adjust accordingly.

## Output
Save the Slack post to: outputs/slack-post.md

Also display the full post in the conversation so the 
user can read and review it immediately.

After displaying it, ask:
"Are you happy with this, or would you like any changes?"

If the user requests changes, make them and display the 
updated version. Repeat until the user is satisfied.

## Input
The enriched JSON output from: skills/clarify/SKILL.md
