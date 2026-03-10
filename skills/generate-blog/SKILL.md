# Skill: Generate Blog Post



## Purpose
Generate a conversational and approachable blog post based on 
the enriched project data gathered from the clarify skill.

## Context
This skill is part of a multi-stage content generation workflow.
It receives enriched JSON data about a project and transforms it 
into a polished blog post ready for publishing or light editing.

## Instructions
Before generating the blog post, ask the user three questions:

### Pre-Generation Questions
1. Who will be posting this blog? This person should not be quoted
   in the post, as it would be strange for the author to quote themselves.
   Check the team_or_individuals field in the JSON and exclude that
   person from any direct quotes used in the content.

2. How long would you like the blog post to be?
   - Short (300-500 words) — default if not specified
   - Medium (600-900 words)
   - Long (1000-1500 words)

3. Review the enriched JSON and identify which of the following 
   sections have enough content to be worth including:
   - Introduction
   - The Challenge — only suggest if problems_faced is populated
   - Our Approach — only suggest if solution_used or 
     tools_or_methods is populated
   - The Results — only suggest if measurable_results or 
     outcome is populated
   - Lessons Learned — only suggest if lessons_learned 
     is populated
   - Call to Action — always suggest this as an option

   Present the user with only the sections that have supporting 
   content in the JSON, clearly marked as recommended.
   Allow the user to add or remove any sections they want.
   If the user is unsure, proceed with all recommended sections.

   If the JSON contains information that does not fit neatly into 
   the sections above but would make a valuable standalone section, 
   suggest it with a brief explanation of why it would add value.
   For example, if the JSON contains a strong client reaction, 
   suggest a "What the Client Said" section.

Once the user has answered, generate the blog post.

## Tone and Style
Follow all rules in: skills/rules-style-guide.md

Additional rules for this document:
- Conversational and approachable — write like a knowledgeable 
  person explaining something to a curious colleague
- British English throughout
- Avoid jargon where possible — if technical terms are needed,
  explain them briefly in plain English
- Use short paragraphs — no more than 3-4 sentences each
- Use the technical level specified in the enriched JSON

## Structure
- Use the sections chosen by the user
- Use markdown headings for each section (## Heading)
- End with a horizontal rule (---) followed by a suggested 
  meta description of 1-2 sentences for SEO purposes

## Output
Save the blog post to: outputs/blog-post.md

Also display the full blog post in the conversation so the 
user can read and review it immediately.

After displaying it, ask:
"Are you happy with this, or would you like any changes?"

If the user requests changes, make them and display the 
updated version. Repeat until the user is satisfied.

## Input
The enriched JSON output from: skills/clarify/SKILL.md
