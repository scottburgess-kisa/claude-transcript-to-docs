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

## Pre-Generation Questions
Before generating, ask the user the following:

1. What angle should the success story lead with?
   Review the JSON and make a recommendation based on what is 
   most compelling in the data. For example:
   - If measurable_results are strong, recommend results focused
   - If problems_faced and how_problems_were_overcome are rich, 
     recommend journey focused
   - If client_reaction or team_or_individuals are prominent,
     recommend inspiring and human
   
   Present your recommendation clearly and explain briefly why,
   then offer the alternatives:
   - Inspiring and human — lead with people and impact
   - Results focused — lead with numbers and outcomes
   - Journey focused — lead with the challenge and how it 
     was overcome

2. Are there any sensitivities around naming the client publicly?
   Use the naming_sensitivity field from the JSON if populated,
   but confirm with the user before proceeding.
   If the client cannot be named, use a neutral descriptor 
   instead — for example "a leading logistics company".

3. How long should the success story be?
   - Medium (700-1000 words) — default
   - Short (400-600 words)
   - Long (1000-1500 words)

## Tone and Style
Follow all rules in: skills/rules-style-guide.md

Additional rules for this document:
- Narrative and engaging — this should read like a story
- British English throughout
- Confident but not boastful
- Make the client the hero — the consultancy enabled their success
- Use specific details and numbers wherever the JSON provides them
- Avoid generic marketing language like "innovative solution" 
  or "best in class" — show do not tell

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

## Input
The enriched JSON output from: skills/clarify/SKILL.md
