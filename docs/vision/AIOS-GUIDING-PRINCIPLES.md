# AIOS — Guiding Principles

**Version:** 1.0  
**Status:** Draft  
**Document Type:** Foundational Principles  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS Guiding Principles define the fundamental rules and beliefs
that guide the design, implementation, operation, and evolution of
AIOS.

These principles provide a decision-making framework when specific
standards or procedures do not yet exist.

Where detailed standards exist, those standards should implement and
remain consistent with these principles.

---

## 2. Principles at a Glance

AIOS is guided by the following principles:

1. Human Accountability
2. Intent Before Implementation
3. Documentation First
4. Architecture Before Code
5. Single Source of Truth
6. Separation of Responsibilities
7. AI Specialization
8. Independent Verification
9. Quality Over Speed
10. Least Privilege
11. Controlled Autonomy
12. Reversible Decisions
13. Explicit Decisions
14. Vendor Neutrality
15. Cloud-First, Local-Ready
16. Security by Design
17. Automation with Guardrails
18. Reusability
19. Simplicity and Minimalism
20. Continuous Improvement

---

## 3. Human Accountability

Humans remain accountable for the systems they create and operate,
regardless of how much AI assistance is used.

AI may propose, generate, analyze, test, or review work.

AI does not become the owner of a technical, business, security, or
production decision merely because it performed the work.

### Practical rule

> **AI can perform work. Humans retain accountability.**

---

## 4. Intent Before Implementation

Engineering begins with understanding the problem.

AIOS should avoid immediately translating an ambiguous request into
code.

Before implementation, the intended outcome should be understood well
enough to define:

- The problem
- The desired outcome
- The scope
- The constraints
- The acceptance criteria

### Practical rule

> **Do not solve an unclear problem faster. Clarify it first.**

---

## 5. Documentation First

Documentation is part of engineering, not an administrative activity
performed after engineering.

Important knowledge should be captured before it disappears from the
working context.

Documentation should explain:

- What we are building
- Why we are building it
- How it works
- What decisions were made
- What constraints exist
- How it should be maintained

### Practical rule

> **If a decision matters, document it.**

---

## 6. Architecture Before Code

Implementation should follow an intentional architecture.

AI-generated code must not become the accidental architecture of a
system.

Architecture should establish appropriate:

- Components
- Responsibilities
- Interfaces
- Data flows
- Dependencies
- Boundaries

The level of architectural planning should be proportional to the
complexity and risk of the work.

### Practical rule

> **Code should implement architecture, not invent it accidentally.**

---

## 7. Single Source of Truth

Important information should have one authoritative location.

Examples include:

- Requirements
- Architecture decisions
- Configuration
- Project standards
- Release information
- AI role definitions

Copies may exist for convenience, but they must not create competing
authoritative versions.

### Practical rule

> **One fact should have one authoritative home.**

---

## 8. Separation of Responsibilities

AIOS separates responsibilities so that one system or agent does not
automatically control the entire engineering lifecycle.

Planning, implementation, review, testing, security, and release may be
performed by different roles.

This separation reduces blind spots and makes failures easier to detect.

### Practical rule

> **Do not allow the producer to be the only judge of its own work.**

---

## 9. AI Specialization

AI systems should be assigned roles according to their strengths and
the requirements of the task.

A single AI may perform multiple roles when appropriate, but the roles
themselves should remain conceptually distinct.

Examples include:

- Architect
- Researcher
- Implementer
- Reviewer
- QA Engineer
- Security Reviewer
- Documentation Engineer

### Practical rule

> **Organize AI around responsibilities, not around brand names.**

---

## 10. Independent Verification

Important work should be independently verified.

Verification may include:

- Automated tests
- Static analysis
- Code review
- Security review
- Architecture review
- Manual validation
- Independent AI review

The level of verification should be proportional to risk.

### Practical rule

> **Generation and verification should not be treated as the same activity.**

---

## 11. Quality Over Speed

AIOS values development speed, but not at the expense of engineering
quality.

The goal is not maximum code generation.

The goal is maximum useful engineering output.

Quality includes:

- Correctness
- Maintainability
- Security
- Testability
- Documentation
- Reliability
- Reproducibility

### Practical rule

> **Optimize for useful outcomes, not lines of code or tokens per minute.**

---

## 12. Least Privilege

AI systems, tools, scripts, and humans should receive only the
permissions required to perform their current responsibility.

Access should be:

- Minimal
- Explicit
- Reviewable
- Revocable

An AI agent that only needs to modify documentation should not receive
unrestricted production access.

### Practical rule

> **Give every actor the minimum authority required for the task.**

---

## 13. Controlled Autonomy

AIOS supports automation and increasing AI autonomy, but autonomy must
operate within defined boundaries.

Autonomous actions should have appropriate:

- Scope
- Permissions
- Validation
- Logging
- Rollback
- Human escalation

Higher-risk operations require stronger controls.

### Practical rule

> **Autonomy must be bounded by engineering controls.**

---

## 14. Reversible Decisions

When uncertainty is high, prefer decisions that can be changed without
large irreversible costs.

Examples include:

- Experimental tools
- Architecture experiments
- Feature flags
- Replaceable service providers
- Versioned configurations

Irreversible decisions require greater analysis and documentation.

### Practical rule

> **When two viable options exist, prefer the one that preserves future
> choices.**

---

## 15. Explicit Decisions

Important engineering decisions should not exist only in chat history,
memory, or undocumented assumptions.

Decisions should record, where appropriate:

- Context
- Options considered
- Decision
- Reason
- Consequences

Architecture Decision Records (ADRs) will provide the formal mechanism
for significant technical decisions.

### Practical rule

> **Important decisions must survive the conversation that created them.**

---

## 16. Vendor Neutrality

AIOS must not become dependent on a particular AI vendor, model, or
tool without deliberate justification.

Tools may be selected for practical reasons, but the underlying
engineering workflow should remain portable where reasonably possible.

### Practical rule

> **Tools are replaceable; engineering principles are not.**

---

## 17. Cloud-First, Local-Ready

AIOS may use cloud AI where it provides the best current capability,
cost, reliability, or accessibility.

However, architecture should avoid unnecessary dependence on cloud-only
implementation details.

Where practical, systems should maintain a migration path toward:

- Alternative cloud providers
- Open models
- Local inference
- Hybrid deployments

### Practical rule

> **Use the best practical technology today without closing tomorrow's
> options.**

---

## 18. Security by Design

Security must be considered during architecture and implementation,
not added only after a system is complete.

AIOS should consider:

- Secrets
- Identity
- Authentication
- Authorization
- Data protection
- Dependencies
- Supply-chain risks
- Infrastructure permissions
- AI tool permissions

### Practical rule

> **Security is an engineering property, not a final inspection step.**

---

## 19. Automation with Guardrails

Automation should remove repetitive work while preserving appropriate
controls.

Automated systems should have suitable:

- Preconditions
- Validation
- Failure handling
- Logging
- Notifications
- Rollback mechanisms

Automation should reduce human error, not merely move errors faster.

### Practical rule

> **Automate repeatable work, but engineer the failure path too.**

---

## 20. Reusability

AIOS should favor reusable engineering assets.

Examples include:

- Templates
- Prompts
- Workflows
- Checklists
- Scripts
- Architecture patterns
- Playbooks
- Knowledge

A solution developed for one project should be evaluated for potential
reuse across other projects.

### Practical rule

> **Solve once where possible; reuse deliberately.**

---

## 21. Simplicity and Minimalism

AIOS should remain as simple as practical.

Every new:

- Tool
- Dependency
- Process
- Agent
- Configuration
- Automation

introduces maintenance cost.

Complexity should therefore have a clear justification.

### Practical rule

> **Do not add complexity unless it creates more value than it costs.**

---

## 22. Continuous Improvement

AIOS is not a static framework.

Engineering experience should feed back into the system.

Lessons learned may result in improvements to:

- Standards
- Workflows
- Prompts
- Tools
- Templates
- Governance
- Architecture

### Practical rule

> **Every significant lesson should have an opportunity to improve the
> system.**

---

## 23. Principle Hierarchy

When principles appear to conflict, they should be evaluated according
to risk, context, and the following general priority:

1. Human safety and accountability
2. Security and protection of assets
3. Correctness and reliability
4. Maintainability
5. Reversibility and future flexibility
6. Simplicity
7. Speed and convenience

This hierarchy is not absolute.

Higher-priority principles may require context-specific interpretation,
but convenience or speed should not silently override safety,
accountability, security, or correctness.

---

## 24. Applying the Principles

The principles should influence decisions at every level of AIOS.

### Strategy

Use the principles to determine what AIOS should and should not become.

### Architecture

Use them to evaluate technical designs and dependencies.

### Implementation

Use them to guide coding, testing, and automation.

### Tool Selection

Use them to evaluate AI models, agents, IDEs, services, and platforms.

### Project Integration

Use them to determine how individual projects adopt AIOS.

### Review

Use them as a baseline for evaluating whether engineering work follows
the AIOS model.

---

## 25. Principle of Proportionality

AIOS should not impose maximum process on every task.

The level of governance, documentation, review, and testing should be
proportional to:

- Complexity
- Risk
- Impact
- Irreversibility
- Security sensitivity

A small text correction should not require the same process as a
production architecture change.

### Practical rule

> **Use enough process to control the risk, but no more process than the
> risk justifies.**

---

## 26. North Star

The principles collectively support the AIOS objective:

> **Build better software with fewer people, without sacrificing
> engineering discipline, human judgment, or long-term maintainability.**