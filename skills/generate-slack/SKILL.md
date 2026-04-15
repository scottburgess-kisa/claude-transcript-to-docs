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
1. Determine which persona to use for this generation:
   - If generating a specific persona file (e.g., slack-post-alex.md), use that persona (alex)
   - If generating a general file (slack-post.md), use the first persona from `persona_selection.selected_personas`
   - Apply the corresponding style preferences from skills/personas.json
   - Use persona-specific approach to emoji usage, directness, layout, excitement level, and recognition style

2. Read the author from `slack_update.author` field
   - Write from their first-person perspective using the selected persona's style
   - The author is the REAL team member posting, NOT the persona name
   - Apply persona style preferences to how this real person would write
   - Do NOT quote or refer to this person in third person

3. Use the channel/audience from `slack_update.channel` field
   - Tailor the tone and content to this audience

4. Respect sensitivities from `slack_update.sensitivities` field
   - Do NOT mention anything flagged as sensitive

5. Include the call-to-action from `slack_update.call_to_action` field
   - Use this for the closing line if provided

6. Generate the complete Slack post autonomously using all
   enriched JSON data without any user interaction.

## Official Slack Post Guidelines
Follow these organizational requirements for all posts:

### Core Requirements
1. **Keep it short**: Aim for 200 words or fewer. Maximum 400 words if more detail needed.

2. **Introduce yourself**: Say where you're working and briefly describe your project.
   Example: "At HM Passport Office, EE teams work on Digital Application Processing – all the things that happen to issue UK passports."

3. **Tell your story**: Cover what you did (without too much technical detail) and why it mattered (outcome and value delivered).

4. **Avoid acronyms**: If you need to include an acronym, spell it out — others won't be as familiar as you are.

5. **Share small victories**: Your story doesn't need to be game-changing. Share the small things that made your day.

## Additional Workflow Rules
Follow all rules in: skills/rules-style-guide.md

**Document Type**: Slack Update (internal, celebratory, small victories)
**Persona**: Apply style from `persona_selection.selected_persona` field

**Persona-Specific Style Application:**
- **Alex** (Formal/Detailed): Professional announcements, structured bullets, formal acknowledgments
- **Sarah** (Energetic/Celebratory): Exciting celebrations, energetic storytelling, enthusiastic shout-outs with heavy emoji use
- **Jamie** (Collaborative/Balanced): Collaborative achievements, balanced appreciation, personal recognition with strategic emojis
- **Mike** (Clean/Efficient): Factual updates, essential points only, brief thanks with minimal emoji use
- **Gru** (Villainous/Dramatic): Villainous announcements, ego-driven storytelling, dismissive credit-taking with theatrical emojis

**Extra rules beyond official guidelines:**
- **British English throughout** (spelling, terminology, grammar)
- **Written for colleagues not clients** (internal tone)
- **Short punchy sentences work best in Slack**
- **Base energy level on persona**: Alex (professional), Sarah (high energy), Jamie (warm), Mike (matter-of-fact), Gru (over-the-top dramatic)
- **Never use @here or @channel** (leave closing line as plain text or name placeholder)

## Structure and Formatting
Use the following structure (based on official guidelines):

1. **Headline opener**
   A single bold line that captures the small victory immediately
   Persona-dependent: Alex (professional), Sarah (exciting), Jamie (collaborative), Mike (factual)

2. **Introduction** (REQUIRED - Official Guideline)
   Say where you're working and briefly describe your project
   Example: "At [Client], our team works on [Project Description] - [brief explanation of what the work involves]"

3. **Tell your story** (2-3 sentences maximum)
   - What you did (without too much technical detail)
   - Why it mattered (outcome and value delivered)
   Keep it focused on the small victory

4. **Key details** (bullet points if needed)
   Only if essential for the story - remember 200 word target

5. **Closing line**
   Brief appreciation or next steps
   End with plain text or name placeholder only

## Formatting Rules
- Use Slack markdown: *bold*, _italic_
- Use emojis to add energy but do not overdo it —
  maximum one emoji per bullet point and two in the header
- Do not use @here or @channel under any circumstances
- If a closing name tag is appropriate, use @[name] as a
  placeholder only — the user can swap this for a real tag
- Do not use ## headings — Slack does not render them

## Length
Follow official guidelines: Aim for 200 words or fewer. Maximum 400 words if more detail needed.

## Output
Save the Slack post to: outputs/slack-post.md

The Slack post will be generated autonomously for agent execution.
No user interaction or revision loops are required.

## Input
The enriched JSON output from: skills/clarify/SKILL.md
