---
status: proposed
date: 2026-04-28
author: pierre-tenedero
tags: [architecture]
---

# Cluster Generation from Scenario Configuration Files

## Context

`edge-toolkit` needs a standardised way to define scenarios through configuration files and reliably transform those
definitions into runnable deployments.

## Decision

We will introduce `et-cli` as a cluster generation tool that reads a scenario configuration (YAML) file and produces the
corresponding deployment artifacts.

### et-cli

`et-cli` is a command line interface tool that serves as the entry point for generating scenarios from an input YAML
file.
It provides a consistent and repeatable mechanism for converting scenario definitions into deployable environments.

It currently supports the following deployments:

- mise
- Docker Compose

#### Example Case: Facility Security

As an example, consider a facility security system with an entrance camera and wearable health trackers for workers.
This scenario can be defined using the following YAML configuration:

```yaml
cluster_name: "facility-security-scenario"
deployment_type: "docker-compose"

agents:
  - name: "entrance-security-camera"
    resources:
      - type: "face-detection"

  - name: "worker-health-tracker"
    resources:
      - type: "har1"
```

From this configuration, `et-cli` infers the required workflow modules based on each agent’s resource definitions.
In this case, the face detection and HAR modules are automatically selected and executed within `ws-server`.

### Verification and validation

`et-cli` supports regenerating scenarios from a designated directory. During regeneration, it performs a diff against
existing artifacts to detect drift and identify any stale generated files. This ensures that scenario outputs remain
up-to-date and consistent with their source definitions.

## Future considerations

The scenario configuration UX will be expanded beyond `et-cli`. A Text User Interface (e.g. Ratatui) and a Graphical
User Interface (e.g. eGUI) may be implemented in the future.

The following future deployment types are also considered:

- mprocs
- nanocl
- k3s
- Rancher
- OpenShift
- Major cloud platforms: AWS, GCP, Azure

## Consequences

### Positive

- Scenario definitions become much easier to read. A reviewer can understand the cluster intent from the YAML file
  without reading the generated runtime files
- Scenario authors can now define clusters with a compact YAML file instead of hand-coding deployment configuration
- The same scenario definition can produce multiple operational formats, keeping cluster intent separate from runtime
  mechanics
- Verification scenarios are easier to add
- Creates a clear extension point for future deployment types

### Negative

- The YAML schema becomes a new contract. When new features are added in the future, migration care is needed to
  account for these changes.
- Output types may not be behaviourally identical

## Author

Pierre Tenedero

## Date

28 April 2026
