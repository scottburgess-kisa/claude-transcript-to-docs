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

## Generation Instructions
Generate the Slack post directly from the enriched JSON data.
All required information has been gathered in the clarify stage.

### Slack Generation Process
1. Read the author from `slack_update.author` field
   - Write from their first-person perspective ("we did X", "I was impressed by Y")
   - Do NOT quote or refer to this person in third person

2. Use the channel/audience from `slack_update.channel` field
   - Tailor the tone and content to this audience

3. Respect sensitivities from `slack_update.sensitivities` field
   - Do NOT mention anything flagged as sensitive

4. Include the call-to-action from `slack_update.call_to_action` field
   - Use this for the closing line if provided

5. Generate the complete Slack post autonomously using all
   enriched JSON data without any user interaction.

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

The Slack post will be generated autonomously for agent execution.
No user interaction or revision loops are required.

## Input
The enriched JSON output from: skills/clarify/SKILL.md
