# Quality Attributes Review Skill

## Purpose

Review a set of quality attributes for completeness, measurability, realism, and appropriate scope.

The review must determine whether the quality attributes meaningfully describe HOW WELL the system must operate.

The review must NOT design the system or introduce implementation-level requirements.

## Scope

Review ONLY quality attributes.

Evaluate whether they are:

- Relevant
- Measurable
- Realistic
- Testable
- System-level
- Non-duplicative
- Appropriately scoped
- Consistent with the project context

Do NOT review or propose:

- Architecture
- Component design
- Technology choices
- Database design
- API design
- Infrastructure
- Deployment design
- Implementation mechanisms
- Detailed test strategies
- Functional requirements

## Number of Attributes

The final set should contain 4–6 quality attributes.

Flag the requirements if:

- There are fewer than 4 and important quality concerns are missing.
- There are more than 6 without a strong justification.
- Multiple attributes represent essentially the same concern.
- Minor concerns have been elevated into separate quality attributes.

Prefer a small number of high-impact attributes.

## Review Dimensions

### 1. Relevance

Determine whether each attribute materially matters to the project.

Ask:

> "Would failure to meet this quality attribute materially affect the usefulness, safety, or success of the system?"

If not, identify it as a potential candidate for removal.

### 2. Measurability

Every quality attribute should have an objective way to determine whether it is satisfied.

Flag vague statements such as:

- "The system should be fast."
- "The system should be secure."
- "The system should be reliable."
- "The system should scale well."

Recommend measurable targets instead.

### 3. Realism

Evaluate whether the stated target is realistic for the type of system.

Flag unrealistic targets such as:

- 100% availability
- zero failures
- zero latency
- 100% successful requests
- impossible security guarantees

Do not automatically impose industry-standard numbers.

If the project context does not provide enough information to determine a target, identify it as an open decision rather than inventing a number.

### 4. Testability

A quality attribute must be objectively measurable.

For example:

Good:
"95% of read requests complete within 1 second."

Weak:
"The system provides excellent response times."

### 5. Appropriate Level of Abstraction

Quality attributes should specify the desired quality level without prescribing implementation.

Flag statements such as:

"The system shall use Redis to achieve 99.9% availability."

"The system shall use Kubernetes for scalability."

"The system shall use AES-256 encryption."

These specify implementation rather than the quality outcome.

The requirement should instead express the desired observable quality.

### 6. Correct Metric

Check whether the metric actually measures the stated quality attribute.

Examples:

- Performance → latency / throughput
- Availability → uptime percentage
- Reliability → failure rate / successful completion / definitive outcome
- Security → policy compliance / unauthorized-access prevention
- Auditability → audit coverage / traceability

Do not accept arbitrary metrics simply because they are quantitative.

### 7. Appropriate Measurement Context

Check whether the measurement specifies enough context to be meaningful.

For example:

Weak:

"95% of requests must complete within 1 second."

Better:

"95% of read-only requests under normal operating load must complete within 1 second."

The review should identify missing context when it materially affects interpretation.

### 8. Duplication

Identify quality attributes that measure essentially the same characteristic.

For example:

QA-001:
"The system shall respond within 1 second."

QA-002:
"The system shall provide fast responses."

These should not be separate quality attributes.

## Financial MCP-Specific Review

Pay particular attention to the following quality concerns:

### Security

Check whether security is expressed as a measurable system-level outcome rather than vague language.

The review should ensure that financial operations cannot be described as successful merely because a request was received.

### Reliability

Check whether financial operations have meaningful success/failure semantics.

For example, the quality attributes should not imply that a timed-out financial operation can simply be treated as failed without regard to its actual transaction state.

Do not prescribe how this is implemented.

### Auditability

Check whether important financial operations are traceable.

A useful auditability target may include coverage of financial operations rather than simply saying that "the system logs requests."

### Performance

Check that latency targets distinguish between operations where appropriate.

A read-only balance lookup and a financial transaction may not have the same realistic response-time expectations.

### Availability

Check that the availability target reflects the importance of the system without requiring unrealistic availability.

## Severity

Use:

### HIGH

A missing, contradictory, or unrealistic quality attribute that could materially affect the system's safety or success.

### MEDIUM

A meaningful measurability, clarity, relevance, or scope issue.

### LOW

A minor wording, metric, or duplication issue.

### INFO

An observation that does not require a change.

Do not provide an overall score or ranking.

## Output Format

The output must contain ONLY review findings.

### Finding 1

**Severity:** HIGH / MEDIUM / LOW / INFO

**Attribute:** QA-XXX

**Issue:** <Specific problem>

**Recommendation:** <Specific improvement>

For missing quality attributes:

### Missing Quality Attribute

**Severity:** HIGH / MEDIUM / LOW

**Gap:** <Quality concern that is not adequately covered>

**Recommendation:** <Proposed high-level measurable quality attribute>

For design-level quality attributes:

### Design-Level Attribute

**Severity:** MEDIUM

**Attribute:** QA-XXX

**Issue:** <Explain why the attribute prescribes implementation rather than a quality outcome.>

**Recommendation:** <Rewrite it as an implementation-neutral quality attribute.>

## Important Review Rules

1. Do not design the system.
2. Do not recommend technologies.
3. Do not prescribe architecture.
4. Do not introduce implementation mechanisms.
5. Do not create functional requirements.
6. Do not require every possible quality attribute.
7. Do not increase the number of attributes unnecessarily.
8. Do not invent unrealistic targets.
9. Do not treat vague industry best practices as measurable requirements.
10. Keep recommendations at the quality-attribute level.

## Final Principle

Quality attributes should answer:

> "How well must the system perform its functional responsibilities?"

The review should determine whether the answer is:

- relevant,
- measurable,
- realistic,
- testable,
- and appropriately high-level.

It should NOT answer:

> "How should we build the system to achieve those qualities?"