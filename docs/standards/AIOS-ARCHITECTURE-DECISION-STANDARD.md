# AIOS — Architecture & Decision Standard

**Version:** 1.0  
**Status:** Draft  
**Document Type:** Engineering Standard  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS Architecture & Decision Standard defines how significant
technical decisions are researched, proposed, evaluated, recorded,
approved, implemented, reviewed, and revisited.

The standard exists to ensure that architecture remains:

- Intentional
- Understandable
- Documented
- Reviewable
- Reversible where practical
- Consistent with requirements
- Independent of temporary AI conversations

It establishes a common architecture and decision process for AIOS
enabled projects.

---

## 2. Core Principle

Architecture should be a deliberate engineering activity rather than an
accidental consequence of implementation.

### Core rule

> **Implementation must not silently become architecture.**

When implementation reveals a need for architectural change, the issue
should be surfaced and handled through the appropriate decision process.

---

## 3. What Is Architecture?

Architecture is the set of significant structural decisions that shape
a system.

Architecture may include:

- System boundaries
- Components
- Interfaces
- Data flows
- Data ownership
- Major dependencies
- Deployment structure
- Security boundaries
- Integration patterns
- Technology choices
- Availability and reliability strategies

Architecture is not limited to diagrams.

---

## 4. Architectural Decision

An architectural decision is a deliberate choice between meaningful
technical alternatives that affects the structure, behavior,
maintainability, security, cost, or operation of a system.

Examples include:

- Selecting a database
- Choosing an authentication model
- Selecting a deployment platform
- Introducing a major dependency
- Defining an API boundary
- Choosing between architectural patterns
- Changing data ownership

Minor implementation choices do not necessarily require formal
architectural decisions.

---

## 5. Decision Significance

Not every technical choice requires an ADR.

A decision should normally be treated as significant when it:

- Has broad system impact
- Is difficult to reverse
- Creates long-term dependency
- Affects security
- Affects data
- Affects major interfaces
- Has meaningful cost implications
- Constrains future architecture
- Requires stakeholder or human judgment

---

## 6. Architecture Principles

AIOS architecture should generally follow these principles:

- Simplicity
- Modularity
- Clear boundaries
- Least privilege
- Explicit dependencies
- Reversibility where practical
- Security by design
- Maintainability
- Observability
- Appropriate scalability
- Minimal unnecessary complexity

Project-specific architecture principles may extend these.

---

## 7. Architecture Inputs

Architecture should be based on appropriate evidence and context.

Inputs may include:

- Requirements
- Existing architecture
- Research
- Constraints
- Security requirements
- Operational requirements
- Performance requirements
- Cost considerations
- Existing technical debt

Architecture should not be designed in isolation from the problem it
must solve.

---

## 8. Architecture Discovery

Before proposing significant architecture, the architect should inspect
the existing system.

Discovery may include:

- Repository structure
- Existing components
- Existing interfaces
- Dependencies
- Configuration
- Data flows
- Deployment model
- Existing ADRs
- Existing constraints

The goal is to avoid designing against an incorrect understanding of
the current system.

---

## 9. Architecture Research

Architecture decisions should use research when uncertainty exists.

Research may evaluate:

- Technology capabilities
- Compatibility
- Performance
- Security
- Cost
- Operational complexity
- Vendor dependency
- Long-term maintainability

Important claims should be supported by appropriate evidence.

---

## 10. Options Analysis

Significant decisions should consider reasonable alternatives.

An options analysis should identify:

- Option
- Advantages
- Disadvantages
- Risks
- Cost
- Complexity
- Reversibility
- Long-term implications

The purpose is not to enumerate every theoretical possibility.

The purpose is to demonstrate that meaningful alternatives were
considered.

---

## 11. Trade-Off Analysis

Architecture is fundamentally about trade-offs.

Common trade-offs include:

- Simplicity vs flexibility
- Cost vs capability
- Performance vs maintainability
- Speed vs robustness
- Vendor convenience vs portability
- Security vs operational convenience
- Scalability vs complexity

Trade-offs should be made explicit rather than hidden inside
implementation details.

---

## 12. Architecture Proposal

A significant architecture proposal should normally contain:

```text
Problem
Context
Requirements
Constraints
Current State
Proposed Architecture
Alternatives
Trade-offs
Risks
Migration Considerations
Verification Approach
Recommendation
```

The proposal is not automatically a decision.

---

## 13. Human Decision Point

Significant architectural decisions require appropriate human
authority.

AI may:

- Research
- Analyze
- Design
- Compare options
- Recommend

AI does not automatically acquire authority to make significant
architectural decisions.

### Principle

> **AI may design the option; authorized humans decide the architecture.**

---

## 14. Architecture Decision Record

Significant architectural decisions should be recorded in an
Architecture Decision Record (ADR).

An ADR should preserve:

- Context
- Decision
- Alternatives
- Consequences
- Status

The ADR becomes part of the project's durable engineering knowledge.

---

## 15. ADR Structure

A recommended ADR structure is:

```text
# ADR-XXXX — Title

Status:

Date:

Decision Makers:

## Context

## Problem

## Decision

## Alternatives Considered

## Trade-offs

## Consequences

## Risks

## Verification

## Related Decisions
```

Projects may extend this structure.

---

## 16. ADR Status

AIOS recommends the following ADR states:

```text
Proposed
    ↓
Accepted
    ↓
Superseded
```

Additional states may include:

```text
Rejected
Deprecated
Withdrawn
```

The status should reflect the current authority of the decision.

---

## 17. Proposed Decision

A proposed ADR represents a decision under consideration.

It may be reviewed and challenged.

It must not be treated as authoritative until appropriately accepted.

AI-generated architecture proposals should normally remain Proposed
until reviewed.

---

## 18. Accepted Decision

An Accepted ADR represents the authoritative architectural decision for
its scope.

Implementation should follow the accepted decision unless an approved
change occurs.

If implementation discovers that an accepted decision cannot safely be
implemented, the issue should be escalated.

---

## 19. Superseded Decision

An ADR becomes Superseded when a later decision replaces it.

The original ADR should normally remain available for historical
context.

The new ADR should reference the superseded decision.

Historical architecture knowledge should not be silently deleted.

---

## 20. Architecture Change

Changing an accepted architectural decision should normally require:

1. Identify the existing decision.
2. Explain why it is insufficient.
3. Research alternatives.
4. Assess consequences.
5. Propose the new decision.
6. Obtain appropriate approval.
7. Record the new ADR.
8. Plan migration.
9. Implement.
10. Verify.

The required depth depends on risk.

---

## 21. Architecture and Implementation Boundary

Implementation operates within approved architecture.

An implementation agent may identify:

- Missing architectural detail
- Contradictions
- Technical impossibility
- Unexpected constraints
- Better alternatives

It should not silently change significant architecture.

The correct response is:

```text
Implementation discovers architecture problem
                    ↓
                Escalate
                    ↓
            Architecture review
                    ↓
              New decision
                    ↓
             Updated ADR
                    ↓
              Implementation
```

---

## 22. Architecture Exceptions

An implementation may require a temporary deviation from approved
architecture.

A temporary exception should identify:

- Reason
- Scope
- Risk
- Duration
- Owner
- Follow-up action

Temporary exceptions should not silently become permanent architecture.

---

## 23. Architecture Debt

Architecture debt is a known architectural compromise that creates
future cost, risk, or complexity.

Examples:

- Temporary integration
- Legacy dependency
- Duplicated service boundary
- Known scalability limitation
- Deferred migration

Architecture debt should be documented when significant.

---

## 24. Reversibility

Architecture decisions should consider reversibility.

A decision is more risky when it is:

- Difficult to undo
- Expensive to replace
- Data-destructive
- Vendor-locking
- Widely distributed
- Security-sensitive

When two options provide similar value, the more reversible option may
be preferable.

Reversibility is a factor, not an absolute rule.

---

## 25. Architecture Verification

Architecture should be verified before significant implementation where
appropriate.

Verification may include:

- Prototype
- Proof of concept
- Compatibility test
- Performance test
- Security analysis
- Failure-mode analysis
- Deployment test

High-risk architecture should not rely solely on theoretical reasoning.

---

## 26. Architecture Review

Architecture review should evaluate:

- Requirement alignment
- Simplicity
- Security
- Maintainability
- Dependencies
- Operational impact
- Cost
- Reversibility
- Long-term consequences

Review should be independent enough to identify weaknesses.

The required independence depends on risk.

---

## 27. Architecture Documentation

Authoritative architecture should be represented through durable
artifacts.

These may include:

- Architecture overview
- Architecture diagrams
- ADRs
- Interface documentation
- Data-flow documentation
- Deployment documentation
- Security architecture

Documentation should reflect the current accepted architecture.

---

## 28. Architecture and AIOS

AIOS architecture governance applies to the AIOS platform itself.

AIOS architecture changes should follow the same principles:

- Explicit proposal
- Appropriate research
- Trade-off analysis
- Human decision
- Durable documentation
- Verification

AIEP implementations must remain consistent with approved AIOS
architecture.

---

## 29. Architecture Governance

Architecture decisions operate under:

- AIOS Vision
- AIOS Guiding Principles
- AIOS Repository Constitution
- AI Organization Model
- AI Role Definitions
- AI Authority & Permission Model
- AI Collaboration & Handover Standard
- AIOS Engineering Lifecycle Standard
- AIOS Task & Change Management Standard

Project-specific architecture standards may be stricter.

Significant exceptions should be explicitly documented.

---

## 30. Core Architecture Principle

Architecture exists to make significant technical decisions explicit,
understandable, reviewable, and maintainable over time.

AI may research, analyze, design, and recommend.

Humans retain authority over significant architectural decisions.

> **Make important technical decisions deliberately, record why they
> were made, and never let architecture emerge accidentally from code.**
