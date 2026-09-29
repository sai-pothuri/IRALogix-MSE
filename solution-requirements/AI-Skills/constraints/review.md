# System Constraints Review Skill

## Purpose

Review a set of system constraints for completeness, correctness, clarity, consistency, and appropriate level of abstraction.

The review must determine whether the constraints accurately represent the fixed conditions and boundaries governing the project.

The review must NOT design the system or introduce new implementation decisions.

## Scope

Review ONLY system constraints.

Evaluate whether the constraints:

- Accurately reflect the provided project context
- Capture important mandatory conditions and boundaries
- Clearly distinguish mandatory constraints from optional or future considerations
- Clearly distinguish constraints from functional requirements
- Clearly distinguish constraints from quality attributes
- Are sufficiently precise
- Are internally consistent
- Remain at an appropriate level of abstraction
- Do not prescribe unnecessary implementation details

Do NOT review or propose:

- Architecture
- API design
- Database design
- Component design
- Technology choices not already established by the project
- Detailed security mechanisms
- Detailed implementation strategies
- Performance targets
- Functional requirements
- Quality attributes

## Core Review Question

For every constraint, ask:

> "Is this a condition or boundary that constrains the solution space?"

If yes, it is likely a valid constraint.

If it describes something the system must do, it is likely a functional requirement.

If it describes how well the system must perform, it is likely a quality attribute.

If it describes how the system should be built, it is likely a design decision.

## Review Dimensions

### 1. Completeness

Check whether important explicit constraints from the project context are represented.

For this project, specifically check coverage of:

#### Technical

- MCP as the mandated tool-surface standard
- Auth0 as the authentication platform
- Existing IRALOGIX APIs as the system of record
- No new IRALOGIX APIs
- Platform compliance services as the compliance source of truth
- Compliance engine treated as swappable
- Python or TypeScript implementation
- Potential IRALOGIX Intelligence hosting environment
- Agent Control Plane as future/design-for integration rather than current implementation

#### Regulatory and Business

- Reg S-P
- Partner data agreements
- FINRA Rule 4511-style retention direction
- Production retention being outside the project
- Fiduciary boundary
- No signatures through chat
- Platform completion of gated signature flows
- PII handling constraint and unresolved sponsor/counsel reconciliation

#### Scope

- No new IRALOGIX APIs
- No voice
- No real-time market data
- No cross-partner data aggregation
- No production hardening/deployment
- External chat-client integration as stretch only
- Extensibility rather than delivery of a specific chat client
- Development accounts and synthetic demo data
- Chat client not required to be built
- Model-size constraint for the demonstration

#### Project

- Approximately four-month timeframe
- Team/resource constraints
- December completion
- Monthly milestone reviews
- Evaluation based on architecture, quality attributes, and construction

Only flag a missing constraint when it is explicitly supported by the project context or is clearly necessary to preserve an explicitly stated boundary.

Do not invent additional constraints.

## 2. Constraint Correctness

Verify that each constraint accurately reflects the source project context.

Pay particular attention to words such as:

- must
- required
- mandated
- prohibited
- out of scope
- stretch
- possible
- future
- designed for

Do not convert:

"possible host"

into:

"required host."

Do not convert:

"stretch goal"

into:

"mandatory capability."

Do not convert:

"designed-for"

into:

"must be implemented."

## 3. Constraint vs Functional Requirement

Identify statements that describe system behavior rather than a restriction on the solution.

Example:

Constraint:
"Existing IRALOGIX APIs must be used as the system of record."

Functional requirement:
"The system shall retrieve account information."

The first is a constraint.

The second is a functional requirement.

Flag requirements that have been placed in the wrong category.

## 4. Constraint vs Quality Attribute

Identify statements that specify how well the system should perform.

Example:

Constraint:
"The project must be completed within approximately four months."

Quality attribute:
"95% of requests must complete within one second."

The first constrains the project.

The second specifies system quality.

Do not move quality attributes into the constraint set.

## 5. Constraint vs Design Decision

Identify statements that prescribe a design or implementation approach rather than establishing a true project constraint.

Examples:

"The system shall use Redis."

"The system shall use Kafka."

"The MCP server shall use microservices."

"The system shall have three backend services."

Unless explicitly mandated by the source project context, these are design decisions rather than constraints.

Do not recommend specific replacement technologies.

## 6. Appropriate Level of Abstraction

Constraints should remain high-level.

Flag constraints that contain:

- class names
- API endpoints
- database schemas
- detailed protocols
- algorithms
- implementation patterns
- detailed infrastructure configurations
- low-level security mechanisms

Example:

Too low-level:

"The service shall refresh Auth0 JWKS keys every 10 minutes."

Appropriate:

"Authentication must use Auth0; custom authentication is not permitted."

## 7. Consistency

Identify conflicting constraints.

Examples:

C-001:
"Only existing IRALOGIX APIs may be used."

C-009:
"The project shall create a new customer-profile API."

Flag the conflict.

Also check for semantic contradictions such as:

- required vs out of scope
- mandatory vs optional
- current implementation vs future integration
- production vs development-only
- synthetic vs production data

## 8. Scope Boundary Integrity

Verify that explicit out-of-scope items are preserved.

For this project, ensure the review checks:

- new APIs
- voice
- real-time market data
- cross-partner aggregation
- production hardening/deployment
- building an external chat client

The reviewer should flag a requirement or constraint that accidentally brings an out-of-scope capability back into the project.

## 9. Source-of-Truth Integrity

Check that constraints correctly distinguish systems that are authoritative.

For example:

- Existing IRALOGIX APIs are the system of record.
- Platform compliance services are the source of truth for compliance.
- Confluence KB is the source for explanation-mode content.

Do not infer additional sources of truth.

## 10. Regulatory Constraint Integrity

Check that regulatory statements are not expanded beyond the supplied project context.

Do not independently interpret:
- Reg S-P
- FINRA rules
- partner agreements
- fiduciary obligations

The review should identify whether the supplied regulatory boundary is represented accurately, not determine legal meaning.

## 11. Project Feasibility

Check whether the constraints accurately preserve major project limitations.

In particular:

- timeline
- team capacity
- December completion
- milestone schedule
- scope boundaries
- stretch-goal status

Do not turn project constraints into architectural recommendations.

## Review Severity

Use:

### HIGH

A missing or incorrect constraint that could materially change project scope, violate a mandatory boundary, or create a significant regulatory/business conflict.

### MEDIUM

A meaningful ambiguity, inconsistency, misclassification, or missing boundary.

### LOW

A minor wording, categorization, duplication, or clarity issue.

### INFO

An observation that does not require a change.

Do not provide an overall score or ranking.

## Output Format

The output must contain ONLY review findings.

### Finding 1

**Severity:** HIGH / MEDIUM / LOW / INFO

**Constraint:** C-XXX

**Issue:** <Specific problem>

**Recommendation:** <Specific correction>

For missing constraints:

### Missing Constraint

**Severity:** HIGH / MEDIUM / LOW

**Gap:** <Missing boundary or limitation>

**Recommendation:** <Proposed high-level constraint>

For misclassified statements:

### Misclassified Statement

**Severity:** MEDIUM

**Constraint:** C-XXX

**Issue:** <Explain whether the statement is actually a functional requirement, quality attribute, or design decision.>

**Recommendation:** <Remove it from the constraint set or reclassify it appropriately.>

## Important Review Rules

1. Do not design the system.
2. Do not introduce technologies.
3. Do not propose architecture.
4. Do not invent constraints.
5. Do not interpret regulations beyond the provided project context.
6. Do not convert optional technologies into mandatory constraints.
7. Do not convert stretch goals into mandatory scope.
8. Do not convert future integrations into current implementation requirements.
9. Do not introduce low-level implementation constraints.
10. Do not turn functional requirements into constraints.
11. Do not turn quality attributes into constraints.
12. Preserve explicit scope exclusions.
13. Preserve the distinction between "mandatory," "possible," "future," "stretch," and "out of scope."
14. Keep recommendations at the same abstraction level as the constraints.

## Final Principle

System constraints should answer:

> "What conditions, boundaries, mandates, or limitations constrain the solution?"

The review should determine whether those boundaries are:

- complete,
- accurate,
- consistent,
- appropriately classified,
- and appropriately high-level.

It should NOT answer:

> "How should the system be designed within those constraints?"