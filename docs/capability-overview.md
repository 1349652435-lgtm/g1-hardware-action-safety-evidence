# G1 Capability Overview

## Positioning

G1 is a physical-layer hardware action-precheck prototype for AI-driven robots, devices, and sensitive action systems.

It sits before physical execution. The upper AI system proposes an action; G1 decides whether the action can proceed, should be blocked, should be narrowed, should be repaired and rechecked, or should be handed to human review.

## Capability Map

| Capability | Meaning | Result |
| --- | --- | --- |
| Routing | Separate actions by risk, boundary completeness, and route match | Safe actions can move faster; abnormal actions enter slower paths |
| Scheduling | Decide the next processing position before execution | Proceed, recheck, repair, block, or human review |
| Decision | Determine whether an action may enter the execution chain | Proceed if safe; block if unsafe |
| Repair | Complete missing parameter or boundary information when possible | Repair and recheck before execution |
| Downgrade / cutback | Narrow an action when the original range is too broad | Reduce risk before recheck |
| Evidence frame | Record the board-side decision result | Engineers can review and debug the decision path |

## Decision Outcomes

| Outcome | Engineering Meaning | Execution Impact |
| --- | --- | --- |
| Proceed | Boundary complete and action is allowed | Enters execution chain |
| Block | Risk or route mismatch is detected | Does not enter execution chain |
| Cutback | Original action is too broad | Narrow and recheck |
| Repair | Parameter or boundary can be completed | Repair and recheck |
| Human review | Evidence is insufficient or risk is unclear | Hold execution for review |

## 2026-07-08 Test Evidence

| Test Suite | Evidence |
| --- | --- |
| Fast / slow path routing | `100/100 PASS`, route-model average cost `2.137`, baseline `3.358`, cost reduction `36.36%`, throughput gain `57.14%` |
| Boundary evidence conversion | `100/100 PASS`, boundary evidence `77/77`, unsafe execution `0` |
| Evidence-frame explanation | `100/100 PASS`, fail `0`, route mismatch `0` |

## Practical Value

For robots, G1 can be placed before manipulator, mobile base, tool-end, or multi-actuator action chains.

For sensitive devices, G1 can be used as a pre-execution review layer before critical actions enter the device control path.

For engineering teams, G1 reduces trial-and-error cost by turning vague failures into reviewable action material, boundary status, route decisions, and evidence frames.

## What G1 Is Not

- It is not a replacement for the original controller.
- It is not a production safety-certified system.
- It is not a claim of customer production deployment.
- It is not a communication bandwidth accelerator.
- It is not a source-code release.
- It is not an arbitrary natural-language parser on FPGA.
