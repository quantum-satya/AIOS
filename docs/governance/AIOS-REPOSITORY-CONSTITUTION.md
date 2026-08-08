# AIOS — Repository Constitution

**Version:** 1.0  
**Status:** Approved  
**Document Type:** Repository Governance  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS Repository Constitution defines the mandatory governance rules
for the AIOS repository.

It translates the AIOS Vision and Guiding Principles into operational
rules for repository structure, documentation, changes, AI
collaboration, version control, security, and maintenance.

The Constitution is the highest-level operational governance document
within the AIOS repository.

---

## 2. Governance Hierarchy

AIOS follows this hierarchy:

```text
AIOS Vision
      ↓
AIOS Guiding Principles
      ↓
Repository Constitution
      ↓
Standards
      ↓
Workflows
      ↓
Implementation
```

Lower-level documents must not intentionally contradict higher-level
governance.

Where a conflict exists, the higher-level document takes precedence
until the conflict is formally resolved.

---

## 3. Human Authority

The designated human owner of AIOS retains final authority over:

- AIOS Vision
- Guiding Principles
- Repository Constitution
- Governance changes
- Architecture decisions
- Security policy
- Tooling policy
- Major structural changes
- Release decisions

AI systems may propose changes but may not independently establish
governance.

### Rule

> **AI may recommend governance; humans approve governance.**

---

## 4. AI-Assisted Repository Changes

AI may be used extensively within the AIOS repository.

AI may:

- Create documentation
- Propose architecture
- Write code
- Analyze changes
- Review changes
- Generate tests
- Research alternatives
- Identify inconsistencies
- Suggest improvements

However, AI-generated changes remain subject to normal repository
governance.

AI must not bypass review requirements merely because it generated the
change.

---

## 5. Protected Governance Areas

The following areas are considered governance-sensitive:

- Vision
- Guiding Principles
- Constitution
- Standards
- Security policies
- AI role definitions
- AI authority boundaries
- Repository architecture
- Tooling governance

Changes to these areas require explicit human approval.

AI agents must not autonomously modify these areas and commit the
changes without human authorization.

---

## 6. Documentation-First Rule

Significant changes must begin with sufficient documentation of intent.

Depending on the change, this may include:

- Requirement
- Design note
- Architecture document
- ADR
- Sprint plan
- Issue
- Change proposal

The required level of documentation must be proportional to the risk
and complexity of the change.

---

## 7. Repository Structure

The AIOS repository maintains a clear separation between:

```text
docs/
prompts/
scripts/
examples/
.github/
```

### `docs/`

Authoritative AIOS documentation.

### `prompts/`

Reusable AI prompts and prompt-related assets.

### `scripts/`

Engineering automation and utility scripts.

### `examples/`

Reference implementations and demonstrations.

### `.github/`

GitHub-specific repository configuration and automation.

New top-level directories should not be created without a documented
reason.

---

## 8. Single Source of Truth

Every authoritative piece of information must have a defined canonical
location.

Duplicated information should be minimized.

If the same information must appear in multiple locations, one location
must be explicitly identified as authoritative.

---

## 9. Change Classification

AIOS changes should be classified according to their impact.

### Class A — Routine

Examples:

- Typographical corrections
- Formatting improvements
- Broken links
- Minor documentation clarification

Normal review is sufficient.

### Class B — Engineering

Examples:

- New workflow
- New template
- New script
- Engineering standard update
- Prompt library changes

Requires review against applicable standards.

### Class C — Governance

Examples:

- Constitution changes
- Principle changes
- AI authority changes
- Repository structure changes
- Security policy changes

Requires explicit human approval.

### Class D — Architectural

Examples:

- Major repository restructuring
- AIOS architecture changes
- Major automation architecture
- Significant dependency or platform changes

Requires documented architectural reasoning and explicit human approval.

---

## 10. Version Control

Git is the authoritative version-control system for AIOS.

All meaningful repository changes must be committed to Git.

Commits should:

- Represent coherent changes
- Use clear messages
- Avoid unrelated modifications
- Preserve traceability

History should remain understandable to future humans and AI systems.

---

## 11. Branching

The `main` branch represents the stable AIOS state.

Work should normally occur through controlled changes before reaching
`main`.

The exact branching and pull-request strategy may evolve as AIOS
matures.

Direct commits to `main` may be acceptable for low-risk changes when
the repository's current workflow explicitly permits them.

Governance-sensitive changes should receive explicit review before
merging.

---

## 12. Commit Discipline

AIOS commits should generally represent one logical change.

Examples:

```text
docs: add AIOS vision v1.0
docs: add guiding principles v1.0
docs: update repository constitution
feat: add prompt validation script
fix: correct documentation link
```

Commit messages should describe the change rather than the conversation
that produced it.

---

## 13. AI Context and Handover

Important engineering context must not exist exclusively inside an AI
conversation.

When a decision, requirement, constraint, or discovery is important to
future work, it should be captured in the repository.

The repository should remain understandable even when:

- The original AI conversation is unavailable.
- A different AI system takes over.
- A different human works on the project.
- The AI model or vendor changes.

### Rule

> **The repository must be able to outlive the conversation.**

---

## 14. AI Role Boundaries

AI roles must have explicit boundaries.

For example:

```text
Architect
    → proposes architecture

Implementer
    → implements approved design

Reviewer
    → evaluates implementation

QA
    → verifies behavior

Security
    → evaluates security

Documentation
    → maintains documentation
```

A role must not silently assume authority belonging to another role.

Where one AI system performs multiple roles, the role boundaries still
apply conceptually.

---

## 15. Independent Review

Changes with meaningful engineering impact should receive verification
appropriate to their risk.

Verification may include:

- Human review
- AI review
- Automated checks
- Tests
- Static analysis
- Security analysis
- Documentation validation

For high-risk changes, the same AI context that generated the change
should not be the only source of verification.

---

## 16. Security

Security-sensitive information must never be committed to the
repository.

This includes:

- Passwords
- API keys
- Access tokens
- Private keys
- Recovery codes
- Personal authentication secrets
- Production credentials

Secrets must use appropriate secure storage mechanisms.

AI systems must not be instructed to expose or commit secrets.

---

## 17. Dependency Discipline

Dependencies must have a justified purpose.

Before introducing a significant dependency, consider:

- Necessity
- Maintenance
- Security
- License
- Compatibility
- Vendor lock-in
- Alternatives
- Long-term sustainability

A dependency should not be added merely because an AI-generated solution
uses it.

---

## 18. Tool Governance

Tools used to operate AIOS are part of the AIEP layer.

Tool selection should be documented separately from AIOS governance.

A tool may be replaced without changing the underlying AIOS principle or
workflow whenever practical.

---

## 19. Repository Cleanliness

The repository should remain clean and understandable.

Do not commit:

- Temporary files
- Generated artifacts unless intentionally required
- Local environment files
- Secrets
- Debug output
- Unnecessary binaries
- Personal configuration

Repository cleanliness is part of maintainability.

---

## 20. Documentation Integrity

Documentation must be treated as an engineering asset.

Changes should avoid creating:

- Contradictory instructions
- Duplicate authoritative documents
- Broken references
- Obsolete standards
- Undocumented governance changes

When a governance change affects other documentation, impacted documents
should be reviewed.

---

## 21. Architecture Decisions

Significant architectural decisions should be recorded as Architecture
Decision Records (ADRs).

An ADR should generally capture:

- Context
- Problem
- Options
- Decision
- Consequences

ADRs are immutable historical records once accepted.

If a decision changes, a new ADR should supersede the previous decision
rather than rewriting history.

---

## 22. Standards

AIOS standards must:

- Trace back to the Vision or Guiding Principles
- Have a defined scope
- Be versioned where appropriate
- Have clear ownership
- Be reviewable
- Avoid unnecessary duplication

Standards should explain what must be done.

Workflows should explain how it is done.

---

## 23. Exceptions

Exceptions to AIOS governance may be necessary.

Exceptions must:

- Be explicit
- Have a reason
- Identify the affected rule
- Define scope
- Define duration where applicable
- Be approved by the appropriate authority

Exceptions must not silently become permanent alternatives to the
standard.

---

## 24. Deprecation

AIOS documentation, workflows, prompts, tools, and standards may become
obsolete.

Deprecated assets should be clearly marked.

Where appropriate, they should identify:

- Why they are deprecated
- What replaces them
- When they became deprecated

Deletion should be preferred when historical preservation is not useful.

---

## 25. Continuous Improvement

The Constitution itself may evolve.

Changes should be driven by:

- Lessons learned
- New engineering requirements
- Security findings
- Technology changes
- AI capability changes
- Project experience

Governance should evolve deliberately rather than through accidental
drift.

---

## 26. Compliance

Projects adopting AIOS should identify which AIOS requirements apply to
them.

AIOS should support different levels of adoption rather than requiring
every project to implement every mechanism immediately.

Compliance should be proportional to:

- Project risk
- Complexity
- Security requirements
- Business impact
- Maturity

---

## 27. Constitution Authority

This Constitution governs the AIOS repository.

It does not automatically override the business, legal, security, or
operational requirements of projects using AIOS.

Individual projects may establish stricter requirements.

They should not weaken AIOS requirements without explicitly documenting
the reason and applicable scope.

---

## 28. Amendment Process

Changes to this Constitution require:

1. A documented change proposal.
2. Review of affected principles and standards.
3. Human approval.
4. A Git commit documenting the change.
5. Review of dependent documentation.

Major changes should include an ADR when appropriate.

---

## 29. Effective Principle

When a situation is not explicitly covered by this Constitution, the
AIOS Guiding Principles remain the primary decision framework.

When uncertainty remains:

> **Prefer the safer, more reversible, more transparent, and more
> maintainable option until the decision can be properly evaluated.**

---

## 30. Final Authority

The AIOS Constitution establishes the operating rules for the
repository.

However, the ultimate authority remains human.

AIOS exists to augment engineering capability, not to transfer
engineering accountability to machines.

> **AI proposes. Humans decide. Engineering standards govern.**
