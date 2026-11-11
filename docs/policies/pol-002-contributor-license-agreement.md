---
status: proposed
author: claude
owner: jayvdb
date: 2026-11-11
review_date: 2027-11-11

tags:
  - governance
  - licensing
related:
  - ADR-002
---

# Contributor License Agreement

This policy records the contributor licensing terms introduced by
[edge-toolkit/core#183](https://github.com/edge-toolkit/core/pull/183). It stays `proposed` until that pull request is
merged.

## Purpose

Curtin University publishes edge-toolkit as open source and needs the right to relicense, sublicense and commercially
exploit the codebase. Contributions from people outside the university create uncertainty about copyright ownership and
patent rights, especially when a contribution was created as part of someone's employment. Without a signed agreement,
the university cannot safely accept external contributions or change licensing terms later.

## Policy

Every commit in a pull request to an edge-toolkit repository must be covered by a signed Contributor Agreement before
the pull request is merged. The agreement is a Harmony-based individual (or entity) non-exclusive licence agreement,
published as `CLA.md` in the edge-toolkit/core repository.

Under the agreement, contributors keep the copyright in their contributions and grant Curtin University a worldwide,
royalty-free, non-exclusive, perpetual and irrevocable licence, with the right to sublicense on any terms, commercial
ones included, plus the traditional patent licence option.

Signatures are collected through [CLA assistant](https://cla-assistant.io/edge-toolkit/core), which asks for a
signature in a comment on a contributor's first pull request. If a contribution was created as part of the
contributor's employment, the employer must approve the agreement before signing. Where a legal entity holds the
copyright, the entity signs the agreement itself. An entity agreement settles ownership and employer approval, but
does not replace individual signatures: every commit author still completes the CLA assistant flow under their own
GitHub account before their pull request can merge.

## Scope

This policy applies to everyone who authors commits submitted to edge-toolkit repositories, external contributors and
organisation members alike. It is introduced in edge-toolkit/core and extends to every organisation repository that
accepts contributions.

## Compliance

CLA assistant reports a status check on each pull request showing whether all commit authors have signed.

A commit must not credit a coding agent as author, committer or in a `-by` trailer, because an agent cannot sign the
agreement. Maintainers verify that every person credited in a `-by` trailer has signed the agreement before the pull
request is merged.

## Enforcement

A pull request whose commit authors have not all signed the agreement is not merged. Questions and employer or entity
approvals go to the policy owner at <john.vandenberg@curtin.edu.au>.

## Review History

| Date       | Reviewer | Changes                                           |
| ---------- | -------- | ------------------------------------------------- |
| 2026-11-11 | @jayvdb  | Initial policy drafted from edge-toolkit/core#183 |
