# Community Use Guide

## Purpose

This repository is a public evidence board for G1 hardware action-precheck validation.

It is also a lightweight intake point for sanitized action-before-execution samples from engineers, researchers, robot developers, and AI-agent builders.

## How To Use This Repository

### 1. Review Existing Evidence

Start with:

- `README.md`
- `docs/2026-07-08-board-public-record.md`
- `docs/unplug-recovery-public-record.md`
- `docs/capability-overview.md`
- `docs/technical-boundary.md`

These files show the current public test boundary and known evidence.

### 2. Submit A Sanitized Sample

Open a GitHub Issue with the title prefix:

```text
[Sample] short scenario name
```

Use the guide:

- `docs/sample-submission-guide.md`

Only submit sanitized action material. Do not submit customer data, source code, credentials, device identifiers, production logs, exact facility names, or confidential configuration.

### 3. Expected Feedback

For suitable samples, the expected feedback format is described here:

- `docs/report-format.md`

The goal is to return an engineering-style review, not marketing text.

## Suitable Sample Types

| Type | Example |
| --- | --- |
| AI-agent action request | A tool call or command that should be checked before execution |
| Robot action material | A simplified manipulator, mobile-base, or tool-end action request |
| Missing-boundary action | A command with incomplete parameters or unclear safe range |
| Risky action | A command that should be blocked, narrowed, repaired, or reviewed |
| Link or transport anomaly | A case where interruption or partial data must not become action approval |

## Not Suitable

Please do not submit:

- Private source code.
- Customer logs.
- Credentials, keys, tokens, or authentication material.
- Device identifiers.
- Exact production topology.
- Facility names or private asset names.
- Payloads intended to damage third-party systems.

## Current Boundary

G1 is currently presented here as a controlled board-side validation prototype.

This repository does not claim production deployment, industrial safety certification, replacement of existing controllers, or customer-site integration.
