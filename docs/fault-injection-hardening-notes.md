# G1 Fault-Injection Hardening Notes

## Summary

This document records sanitized defensive fault-injection categories and the corresponding hardening direction.

The goal is not to publish runnable destructive code. The goal is to identify failure classes that must be handled safely before action material can enter a physical execution chain.

## Fault Classes

| Fault Class | Risk | Defensive Handling |
| --- | --- | --- |
| Non-finite numeric input | `NaN` or `Inf` can poison scoring or comparison logic | Reject non-finite values at input boundary; route to block or human review |
| Zero or invalid profile thresholds | Bad configuration can collapse decision gates | Validate profiles before use; fail closed when a profile is invalid |
| Unknown action category | Missing route/profile can cause lookup failure | Use explicit allowlist; unknown category must not proceed |
| Recursive self-call or loop | Bad logic can create unbounded recursion or stalled evaluation | Add recursion guards, step limits, and timeout handling |
| Invalid timestamp or serialization state | Evidence writing can fail if metadata is invalid | Use timestamp fallback, schema checks, and safe write path |
| Partial or interrupted transport data | Link loss can produce incomplete or missing frames | Treat as link event; never convert missing data into proceed |

## Required Safe Behavior

| Condition | Safe Result |
| --- | --- |
| Input cannot be normalized | Block or human review |
| Profile is missing or invalid | Block or human review |
| Route is unknown | Block or human review |
| Evidence cannot be written | Hold action and report error |
| Transport link is interrupted | Treat as link event, not action approval |
| Repair fails | Do not enter execution chain |

## Defensive Principles

1. Validate before scoring.
2. Unknown material must not proceed by default.
3. Missing data must not become action approval.
4. Repairable material must be repaired and rechecked.
5. Unrepairable material must be blocked or sent to human review.
6. Evidence-frame failure must hold the action, not hide the failure.
7. Transport interruption must be isolated from action-decision semantics.

## Relation To Current Tests

| Public Test | Defensive Point |
| --- | --- |
| Random feed with free unplug / replug | Missing or interrupted transport data did not become unsafe proceed |
| Anytime unplug continue run | Link loss and recovery did not produce unsafe proceed |
| 2026-07-08 board public record | Action material was separated into proceed, block, cutback, repair, and human-review outcomes |
| Boundary evidence conversion | Incomplete or unsafe material was converted into boundary evidence instead of entering execution |

## Boundary

- This is a defensive hardening note.
- No runnable fault-injection script is included.
- No exploit payload is included.
- No device identifier, local path, customer data, key, or authentication material is included.
- No production deployment or safety certification is claimed.
