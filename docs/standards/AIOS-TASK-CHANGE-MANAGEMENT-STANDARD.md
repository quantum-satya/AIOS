# AIOS — Task & Change Management Standard

**Version:** 1.0  
**Status:** Draft  
**Document Type:** Engineering Standard  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS Task & Change Management Standard defines how engineering
work is identified, classified, planned, executed, tracked, reviewed,
and completed.

The standard provides a consistent way to manage engineering work across
AIOS-enabled projects while allowing process depth to remain
proportional to risk.

It defines:

- Work item types
- Change classification
- Risk classification
- Scope
- Priority
- Required artifacts
- Approval requirements
- Change lifecycle
- Emergency changes
- Completion criteria

---

## 2. Core Principle

Every meaningful engineering action should have an understood purpose,
scope, and appropriate level of control.

AIOS does not require identical process for every task.

### Core rule

> **Classify the work before deciding how much process it requires.**

---

## 3. Work Item Definition

A work item is a bounded unit of engineering activity with a defined
objective and expected outcome.

A work item may be:

- A feature
- A bug fix
- An enhancement
- A refactor
- A documentation change
- A research task
- An architecture change
- A security change
- A maintenance task
- An operational task
- An emergency change

A work item may contain smaller tasks.

---

## 4. Work Type

AIOS distinguishes work according to its primary purpose.

The primary work types are:

1. Feature
2. Bug Fix
3. Enhancement
4. Refactor
5. Documentation
6. Research
7. Architecture Change
8. Security Change
9. Maintenance
10. Operational Change
11. Emergency Change

The work type describes **what kind of work it is**.

It does not by itself determine risk.

---

## 5. Feature

A feature introduces new user-visible or system capability.

Examples:

- New website functionality
- New API capability
- New workflow
- New application component
- New business capability

Features normally require:

- Requirements
- Acceptance criteria
- Appropriate design
- Implementation
- Verification

Process depth depends on risk.

---

## 6. Bug Fix

A bug fix corrects behavior that does not meet an existing requirement
or expected behavior.

Examples:

- Incorrect calculation
- Broken UI behavior
- Failed integration
- Regression
- Incorrect validation

Bug fixes should identify:

- Observed behavior
- Expected behavior
- Root cause where practical
- Correction
- Verification

A bug fix may become a larger change if the underlying architecture
requires modification.

---

## 7. Enhancement

An enhancement improves an existing capability without introducing a
fundamentally new capability.

Examples:

- Improve usability
- Improve performance
- Improve accessibility
- Improve error handling
- Improve maintainability

Enhancements should still have a clear expected outcome.

---

## 8. Refactor

A refactor changes internal implementation without intentionally
changing externally expected behavior.

Examples:

- Code restructuring
- Removing duplication
- Improving naming
- Simplifying architecture
- Improving maintainability

Refactoring must preserve required behavior unless a behavior change is
explicitly part of the work.

Large refactors may require architecture review.

---

## 9. Documentation Change

A documentation change modifies engineering knowledge without directly
changing software behavior.

Examples:

- README update
- Architecture documentation
- SOP
- ADR
- API documentation
- User documentation
- Knowledge-base update

Documentation changes should still preserve authoritative information.

---

## 10. Research Task

A research task exists to reduce uncertainty before a decision or
implementation.

Examples:

- Evaluate a technology
- Compare vendors
- Test compatibility
- Investigate an error
- Evaluate AI tools

Research should produce evidence and recommendations rather than
unbounded exploration.

---

## 11. Architecture Change

An architecture change modifies the technical structure or major
boundaries of a system.

Examples:

- Changing deployment architecture
- Replacing a major dependency
- Changing data architecture
- Introducing a new integration boundary
- Changing authentication architecture

Architecture changes normally require:

- Explicit scope
- Architecture analysis
- Risk assessment
- ADR where appropriate
- Appropriate human approval

---

## 12. Security Change

A security change modifies security controls, authentication,
authorization, secrets handling, data protection, or security-sensitive
infrastructure.

Examples:

- Authentication changes
- Permission changes
- Secret-management changes
- Security configuration
- Dependency security remediation

Security changes require appropriate security review.

---

## 13. Maintenance

Maintenance keeps systems healthy without introducing significant new
capability.

Examples:

- Dependency updates
- Routine cleanup
- Configuration maintenance
- Tool updates
- Repository housekeeping

Maintenance still requires verification proportional to risk.

---

## 14. Operational Change

An operational change modifies the way a system is built, deployed,
monitored, or operated.

Examples:

- CI/CD changes
- Deployment configuration
- Monitoring changes
- Infrastructure configuration
- Environment changes

Operational changes should consider rollback and operational impact.

---

## 15. Emergency Change

An emergency change is required to respond to an urgent threat or
failure affecting:

- Security
- Availability
- Data
- Users
- Critical business operations

Emergency classification changes the process sequence, not the
governance requirement.

Emergency work should remain:

- Authorized
- Bounded
- Documented
- Verified where possible
- Reviewed afterward

---

## 16. Risk Classification

AIOS uses four risk levels.

### Low Risk

Limited impact, easily reversible, and unlikely to affect security or
production.

Examples:

- Typo correction
- Documentation formatting
- Local refactor
- Non-production test adjustment

### Medium Risk

Meaningful technical or user impact but generally reversible.

Examples:

- Feature implementation
- Dependency update
- Significant refactor
- CI change

### High Risk

Potential significant impact to security, production, architecture, or
business operations.

Examples:

- Authentication changes
- Major architecture changes
- Production deployment changes
- Sensitive data handling

### Critical Risk

Potential severe or irreversible impact.

Examples:

- Destructive production migration
- Critical credential changes
- Major security boundary changes
- Irreversible data operations

---

## 17. Risk Factors

Risk should consider multiple dimensions.

### Impact

What happens if the change fails?

### Scope

How much of the system is affected?

### Reversibility

Can the change be safely undone?

### Security

Does the change affect security or sensitive data?

### Production Exposure

Does it affect production?

### Dependency

Does it affect critical external dependencies?

### Business Impact

Could failure materially affect the business?

The highest relevant factor should influence the final risk level.

---

## 18. Priority

Priority describes how urgently work should be addressed.

AIOS distinguishes priority from risk.

A change may be:

```text
High Risk + Low Priority
```

or:

```text
Low Risk + High Priority
```

Priority should consider:

- User impact
- Business impact
- Security
- Deadlines
- Dependencies
- Operational urgency

Priority does not override required safety controls.

---

## 19. Scope

Every work item should have a defined scope.

Scope should identify:

- Included work
- Excluded work
- Affected systems
- Affected files or components where known
- Expected outcome

Scope expansion should be explicit.

An AI should not silently expand the scope because it believes
additional changes would be useful.

---

## 20. Change Lifecycle

A standard work item follows:

```text
Identify
   ↓
Classify
   ↓
Define Scope
   ↓
Assess Risk
   ↓
Plan
   ↓
Authorize
   ↓
Execute
   ↓
Verify
   ↓
Document
   ↓
Close
```

Not every work item requires identical artifacts.

---

## 21. Work Item States

AIOS recommends the following states:

```text
Proposed
   ↓
Triaged
   ↓
Ready
   ↓
In Progress
   ↓
Verification
   ↓
Approved
   ↓
Released
   ↓
Closed
```

Additional states may include:

```text
Blocked
Deferred
Rejected
Cancelled
Emergency
```

Projects may adapt the terminology while preserving the underlying
meaning.

---

## 22. Definition of Ready

A work item is Ready when:

- Objective is understood
- Scope is sufficiently defined
- Required context exists
- Risk is assessed
- Required authority is identified
- Dependencies are understood
- Acceptance criteria exist where appropriate

High-risk work requires stronger readiness evidence.

---

## 23. Definition of Done

A work item is Done when:

- Intended work is complete
- Required verification is complete
- Known issues are documented
- Required documentation is updated
- Required approvals exist
- Release state is known
- No unresolved blocking condition remains

Done criteria should be proportional to risk.

---

## 24. Change Approval

Approval requirements depend on risk.

### Low Risk

May be executed within delegated authority.

### Medium Risk

May require review before completion or release.

### High Risk

Normally requires explicit human approval at appropriate decision
points.

### Critical Risk

Requires explicit human authorization and enhanced verification.

AI may recommend approval.

AI does not acquire approval authority merely because it prepared the
work.

---

## 25. AI Participation

AI may assist with:

- Classification
- Research
- Planning
- Implementation
- Testing
- Documentation
- Review

AI must remain within its assigned role and authority.

AI should not classify a change in a lower-risk category merely to avoid
required controls.

---

## 26. Change Dependencies

Work items should identify meaningful dependencies.

Dependencies may include:

- Other tasks
- Architecture decisions
- External services
- Libraries
- Credentials
- Infrastructure
- Human approvals
- Business decisions

A blocked dependency should be recorded rather than hidden.

---

## 27. Change Evidence

Important changes should retain evidence appropriate to risk.

Evidence may include:

- Requirements
- Tests
- Review results
- Security findings
- Git commits
- Deployment records
- Screenshots
- Logs
- Approval records

The evidence should allow a qualified reviewer to understand what
happened.

---

## 28. Change Cancellation and Rollback

A work item may be cancelled when:

- Requirements change
- The work is no longer valuable
- Risk becomes unacceptable
- A better solution replaces it

A released change may require rollback when:

- It causes unacceptable impact
- Verification fails
- Security risk is discovered
- Operational stability is threatened

Rollback procedures should be considered for higher-risk changes before
execution.

---

## 29. Change Governance

Task and change management operates under the AIOS Engineering
Lifecycle Standard and higher-level AIOS governance.

Project-specific standards may be stricter.

Changes to:

- AIOS governance
- Security boundaries
- Authority models
- Production controls

must follow the applicable governance requirements.

---

## 30. Core Task & Change Principle

AIOS task and change management exists to make engineering work
understandable, bounded, traceable, and appropriately controlled.

The system should provide enough structure to manage risk without
creating unnecessary bureaucracy.

> **Classify the work, understand the risk, control the change, and leave
> evidence of what was done.**
