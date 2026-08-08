# AIOS — Engineering Lifecycle Standard

**Version:** 1.0  
**Status:** Approved  
**Document Type:** Engineering Standard  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS Engineering Lifecycle Standard defines the canonical process for
planning, designing, implementing, verifying, releasing, and improving
engineering work.

The lifecycle provides a common operating model that can be reused
across AIOS-enabled projects.

It defines:

- Lifecycle stages
- Responsibilities
- Required artifacts
- Entry and exit criteria
- Human decision points
- AI participation
- Verification
- Risk-based tailoring
- Feedback loops
- Definition of Ready
- Definition of Done

---

## 2. Lifecycle Philosophy

AIOS uses a controlled, iterative engineering lifecycle.

The lifecycle is not a rigid waterfall process.

Engineering work may move backward when new information, defects,
constraints, or risks are discovered.

### Core principles

- Intent precedes implementation.
- Architecture precedes significant implementation.
- Verification follows implementation.
- Evidence supports important claims.
- Documentation preserves engineering context.
- Risk determines process depth.
- Human accountability remains throughout the lifecycle.

---

## 3. Lifecycle Overview

The canonical lifecycle is:

```text
Human Intent
     ↓
Discovery
     ↓
Requirements
     ↓
Research
     ↓
Architecture
     ↓
Planning
     ↓
Implementation
     ↓
Verification
     ↓
Review
     ↓
Release
     ↓
Operations
     ↓
Learning & Feedback
     ↓
Next Cycle
```

Not every task requires every stage.

The required stages depend on scope, complexity, risk, and reversibility.

---

## 4. Human Intent

Every meaningful engineering change begins with an understood objective.

Human intent may originate from:

- Business objectives
- Product requirements
- User needs
- Defects
- Operational problems
- Technical improvements
- Security requirements
- Strategic decisions

AI may help interpret intent but must not silently redefine it.

### Entry condition

A meaningful objective exists.

### Exit condition

The objective is sufficiently understood to begin discovery or
requirements analysis.

---

## 5. Discovery

Discovery establishes the current state before engineering decisions are
made.

Activities may include:

- Repository inspection
- Existing documentation review
- System inspection
- Dependency inspection
- Existing behavior analysis
- Constraint identification
- Stakeholder clarification

Discovery should prevent premature implementation.

### Output

A clear understanding of:

- Current state
- Desired state
- Relevant constraints
- Existing architecture
- Known risks
- Missing information

---

## 6. Requirements

Requirements translate intent into testable engineering expectations.

Requirements may include:

- Functional requirements
- Non-functional requirements
- Acceptance criteria
- Security requirements
- Performance requirements
- Compatibility requirements
- Operational requirements

Requirements should distinguish:

- Confirmed requirements
- Assumptions
- Open questions
- Constraints

### Exit condition

The work has sufficient requirements to proceed safely.

---

## 7. Research

Research provides evidence required for technical decisions.

Research may include:

- Technology evaluation
- Official documentation review
- Compatibility analysis
- Feasibility testing
- Security research
- Cost analysis
- Alternative comparison

Research should be proportional to the uncertainty and risk of the
decision.

### Output

Research findings should identify:

- Evidence
- Sources
- Alternatives
- Risks
- Recommendation
- Remaining uncertainty

---

## 8. Architecture

Architecture defines the technical structure required to satisfy the
approved requirements.

Architecture may include:

- Components
- Interfaces
- Data flows
- Dependencies
- Technology choices
- Security boundaries
- Integration patterns
- Operational considerations

Significant architectural decisions should be recorded as durable
engineering artifacts.

### Exit condition

The technical approach is sufficiently defined for implementation.

Major architectural decisions requiring human approval must be approved
before implementation proceeds.

---

## 9. Planning

Planning converts approved requirements and architecture into an
implementable sequence of work.

Planning may define:

- Tasks
- Dependencies
- Implementation order
- Verification strategy
- Risks
- Rollback considerations
- Documentation requirements

Planning should not introduce major architectural decisions that have
not been reviewed.

---

## 10. Implementation

Implementation converts approved plans and designs into working
engineering artifacts.

Activities may include:

- Coding
- Configuration
- Refactoring
- Test creation
- Integration
- Documentation updates

Implementation must remain within:

- Approved scope
- Architecture
- Security boundaries
- Repository governance
- Assigned permissions

Unexpected architectural or scope problems should be escalated rather
than silently absorbed.

---

## 11. Verification

Verification evaluates whether the implementation satisfies its intended
requirements.

Verification may include:

- Automated tests
- Manual tests
- Code review
- Static analysis
- Integration tests
- Regression tests
- Security checks
- Performance checks

Verification must be supported by appropriate evidence.

### Principle

> **Working code is not sufficient evidence of correctness.**

---

## 12. Review

Review evaluates engineering work before release or completion.

Review may examine:

- Requirements
- Architecture
- Implementation
- Tests
- Security
- Documentation
- Operational readiness

Review depth should be proportional to risk.

Higher-risk work should receive stronger independent review.

---

## 13. Release

Release makes validated engineering work available to its intended
environment.

Release activities may include:

- Build
- Packaging
- Deployment
- Configuration
- Publishing
- Release notes
- Approval

Production release requires appropriate authorization.

Verification status must be known before release.

---

## 14. Operations

Operations confirms that released work behaves correctly in its intended
environment.

Activities may include:

- Monitoring
- Health checks
- Log inspection
- Performance observation
- User-impact assessment
- Incident detection
- Rollback

Operational verification is part of the engineering lifecycle rather
than an activity outside engineering.

---

## 15. Learning & Feedback

The lifecycle does not end at release.

Engineering teams should capture:

- Lessons learned
- Defects
- Operational findings
- Process weaknesses
- Architecture improvements
- Documentation gaps
- Tool performance

Important learning should become durable engineering knowledge.

---

## 16. Lifecycle Artifacts

The lifecycle should produce appropriate durable artifacts.

Examples include:

```text
Requirements
Research Reports
Architecture Documents
ADRs
Plans
Source Code
Tests
Review Reports
Security Findings
Release Records
Operational Records
Lessons Learned
```

Not every task requires every artifact.

Artifact requirements should be proportional to risk and complexity.

---

## 17. Entry Criteria

Each lifecycle stage should have sufficient information to begin.

Examples:

### Requirements

Intent is sufficiently understood.

### Research

A specific research question exists.

### Architecture

Requirements are sufficiently defined.

### Implementation

Architecture and scope are sufficiently clear.

### Verification

Implementation is complete enough to test.

### Release

Required verification and approvals are complete.

A stage should not begin merely because the previous conversation
ended.

---

## 18. Exit Criteria

A lifecycle stage is complete only when its required outputs exist.

Examples:

### Requirements

Acceptance criteria are defined.

### Architecture

Required design decisions are documented.

### Implementation

The intended change is implemented and locally verified.

### Verification

Required tests and reviews are complete.

### Release

The authorized release has been successfully executed.

### Operations

Post-release state is known.

Exit criteria may be tailored by risk.

---

## 19. Risk-Based Tailoring

AIOS does not require identical process depth for every task.

Work should be classified according to factors such as:

- Impact
- Complexity
- Reversibility
- Security sensitivity
- Production exposure
- Data sensitivity
- Business consequence

### Low Risk

May use:

```text
Intent
  ↓
Implementation
  ↓
Basic Verification
```

### Medium Risk

May use:

```text
Intent
  ↓
Requirements
  ↓
Architecture
  ↓
Implementation
  ↓
Verification
  ↓
Documentation
```

### High Risk

May use:

```text
Intent
  ↓
Requirements
  ↓
Research
  ↓
Architecture
  ↓
Independent Review
  ↓
Human Approval
  ↓
Implementation
  ↓
Independent Verification
  ↓
Security Review
  ↓
Human Release Approval
  ↓
Operations
```

---

## 20. Definition of Ready

A work item is **Ready** when sufficient information exists for the
assigned role to begin safely.

Depending on risk, this may require:

- Clear objective
- Defined scope
- Requirements
- Acceptance criteria
- Relevant context
- Known constraints
- Appropriate authority
- Identified dependencies
- Verification expectations

A work item should not be marked Ready simply because someone wants to
start implementation.

---

## 21. Definition of Done

A work item is **Done** when its required lifecycle obligations have
been satisfied.

Depending on risk, this may include:

```text
Requirement satisfied
        ↓
Implementation complete
        ↓
Tests completed
        ↓
Review completed
        ↓
Security considerations addressed
        ↓
Documentation updated
        ↓
Changes recorded
        ↓
Release status known
```

Done is risk-adjustable.

A documentation correction and a production database migration do not
require identical completion criteria.

---

## 22. Change Loops

AIOS supports controlled backward movement through the lifecycle.

Examples:

```text
Implementation
      ↓
Verification
      ↓
Architecture problem
      ↓
Architecture
      ↓
Implementation
```

Or:

```text
Research
   ↓
New evidence
   ↓
Requirements reconsidered
   ↓
Human decision
   ↓
Architecture
```

Backward movement is not failure.

It is a normal engineering response to new information.

---

## 23. Emergency Changes

Emergency changes may bypass portions of the normal lifecycle when
necessary to protect:

- Users
- Security
- Availability
- Data
- Critical business operations

Emergency changes must still have:

- Explicit reason
- Appropriate authorization
- Minimal necessary scope
- Verification where possible
- Post-change review
- Documentation

Emergency status must not become a permanent shortcut around governance.

---

## 24. AI Participation

AI may participate in any lifecycle stage where its role, authority,
permissions, and risk level permit.

Examples:

```text
Research AI
    → Research

Architecture AI
    → Architecture

Implementation AI
    → Coding

Verification AI
    → Testing / Review

Documentation AI
    → Knowledge capture
```

One AI may perform multiple roles.

Multiple AIs may collaborate on one stage.

The role and authority rules remain applicable regardless of the tool.

---

## 25. Human Decision Points

Human involvement is required where decisions exceed delegated AI
authority.

Typical human decision points include:

- Business objectives
- Major scope changes
- Significant architecture
- Significant security risk
- Financial commitments
- Irreversible actions
- Production risk
- Governance changes
- High-impact releases

AI may prepare decisions and recommendations.

Human accountability remains.

---

## 26. Lifecycle Evidence

Important lifecycle claims should be supported by evidence.

Examples:

```text
Requirement satisfied
    → Acceptance test

Build successful
    → Build result

Security reviewed
    → Security report

Deployment successful
    → Deployment result

Production healthy
    → Operational verification
```

Statements such as "it works" should not substitute for appropriate
evidence.

---

## 27. Lifecycle Handover

When responsibility changes between roles, the AIOS Collaboration &
Handover Standard applies.

A handover should preserve:

- Objective
- Current state
- Requirements
- Decisions
- Constraints
- Changes
- Evidence
- Known issues
- Open questions
- Expected next action
- Verification status

The receiving role should validate critical information rather than
blindly trusting the handover.

---

## 28. Continuous Improvement

AIOS engineering processes should improve based on evidence.

Improvement may result from:

- Repeated defects
- Handover failures
- Release incidents
- Excessive rework
- Tool limitations
- Automation failures
- Documentation gaps
- New engineering capabilities

Process changes should be documented and governed appropriately.

---

## 29. Lifecycle Governance

The Engineering Lifecycle Standard operates under the AIOS Repository
Constitution and related governance documents.

The lifecycle must remain consistent with:

- AIOS Vision
- AIOS Guiding Principles
- AIOS Repository Constitution
- AI Organization Model
- AI Role Definitions
- AI Authority & Permission Model
- AI Collaboration & Handover Standard

Project-specific processes may be stricter.

They should not weaken higher-level AIOS governance without an approved
exception.

---

## 30. Core Lifecycle Principle

The AIOS Engineering Lifecycle exists to provide a reliable, reusable,
and risk-aware method for turning human intent into validated
engineering outcomes.

It is designed to provide enough structure for quality without creating
unnecessary bureaucracy.

The lifecycle should remain:

- Intent-driven
- Evidence-based
- Risk-aware
- Iterative
- Documented
- Verifiable
- Human-accountable

> **Move deliberately from intent to outcome, verify what was built, and
> preserve what was learned.**
