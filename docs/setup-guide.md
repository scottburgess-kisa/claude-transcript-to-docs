# Transcript to Docs: Windows Setup Guide (Claude Desktop App)

Use this workflow on Windows to turn a meeting transcript into a blog post, Slack update, and success story in minutes.

---

## Before You Start

You will need the following:

**A Claude Pro account (or higher)**
The workflow runs inside the Claude desktop app, which requires a paid Claude subscription. Sign up at claude.ai.

**The Claude desktop app**
Download and install the Claude desktop app from claude.ai. Once installed, open it and make sure you can see the *Code* tab.

**Git**
Used to download the workflow files. Open PowerShell and type `git --version` to check if it is installed. If nothing appears, download it from git-scm.com and run the installer with default settings.

**Python and python-docx**
Used to read .docx transcript files. Open PowerShell and type `python --version` to check if Python is installed. If nothing appears, download it from python.org. During installation, make sure to tick *Add Python to PATH*.

Once Python is installed, install the required library by running:

`pip install python-docx`

---

## Getting Set Up

**1. Open PowerShell**
Press `Windows + R`, type `powershell`, and press Enter.

**2. Choose where to store the workflow**
Navigate to the folder where you want to keep the workflow. For example, to store it in your Documents folder:

`cd $env:USERPROFILE\Documents`

If you want to create a new folder for it first:

```
mkdir ai-tools
cd ai-tools
```

**3. Get the workflow files**
Run the following to download everything you need:

`git clone https://github.com/scottburgess-kisa/claude-transcript-to-docs.git`

This creates a new folder called `claude-transcript-to-docs` inside your chosen location.

**4. Open the folder in Claude**
Open the Claude desktop app, go to the *Code* tab, and open the `claude-transcript-to-docs` folder you just cloned.

**5. Add your transcript**
Copy your transcript file (.docx) into the `transcripts` folder inside the project.

---

## Running the Workflow

In the Claude Code chat, type:

*"Please run the workflow.md with my transcript"*

Claude will guide you through the rest step by step, asking questions along the way before generating your documents.

---

## Output Files

Your finished documents will appear in the `outputs` folder:

- *blog-post.md* — LinkedIn blog post
- *slack-post.md* — Internal Slack update
- *success-story.md* — External success story

---

## Tips

- Your transcript file can have any name, just make sure it is in the `transcripts` folder
- The `working` folder is managed automatically by the workflow, you do not need to touch it
- To run the workflow again with a new transcript, copy the new file into `transcripts` and start again
- To get the latest version of the workflow at any time, open PowerShell in the project folder and run: `git pull`

---

*Questions or issues? Reach out to Scott Burgess.*
