# Skill: Generate Blog Post



## Purpose
Generate a conversational and approachable blog post based on 
the enriched project data gathered from the clarify skill.

## Context
This skill is part of a multi-stage content generation workflow.
It receives enriched JSON data about a project and transforms it 
into a polished blog post ready for publishing or light editing.

## Instructions
Generate the blog post directly from the enriched JSON data.
All required information has been gathered in the clarify stage.

### Blog Generation Process
1. Determine which persona to use for this generation:
   - If generating a specific persona file (e.g., blog-post-jamie.md), use that persona (jamie)
   - If generating a general file (blog-post.md), use the first persona from `persona_selection.selected_personas`
   - Apply the corresponding style preferences from skills/personas.json
   - Use persona-specific approach to opening style, section treatment, and conclusion approach

2. Read the author from `blog_post.author` field
   - This is the REAL team member authoring the post, NOT the persona name
   - Apply the selected persona's style to how this real person would write
   - Do NOT quote this person in the post
   - Exclude them from any direct quotes in the content

3. Use the length from `blog_post.length` field:
   - Short (300-500 words)
   - Medium (600-900 words)
   - Long (1000-1500 words)

4. Use the sections from `blog_post.sections` array
   - Only include sections that were selected during clarification
   - Use the technical level from `blog_post.technical_level`

5. Generate the complete blog post autonomously using all
   enriched JSON data without any user interaction.

## Tone and Style
Follow all rules in: skills/rules-style-guide.md

**Document Type**: Blog Post (conversational, informative, approachable)
**Persona**: Apply style from `persona_selection.selected_persona` field

**Persona-Specific Style Application:**
- **Alex** (Formal/Detailed): Structured overview openings, detailed methodical sections, professional summary conclusions
- **Sarah** (Energetic/Celebratory): Exciting hook openings, energetic storytelling sections, celebratory call-to-action conclusions
- **Jamie** (Collaborative/Balanced): Collaborative context openings, balanced narrative sections, thoughtful reflection conclusions
- **Mike** (Clean/Efficient): Direct purpose openings, efficient facts sections, brief next-steps conclusions
- **Gru** (Villainous/Dramatic): Villainous proclamation openings, credit-claiming narrative sections, triumphant victory lap conclusions
- **DungeonAI** (Game Show Host): Game show episode intro openings, achievement unlock narrative sections, ratings success commentary conclusions
- **PrincessDonut** (Royal Cat): Royal cat survey openings, condescending servant praise sections, grudging approval treats conclusions

Additional rules for this document:
- British English throughout
- Avoid jargon where possible — if technical terms are needed, explain them briefly in plain English
- Use short paragraphs — no more than 3-4 sentences each
- Use the technical level specified in the enriched JSON
- Adjust approachability based on persona: Alex (structured), Sarah (enthusiastic), Jamie (collaborative), Mike (direct)

## Structure
- Use the sections chosen by the user
- Use markdown headings for each section (## Heading)
- End with a horizontal rule (---) followed by a suggested 
  meta description of 1-2 sentences for SEO purposes

## Output
Save the blog post to: outputs/blog-post.md

The blog post will be generated autonomously for agent execution.
No user interaction or revision loops are required.

## Input
The enriched JSON output from: skills/clarify/SKILL.md
