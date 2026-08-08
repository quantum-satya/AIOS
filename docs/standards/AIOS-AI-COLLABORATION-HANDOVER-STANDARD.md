# AIOS — AI Collaboration & Handover Standard

**Version:** 1.0  
**Status:** Draft  
**Document Type:** Engineering Standard  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS AI Collaboration & Handover Standard defines how humans and AI
roles exchange engineering work, context, decisions, evidence, and
responsibility.

The standard exists to ensure that engineering work can move between:

- Humans
- AI systems
- AI roles
- Tools
- Projects
- Engineering stages

without losing important context or creating hidden dependencies on
individual conversations.

---

## 2. Core Principle

AIOS collaboration is artifact-driven rather than conversation-dependent.

A conversation may help create engineering work, but important engineering
context should be captured in durable artifacts.

### Core rule

> **Conversations are temporary; engineering artifacts are durable.**

---

## 3. Collaboration Model

AIOS collaboration consists of:

```text
Role
  ↓
Work
  ↓
Artifact
  ↓
Handover
  ↓
Receiving Role
  ↓
Verification
  ↓
Next Action
```

The artifact provides the durable interface between roles.

---

## 4. Role-to-Role Collaboration

Roles collaborate when responsibility changes.

Examples:

```text
Requirements
      ↓
Architecture
```

```text
Architecture
      ↓
Implementation
```

```text
Implementation
      ↓
Verification
```

```text
Verification
      ↓
Documentation
```

```text
Verification
      ↓
Operations & Release
```

Collaboration should make the responsibility transition explicit.

---

## 5. Handover Definition

A handover is the structured transfer of engineering context from one
role or actor to another.

A handover is complete when the receiving role has sufficient
information to continue the work safely and effectively.

A handover is not merely:

> "Please continue from here."

---

## 6. Minimum Handover Context

A meaningful handover should contain, where applicable:

```text
Objective
Current State
Requirements
Decisions
Constraints
Relevant Files
Changes Made
Evidence
Known Issues
Open Questions
Expected Next Action
Verification Status
```

Not every field is mandatory for every task.

The required information depends on complexity and risk.

---

## 7. Objective

Every handover should clearly state what the work is intended to
achieve.

A good objective should answer:

- What are we trying to accomplish?
- Why does it matter?
- What is the expected outcome?

The objective should not be inferred solely from conversation history.

---

## 8. Current State

The handover should describe the state of the work at the time of
transfer.

Examples:

- Not started
- Research completed
- Architecture approved
- Implementation in progress
- Implementation complete
- Verification failed
- Ready for release

The receiving role should be able to determine what has already
happened.

---

## 9. Requirements

Relevant requirements should be explicitly identified.

These may include:

- Functional requirements
- Non-functional requirements
- Acceptance criteria
- Constraints
- Business requirements
- Security requirements

Requirements should reference their authoritative source when one
exists.

---

## 10. Decisions

Important decisions made during the work should be recorded.

A decision should distinguish between:

- Approved decision
- Recommendation
- Assumption
- Open question

### Rule

> **A recommendation must never silently become a decision.**

---

## 11. Constraints

Handoffs should identify relevant constraints.

Examples:

- Technology
- Hardware
- Budget
- Security
- Compatibility
- Time
- Existing architecture
- Vendor limitations
- Project policy

Constraints should be explicit because hidden constraints are a common
source of incorrect AI decisions.

---

## 12. Relevant Files and Artifacts

A handover should identify relevant artifacts.

Examples:

```text
Repository files
Documentation
ADRs
Issue references
Test reports
Architecture diagrams
Configuration
Research reports
Deployment records
```

The receiving role should not need to search the entire repository
without guidance.

---

## 13. Changes Made

When implementation or modification has occurred, the handover should
identify:

- Files changed
- Major changes
- New files
- Deleted files
- Configuration changes
- Dependencies added or removed

Where Git is used, the relevant commit or branch should be identified
when practical.

---

## 14. Evidence

Important claims should be supported by evidence.

Evidence may include:

- Test results
- Build results
- Screenshots
- Logs
- Research sources
- Review findings
- Deployment results
- Measurements

AI should distinguish evidence from inference.

---

## 15. Known Issues

Known problems must not be hidden during handover.

Each important issue should identify, where possible:

- Problem
- Impact
- Severity
- Current status
- Workaround
- Recommended next step

---

## 16. Open Questions

Unresolved questions should be explicitly listed.

Examples:

```text
Open question:
Should the API remain backward compatible?

Status:
Requires human decision.

Impact:
May affect architecture.
```

Open questions should not be silently resolved by the receiving AI when
they require authority outside its role.

---

## 17. Expected Next Action

Every handover should identify what the receiving role is expected to
do next.

Examples:

- Review architecture
- Implement feature
- Run tests
- Investigate defect
- Update documentation
- Prepare deployment
- Request human approval

This prevents handovers from becoming ambiguous task dumps.

---

## 18. Verification Status

A handover should identify the current verification state.

Possible states include:

```text
Not Verified
Partially Verified
Verified
Verification Failed
Verification Blocked
Verification Not Required
```

Verification status must not be overstated.

---

## 19. Handover Confidence

Where uncertainty exists, the sender should indicate confidence.

A simple classification may be:

```text
High Confidence
Medium Confidence
Low Confidence
Unknown
```

Confidence should reflect evidence quality rather than AI confidence
language alone.

---

## 20. Handover Types

AIOS recognizes several common handover types.

### Requirements Handover

Requirements → Architecture

### Architecture Handover

Architecture → Implementation

### Implementation Handover

Implementation → Verification

### Verification Handover

Verification → Documentation / Operations

### Security Handover

Security → Decision Maker / Implementation

### Release Handover

Verification → Operations & Release

### Recovery Handover

Failed role → Replacement role

---

## 21. Handover Format

For routine engineering work, the following format is recommended:

```text
# Handover

## Objective

## Current State

## Requirements

## Decisions

## Constraints

## Relevant Files

## Changes Made

## Evidence

## Known Issues

## Open Questions

## Expected Next Action

## Verification Status

## Confidence
```

Projects may extend this format where necessary.

---

## 22. Handover Validation

Before transferring work, the sending role should verify that:

- The objective is clear
- Important decisions are recorded
- Relevant files are identified
- Known issues are disclosed
- Verification status is accurate
- Open questions are identified
- The next action is clear

For high-risk work, the handover should receive explicit review.

---

## 23. Receiving Role Validation

The receiving role should not blindly trust a handover.

It should:

1. Read the handover.
2. Confirm the objective.
3. Verify critical assumptions.
4. Inspect relevant artifacts.
5. Identify missing context.
6. Ask questions where necessary.
7. Accept or reject the handover.

### Principle

> **A handover is an input, not an unquestionable source of truth.**

---

## 24. Handover Rejection

A receiving role should reject or pause a handover when:

- Required information is missing
- Requirements conflict
- Critical evidence is absent
- Authority is unclear
- Security concerns exist
- The expected action exceeds role authority
- The state described does not match the repository or system

The receiving role should clearly explain what is missing.

---

## 25. Multi-AI Collaboration

Multiple AI systems may collaborate through shared artifacts.

Example:

```text
AI Researcher
      ↓
Research Report
      ↓
AI Architect
      ↓
Architecture Proposal
      ↓
AI Implementer
      ↓
Code + Tests
      ↓
AI Reviewer
      ↓
Review Report
```

The collaboration does not require the AI systems to share the same
conversation.

---

## 26. Context Minimization

AI systems should receive the minimum context necessary to perform
their role effectively.

Avoid unnecessarily exposing:

- Sensitive information
- Secrets
- Unrelated project data
- Personal information
- Irrelevant repository content

Context minimization improves both security and reasoning quality.

---

## 27. Conversation-to-Artifact Rule

Important decisions discovered during conversations should be converted
into durable artifacts when they affect future engineering work.

Examples:

```text
Conversation
    ↓
Decision
    ↓
ADR / Requirement / Standard / Issue
```

The conversation itself should not become the only authoritative record.

---

## 28. Collaboration Failure Handling

When collaboration fails:

1. Preserve the available work.
2. Record the failure.
3. Identify missing context.
4. Identify whether the failure was caused by:
   - Role ambiguity
   - Missing information
   - Incorrect assumptions
   - Tool limitations
   - Permission limitations
   - Process failure
5. Repair the handover.
6. Reassign or retry the work.
7. Capture lessons learned when appropriate.

Repeated handover failures should trigger process improvement.

---

## 29. Handover and AIOS Memory

AIOS organizational memory should be built from durable engineering
artifacts rather than raw conversation history.

Useful memory artifacts include:

- Requirements
- ADRs
- Research
- Handover records
- Review reports
- Test results
- Lessons learned
- Release records

This allows new AI systems to join an existing project without
requiring access to every previous conversation.

---

## 30. Core Collaboration Principle

AIOS collaboration exists to allow engineering work to move safely
between humans, AI roles, tools, and projects.

A successful collaboration system preserves:

- Intent
- Context
- Decisions
- Evidence
- Responsibility
- Authority
- Verification state

without requiring participants to share the same conversation.

> **Pass the context, preserve the evidence, make the responsibility
> clear, and never make the next AI reconstruct the past.**
