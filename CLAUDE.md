# Transcript to Docs

This project takes a meeting transcript and transforms it into polished
output documents through a series of structured stages.

## How to Run

To start the workflow, say:
"Please run the workflow.md with my transcript"

## Folder Structure

- `transcripts/` — drop your input transcript file here before running
- `working/` — intermediate JSON files managed automatically by the workflow, do not edit
- `outputs/` — final generated documents appear here
- `skills/` — skill files used by each stage of the workflow
- `workflow.md` — the main workflow definition

## Rules

- Never modify, move, rename, or delete files in the `transcripts/` folder
- Never manually edit files in the `working/` folder
- The `outputs/` folder is safe to clear between runs
- Always follow the rules in `skills/rules-style-guide.md` when generating documents
