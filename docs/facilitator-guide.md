# Transcript to Docs: Facilitator Guide

This guide is for the person running the team conversation that will be turned into documents. Follow these steps to get the most out of the session.

---

## Before the Meeting

**Turn on transcription in your meeting tool**
The workflow reads the transcript from your meeting, so transcription must be enabled before anyone starts speaking. Most tools support this natively:

- *Microsoft Teams* — click More > Record and transcribe
- *Google Meet* — click Activities > Recording
- *Zoom* — click Record and enable transcription in settings

Make sure everyone in the meeting is aware they are being recorded.

**Download the transcript afterwards**
Once the meeting ends, download the transcript as a .docx or text file. Drop it into the `transcripts/` folder before running the workflow.

---

## Before You Start: A Note on Sensitive Information

Before the meeting begins, make the following clear to all participants.

The transcript from this session will be processed by Claude, an AI tool whose servers are based in the United States. This means anything said in the meeting may be sent to and processed on US-based infrastructure.

Participants should not share anything during the session that they would not be comfortable sending outside of the UK or outside of their organisation. This includes:

- Personal data about individuals
- Commercially sensitive information such as contract values, rates, or financials
- Client information that is confidential or covered by an NDA
- Any data that is subject to UK GDPR or government security classifications

If in doubt, leave it out. The workflow produces better outputs from high-level discussion than from sensitive detail anyway.

---

## Running the Session

The conversation works best when it is informal and flowing. You are not conducting interviews — you are having a team discussion that happens to be recorded. The more people talk naturally, the better the outputs will be.

Aim for 30 to 45 minutes. Work through the questions below in order, but do not be rigid. Let the conversation breathe.

---

## Questions to Ask

### Setting the Scene

- When did this project start, and when did each person join the team?
- What were we asked to deliver, and what did the client expect that to look like?
- Were there any expectations we had to push back on or reframe early on?

### What We Have Been Doing

- What have been the main areas of work so far?
- What tools or methods have we been using, and how have we been working with AI?
- Has our approach changed from how we originally planned to do things?

### Problems and How We Solved Them

- What has been the hardest thing to deal with on this project?
- Were there any blockers or surprises that slowed us down?
- How did we get around those problems?

### Achievements and Results

- What is each person most proud of from the work so far?
- What has been completed that we can point to as a concrete output?
- Are there any numbers or comparisons that show the impact? For example, time saved or quality improvements.

### Client and Stakeholder Reaction

- How has the client responded to what we have delivered?
- Have there been any misconceptions we have had to manage?
- Is there anything the client has said that stands out as particularly positive?

### Lessons Learned

- What do we know now that we wish we had known at the start?
- Is there anything we would do differently next time?
- What advice would we give to another team starting a similar project?

### Looking Ahead

- What phase are we in now, and what comes next?
- Is there anything still unresolved or uncertain that is worth mentioning?

---

## Tips for a Good Session

- **Say names before speaking.** If people jump in over each other, names in the transcript help the workflow attribute comments correctly.
- **Avoid jargon without explanation.** If you use acronyms or project-specific terms, say what they mean at least once.
- **Encourage quiet members.** Ask each person directly for their view — the workflow benefits from hearing multiple perspectives.
- **State things explicitly.** Do not assume context. If something is obvious to the room, say it anyway — the workflow only knows what is in the transcript.
- **Avoid side conversations.** Keep the discussion on topic. Unrelated chat adds noise that the workflow has to filter out.

---

*Once your transcript is ready, the next step is to run it through the workflow. See the* [Setup Guide](setup-guide.md) *for instructions on how to do that.*

*Ideally, the person who facilitated the meeting should also be the one to run the workflow. The reason for this is the clarification phase: after analysing the transcript, the workflow asks a series of follow-up questions to fill gaps and gather detail that was not covered in the conversation. The facilitator will have the most context to answer these accurately and quickly.*

*If someone else is running the workflow on your behalf, it is worth pairing with them for the clarification phase rather than handing it over entirely. A short call or shared screen session at that stage will produce much better outputs than answering questions second-hand.*
