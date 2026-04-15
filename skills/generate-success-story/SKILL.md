# Skill: Generate Success Story

## Purpose
Generate a compelling marketing success story based on the 
enriched project data gathered from the clarify skill.
This document is intended for external audiences such as 
potential clients, marketing material, or the company website.

## Context
This skill is part of a multi-stage content generation workflow.
It receives enriched JSON data about a project and transforms it
into a narrative success story that reads like a case study 
meets human interest piece.
The goal is to make the reader feel the impact of the work —
not just understand it intellectually.

## Generation Instructions
Generate the success story directly from the enriched JSON data.
All required information has been gathered in the clarify stage.

### Success Story Generation Process
1. Determine which persona to use for this generation:
   - If generating a specific persona file (e.g., success-story-mike.md), use that persona (mike)
   - If generating a general file (success-story.md), use the first persona from `persona_selection.selected_personas`
   - Apply the corresponding style preferences from skills/personas.json
   - Use persona-specific approach to narrative stance, challenge framing, and result emphasis

2. Use the angle from `success_story.angle` field:
   - Results focused — lead with numbers and outcomes
   - Journey focused — lead with the challenge and how it was overcome
   - Inspiring and human — lead with people and impact

3. Respect naming sensitivities from `success_story.naming_sensitivity` field
   - If client cannot be named, use neutral descriptors
   - Example: "a leading logistics company" instead of specific name

4. Use the length from `success_story.length` field:
   - Short (400-600 words)
   - Medium (700-1000 words)
   - Long (1000-1500 words)

5. Generate the complete success story autonomously using all
   enriched JSON data without any user interaction.

## Tone and Style
Follow all rules in: skills/rules-style-guide.md

**Document Type**: Success Story (narrative, engaging, external marketing)
**Persona**: Apply style from `persona_selection.selected_persona` field

**Persona-Specific Style Application:**
- **Alex** (Formal/Detailed): Professional partnership stance, systematic challenge analysis, comprehensive outcome emphasis
- **Sarah** (Energetic/Celebratory): Transformative journey stance, dramatic stakes framing, exciting breakthrough emphasis
- **Jamie** (Collaborative/Balanced): Collaborative success stance, shared challenge framing, collective achievement emphasis
- **Mike** (Clean/Efficient): Efficient delivery stance, practical problem framing, clear metrics emphasis
- **Gru** (Villainous/Dramatic): Mastermind genius stance, impossible odds overcome framing, world-changing brilliance emphasis

Additional rules for this document:
- Narrative and engaging — this should read like a story
- British English throughout
- Make the client the hero — the consultancy enabled their success
- Use specific details and numbers wherever the JSON provides them
- Avoid generic marketing language like "innovative solution" or "best in class" — show do not tell
- Adjust confidence level based on persona: Alex (professional), Sarah (bold), Jamie (collaborative), Mike (factual), Gru (supremely arrogant)

## Structure
Use the following structure, adapting based on the chosen angle:

1. Opening hook (1-2 sentences)
   Draw the reader in immediately — a striking result, 
   a relatable problem, or a compelling human moment

2. The Challenge (1-2 paragraphs)
   Set the scene — what was the client facing and why did it matter?

3. The Approach (1-2 paragraphs)
   How was the problem tackled? Keep this clear and accessible.
   Mention tools or methods only if they add to the story.

4. The Results (1-2 paragraphs)
   What changed? Lead with the most impressive measurable result.
   Use specific numbers wherever possible.

5. Client Quote (optional)
   Only include if client_quote is populated in the JSON.
   Format as a proper pull quote:
   > "Quote text here." — Client Name, Job Title, Company

6. What This Means (1 paragraph)
   A brief closing reflection on the broader significance 
   of the work — why it matters beyond the numbers.

## Formatting Rules
- The title must be professional and substantive, in keeping with
  the tone of the content. Avoid clever or witty headlines.
  Opt for clear titles that reflect the narrative directly.
- Use markdown headings (## Heading) for each section
- Use bold sparingly to highlight the single most important 
  result or moment in each section
- No bullet points — this is a narrative document, 
  use flowing prose throughout
- End with a horizontal rule (---) followed by a suggested 
  pull quote of 1-2 sentences for use in marketing materials

## Length
Default to 700-1000 words.
If the user specifies shorter or longer, adjust accordingly.

## Output
Save the success story to: outputs/success-story.md

The success story will be generated autonomously for agent execution.
No user interaction or revision loops are required.

## Input
The enriched JSON output from: skills/clarify/SKILL.md
