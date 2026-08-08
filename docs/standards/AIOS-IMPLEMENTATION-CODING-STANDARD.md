# AIOS — Implementation & Coding Standard

**Version:** 1.0  
**Status:** Draft  
**Document Type:** Engineering Standard  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS Implementation & Coding Standard defines how software should
be implemented within an AIOS-controlled engineering environment.

It establishes common expectations for:

- Repository inspection
- Implementation planning
- Code modification
- Testing
- Dependency management
- AI-generated code
- Code review
- Git discipline
- Security
- Documentation
- Change boundaries

The standard applies to human-assisted and AI-assisted implementation.

---

## 2. Core Principle

Implementation begins with understanding rather than code generation.

The implementation process should be:

```text
Understand
   ↓
Inspect
   ↓
Plan
   ↓
Implement
   ↓
Validate
   ↓
Review
   ↓
Commit
```

### Core rule

> **Understand the system before changing the system.**

---

## 3. Repository Inspection

Before making meaningful changes, the implementation role should inspect
the relevant repository context.

Inspection may include:

- Repository structure
- Relevant source files
- Documentation
- Configuration
- Dependencies
- Tests
- Build system
- Existing conventions
- Git status
- Recent changes

The depth of inspection should match the scope and risk of the task.

---

## 4. Existing Architecture

Implementation must respect approved architecture.

Before modifying a significant component, the implementer should
identify:

- Its purpose
- Its dependencies
- Its consumers
- Its interfaces
- Its constraints
- Relevant architecture decisions

If the implementation appears to require an architectural change, the
issue should be escalated according to the Architecture & Decision
Standard.

---

## 5. Requirements Alignment

Implementation should be traceable to approved requirements.

Before coding, the implementer should understand:

- Intended behavior
- Acceptance criteria
- Scope
- Constraints
- Expected edge cases

Implementation should not silently introduce unrelated requirements.

---

## 6. Implementation Planning

Non-trivial changes should have an implementation plan before code is
modified.

A plan should identify:

- Files or components likely to change
- Major implementation steps
- Dependencies
- Testing approach
- Risks
- Potential rollback

Plans should be proportional to task complexity.

A one-line typo correction does not require a formal implementation plan.

---

## 7. Minimal Change Principle

Implementation should change only what is necessary to satisfy the
approved objective.

Avoid unnecessary:

- Refactoring
- Dependency changes
- Formatting changes
- File movement
- Architecture changes
- Configuration changes

unless they are part of the approved scope.

### Principle

> **Prefer the smallest change that correctly solves the problem.**

---

## 8. Scope Control

The implementer must remain within the approved scope.

If additional work is discovered, classify it separately when appropriate.

Examples:

```text
Original task:
Fix login validation.

Discovered:
Authentication architecture needs redesign.

Correct response:
Complete the scoped fix if safe,
then raise the architecture issue separately.
```

AI should not expand scope merely because it identifies improvements.

---

## 9. Coding Conventions

Implementation should follow the project's established coding
conventions.

Where project conventions do not exist, use:

- Clear naming
- Consistent structure
- Simple design
- Appropriate abstraction
- Readable code
- Maintainable patterns
- Standard language practices

Project-specific standards take precedence over generic AI preferences.

---

## 10. Simplicity

Implementation should prefer simple solutions over unnecessary
complexity.

Avoid:

- Premature abstraction
- Unnecessary frameworks
- Excessive indirection
- Speculative features
- Over-engineering

Complexity should have a justified purpose.

---

## 11. AI-Generated Code

AI-generated code is treated as **unverified engineering output** until
it has been appropriately reviewed and tested.

AI may generate:

- Functions
- Components
- Tests
- Documentation
- Configuration
- Scripts

Generated code must still satisfy:

- Requirements
- Architecture
- Coding standards
- Security requirements
- Verification requirements

### Core rule

> **Generated code is not trusted merely because an AI generated it.**

---

## 12. Code Understanding

Before modifying existing code, the implementer should understand the
relevant behavior.

This may require:

- Reading surrounding code
- Following data flow
- Inspecting callers
- Inspecting tests
- Checking configuration
- Reviewing documentation

Blind replacement of unfamiliar code should be avoided.

---

## 13. Dependency Management

New dependencies should be introduced deliberately.

Before adding a dependency, consider:

- Necessity
- Maintenance
- Security
- License
- Size
- Compatibility
- Stability
- Vendor dependency
- Alternatives

Do not add a dependency merely because it makes a small implementation
easier.

---

## 14. Dependency Changes

Dependency upgrades and removals should be treated as explicit changes.

The implementer should consider:

- Compatibility
- Breaking changes
- Security implications
- Lock files
- Build impact
- Runtime impact
- Regression risk

Higher-risk dependency changes should receive additional verification.

---

## 15. Secrets and Sensitive Data

Implementation must protect secrets and sensitive information.

Do not place secrets in:

- Source code
- Git commits
- Logs
- Documentation
- Test fixtures
- Prompts
- Generated files

Sensitive values should use appropriate secret-management mechanisms.

If a task appears to require direct exposure of a secret, stop and
escalate.

---

## 16. Configuration

Configuration changes should be treated as engineering changes rather
than incidental edits.

Consider:

- Environment differences
- Defaults
- Security
- Deployment
- Backward compatibility
- Secrets
- Rollback

Development configuration should not accidentally become production
configuration.

---

## 17. Testing During Implementation

Implementation should include appropriate testing as work progresses.

Testing may include:

- Unit tests
- Integration tests
- End-to-end tests
- Manual validation
- Static analysis
- Type checking
- Build verification

Testing depth should match risk.

The implementer should avoid postponing all verification until the end
of a large change.

---

## 18. Test Modification

Tests should be modified only when justified.

A test should not be changed merely to make an implementation pass.

When behavior intentionally changes:

1. Requirement is confirmed.
2. Expected behavior is updated.
3. Test is updated.
4. New behavior is verified.

Changing tests to conceal regressions is prohibited.

---

## 19. Regression Awareness

Implementation should consider whether the change can affect existing
behavior.

Potential regression areas include:

- Shared components
- Public interfaces
- Authentication
- Data handling
- Configuration
- Dependencies
- Performance
- Existing workflows

Relevant regression tests should be executed.

---

## 20. Error Handling

Implementation should handle expected failures appropriately.

Consider:

- Invalid input
- Missing resources
- Network failures
- Permission failures
- Dependency failures
- Unexpected states

Errors should not be silently ignored.

Error handling should provide enough information for diagnosis without
exposing sensitive information.

---

## 21. Documentation During Implementation

Implementation should update relevant documentation when behavior,
architecture, configuration, or interfaces change.

Documentation may include:

- README
- API documentation
- Architecture documentation
- ADRs
- Configuration documentation
- Operational instructions

Documentation updates should occur as part of the change rather than
being forgotten afterward.

---

## 22. Git Discipline

Implementation should preserve a clean and understandable Git history.

Before starting meaningful work:

```text
Check repository state.
```

During work:

```text
Review changes.
```

Before commit:

```text
Inspect diff.
Run required verification.
Confirm intended files only.
```

Commits should represent coherent engineering changes.

Unrelated changes should not be mixed into the same commit without
justification.

---

## 23. Commit Discipline

A commit should communicate what changed and why.

Good commits are:

- Focused
- Traceable
- Reviewable
- Reversible where practical

Commit messages should follow the project's established convention.

AI should not create commits containing changes it cannot explain.

---

## 24. Generated and Temporary Files

Implementation should not unnecessarily commit:

- Build artifacts
- Temporary files
- Logs
- Caches
- Local environment files
- Secrets
- Debug output

Generated files should be committed only when they are intentionally
part of the repository.

---

## 25. Code Review

Meaningful implementation should receive appropriate review.

Review may evaluate:

- Requirements
- Architecture
- Correctness
- Security
- Maintainability
- Tests
- Scope
- Documentation

AI may perform review.

Independent verification should be used when required by risk.

---

## 26. Implementation Verification

Before implementation is considered complete, the implementer should
confirm:

- Intended files changed
- No unintended changes exist
- Tests pass as required
- Build succeeds where applicable
- Requirements are satisfied
- Documentation is updated where necessary
- Security considerations are addressed
- Git diff is understood

Verification results should be recorded where appropriate.

---

## 27. Implementation Handover

When implementation responsibility changes, the AIOS Collaboration &
Handover Standard applies.

The handover should identify:

- Objective
- Current state
- Changes
- Relevant files
- Tests
- Evidence
- Known issues
- Open questions
- Verification status
- Expected next action

The receiving role should validate critical information.

---

## 28. Implementation Exceptions

Exceptions to this standard may be required for:

- Legacy systems
- Emergency fixes
- Generated code
- External vendor constraints
- Experimental prototypes

Exceptions should be:

- Explicit
- Bounded
- Justified
- Documented where significant
- Reviewed when appropriate

Exceptions should not silently become permanent practice.

---

## 29. AIOS Implementation Governance

Implementation operates under:

- AIOS Repository Constitution
- AIOS AI Role Definitions
- AIOS Authority & Permission Model
- AIOS Collaboration & Handover Standard
- AIOS Engineering Lifecycle Standard
- AIOS Task & Change Management Standard
- AIOS Architecture & Decision Standard

Project-specific coding standards may be stricter.

The implementation role must not use coding authority to bypass
governance, architecture, security, or approval requirements.

---

## 30. Core Implementation Principle

Implementation exists to transform approved engineering intent into
working, maintainable, and verifiable artifacts.

AI should accelerate implementation without replacing engineering
discipline.

The process should remain:

- Understandable
- Scoped
- Minimal
- Testable
- Reviewable
- Secure
- Documented
- Reversible where practical

> **Understand before changing, change only what is justified, and verify
> what you changed.**
