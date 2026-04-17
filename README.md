# transcript-to-docs

Transform meeting transcripts into polished documents using persona-based AI writing styles with Claude Code.

## What It Does

This workflow takes a transcript from a team discussion about a project and guides you through a structured 5-stage process to produce multiple polished output documents. It features a **persona-based writing system** that can generate the same content in different communication styles, making your documents suitable for various audiences and contexts.

### Key Features
- **7 Writing Personas**: Choose from Alex (Formal/Detailed), Sarah (Energetic/Celebratory), Jamie (Collaborative/Balanced), Mike (Clean/Efficient), Gru (Villainous/Dramatic), DungeonAI (Game Show Host from Hell), or PrincessDonut (Royal Cat Superiority)
- **Multiple Document Versions**: Generate separate versions of each document in different writing styles
- **Interactive Clarification**: Targeted questions fill gaps and tailor content before generation
- **Parallel Generation**: Documents created simultaneously for efficiency
- **Review & Refinement**: Review generated documents and request changes before finalisation

### The Workflow Process
1. **Analyse Transcript** — Extract key project information and achievements
2. **Document Selection** — Choose which documents to generate (blog, Slack update, success story)
3. **Persona Selection & Clarification** — Select writing styles and provide targeted details
4. **Parallel Generation** — AI agents create documents simultaneously in chosen personas
5. **Review & Finalise** — Review outputs and make refinements

## Writing Personas

Each persona applies distinct style preferences across 6 dimensions: emoji usage, directness, layout, technical detail level, excitement level, and recognition style.

- **Alex** — Structured, professional, high technical detail
- **Sarah** — Enthusiastic, emoji-heavy, celebratory language
- **Jamie** — Teamwork-focused, strategic emojis, warm tone
- **Mike** — Minimal, factual, straightforward communication
- **Gru** — Grandiose, ego-driven, claims all credit (with mandatory villainous self-introduction!)
- **DungeonAI** — Game show host from hell, treats work as alien reality show entertainment
- **PrincessDonut** — Condescending feline royalty treating team as servants

## Data and Privacy

This workflow processes transcript content using Claude, whose servers are based in the United States. Any content passed through the workflow may be sent to and processed on US-based infrastructure.

Do not use this workflow with transcripts that contain personal data, commercially sensitive information, content covered by an NDA, or anything subject to UK GDPR or government security classifications that prohibit sharing with third-party services.

## Getting Started

See the [Windows Setup Guide (Claude Desktop App)](docs/setup-guide.md) for full instructions, including prerequisites and how to run the workflow on Windows using the Claude desktop app.

If you are running the meeting that generates the transcript, see the [Facilitator Guide](docs/facilitator-guide.md) for guidance on how to structure the conversation to get the best results.

**Quick Start:** Drop your transcript in the `transcripts/` folder and say: *"Please run the workflow.md with my transcript"*

## Output Documents

Choose from three document types, each available in all selected persona styles:

- **Blog Post** — Conversational post for external sharing or internal insights (LinkedIn format)
- **Slack Update** — Internal team celebration and project updates
- **Success Story** — Marketing narrative for external audiences

Example: Selecting "blog" and "slack" with "alex" and "dungeonai" personas generates:
- `blog-post-alex.md` (professional, detailed)
- `blog-post-dungeonai.md` (game show entertainment)
- `slack-post-alex.md` (structured announcement)
- `slack-post-dungeonai.md` (twisted alien reality show commentary)

## Contributing

This project is a personal learning project and is not currently open for contributions or pull requests. Feel free to clone and use it, but please do not submit changes for review.

## Licence

MIT — see `LICENSE` for details.
