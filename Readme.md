# PMO Meeting Copilot

An executive-meeting copilot that turns transcripts, meeting materials, and participant context into decision objects — not just meeting notes.

## Why this exists

Executive meetings usually do not fail at note-taking.
They fail at preserving:

- decision context
- decision boundaries
- what was *not* decided
- what should happen next
- who should move, review, align, or be informed

Most meeting tools stop at summaries.
PMO Meeting Copilot aims to go one step further: reconstruct the meeting into structured execution objects.

## Why I’m building this

After 15 years working in marketing, I’ve seen a recurring problem in executive decision-making:

the issue is usually not the decision itself, but what gets lost as that decision travels into execution.

By the time a decision reaches cross-functional teams, key pieces are often missing:
- the original context behind the decision
- the boundaries of what was and was not decided
- the tradeoffs that were implicitly accepted
- the additional information teams need in order to act with confidence

That gap creates friction, misalignment, and unnecessary rework.

PMO Meeting Copilot is motivated by that gap.
Its goal is not to produce better meeting notes, but to help reconstruct the context, boundaries, and next steps that make executive decisions executable.

## What it does

Given a meeting transcript, optional supporting materials (deck, memo, pre-read), and optional participant relationships, PMO Meeting Copilot produces:

- **Decisions** — what appears to have been decided
- **Decision context** — why the decision exists, what background shaped it
- **Decision boundaries** — what is explicitly or implicitly out of scope / not yet decided
- **Next steps** — what should happen next
- **Stakeholder-aware completion** — likely owners, collaborators, approvers, impacted parties
- **Open questions and risks** — unresolved issues, assumptions, fragile points

## What it is not

This is **not**:

- a generic meeting summarizer
- an audio transcription tool
- a full PM suite
- a replacement for human judgment in executive decision-making

The goal is not to generate prettier minutes.
The goal is to transform messy discussion into a more complete decision-to-execution bridge.

## MVP scope

### Inputs

1. **Transcript** (required)
2. **Supporting material** (optional)
- deck
- memo
- pre-read
- strategy note
3. **Participant map** (optional)
- decision maker
- presenter / owner
- collaborators
- reviewers
- informed stakeholders

### Outputs

The MVP should produce a structured object like this:

```yaml
meeting_title: Q3 Beverage Strategy Review
meeting_topic: Pricing and portfolio review for new beverage platforms

decisions:
- statement: Keep the portfolio architecture aligned with the global platform structure, but localize flavor design for China.
confidence: medium
evidence_refs: [slide_12, transcript_chunk_07]

- statement: Treat pricing as a core growth lever, not a supporting page.
confidence: medium
evidence_refs: [slide_15, transcript_chunk_11]

decision_context:
- statement: China beverage growth is concentrated in the mass tier, where affordability and scale shape competition.
evidence_refs: [slide_02, slide_03]

- statement: Consumers want indulgence, but increasingly expect lower sugar and lower guilt options.
evidence_refs: [slide_06, slide_07]

decision_boundaries:
- statement: The meeting did not finalize the exact long-term anchor product for the new beverage portfolio.
confidence: medium

- statement: CLT results were discussed, but benchmark interpretation remained open.
confidence: high

next_steps:
- action: Rewrite the CLT page so that 4/5 platforms passing is framed positively while Energizer remains an open item.
owner_candidate: deck owner
collaborators: [insights_lead, category_lead]
rationale: Current framing over-amplifies the failure signal.
evidence_refs: [slide_14, transcript_chunk_10]

- action: Reconcile list price, effective price, and a la carte price definitions before final pricing discussion.
owner_candidate: pricing_owner
collaborators: [finance, business_owner]
rationale: Conflicting price concepts weaken decision quality.
evidence_refs: [slide_15, slide_16, transcript_chunk_12]

stakeholders:
decision_makers:
- role: executive sponsor
owner_candidates:
- role: deck owner
- role: pricing owner
collaborators:
- role: insights lead
- role: finance partner
impacted:
- role: store operations
- role: category teams

open_questions:
- What benchmark standard should be used to interpret CLT results?
- Should a single representative SKU be allowed to stand in for a full platform?
- What exact price ladder is defensible across coffee vs non-coffee?

risks:
- Upgrade volume may be misclassified as pure incremental volume.
- Price definitions may be inconsistent across slides.
- Decision rationale may be lost if only a short summary is shared.

