# AIOS — Verification & QA Standard

**Version:** 1.0  
**Status:** Draft  
**Document Type:** Engineering Standard  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS Verification & QA Standard defines how engineering work is
evaluated to determine whether it satisfies its intended requirements,
quality expectations, security constraints, and operational conditions.

The standard establishes:

- Verification principles
- Testing expectations
- Evidence requirements
- Review independence
- Defect handling
- Regression testing
- Risk-based QA
- Acceptance criteria
- Verification status
- Release readiness

---

## 2. Core Principle

Verification is the process of obtaining sufficient evidence that an
engineering outcome satisfies its intended requirements.

A claim is not evidence merely because an AI system makes the claim.

### Core rule

> **Do not trust the claim; verify the result.**

---

## 3. Verification vs Validation

AIOS distinguishes verification from validation.

### Verification

Asks:

> Did we build the system correctly according to the specified
> requirements?

### Validation

Asks:

> Did we build the right thing for the intended purpose?

Both may be required.

A system can pass technical verification while failing to satisfy the
actual user or business objective.

---

## 4. Quality Assurance

Quality Assurance is broader than testing.

QA includes:

- Process quality
- Requirements quality
- Architecture quality
- Implementation quality
- Verification quality
- Security quality
- Documentation quality
- Release quality

QA should improve the engineering process, not merely detect defects
after implementation.

---

## 5. Verification Scope

Verification scope should be determined by:

- Requirements
- Risk
- Change scope
- System complexity
- Security sensitivity
- Production exposure
- Reversibility
- User impact

Higher-risk changes require stronger verification.

---

## 6. Verification Levels

AIOS recognizes several verification levels.

### Level 0 — Informal Check

Examples:

- Visual inspection
- Basic review
- Simple documentation check

Appropriate for very low-risk changes.

### Level 1 — Basic Verification

Examples:

- Unit test
- Build
- Lint
- Type check
- Manual functional check

### Level 2 — Standard Verification

May include:

- Unit tests
- Integration tests
- Regression tests
- Code review
- Acceptance testing

### Level 3 — Enhanced Verification

May include:

- Independent review
- Security review
- Performance testing
- Failure-mode testing
- Deployment verification

### Level 4 — High-Assurance Verification

May be required for critical systems or high-impact changes.

May include:

- Independent verification
- Multiple evidence sources
- Security assessment
- Controlled deployment
- Rollback validation
- Production monitoring
- Explicit human approval

---

## 7. Verification Independence

Verification independence means that verification is sufficiently
separated from implementation to provide meaningful challenge.

The required level depends on risk.

### Low Risk

The implementer may perform verification.

### Medium Risk

A separate review or verification step is recommended.

### High Risk

Independent verification should normally be required.

### Critical Risk

Independent verification and explicit human oversight are required.

Independence may be achieved by:

- Different human
- Different AI role
- Different AI system
- Different test mechanism
- Separate validation process

---

## 8. AI Verification

AI systems may perform verification activities.

Examples:

- Code review
- Test generation
- Test execution
- Static analysis
- Requirement comparison
- Security review
- Documentation review

However, AI verification remains subject to the same evidence
requirements as other verification.

An AI reviewer should not simply repeat the implementer's conclusion.

---

## 9. Verification Evidence

Verification claims should be supported by evidence appropriate to
risk.

Evidence may include:

- Test results
- Build results
- Logs
- Screenshots
- Review findings
- Static-analysis results
- Security reports
- Performance measurements
- Deployment results
- Acceptance records

Evidence should be reproducible where practical.

---

## 10. Evidence Quality

Evidence should be evaluated according to:

- Relevance
- Reliability
- Completeness
- Reproducibility
- Independence
- Recency

A screenshot may prove a visual state but not necessarily prove
underlying system correctness.

A passing unit test may prove a specific behavior but not the entire
system.

Evidence must support the specific claim being made.

---

## 11. Acceptance Criteria

Verification should map to defined acceptance criteria where
available.

For each criterion:

```text
Requirement
    ↓
Verification Method
    ↓
Evidence
    ↓
Result
```

A requirement should not be considered satisfied merely because related
tests pass.

---

## 12. Test Strategy

Testing should be proportional to risk.

Possible testing levels include:

```text
Unit
  ↓
Integration
  ↓
System
  ↓
End-to-End
  ↓
Operational
```

Not every change requires every level.

The selected testing strategy should cover the relevant failure modes.

---

## 13. Unit Testing

Unit tests verify isolated behavior.

They are particularly useful for:

- Business logic
- Algorithms
- Validation
- Data transformation
- Utility functions

Unit tests should be:

- Focused
- Repeatable
- Deterministic where practical
- Understandable

Passing unit tests does not prove system-level correctness.

---

## 14. Integration Testing

Integration tests verify interactions between components.

Examples:

- API to database
- Service to service
- Application to external provider
- Authentication integration
- File-system integration

Integration testing is important when failures may occur at component
boundaries.

---

## 15. End-to-End Testing

End-to-end tests verify complete user or system workflows.

Examples:

```text
User
 ↓
Interface
 ↓
Application
 ↓
API
 ↓
Database
 ↓
Expected outcome
```

End-to-end testing should be used where system-level behavior matters.

---

## 16. Regression Testing

Regression testing determines whether existing behavior remains intact
after a change.

Regression scope should consider:

- Changed components
- Dependencies
- Shared interfaces
- Related workflows
- Historical defects

A change that passes its new feature test may still introduce a
regression elsewhere.

---

## 17. Security Verification

Security-sensitive changes require security verification.

Possible activities include:

- Authentication testing
- Authorization testing
- Input validation
- Dependency analysis
- Secret scanning
- Configuration review
- Threat analysis
- Permission verification

Security verification should be proportional to risk.

---

## 18. Performance Verification

Performance verification may be required when changes affect:

- Response time
- Throughput
- Resource usage
- Scalability
- Database performance
- Build or deployment time

Performance claims should be supported by measurements rather than
assumptions.

---

## 19. Failure Testing

Important systems should be tested against expected failure conditions.

Examples:

- Invalid input
- Network failure
- Service unavailable
- Authentication failure
- Database failure
- Missing configuration
- Partial deployment

Failure testing should be proportional to impact and risk.

---

## 20. Defect Classification

Defects should be classified according to impact.

A practical classification is:

### Low

Minor inconvenience or cosmetic issue.

### Medium

Meaningful functional problem without severe impact.

### High

Major functionality, security, or operational impact.

### Critical

Severe security, data, availability, or business impact.

Projects may define more detailed severity models.

---

## 21. Defect Lifecycle

A defect may follow:

```text
Detected
   ↓
Triaged
   ↓
Assigned
   ↓
Investigated
   ↓
Fixed
   ↓
Verified
   ↓
Closed
```

A defect should not be closed solely because a code change was made.

The correction must be verified.

---

## 22. Failed Verification

When verification fails:

1. Record the failure.
2. Identify the affected requirement.
3. Determine severity.
4. Return work to the appropriate lifecycle stage.
5. Correct the issue.
6. Re-run required verification.

Verification failure is a valid lifecycle state.

It is not something to hide in order to declare a task complete.

---

## 23. Verification Status

AIOS recognizes:

```text
Not Verified
Partially Verified
Verified
Verification Failed
Verification Blocked
Verification Not Required
```

The status must accurately represent the evidence available.

"Verified" should not be used when significant required verification
remains incomplete.

---

## 24. Verification Report

For meaningful work, a verification report should identify:

```text
Scope
Requirements Tested
Tests Performed
Results
Evidence
Defects
Limitations
Residual Risk
Verification Status
Reviewer
Date
```

The depth should be proportional to risk.

---

## 25. Independent Review

Independent review should challenge:

- Requirements
- Architecture
- Implementation
- Tests
- Security
- Evidence
- Residual risk

An independent reviewer should be willing to conclude:

```text
Pass
Fail
Pass with Conditions
Insufficient Evidence
```

Review should not become a ceremonial approval step.

---

## 26. AI Reviewer Independence

When AI is used for independent verification, the verification context
should be sufficiently separated from implementation bias.

Where practical:

- Use a different AI system
- Use a different role
- Provide the requirements independently
- Avoid giving the reviewer the implementer's conclusions first
- Require evidence-based findings

For high-risk work, AI review should not be the sole assurance mechanism.

---

## 27. Verification Handover

When implementation is handed to verification, the handover should
include:

- Objective
- Requirements
- Changes
- Relevant files
- Known risks
- Test expectations
- Existing evidence
- Known issues
- Open questions

The verification role should independently determine what additional
testing or evidence is required.

---

## 28. Residual Risk

Verification does not guarantee zero risk.

After verification, remaining uncertainty or risk should be identified.

Residual risk may include:

- Untested edge cases
- External dependency uncertainty
- Limited test coverage
- Performance uncertainty
- Operational uncertainty
- Known defects

High residual risk should be escalated before release.

---

## 29. QA Governance

Verification and QA operate under:

- AIOS Repository Constitution
- AIOS AI Organization Model
- AIOS AI Role Definitions
- AIOS AI Authority & Permission Model
- AIOS Collaboration & Handover Standard
- AIOS Engineering Lifecycle Standard
- AIOS Task & Change Management Standard
- AIOS Architecture & Decision Standard
- AIOS Implementation & Coding Standard

Project-specific QA standards may be stricter.

Verification requirements must not be weakened merely to accelerate
delivery.

---

## 30. Core Verification Principle

Verification exists to provide evidence that engineering work satisfies
its intended requirements and is sufficiently safe for its intended
use.

The purpose of QA is not to produce paperwork or positive conclusions.

It is to provide meaningful assurance.

> **Verification is evidence, not confidence; quality is demonstrated,
> not declared.**
