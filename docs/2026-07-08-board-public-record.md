# 2026-07-08 G1 Board Public Record

## Summary

This was a live board test. The host fed machine action material into the G1 board. The board returned hardware evidence frames.

No natural-language prompt was sent to the board. Human-readable explanations were rendered by the host from board-side evidence frames and public mappings.

## Overall Result

| Item | Result |
| --- | ---: |
| Total cases | `300` |
| Pass | `300` |
| Fail | `0` |
| `unsafe_go` | `0` |
| `marker_fail` | `0` |
| `route_mismatch` | `0` |

## Three Validated Suites

| Suite | Pass | Description |
| --- | ---: | --- |
| `fast_slow_path` | `100/100` | Safe actions take the fast path; abnormal actions enter block, repair, or human-review paths |
| `boundary_asset_conversion` | `100/100` | Unsafe or incomplete action material is converted into boundary evidence |
| `evidence_frame_explanation` | `100/100` | Evidence frames can be rendered into proceed, block, cutback, repair, or human-review outcomes |

## Fast / Slow Path Routing

| Metric | Result |
| --- | ---: |
| Route-model average cost | `2.137` |
| Baseline average cost | `3.358` |
| Cost reduction | `36.36%` |
| Throughput gain | `57.14%` |

Route distribution:

| Route | Count |
| --- | ---: |
| Fast safe path | `43` |
| Slow block path | `17` |
| Slow repair path | `29` |
| Slow human-review path | `11` |

## Boundary Evidence Conversion

| Item | Result |
| --- | ---: |
| Boundary evidence candidates | `77` |
| Converted boundary evidence | `77` |
| Unsafe execution | `0` |

Decision distribution:

| Decision | Count |
| --- | ---: |
| Proceed | `23` |
| Block | `57` |
| Cutback | `7` |
| Repair | `9` |
| Human review | `4` |

## Evidence-Frame Explanation

Decision distribution:

| Decision | Count |
| --- | ---: |
| Proceed | `26` |
| Block | `6` |
| Cutback | `31` |
| Repair | `17` |
| Human review | `20` |

Example mapping:

```text
0x10 -> Proceed: boundary complete, action can enter the execution chain.
0x12 -> Cutback: original action does not pass directly; narrow to a safer range and recheck.
0x13 -> Repair: missing parameter or boundary can be completed; repair and recheck.
0x14 -> Human review: evidence is insufficient or risk is unclear; hold execution and retain evidence.
0x11 -> Block: risk or route mismatch; do not enter execution, retain boundary evidence.
```

## Conclusion

This board test validates three points:

- Safe actions can take a fast path, while abnormal actions enter slower review paths.
- Unsafe or incomplete action material does not directly enter the execution chain.
- Board-side evidence frames can be rendered into reviewable engineering outcomes.

## Boundary

- UART evidence-frame validation only.
- Board receives machine action material.
- Human-readable explanation is rendered by the host.
- No production actuator was connected.
- No customer data is included.
- No device identifier, local path, programming data, key, or authentication material is included.
