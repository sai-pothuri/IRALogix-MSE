# Quality Attributes Skill

## Purpose

Generate a small set of high-priority, measurable, and realistic quality attributes for the project.

Quality attributes describe HOW WELL the system must perform its functional responsibilities.

They must complement the functional requirements without specifying system architecture or implementation.

## Scope

Generate ONLY quality attributes.

Do not generate:
- Functional requirements
- Architecture
- Design decisions
- Technology choices
- Implementation details
- Component specifications
- API specifications
- Database requirements
- Detailed security controls

## Number of Quality Attributes

Generate ONLY 4–6 quality attributes.

Prefer 5 when the project context supports them.

Do not create separate quality attributes for minor concerns.

Prioritize attributes that materially affect the success, safety, or usability of the system.

## Required Characteristics

Every quality attribute must be:

### 1. Relevant

It must matter to the project's actual use case.

### 2. Measurable

It must contain a quantitative target or objective threshold whenever practical.

Avoid vague statements such as:

- "The system should be highly available."
- "The system should be fast."
- "The system should be secure."
- "The system should be reliable."

Instead define measurable targets.

### 3. Realistic

Targets should be achievable for the type of system being described.

Do not default to unrealistic targets such as:
- 100% availability
- zero failures
- zero latency
- zero security incidents

### 4. System-Level

Describe externally observable system behavior rather than implementation mechanisms.

Bad:

"The system shall use Redis to achieve low latency."

Good:

"95% of read-only requests shall receive a response within 1 second under normal operating load."

### 5. Testable

A team should be able to determine whether the system satisfies the quality attribute.

## Recommended Quality Attributes

For this project, consider the following five attributes.

### QA-001 — Availability

Define the expected availability of the MCP service.

Example:

"The MCP service shall achieve at least 99.9% monthly availability, excluding planned maintenance."

Use an appropriate availability target based on the project's expected criticality.

Do not assume 99.99% or 99.999% unless justified by the project context.

### QA-002 — Performance

Define response-time expectations for common operations.

Separate read-heavy operations from more expensive operations where appropriate.

Example:

"Under normal operating conditions, 95% of read-only requests shall receive a response within 1 second."

If different operations have materially different performance characteristics, define separate targets rather than forcing one target onto all operations.

Avoid specifying internal implementation latency.

### QA-003 — Security

Define measurable security outcomes rather than implementation mechanisms.

Examples:

"100% of financial operation requests shall be evaluated against the applicable access-control policy before execution."

"Unauthorized attempts to access financial resources shall be rejected."

Where possible, express security requirements in terms of observable outcomes and measurable compliance.

Do not prescribe:
- OAuth
- JWT
- encryption algorithms
- specific security products
- network architecture

unless explicitly required by the project context.

### QA-004 — Reliability

Define the expected behavior when requests fail or external dependencies are unavailable.

Example:

"At least 99.9% of successfully accepted financial operation requests shall reach a definitive completed or failed state without being duplicated."

Focus on externally observable reliability.

Do not prescribe:
- retry mechanisms
- queues
- databases
- idempotency implementations
- specific failure-recovery technologies

### QA-005 — Auditability

Define the degree to which important system actions can be reliably traced.

Example:

"100% of financial operations shall produce an auditable record containing the authenticated actor, operation, timestamp, outcome, and transaction reference."

Focus on what must be observable and traceable, not how audit records are stored.

## Metrics

Prefer metrics such as:

- Availability percentage
- Percentile latency (P50/P95/P99)
- Error rate
- Successful-operation rate
- Unauthorized-operation rejection rate
- Audit-record coverage
- Duplicate-operation rate
- Definitive transaction-state rate

Avoid arbitrary metrics that do not directly represent system quality.

## Targets

When defining targets:

1. Prefer realistic industry-appropriate values.
2. Use percentages or percentiles where appropriate.
3. Define the measurement context.
4. Distinguish normal operating conditions from exceptional conditions.
5. Avoid false precision.

For example:

Good:
"95% of read requests under normal operating load shall complete within 1 second."

Bad:
"All requests must complete within exactly 800 milliseconds."

## Output Format

The output must contain ONLY the quality attributes.

Do not include:
- Executive summary
- Architecture
- Assumptions
- Design recommendations
- Functional requirements
- Test plans
- Explanations
- Review comments

Use this format:

QA-001 — <Quality Attribute>

<One or two sentences describing the measurable quality requirement.>

Target: <quantitative target>

Measurement: <how the attribute can be objectively measured>

Repeat for 4–6 quality attributes.

## Important

Do not create a quality attribute simply because it is common in software engineering.

Only include attributes that materially matter to the project.

The goal is a small set of meaningful, measurable quality attributes rather than an exhaustive quality-attribute catalog.