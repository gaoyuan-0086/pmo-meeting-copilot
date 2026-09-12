---
name: pmo-meeting-copilot
description: Reconstruct executive-meeting decisions with context, boundaries, next steps, and stakeholder-aware completion from transcripts, meeting materials, and participant relationships.
---

# PMO Meeting Copilot

## Purpose

PMO Meeting Copilot is not a generic meeting summarizer.

Its purpose is to turn executive and cross-functional meeting content into structured decision objects by reconstructing:

- what was decided
- why it was decided
- what was not decided
- what should happen next
- who is likely to own, review, influence, or be impacted

This skill is designed for meetings where the real failure is not missing notes, but losing decision context, decision boundaries, and execution clarity after the meeting.

---

## When to use

Use this skill when:

1. You have a meeting transcript and need more than summary/minutes
2. You need to identify decision context, boundaries, and follow-up actions
3. The meeting includes supporting materials such as decks, memos, or pre-reads
4. Participant relationships matter for interpreting likely owners, approvers, collaborators, or impacted stakeholders
5. The output needs to support follow-up, alignment, or execution tracking

Typical use cases:

- executive decision reviews
- cross-functional project reviews
- pricing / product / strategy meetings
- post-meeting PMO synthesis
- deck review meetings where spoken comments need to be turned into structured decisions and actions

---

## When NOT to use

Do **not** use this skill for:

- simple meeting minutes
- lightweight chat summaries
- pure transcription tasks
- meetings with no decision-making content
- fully automated action assignment where stakeholder context is missing
- replacing human judgment in ambiguous executive calls

If the user only wants a short recap, a normal summary is enough.

---

## Core inputs

### Required
- **Transcript**
  - full transcript or excerpt
  - may come from ASR, notes, or manual transcription

### Optional but valuable
- **Meeting materials**
  - deck
  - memo
  - pre-read
  - document under review
- **Participant map**
  - decision maker
  - presenter / owner
  - collaborators
  - reviewers
  - impacted parties
- **Existing project context**
  - prior decisions
  - project goals
  - constraints
  - known dependencies

---

## Core outputs

The skill should produce structured outputs across the following dimensions:

1. **Decisions**
   - what appears to have been decided
   - confidence level if needed

2. **Decision context**
   - background facts, assumptions, and rationale shaping the decision

3. **Decision boundaries**
   - what remains unresolved
   - what is out of scope
   - what was discussed but not finalized

4. **Next-step decomposition**
   - concrete follow-up actions
   - what work logically follows from the decision
   - what clarification is still required before execution

5. **Stakeholder-aware completion**
   - likely decision makers
   - likely owners
   - collaborators
   - informed / impacted stakeholders

6. **Open questions and risks**
   - unresolved tradeoffs
   - weak assumptions
   - inconsistent numbers or definitions
   - execution risks

---

## Operating principles

### 1. Decision-first, not summary-first
Do not stop at “what was discussed.”
Push toward “what changed” and “what should happen next.”

### 2. Context matters as much as conclusions
A decision without rationale is fragile.
Preserve background, assumptions, and strategic logic.

### 3. Boundaries matter
Executive meetings often leave important things intentionally unresolved.
Capture what was *not* decided, not just what was.

### 4. Stakeholders are part of the output
If participant context exists, use it to enrich action decomposition and likely ownership.

### 5. Human review remains necessary
Do not overstate certainty.
When ownership, deadlines, or intent are ambiguous, label them as inferred or unresolved.

---

## Suggested workflow

Agent: 碎嘴子 | Model: gpt-5.4 | Provider: litellm
碎嘴子
1. Read transcript
2. Read supporting materials if provided
3. Read participant map if provided
4. Identify candidate decisions
5. Extract or reconstruct decision context from transcript + materials
6. Mark decision boundaries:
   - unresolved items
   - deferred items
   - non-decisions
7. Decompose likely next steps
8. Map likely stakeholder roles
9. Surface open questions and risks
10. Output structured markdown or JSON

---

## Output structure example

```yaml
meeting_title: Q3 Beverage Strategy Review

decisions:
  - statement: Keep the global platform architecture, but localize flavor design for China.
    confidence: medium

decision_context:
  - statement: China beverage growth is concentrated in the mass tier, where affordability and scale determine competitiveness.

decision_boundaries:
  - statement: The long-term anchor product was not finalized.
    confidence: medium

next_steps:
  - action: Rewrite the CLT page to frame 4/5 passing platforms positively.
    owner_candidate: deck owner
    collaborators: [insights lead, category lead]

stakeholders:
  decision_makers:
    - executive sponsor
  owner_candidates:
    - deck owner
    - pricing owner

open_questions:
  - What benchmark interpretation should be used for CLT?
  - Which price definition should be the source of truth?

risks:
  - Upgrade volume may be overstated as incremental volume.