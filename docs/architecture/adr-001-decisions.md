---
status: accepted
date: 2026-03-18
author: jayvdb
tags: [architecture]
---

# Require architectural decision records

## Context

<!-- What is the issue that we're seeing that motivates this decision or change? -->

The Curtin project requires a systematic approach to documenting architectural and significant technical decisions.
Without a formal decision-making framework, knowledge about why certain architectural choices were made is lost over
time, making it difficult for current and future team members to understand the rationale behind the system's design.

Additionally, architectural decisions often involve intellectual property (IP) considerations related to new components
and third-party integrations.

Having a formal review process allows IP matters to be identified and assessed before significant IP is created,
reducing legal and licensing risks.

## Decision

<!-- What is the change that we're proposing and/or doing? -->

We will require that all significant architectural decisions, system design choices, and technical direction changes be
documented using Architectural Decision Records (ADRs).

An ADR is a short text document that captures a single architectural decision in a specific format.

## Consequences

### Positive

<!-- What becomes easier or possible as a result of this change? -->

- **Knowledge Preservation**: Decision rationale is preserved for future reference and context
- **Communication**: Ensures all stakeholders understand the reasoning behind major decisions
- **Consistency**: Establishes a uniform approach to decision-making across the project
- **Trace-ability**: Creates an auditable record of decisions and their evolution
- **Onboarding**: New team members can quickly understand architectural choices and their justifications
- **IP Management**: Enables intellectual property matters related to new proposed components to be reviewed
  and addressed before IP is created, reducing legal and licensing risks
- **Research Reporting**: As a research project, ADRs capture key decisions throughout the project lifecycle
  that can be referenced and highlighted in quarterly reports

### Negative

<!-- What becomes more difficult or impossible as a result of this change? -->

- **Overhead**: Requires commitment to documenting decisions in addition to implementation
- **Time Investment**: Initial setup and learning curve for the ADR format and process
- **Maintenance**: Deprecated decisions must be marked as superseded to prevent confusion

### Neutral

<!-- What other effects does this change have? -->

## Alternatives Considered

<!--
### Alternative 1: Option

**Description:**

**Pros:**
-----

**Cons:**
-----

**Why not chosen:**
-->

## References

<!-- Links to relevant documentation, RFCs, prior art, etc. -->

## Notes

<!-- Any additional information, implementation notes, or follow-up items -->

### Implementation Notes

- Each ADR will be numbered sequentially starting from 0001, with a short name given to each.
- ADRs should follow the standard template with Status, Context, Decision, Author, and Date.
- ADRs may include other sections after those sections, such as References, Alternatives, Consequences,
  Implementation Notes, etc.
- Status values: Draft, Proposed, Accepted, Rejected, Deprecated, Superseded
- Team members should review and discuss Proposed ADRs before they are Accepted or Rejected.
- ADR in Draft status are incomplete, and should not be considered ready for consideration.
- Decisions involving private or sensitive information should not be included in public ADRs.
- Public ADRs should define public interfaces and contracts that enable private components to be constructed
  in separate private repositories.
