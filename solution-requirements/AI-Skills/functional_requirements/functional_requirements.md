# Functional Requirements Skill

## Purpose

Generate the high-level functional requirements for the project based on the provided project description and business context.

The output must describe WHAT the system must do from a functional/business perspective.

The output must NOT describe HOW the system will be designed or implemented.

## Scope

Only identify functional requirements.

Functional requirements describe:
- Capabilities the system must provide
- Actions users or external systems must be able to perform
- Information the system must provide
- Business behaviors the system must support
- Expected behavior for important functional scenarios

Do NOT produce:
- System architecture
- Component design
- API design
- MCP protocol details
- Database design
- Technology choices
- Infrastructure
- Authentication mechanisms
- Authorization mechanisms or implementation
- Algorithms
- Data structures
- Internal services
- Deployment architecture
- Performance specifications
- Monitoring implementation
- Logging implementation
- Low-level error handling
- Implementation details

If a requirement can be satisfied in multiple implementation approaches, describe the desired behavior rather than selecting an implementation.

## Level of Abstraction

Requirements must remain at a high business/functional level.

Good:

"The system shall allow authorized users to retrieve the current balance of an account."

"The system shall allow users to retrieve recent transactions for an account."

"The system shall allow users to initiate financial transactions."

"The system shall support requests that require multiple financial operations."

Too low-level:

"The MCP server shall validate OAuth JWTs using JWKS."

"The server shall use Redis for idempotency."

"The system shall expose a get_balance MCP tool."

"The system shall use PostgreSQL to store transaction state."

These are design or implementation decisions and must not appear in the functional requirements.

## Requirements

Each requirement must:

1. Describe one functional capability or behavior.
2. Be understandable without knowing the system architecture.
3. Be testable at a functional level.
4. Avoid prescribing implementation.
5. Avoid unnecessary technical terminology.
6. Be concise.
7. Represent a meaningful business/system capability.

## Requirement Format

Use the following format:

FR-001 — <Short title>

<One or two sentence description of the functional behavior.>

Do not add:
- detailed acceptance criteria
- implementation notes
- architecture notes
- rationale
- design recommendations
- test cases

## Functional Areas to Consider

Based on the project context, consider whether requirements are needed for:

### Financial Information

- Account information
- Account balances
- Transaction history
- Transaction details

### Financial Operations

- Deposits
- Transfers
- Withdrawals
- Payments
- Other supported financial operations

### User Requests

- Single-operation requests
- Requests containing multiple operations
- Requests where operations depend on one another

### Transaction Behavior

- Successful financial operations
- Operations requiring user confirmation
- Operations that cannot be completed
- Operations whose status is not immediately determined

### Access and Security Behavior

Only describe security as a functional behavior.

For example:

"The system shall prevent users from performing financial operations on accounts they are not authorized to access."

Do NOT specify how authentication or authorization is implemented.

### Errors and Exceptions

Only include high-level functional behavior.

For example:

"The system shall inform the user when a requested financial operation cannot be completed."

Do NOT specify HTTP status codes, retry strategies, exception classes, or internal error handling.

### External AI Clients

The system may be accessed through different AI clients or agents.

Functional requirements may describe behavior that must remain consistent regardless of the client used.

Do not specify client architecture or model behavior.

## Multi-Operation Requests

A single user request may require multiple system capabilities.

For example:

"Show my account balance and my five most recent transactions."

This should result in separate functional requirements for:
- retrieving an account balance
- retrieving recent transactions

Do not define how the request is decomposed or orchestrated.

Similarly, if a request requires sequential operations, describe the required business behavior rather than the orchestration mechanism.

## Output Rules

The output must contain ONLY the functional requirements.

Do not include:

- Executive summary
- Scope
- Architecture
- Assumptions
- Open questions
- Recommendations
- Non-functional requirements
- Design considerations
- Explanation of the requirements
- Review comments

Use a simple numbered list:

FR-001 — ...
FR-002 — ...
FR-003 — ...

Do not create requirements merely to increase the number of requirements.

Prefer a smaller set of meaningful, high-level functional requirements over a large set of implementation-level requirements.