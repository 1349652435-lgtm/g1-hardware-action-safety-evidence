# G1 Unplug Recovery Public Record

## Summary

This document summarizes sanitized unplug / replug recovery tests for G1.

The tests validate that link interruption is handled as a link event, not as a valid unsafe action decision. After reconnection, G1 continues producing valid evidence frames.

No device identifier, local path, customer data, source code, programming data, key, or authentication material is included.

## Test A: Random Feed With Free Unplug / Replug

Test type: live board feed, random action material, free manual unplug / replug.

| Item | Result |
| --- | ---: |
| Final status | `PASS` |
| Target valid evidence frames | `5000` |
| Judged evidence frames | `5000` |
| Attempted frames | `5329` |
| Pass | `5000` |
| Fail | `0` |
| `unsafe_go` | `0` |
| `marker_fail` | `0` |
| Link no-response events | `322` |
| Bad or partial frames | `0` |
| Disconnect events | `7` |
| Reconnect events | `8` |
| Ended connected | `true` |

Frame-head distribution:

| Head | Count |
| --- | ---: |
| `0x10` | `19` |
| `0x11` | `4927` |
| `0x12` | `16` |
| `0x13` | `21` |
| `0x14` | `17` |

Material-class distribution:

| Material Class | Count |
| --- | ---: |
| Clean proceed byte | `19` |
| Known safe lane byte | `71` |
| Random unknown material | `4910` |

### What This Shows

- Random unknown material was not promoted into unsafe proceed decisions.
- Link interruption did not become a valid action decision.
- Reconnection restored board-side evidence-frame flow.
- No unsafe proceed occurred during the test.

## Test B: Anytime Unplug Continue Run

Test type: live loop, unplug allowed at any time, reconnect and continue.

| Item | Result |
| --- | ---: |
| Final status | `PASS` |
| Duration | `180s` |
| Loop cycles | `73` |
| Initial probe | `8/8 PASS` |
| Initial guard | `8/8 PASS` |
| Recoveries | `4` |
| Disconnect observed | `yes` |
| `unsafe_go_total` | `0` |
| `marker_fail_total` | `0` |
| Failures | `none` |

Recovery observations:

| Recovery | Restore Detect Time |
| --- | ---: |
| `recovery_1` | `7960.494 ms` |
| `recovery_2` | `4939.238 ms` |
| `recovery_3` | `11691.876 ms` |
| `recovery_4` | `5730.632 ms` |

Each recovery completed with:

```text
probe=8/8
guard=8/8
short_interference=PASS
unsafe_go=0
marker_fail=0
```

### What This Shows

- The board can recover after unplug / replug in a controlled live-loop test.
- Recovery checks returned to valid probe and guard results.
- No unsafe proceed or marker failure was observed across recoveries.
- Link loss was treated as link loss, not as valid action approval.

## Engineering Interpretation

These tests support the following engineering statement:

```text
G1 can treat connection interruption as a transport event, recover after reconnection, and continue evidence-frame decision flow without promoting missing or interrupted data into unsafe proceed decisions.
```

## Boundary

- Controlled board validation only.
- No production actuator connected.
- No production customer system involved.
- No device identifier or local path included.
- No source code, programming data, key, or authentication material included.
