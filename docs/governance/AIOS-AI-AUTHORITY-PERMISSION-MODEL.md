# AIOS — AI Authority & Permission Model

**Version:** 1.0  
**Status:** Draft  
**Document Type:** AI Authority & Security Governance  
**Last Updated:** 2026-08-08

---

## 1. Purpose

The AIOS AI Authority & Permission Model defines what AI systems may
observe, recommend, prepare, modify, execute, and approve within an
AIOS-controlled engineering environment.

The model exists to ensure that AI capability does not automatically
translate into unrestricted authority.

It establishes:

- Authority dimensions
- Permission levels
- Action classes
- Human approval requirements
- Tool permissions
- Risk boundaries
- Escalation requirements
- Autonomy controls
- Separation of responsibility and authority

---

## 2. Core Principle

AIOS separates:

```text
Responsibility
     ≠
Authority
     ≠
Technical Permission
     ≠
Accountability
```

A role may be responsible for a task without possessing authority to
approve it.

An AI may technically be capable of performing an action without being
authorized to perform it.

A human may delegate execution without transferring accountability.

### Core rule

> **Capability does not imply permission.**

---

## 3. Authority Dimensions

AIOS recognizes the following authority dimensions:

1. Observe
2. Analyze
3. Recommend
4. Prepare
5. Modify
6. Execute
7. Approve
8. Release

These dimensions are independent capabilities.

An AI may possess one capability without possessing all higher or
adjacent capabilities.

---

## 4. Observe

### Definition

The ability to read or inspect information within an authorized scope.

Examples:

- Read repository files
- Inspect documentation
- Inspect logs
- Read configuration
- Review test results
- Read Git history

### Risk

Generally low, but access to sensitive information may increase risk.

### Rule

Observation must still respect:

- Data sensitivity
- Privacy
- Security boundaries
- Least privilege

---

## 5. Analyze

### Definition

The ability to process observed information and derive conclusions.

Examples:

- Analyze code
- Analyze architecture
- Analyze logs
- Identify defects
- Compare alternatives
- Detect inconsistencies

Analysis does not itself authorize modification or execution.

---

## 6. Recommend

### Definition

The ability to propose an action or decision.

Examples:

- Recommend architecture
- Recommend a dependency
- Recommend a code change
- Recommend a release
- Recommend remediation
- Recommend a tool

Recommendations are advisory unless explicitly approved.

### Rule

> **A recommendation is not an authorization.**

---

## 7. Prepare

### Definition

The ability to create a proposed change without making it authoritative
or operational.

Examples:

- Draft code
- Create a patch
- Prepare a pull request
- Draft documentation
- Prepare a deployment plan
- Generate a migration script

Preparation should normally be reversible.

---

## 8. Modify

### Definition

The ability to change authorized engineering artifacts.

Examples:

- Edit source files
- Update documentation
- Modify tests
- Update configuration
- Create or modify branches
- Update approved project artifacts

Modification authority must be scoped.

An implementation role should not automatically have permission to
modify governance documents.

---

## 9. Execute

### Definition

The ability to cause an operational action to occur.

Examples:

- Run scripts
- Run tests
- Build software
- Create releases
- Deploy software
- Execute migrations
- Trigger automation

Execution is higher risk than preparation because it produces external
effects.

---

## 10. Approve

### Definition

The authority to authorize a significant action or decision.

Examples:

- Approve architecture
- Approve governance changes
- Approve production release
- Accept significant security risk
- Approve major scope changes

### Human Authority

AIOS reserves ultimate approval authority for significant decisions to
the human owner or explicitly authorized human decision-maker.

AI may provide approval recommendations but does not acquire human
accountability merely by being assigned an approval-related role.

---

## 11. Release

### Definition

The authority to make validated engineering work available to its
intended operational environment.

Examples:

- Production deployment
- Public website deployment
- Publishing a release
- Activating a production configuration

Release authority must be explicitly granted.

Production release is not automatically implied by implementation or
operations responsibility.

---

## 12. Authority Levels

AIOS defines five practical authority levels:

### Level 0 — Observe

AI may:

- Read
- Inspect
- Analyze

AI may not modify or execute.

---

### Level 1 — Recommend

AI may:

- Observe
- Analyze
- Recommend

No external modification or execution is authorized.

---

### Level 2 — Prepare

AI may:

- Draft
- Create patches
- Prepare changes
- Prepare pull requests
- Prepare deployment plans

Human or authorized automation must approve execution.

---

### Level 3 — Execute with Approval

AI may:

- Modify authorized artifacts
- Run authorized commands
- Execute approved workflows

Actions requiring approval must stop before execution.

---

### Level 4 — Bounded Execution

AI may execute predefined actions automatically within explicitly
defined boundaries.

Examples:

- Run tests
- Format code
- Build artifacts
- Deploy to development
- Perform approved low-risk automation

The boundaries must be technically enforced where practical.

---

### Level 5 — Controlled Autonomous Operation

AI may perform a defined workflow with limited human intervention.

This requires:

- Explicit scope
- Defined permissions
- Monitoring
- Logging
- Rollback
- Failure handling
- Clear termination conditions
- Human escalation path

Level 5 does not grant unrestricted authority.

---

## 13. Authority Is Capability-Specific

An AI may have different authority levels for different actions.

For example:

```text
Repository Reading       → Level 4
Code Modification        → Level 3
Git Push                 → Level 2
Production Deployment    → Level 1
Governance Modification  → Level 0
```

This is preferable to assigning one global autonomy level to an AI.

---

## 14. Least Privilege

AI systems must receive the minimum permissions required to perform
their assigned responsibility.

Permissions should be:

- Narrow
- Explicit
- Scoped
- Revocable
- Auditable
- Time-appropriate

Additional permissions should be granted only when justified.

### Principle

> **Give the minimum authority necessary to complete the task.**

---

## 15. Default Deny

AIOS follows a default-deny security model for consequential actions.

If permission is not explicitly granted, the AI should assume it does
not have permission.

This applies particularly to:

- Production
- Secrets
- Governance
- External communication
- Financial actions
- Destructive operations
- Irreversible changes

---

## 16. Action Classification

AIOS classifies actions into four broad categories.

### Class A — Read

Examples:

- Read files
- Inspect documentation
- Review logs
- Read Git history

Normally low risk.

### Class B — Reversible Change

Examples:

- Edit code
- Create documentation
- Create branches
- Generate patches
- Run tests

Generally reversible.

### Class C — External Effect

Examples:

- Push code
- Merge changes
- Deploy
- Send external communication
- Modify external services

Requires stronger controls.

### Class D — Irreversible or High-Impact

Examples:

- Delete production data
- Rotate critical credentials
- Modify security boundaries
- Publish sensitive information
- Execute destructive migrations
- Accept major security risk

Requires explicit authorization.

---

## 17. Permission Matrix

A conceptual default matrix is:

| Action | Default AI Permission | Human Approval |
|---|---|---|
| Read repository | Yes | No |
| Read documentation | Yes | No |
| Analyze code | Yes | No |
| Draft documentation | Yes | No |
| Draft code | Yes | No |
| Run local tests | Yes | No |
| Modify project files | Scoped | Sometimes |
| Create branch | Scoped | No |
| Create pull request | Scoped | No |
| Push to repository | Restricted | Depending on workflow |
| Merge pull request | Restricted | Normally required |
| Modify governance | No | Required |
| Access secrets | No by default | Explicit authorization |
| Deploy development | Scoped | Depending on workflow |
| Deploy production | Restricted | Required |
| Delete production data | No | Explicit human authorization |
| Accept major security risk | No | Required |
| Change AI authority | No | Required |

This matrix is a governance baseline.

Projects may impose stricter rules.

---

## 18. Governance Protection

The following areas are protected by default:

```text
AIOS Vision
AIOS Guiding Principles
AIOS Constitution
AIOS Organization Model
AIOS Role Definitions
AIOS Authority Model
Security Policies
AI Authority Boundaries
```

AI systems may analyze and propose changes to these documents.

They must not independently approve or establish changes to them.

---

## 19. Secret Protection

AI systems must not receive unrestricted access to secrets.

Secrets include:

- Passwords
- API keys
- Access tokens
- Private keys
- Recovery codes
- Production credentials
- Authentication secrets

Where a workflow requires secret use, access should be:

- Scoped
- Temporary where possible
- Masked
- Audited
- Limited to the required operation

Secrets must never be written into prompts, commits, logs, or
documentation unnecessarily.

---

## 20. Destructive Operations

Destructive operations require special handling.

Examples include:

- Deleting files
- Deleting branches
- Dropping databases
- Removing production resources
- Destructive migrations
- Overwriting critical configuration

AI should not perform destructive operations unless:

1. The operation is explicitly within scope.
2. Appropriate authorization exists.
3. Recovery or rollback has been considered.
4. The impact is understood.

High-impact destructive operations require explicit human
authorization.

---

## 21. External Communication

External communication includes:

- Sending emails
- Publishing content
- Posting to websites
- Sending business messages
- Creating public releases
- Communicating with customers or suppliers

AI may draft external communication.

Actual external communication requires authorization appropriate to the
risk and context.

Public, contractual, legal, financial, or sensitive communication
normally requires human approval.

---

## 22. Financial Actions

AIOS does not grant AI unrestricted financial authority.

Financial actions include:

- Payments
- Purchases
- Refunds
- Financial commitments
- Contract acceptance
- Banking operations

AI may assist with:

- Analysis
- Reconciliation
- Drafting
- Calculation
- Recommendations

Actual financial authorization remains subject to human-controlled
financial processes.

---

## 23. Production Authority

Production access is treated as a privileged capability.

Production permissions should be:

- Explicit
- Scoped
- Auditable
- Revocable
- Environment-specific

Development access does not imply production access.

Testing authority does not imply release authority.

Implementation authority does not imply production authority.

---

## 24. Permission Escalation

An AI may request additional permission when necessary.

The request should state:

1. Required permission
2. Purpose
3. Scope
4. Duration
5. Risk
6. Alternative options

The AI must not circumvent permission controls.

### Principle

> **Permission must be granted, not inferred.**

---

## 25. Autonomy and Permissions

Autonomy is the ability to perform a sequence of authorized actions.

Permission is authorization to perform a specific action.

Therefore:

```text
Autonomy
    ≠
Permission
```

Higher autonomy requires a defined permission set.

An autonomous agent with broad permissions is higher risk than an
autonomous agent with narrowly bounded permissions.

---

## 26. Permission Boundaries

Permissions should be bounded by:

### Scope

What resources can be accessed?

### Action

What can be done?

### Environment

Where can it be done?

### Time

For how long?

### Identity

Under which authorized identity?

### Risk

What level of impact is permitted?

---

## 27. Auditability

Consequential AI actions should be traceable.

Where practical, systems should record:

- Actor
- Role
- Action
- Resource
- Time
- Authorization
- Result
- Failure
- Escalation

The purpose is to allow humans to understand what happened after the
fact.

---

## 28. Revocation

AI permissions must be revocable.

When an AI system, tool, workflow, or project is no longer trusted or
required, its permissions should be removable without redesigning the
entire organization.

Temporary permissions should expire where practical.

---

## 29. Permission Governance

Technical permission implementation belongs to the AIEP and project
security layers.

AIOS defines the governance principles and authority boundaries.

AIEP and project infrastructure determine how those boundaries are
technically enforced.

The relationship is:

```text
AIOS
  ↓
Defines authority policy
  ↓
AIEP
  ↓
Maps policy to tools and agents
  ↓
Project Infrastructure
  ↓
Enforces technical permissions
```

---

## 30. Core Authority Principle

AIOS exists to ensure that AI capability remains bounded by deliberate
engineering governance.

AI should be powerful enough to perform useful engineering work but
never receive authority merely because that authority is technically
possible.

> **AI may act only within explicit authority, bounded permissions, and
> appropriate human accountability.**
