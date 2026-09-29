# System Constraints Skill

## Purpose

Identify and document the system constraints that govern the project.

Constraints describe conditions, boundaries, mandated technologies, external dependencies, regulatory obligations, project limitations, or scope restrictions that constrain the solution space.

The output must capture WHAT IS FIXED, MANDATED, REQUIRED, OR OUT OF BOUNDS.

Constraints are not functional requirements and are not quality attributes.

## Scope

Generate ONLY system constraints.

Do not generate:

- Functional requirements
- Quality attributes
- System architecture
- Design decisions
- Implementation plans
- Recommendations
- Open questions
- Explanations
- Acceptance criteria

Do not transform a constraint into a functional requirement.

## Constraint Categories

Classify each constraint into one of the following categories:

### 1. Technical Constraints

Technology, platform, integration, or implementation choices that are already mandated or fixed.

Examples from this project include:

- MCP is the mandated tool-surface standard.
- Auth0 is the user-authentication platform.
- Existing IRALOGIX platform APIs are the system of record.
- No new IRALOGIX APIs may be created.
- Implementation must use Python or TypeScript.
- The Agent Control Plane integration must be designed for, but is not part of the current implementation.

### 2. Regulatory and Business Constraints

External rules, policies, legal boundaries, or business decisions that constrain the solution.

Examples include:

- Reg S-P governs accountholder data handling.
- Partner data agreements govern applicable data handling.
- The system operates within a fiduciary boundary and must inform rather than recommend.
- Signatures cannot be collected through chat.
- Platform compliance services are the source of truth for compliance decisions.

Do not interpret or expand regulatory requirements beyond what is explicitly provided.

### 3. Scope Constraints

Explicit boundaries on what is and is not part of the project.

Examples include:

- No new IRALOGIX APIs.
- No voice surfaces.
- No real-time market data.
- No cross-partner data aggregation.
- No production hardening or production deployment.
- External chat-client integration is a stretch goal rather than a required deliverable.

### 4. Project Constraints

Constraints arising from time, staffing, resources, milestones, or project expectations.

Examples include:

- Approximately four months of development.
- Approximately six team members.
- Approximately 240 team-hours per week.
- December completion.
- Monthly milestone reviews.
- The project is evaluated on architecture, quality attributes, and construction.

### 5. Data Constraints

Constraints governing data sources, data types, or permitted data usage.

Examples include:

- Confluence KB is the RAG source for explanation-mode content.
- Demo environments use synthetic data.
- Production customer data is not used for the project demonstration.

Only include data constraints that are explicitly supported by the project context.

## Constraint Identification Rules

A statement should be considered a constraint when it does one or more of the following:

- Mandates a technology or platform.
- Prohibits a technology, capability, or implementation.
- Requires the system to use an existing system or source of truth.
- Establishes a regulatory or business boundary.
- Establishes a project scope boundary.
- Establishes a fixed project resource or schedule limitation.
- Restricts the data that can be used.
- Establishes something that the project must be compatible with even if it is not implemented now.

## Do Not Confuse Constraints With Requirements

Constraint:

"The system must use the existing IRALOGIX platform APIs."

Functional requirement:

"The system shall allow users to retrieve account information."

Quality attribute:

"95% of account-information requests shall complete within one second."

Keep these concepts separate.

## Constraint Granularity

Keep constraints at a high level.

Do not turn one constraint into many low-level implementation constraints.

Good:

"Authentication must use Auth0; custom authentication is out of scope."

Too detailed:

"The authentication service shall validate Auth0 JWTs using JWKS every five minutes."

The second statement is an implementation/design requirement and should not appear here.

## Project-Specific Constraints

The following constraints are explicitly established for this project and should be captured when generating the constraint set.

### Technical

- MCP is the mandated tool-surface standard.
- Deviating from MCP would require strong evidence and is impractical within the project timeframe.
- Auth0 is the user-authentication platform.
- Custom authentication is not permitted.
- Existing IRALOGIX platform APIs are the system of record.
- Existing IRALOGIX APIs are consumed rather than duplicated.
- No new IRALOGIX APIs are in scope.
- Platform compliance services are the source of truth for compliance decisions.
- The dedicated compliance engine under development must therefore be treated as replaceable/swappable from the project perspective.
- Implementation must use Python or TypeScript.
- The IRALOGIX Intelligence platform, using Python/FastAPI, is a possible hosting environment.
- The Agent Control Plane must be considered for future integration, but its implementation is outside the current project.

### Regulatory and Business

- Reg S-P and applicable partner data agreements govern accountholder data handling.
- Supervision is designed toward FINRA Rule 4511-style retention requirements.
- Production retention implementation is outside the current project.
- The system operates within a fiduciary boundary: it informs users but does not make recommendations.
- Signatures cannot be collected through chat.
- Gated signature flows must be completed by the platform.
- The project's treatment of PII returned to an authenticated owner is subject to sponsor/counsel confirmation where existing packet language conflicts with the stated sponsor position.
- Regulatory and legal interpretations must not be invented by the system-design process.

### Project and Scope

- The project is approximately four months long.
- The project has approximately six team members.
- The project has approximately 240 team-hours per week available.
- Completion is targeted for December.
- Monthly milestone reviews are part of the project.
- The project is evaluated on architecture, quality attributes, and construction.
- New IRALOGIX APIs are out of scope.
- Voice interfaces are out of scope.
- Real-time market data is out of scope.
- Cross-partner data aggregation is out of scope.
- Production hardening and production deployment are out of scope.
- Working integration with an external chat client is a stretch goal, not a required deliverable.
- The required deliverable is extensibility to external chat clients rather than delivery of a specific external chat client.
- The demonstration uses development accounts and synthetic data.
- Building the external chat client itself is not required.
- The demonstration may use any model meeting the project's minimum model-size requirement of approximately 35B parameters or greater.

## Output Format

The output must contain ONLY the constraints.

Use:

C-001 — <Constraint title>

**Category:** Technical / Regulatory & Business / Scope / Project / Data

**Constraint:** <Concise description of the constraint.>

Repeat for each constraint.

## Output Rules

1. Do not include an introduction.
2. Do not include a summary.
3. Do not include recommendations.
4. Do not include assumptions.
5. Do not include open questions.
6. Do not include functional requirements.
7. Do not include quality attributes.
8. Do not include architecture.
9. Do not prescribe implementation details beyond an explicitly stated constraint.
10. Do not invent constraints that are not supported by the project context.
11. Preserve the distinction between "must," "out of scope," "stretch," and "possible."
12. Do not accidentally convert a possible technology/platform into a mandatory requirement.
13. Keep each constraint concise.
14. Consolidate closely related constraints when doing so improves clarity.
15. Prefer a smaller number of meaningful constraints over excessive fragmentation.