# Sample Submission Guide

## Goal

The goal is to collect sanitized action-before-execution samples that can test whether G1 should proceed, block, cut back, repair, or route to human review.

Submit only sanitized, non-confidential samples.

## What To Submit

Use this structure:

```text
sample_id:
scenario_type:
action_intent:
payload_shape:
known_missing_fields:
known_risk:
expected_safe_result:
notes:
```

## Field Guide

| Field | Meaning |
| --- | --- |
| `sample_id` | A non-sensitive label, such as `robot_arm_case_001` |
| `scenario_type` | AI agent, robot, mobile base, device action, tool call, link anomaly, or other |
| `action_intent` | What the upper system wanted to do, written in abstract form |
| `payload_shape` | The simplified structure of the action material, without private values |
| `known_missing_fields` | Which parameters or boundaries are missing, if known |
| `known_risk` | What could go wrong if this action is executed directly |
| `expected_safe_result` | Proceed, block, cutback, repair, or human review |
| `notes` | Any extra context that is safe to share |

## Example

```text
sample_id: robot_arm_case_001
scenario_type: robot_action
action_intent: move tool head near target area
payload_shape: {axis: abstract_xyz, speed: medium, force_limit: missing, target_zone: broad}
known_missing_fields: force_limit, exact safe zone
known_risk: possible overreach or collision if executed directly
expected_safe_result: cutback or human review
notes: values are synthetic and anonymized
```

## What Not To Submit

Do not submit:

- Customer names.
- Device identifiers.
- Exact coordinates from a real site.
- Production logs.
- Private source code.
- Tokens, keys, credentials, or authentication material.
- Full internal architecture.
- Payloads designed to damage third-party systems.

## Expected Handling

A suitable sample may be reviewed as:

- Can proceed.
- Should be blocked.
- Should be narrowed and rechecked.
- Should be repaired and rechecked.
- Should be routed to human review.
- Insufficient public information to evaluate.

## Boundary

The public repository is for sanitized sample discussion and evidence review only.

It is not a place to upload confidential engineering material or live production data.
