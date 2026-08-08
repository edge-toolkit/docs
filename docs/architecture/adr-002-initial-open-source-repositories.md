---
author: jayvdb
date: 2026-03-18
status: accepted
tags: []
---

# Initial Open Source Repositories

<!-- Brief introduction: what this document is about -->

## Context

This project aims to build a comprehensive multi-agent system architecture that separates concerns
between infrastructure management and machine learning components.

Creating dedicated open source repositories allows for modular development, independent versioning, and
community contribution while maintaining clear architectural boundaries.

The architecture requires:

- A foundation layer that provides Kubernetes infrastructure componentry for orchestrating and managing many
  heterogeneous agents located in separate physical assets. Includes robots with autonomy, mobility, and
  ability to disengage and reengage from the infrastructure as required to achieve their goal.
- Deployable to multi-cloud environments, raw metal infrastructure, air-gapped (dark) sites, or laptop
  development environments with limited resources.
- Support for varied ML topologies, including mixes of cooperative and non-cooperative agents, over varied networks
  from permanent low-latency connections, to dark nodes.
- Nodes able to represent physical assets that can not be respawned, with pluggable strategies for intentional
  node attrition, and adaption to nodes being attrited (self-healing).
- An application layer that implements machine learning and agent-specific logic built on top of the Kubernetes
  foundation.
- Provides policies that describe the multilevel security of components.

## Decision

### Copyright and administration

We will establish a new GitHub organisation "edge-toolkit" specifically for the project.

Initially the GitHub organisation must:

- Only contain public repositories.
- Not contain any "secrets" in the organisation and repository settings.
- Not contain any access mechanisms, such as usernames, passwords, or tokens.

As a consequence, all CI/CD in these repositories can only access public systems.
Additional governance and security may be added to the GitHub organisation in the future
in order to remove this limitation.

Two members of the team will hold Administrator rights to the GitHub org at any time.

The School (EECMS), Thales, and team members may at any time request to be shown that
GitHub organisation and repository settings comply with the above.

The GitHub organisation can be taken over by the school or university at any time they
are ready to provide additional governance.

#### Licensing

All repositories in this organisation must be dual licensed under MIT and Apache 2.0 licenses,
with copyright assigned to Curtin University.

Each repository in this organisation will contain the following blurb in the `README.md`:

```
This repository is part of a grant managed by the School of EECMS, Curtin University.

ABN 99 143 842 569.

CRICOS Provider Code 00301J.

TEQSA PRV12158
```

### Repository 1: Documentation

**Purpose**: All public ADRs are stored, indexed and improved in this repository.

**Responsibilities**:

- Small & simple repository for a wider audience to participate in.
- Markdown is the only language needed to contribute.
- Diagrams will be authored in either PlantUML or MermaidJS.
- Notifications for this repository track high level project progress.

### Repository 2: Core

**Purpose**: Provides Kubernetes infrastructure components, utilities, and patterns for orchestrating, deploying,
monitoring, and managing adaptive multi-agent systems across multi-cloud environments, raw metal infrastructure,
and air-gapped (dark) sites, with research capabilities.

**Responsibilities**:

- Kubernetes manifests and operators for agent deployment
- Service discovery and communication infrastructure
- Dynamic agent capability detection (e.g. sensors and mobility)
- Resource management and scheduling for multi-agent workloads
- Monitoring and observability infrastructure for agents
- High availability and fault tolerance patterns
- Container image standards and base images for agents
- Basic implementations of the pluggable interfaces to support integration tests

**Implementation Language Approach**: This repository follows software engineering principles and
uses compiled languages (Rust, Go, C++, Java, etc.) to provide safety, performance, and reliability.
Implementations prefer software that does not require a virtual machine or garbage collection, enabling
efficient resource utilization on constrained physical assets and minimal operational overhead.

The core may use preexisting open source components written in interpreted languages, in order to complete the
platform, until a compiled replacement has been evaluated successfully.

### Repository 3: Research

**Purpose**: Implements machine learning components and agent-specific logic that builds on the Kubernetes
infrastructure repository.

**Responsibilities**:

- Agent implementations and frameworks
- Machine learning models and training pipelines
- Agent coordination and collaboration patterns
- Agent state management and persistence
- Extensions and plugins for agent capabilities
- Integration with the Kubernetes infrastructure

**Leadership and Implementation Language Approach**: This repository is led by the ML team and
can use scripted languages such as Python and "R".

These languages are well-suited to rapid prototyping, experimentation, and research iteration in
machine learning workflows, and the Research repository's dependence on the Core repository's
infrastructure abstracts performance-critical operations.

**Dependency**: This repository explicitly depends on and extends the Kubernetes Infrastructure repository.

## Consequences

### Positive

- **Separation of Concerns**: Infrastructure and application logic are cleanly separated,
  allowing independent evolution
- **Modularity**: Each repository can be versioned, released, and evolved independently
- **Reusability**: The Kubernetes infrastructure layer can be used with agents beyond this project
- **Community Contribution**: Clear repository boundaries make it easier for external contributors to understand scope
- **Testing**: Each repository can have focused test strategies for its domain
- **Deployment Flexibility**: Teams can use the infrastructure layer without requiring all ML components
- **Clear Dependencies**: The ML repository's dependency on the infrastructure repository is explicit
  and version-controlled
- **Access to Advanced Tools**: Open-source repositories can leverage leading agentic coding tools for
  enhanced development productivity
- **Industry Collaboration**: Open-source repositories streamline the ability for industry partners to
  collaborate with the projects
- **Cost-Effective CI/CD**: Open-source repositories provide free CI/CD services, allowing extensive unit testing
  without driving up project costs
- **Academic Freedom**: Open-source ML repositories support academic freedom by allowing unrestricted access,
  modification, and research use

### Negative

- **Coordination Overhead**: Development across two repositories requires careful synchronization
  and integration testing
- **Versioning Complexity**: Managing compatible versions between repositories adds complexity
- **Documentation Burden**: Interdependencies must be clearly documented to avoid confusion
- **Release Management**: Coordinated releases between repositories may be required for certain features

## Implementation Notes

- Repository names should clearly reflect their purposes (e.g., `k8s-multi-agent` and `ml-agents`)
- Each repository should have its own test, documentation, and CI/CD pipeline
- API contracts between repositories should be versioned and clearly documented
- Dependencies between repositories, including any common code or utilities, should be expressed through
  versioned packages published to open-source package managers (pip, npm, etc.)
- Regular integration testing should verify compatibility between repositories

## Prior art

### Thales fred & Agilab

Thales has created [`fred`](https://fredk8.dev/),
which is a modular multi-agent AI assistant for Kubernetes.

It follows a similar architecture of an Open Source (Apache 2.0) core that allows Thales
to build commercial I.P. plugins.

The open source repository is at <https://github.com/ThalesGroup/fred>.

See also:

- https://fredk8.dev/docs/rationale/why-fred-a-developer-manifesto/
- https://fredk8.dev/blog/fred-design-and-architecture/Fred.pdf

Thales has also created "Agilab" as an ML experimentation platform, again using
Open Source (BSD-3) for the core, on which their employees conduct proprietary research.

The open source repository is at <https://github.com/ThalesGroup/agilab>.

fred & Agilab are both written in Python language, whereas this project requires
compiled languages be used for the core components.
