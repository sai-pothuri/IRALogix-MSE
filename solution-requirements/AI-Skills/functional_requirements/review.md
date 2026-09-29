# Functional Requirements Review Skill

## Purpose

Review a set of functional requirements for completeness, clarity, consistency, and appropriate level of abstraction.

The review must determine whether the requirements adequately describe WHAT the system needs to do.

The review must NOT design the system or introduce implementation-level requirements.

## Scope

Review ONLY functional requirements.

Evaluate whether the requirements:

- Cover the important functional capabilities of the system
- Correctly represent the stated business needs
- Are clear and unambiguous
- Are sufficiently specific to be testable
- Are consistent with one another
- Avoid unnecessary duplication
- Remain at an appropriate high level
- Avoid prescribing implementation

Do NOT review or propose:

- Architecture
- System components
- API design
- MCP protocol implementation
- Database design
- Technology choices
- Infrastructure
- Deployment
- Authentication mechanisms
- Authorization mechanisms
- Encryption mechanisms
- Algorithms
- Data structures
- Internal service design
- Logging implementation
- Monitoring implementation
- Retry mechanisms
- Caching
- Message queues
- Specific implementation patterns

## Core Review Question

For every requirement, ask:

> "Does this describe something the system must do, without specifying how the system does it?"

If yes, it is within scope.

If it specifies how the system is implemented, identify it as a design-level requirement and recommend keeping it out of the functional requirements.

## Review Dimensions

### 1. Completeness

Check whether the requirements cover the important functional capabilities described in the project context.

For this MCP financial system, consider whether requirements appropriately cover areas such as:

- Retrieving account information
- Retrieving account balances
- Retrieving transactions
- Performing supported financial operations
- Handling multiple operations within a user request
- Handling dependent operations
- User confirmation where functionally required
- Preventing unauthorized financial actions
- Communicating unsuccessful operations
- Communicating operation status

Only identify missing capabilities that are supported by the project context.

Do not invent detailed financial policies.

### 2. Clarity

Identify requirements that are:

- vague
- ambiguous
- open to multiple interpretations
- missing important functional context

Example:

Weak:
"The system shall support transactions."

Better:
"The system shall allow users to initiate supported financial transactions."

### 3. Testability

A requirement should allow someone to determine whether the system satisfies it from its externally observable behavior.

Weak:
"The system shall be reliable."

Better:
"The system shall inform the user when a requested financial operation cannot be completed."

Do not introduce technical testing mechanisms.

### 4. Consistency

Identify requirements that:

- contradict each other
- overlap unnecessarily
- describe incompatible behaviors
- use inconsistent terminology

Reference the requirement IDs involved.

### 5. Appropriate Level of Abstraction

This is a critical part of the review.

Flag requirements that are too detailed.

Examples:

"The system shall use OAuth 2.0."

"The system shall store sessions in Redis."

"The MCP server shall expose a `get_balance` tool."

"The system shall use a PostgreSQL database."

These are design/implementation decisions rather than high-level functional requirements.

Also flag requirements that are too vague to represent a meaningful functional behavior.

### 6. Atomicity

Prefer requirements that represent one meaningful functional behavior.

If a requirement combines unrelated capabilities, identify it.

Example:

"The system shall allow users to view balances, transfer funds, update their profile, and download statements."

This may need to be separated into multiple functional requirements.

### 7. Duplication

Identify requirements that express essentially the same functional behavior.

Do not split requirements merely because they have similar wording.

## Review Severity

Classify findings as:

### HIGH

A problem that causes a significant functional capability to be missing, contradictory, or incorrectly specified.

### MEDIUM

A meaningful ambiguity, incomplete behavior, or abstraction problem.

### LOW

A minor clarity, duplication, or wording issue.

### INFO

A useful observation that does not require a change.

Do not assign an overall score or ranking to the requirements.

## Output Format

The output should contain ONLY the review findings.

Use:

### Finding 1

**Severity:** HIGH / MEDIUM / LOW / INFO

**Requirement:** FR-XXX

**Issue:** <Concise description of the problem.>

**Recommendation:** <Specific recommendation for improving the functional requirement.>

For missing requirements:

### Missing Requirement

**Severity:** HIGH / MEDIUM / LOW

**Gap:** <Functional capability that is missing.>

**Recommendation:** <Proposed high-level functional requirement.>

For design-level requirements:

### Design-Level Requirement

**Severity:** MEDIUM

**Requirement:** FR-XXX

**Issue:** <Explain why this specifies implementation rather than functional behavior.>

**Recommendation:** <Recommend rewriting it as a high-level functional behavior or removing it from the functional requirements.>

## Important Review Rules

1. Do not redesign the system.
2. Do not propose architecture.
3. Do not propose technologies.
4. Do not introduce implementation details.
5. Do not turn non-functional requirements into functional requirements.
6. Do not invent business rules that were not provided.
7. Do not critique a requirement for failing to specify implementation details.
8. Do not require low-level security mechanisms in the functional requirements.
9. Do not require API/tool names in the functional requirements.
10. Keep all recommendations at the same abstraction level as the functional requirements.

## Final Principle

The functional requirements should answer:

> "What capabilities and behaviors must the system provide?"

The review should determine whether they answer that question completely and clearly.

The review should NOT answer:

> "How should we build the system?"