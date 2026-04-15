# Persona Engine

## Purpose
The persona engine applies named writer personas to document generation, allowing the same content to be written in different author voices while maintaining document type requirements.

## How Personas Work
Each persona represents a different writing style that can be applied to any real author's voice across 6 dimensions:
- **Emoji usage** - How and when emojis are used
- **Directness** - Communication style and approach
- **Layout** - Formatting and structural preferences
- **Technical detail level** - Amount of technical depth included
- **Excitement level** - Tone and energy in communication
- **Recognition style** - How appreciation and praise are expressed

**IMPORTANT**: Personas are writing styles, NOT identities. The workflow always asks who the real author is (e.g., Team Member A, Team Member B) and then applies the selected persona's style preferences to that person's voice. Never use persona names as authors - always use the real team member's name who will be posting the content.

## Persona Application Process

### 1. Persona Selection
During the clarify stage, users select a persona based on:
- Detailed style breakdowns for each persona
- Usage statistics (global and personal patterns)
- Smart recommendations based on context

### 2. JSON Integration
Selected persona is stored in `working/clarify-output.json`:
```json
{
  "persona_selection": {
    "selected_persona": "Jamie",
    "persona_details": {
      "emoji_usage": "strategic_content_tied",
      "directness": "collaborative_supportive",
      "layout": "balanced_personal",
      "technical_detail": "moderate_high",
      "excitement_level": "warm_appreciative",
      "recognition_style": "personal_thoughtful"
    }
  }
}
```

### 3. Generation Skill Application
Each generation skill reads the persona selection and applies style modifications:

**Document Type Guidance** (unchanged)
↓
**Persona Style Application** (new layer)
↓
**Universal Style Rules** (unchanged)

## Style Application Examples

### Emoji Usage
- **Alex**: None or minimal professional use only
- **Sarah**: Heavy celebratory emojis throughout
- **Jamie**: Strategic placement tied to content themes
- **Mike**: Single purposeful emoji if any
- **Gru**: Theatrical villainous emojis (🏆 ⚡ 💀 🎭 👑 🔥 💥 🚀)

### Recognition Style
- **Alex**: "The team delivered excellent results with professional execution."
- **Sarah**: "Huge shout-out to the amazing team - you absolutely crushed it!"
- **Jamie**: "Big thanks to @person1, @person2, and @person3 for their thoughtful collaboration."
- **Mike**: "Thanks to the delivery team."
- **Gru**: "It is I, Gru, who has once again achieved the impossible! My minions assisted adequately." (NOTE: Must always identify himself as 'Gru' in opening sentence)

### Technical Detail Level
- **Alex**: Includes comprehensive technical specifications and methodologies
- **Sarah**: Focuses on impact and outcomes over technical specifics
- **Jamie**: Moderate detail that remains accessible to broad audience
- **Mike**: Essential facts only, no extraneous technical information
- **Gru**: Presents all technical details as personal innovations and brilliant schemes

## Integration with Document Types

### Blog Posts
Personas modify:
- Opening approach (hook vs overview vs context)
- Section treatment (detailed vs energetic vs balanced vs efficient)
- Conclusion style (summary vs call-to-action vs reflection vs next-steps)

### Slack Updates
Personas modify:
- Headline style (professional vs exciting vs collaborative vs factual)
- Body treatment (structured vs storytelling vs appreciative vs essential)
- Closing approach (formal vs enthusiastic vs personal vs brief)

### Success Stories
Personas modify:
- Narrative stance (partnership vs transformation vs collaboration vs efficiency)
- Challenge framing (systematic vs dramatic vs shared vs practical)
- Result emphasis (comprehensive vs breakthrough vs collective vs metrics)

## Usage Tracking Integration
The persona engine tracks:
- **Global statistics**: How often each persona is used across all sessions
- **Personal patterns**: Individual user's persona preferences
- **Context awareness**: Project type correlations (government = Alex, startup = Sarah)
- **Recommendation logic**: Smart suggestions based on patterns

## Technical Implementation Notes

### Generation Skill Integration Pattern
Each generation skill includes:
```markdown
## Tone and Style
Follow all rules in: skills/rules-style-guide.md

**Document Type**: [Blog/Slack/Success Story] ([document specific guidance])
**Persona**: {{ selected_persona }}
Apply persona style from: skills/personas.json

{{ persona_specific_instructions }}

Additional document-specific rules:
[existing document guidance...]
```

### Style Conflict Resolution
When persona style conflicts with document requirements:
1. **Document type requirements take precedence** (e.g., Slack posts must be internal/celebratory)
2. **Persona modifies HOW requirements are met** (e.g., Alex celebrates formally, Sarah celebrates energetically)
3. **Universal style rules always apply** (e.g., no em dashes, British English)

### Fallback Behavior
If persona selection fails or is missing:
1. Default to Alex (formal/detailed) persona
2. Log the fallback for debugging
3. Continue generation with standard style

## Quality Assurance
The persona system ensures:
- **Consistency**: Same persona produces consistent voice across documents
- **Appropriateness**: Personas enhance without undermining document purpose
- **Flexibility**: System supports adding new personas and style dimensions
- **Tracking**: Usage patterns inform recommendations and improvements