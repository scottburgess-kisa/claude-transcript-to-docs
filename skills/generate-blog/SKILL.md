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
1. Read the author from `blog_post.author` field
   - Do NOT quote this person in the post
   - Exclude them from any direct quotes in the content

2. Use the length from `blog_post.length` field:
   - Short (300-500 words)
   - Medium (600-900 words)
   - Long (1000-1500 words)

3. Use the sections from `blog_post.sections` array
   - Only include sections that were selected during clarification
   - Use the technical level from `blog_post.technical_level`

4. Generate the complete blog post autonomously using all
   enriched JSON data without any user interaction.

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

The blog post will be generated autonomously for agent execution.
No user interaction or revision loops are required.

## Input
The enriched JSON output from: skills/clarify/SKILL.md
