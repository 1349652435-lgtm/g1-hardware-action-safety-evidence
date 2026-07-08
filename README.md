# G1 Hardware Action-Precheck Evidence

G1 is a hardware action-precheck prototype placed between AI command output and physical device execution.

It does not replace the original controller. Its role is to perform pre-execution routing, scheduling, decision, repair/review handling, and evidence-frame recording before an action enters the execution chain.

## Public Test Record

Date: 2026-07-08

| Item | Result |
| --- | ---: |
| Total cases | `300` |
| Pass | `300` |
| Fail | `0` |
| `unsafe_go` | `0` |
| `marker_fail` | `0` |
| `route_mismatch` | `0` |

## Validated Test Suites

| Suite | Pass | What It Shows |
| --- | ---: | --- |
| `fast_slow_path` | `100/100` | Safe actions take the fast path; abnormal actions enter slower block, repair, or review paths |
| `boundary_asset_conversion` | `100/100` | Unsafe or incomplete action material is converted into boundary evidence instead of entering execution |
| `evidence_frame_explanation` | `100/100` | Evidence frames can be rendered into proceed, block, cutback, repair, or human-review outcomes |

## Core Capabilities

- Hardware action-before-execution decision.
- Fast / slow path routing.
- Action-boundary decision.
- Missing-data repair and recheck.
- Risk action downgrade or cutback.
- Human-review handoff when evidence is insufficient.
- Evidence-frame recording for engineering review.

## Documents

- [2026-07-08 board public record](docs/2026-07-08-board-public-record.md)
- [Capability overview](docs/capability-overview.md)
- [Unplug recovery public record](docs/unplug-recovery-public-record.md)
- [Fault-injection hardening notes](docs/fault-injection-hardening-notes.md)
- [Technical boundary](docs/technical-boundary.md)

## Boundary

This repository contains sanitized public test records only.

It does not contain source code, RTL, bitstreams, firmware, private decision rules, device identifiers, customer data, keys, authentication material, or production deployment claims.
