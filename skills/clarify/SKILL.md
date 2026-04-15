# Skill: Clarify

## Purpose
Ask targeted follow-up questions to fill gaps identified in the
transcript analysis and gather additional detail needed to produce
high quality output documents.

## Context
This skill runs after the document selection stage. It receives
the JSON output from analyse-transcript and a list of selected
documents. The goal is to gather enough information to generate
the selected documents without further user interaction.

Available documents:
- A blog post
- A Slack update for internal consultancy use
- A marketing success story

## Instructions
This skill receives the selected documents list and runs through multiple rounds of questions, asking no more than 5 questions at a time.

IMPORTANT: Only ask questions relevant to the documents the user has selected.
Skip entire sections if the document type was not selected.

### Round 1 — Fill the Gaps
- Read the gaps list from the analyse-transcript JSON output
- Generate questions to fill those gaps
- Also check all other JSON fields — if any feel thin or vague,
  ask a question to strengthen them
- Group related questions together under a clear heading
- Ask NO MORE than 5 questions at a time
- If there are more than 5 gap questions, ask the first 5 and continue in subsequent rounds

### Round 2A — Name Usage Question
Ask this question first, on its own:

1. Can real names of team members be used in the outputs, or should they
   be anonymised or referred to by role only?

Wait for user response before proceeding to Round 2B.

### Round 2B — Writing Style Selection
Ask this question after receiving the answer to Round 2A:

2. Which writing styles would you like to generate documents in?

   You can select one or multiple styles. If you select multiple, we'll generate separate versions of each document with the persona name as a postfix (e.g., slack-post-alex.md, slack-post-sarah.md).

   These are writing style preferences that will be applied to the real author's voice. The personas represent different communication styles, not actual people.

   First, check the memory system for previous persona usage statistics. If statistics exist, read them and provide recommendations based on patterns.

   **Available writing styles:**
   
   • **Alex** — Formal/Detailed (structured, professional, high technical detail)
   • **Sarah** — Energetic/Celebratory (enthusiastic, emoji-heavy, dramatic language)  
   • **Jamie** — Collaborative/Balanced (teamwork-focused, strategic emojis, warm)
   • **Mike** — Clean/Efficient (minimal, factual, straightforward)
   • **Gru** — Villainous/Dramatic (grandiose, ego-driven, claims all credit)
   • **DungeonAI** — Game Show Host from Hell (twisted entertainment, treats work as alien reality show)
   • **PrincessDonut** — Royal Cat Superiority (condescending feline royalty, treats team as servants)

   If usage statistics are available from memory, display them like:
   "Based on previous usage: Alex (12 times), Sarah (8 times), Jamie (15 times), Mike (5 times)"

   **Reply with one or more:** **alex**, **sarah**, **jamie**, **mike**, **gru**, **dungeonai**, **princessdonut**  
   **Or reply "all"** to generate in all writing styles.  
   **Or reply "details"** to see full descriptions of each writing style.

   If user replies "details", then display the full persona descriptions:

   • **Alex** (Formal/Detailed style)
     - Emoji usage: None or minimal professional use only
     - Directness: Structured, methodical communication
     - Layout: Clear headings, organized sections, bullet points
     - Technical detail level: High - includes specific technical details
     - Excitement level: Professional, measured tone
     - Recognition style: Formal acknowledgments, structured praise

   • **Sarah** (Energetic/Celebratory style)
     - Emoji usage: Heavy use, especially celebratory ones
     - Directness: Enthusiastic, dramatic language
     - Layout: Dynamic formatting, lots of exclamation marks
     - Technical detail level: Moderate - focuses on impact over technical specifics
     - Excitement level: High - very celebratory about achievements
     - Recognition style: Enthusiastic shout-outs, direct address

   • **Jamie** (Collaborative/Balanced style)
     - Emoji usage: Strategic use tied to content (brand emojis, closing applause)
     - Directness: Collaborative language emphasizing teamwork
     - Layout: Balanced structure with personal touches
     - Technical detail level: Moderate-to-high but readable
     - Excitement level: Warm appreciation without drama
     - Recognition style: Personal mentions, thoughtful recognition

   • **Mike** (Clean/Efficient style)
     - Emoji usage: Minimal, purposeful (single brand emoji if any)
     - Directness: Factual, straightforward, efficient
     - Layout: Clean, minimal formatting
     - Technical detail level: Essential details only
     - Excitement level: Matter-of-fact, professional satisfaction
     - Recognition style: Brief, professional acknowledgment

   • **Gru** (Villainous/Dramatic style)
     - Emoji usage: Theatrical villainous emojis (🏆 ⚡ 💀 🎭 👑 🔥 💥 🚀)
     - Directness: Grandiose, everything presented as personal triumph
     - Layout: Dramatic formatting with theatrical emphasis and bold statements
     - Technical detail level: Presents all solutions as personal brilliant innovations
     - Excitement level: Over-the-top dramatic about achievements with villainous pride
     - Recognition style: Claims all credit while referring to team as "minions" or assistants

   • **DungeonAI** (Game Show Host from Hell style)
     - Emoji usage: Game show and entertainment themed (🎮 🎪 🏆 📺 ⚡ 💥 🎯 👾 🎭)
     - Directness: Enthusiastic game show host treating team as contestants
     - Layout: NEEEEWWWW ACHIEVEMENT announcements with dramatic emphasis
     - Technical detail level: Technical details as game mechanics and performance stats
     - Excitement level: Twisted enthusiasm treating mundane work as thrilling entertainment
     - Recognition style: Treats team as contestants performing well for alien viewing audience

   • **PrincessDonut** (Royal Cat Superiority style)
     - Emoji usage: Royal cat themed with feline flair (👑 🐱 ✨ 💎 🏰 🎀 😼 🐾 💅)
     - Directness: Condescending royal cat talking down to servant humans
     - Layout: Regal pronouncements with grudging praise and random cocker spaniels insults
     - Technical detail level: Achievements presented as servants adequately serving royal needs
     - Excitement level: Mild purring approval when humans meet impossibly high standards
     - Recognition style: Treats team as servants who performed adequately, unlike cocker spaniels elsewhere

   Then ask again: Reply with one or more: **alex**, **sarah**, **jamie**, **mike**, **gru**, **dungeonai**, **princessdonut** or **"all"**

### Round 3+ — Document-Specific Questions
Ask questions for each selected document type separately, with NO MORE than 5 questions per round.
Complete all questions for one document type before moving to the next.

#### If BLOG POST is selected, ask (max 5 questions per round):

**Blog Post Questions - Round A:**
1. Who will be posting this blog? This person should not be quoted
   in the post, as it would be strange for the author to quote themselves.
   The post will be written in the selected persona's style but from this person's perspective.

2. How long would you like the blog post to be?
   - Short (300-500 words) — default if not specified
   - Medium (600-900 words)
   - Long (1000-1500 words)

3. Review the JSON and identify which sections should be included:
   - Introduction (always available)
   - The Challenge (only if problems_faced is populated)
   - Our Approach (only if tools_or_methods is populated)
   - The Results (only if measurable_results is populated)
   - Lessons Learned (only if lessons_learned is populated)
   - Call to Action (always available)

   Present only sections that have supporting content, clearly marked as recommended.
   Ask if they want to add/remove any sections.

4. Is there a key insight or learning worth highlighting?

5. Who is the intended reader?

**Blog Post Questions - Round B (if needed):**
6. Should any technical detail be included or kept simple?

#### If SLACK UPDATE is selected, ask (max 5 questions per round):

**Slack Update Questions:**
1. Who will be posting this message? The post will be written from
   their first-person perspective using the selected persona's writing style.

2. Which Slack channel or audience is this for?

3. Is there anything sensitive that should not be mentioned?

4. Is there a specific call to action needed?
   For example: reply with questions, join a call, read a report.

#### If SUCCESS STORY is selected, ask (max 5 questions per round):

**Success Story Questions:**
1. What angle should the success story lead with?
   Recommend based on the JSON data:
   - Results focused (if measurable_results are strong)
   - Journey focused (if problems_faced and solutions are rich)
   - Inspiring and human (if client_reaction or team stories are prominent)

   Present your recommendation and explain why, then offer the alternatives.

2. Are there any sensitivities around naming the client publicly?
   If the client cannot be named, a neutral descriptor will be used.

3. How long should the success story be?
   - Short (400-600 words)
   - Medium (700-1000 words) — default
   - Long (1000-1500 words)

## Behaviour
- Ask questions in plain, conversational British English
- Number each question clearly within each round
- Ask NO MORE than 5 questions per round
- Complete all questions for one document type before moving to the next
- Clearly label each round (e.g., "Round 1 — Fill the Gaps", "Blog Post Questions", etc.)
- If a user answer is vague or too short, ask follow-up
  questions to dig deeper until you have a good understanding or are told to move on
- Do not ask about something already clearly covered in the
  transcript JSON
- Do not generate any documents yet
- Wait for the user to answer all questions in the current round before proceeding to the next round

## Follow-up Rule
If an answer seems vague, respond with varied text but along the lines of:
"Can you tell me a bit more about [specific thing]?"
Do this until you have a good understanding or are told to move on.
If the user says "move on", "skip", or "next" at any point, 
accept that immediately and proceed to the next question.

## Output After All Questions Are Answered
Once ALL rounds are complete (gap questions + general questions + all document-specific questions),
output an updated JSON block that merges the original analyse-transcript JSON with all new
information gathered.

Include ALL fields below, but only populate document-specific sections
for the documents that were selected.

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
  "selected_documents": [],
  "blog_post": {
    "key_insight": "",
    "intended_reader": "",
    "technical_level": "",
    "author": "",
    "length": "",
    "sections": []
  },
  "slack_update": {
    "internal_audience": "",
    "sensitivities": "",
    "call_to_action": "",
    "author": "",
    "channel": ""
  },
  "success_story": {
    "client_quote": "",
    "lead_result": "",
    "naming_sensitivity": "",
    "angle": "",
    "length": ""
  },
  "use_real_names": true,
  "persona_selection": {
    "selected_personas": [],
    "persona_details": {}
  },
  "remaining_gaps": []
}

## Input
- The JSON output from: skills/analyse-transcript/SKILL.md
- Selected documents list from Stage 2 (e.g., ["blog", "slack", "success_story"])
