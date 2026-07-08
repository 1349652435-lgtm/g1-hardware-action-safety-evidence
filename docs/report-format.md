# Public Report Format

When a sanitized sample is reviewed, the expected response should be concise and engineering-oriented.

## Report Structure

```text
sample_id:
review_status:
decision:
reason:
missing_boundary:
suggested_next_step:
evidence_frame_view:
limits:
```

## Field Guide

| Field | Meaning |
| --- | --- |
| `sample_id` | The non-sensitive sample label |
| `review_status` | Reviewed, needs more information, out of scope, or rejected for privacy/safety |
| `decision` | Proceed, block, cutback, repair, human review, or not enough evidence |
| `reason` | Short explanation of the decision path |
| `missing_boundary` | Boundary fields or constraints that are missing |
| `suggested_next_step` | What should be changed before recheck |
| `evidence_frame_view` | Human-readable view of the expected evidence-frame result |
| `limits` | What this review does not prove |

## Example

```text
sample_id: robot_arm_case_001
review_status: reviewed
decision: cutback + human review
reason: target zone is too broad and force limit is missing
missing_boundary: force_limit, exact safe zone
suggested_next_step: add force limit and narrow target zone before recheck
evidence_frame_view: action cannot proceed directly; retain boundary evidence
limits: sanitized review only; not a production safety certification
```

## Report Rules

- Do not expose private implementation details.
- Do not return customer data.
- Do not claim production certification.
- Do not claim replacement of existing controllers.
- Keep the result tied to the provided sanitized sample.
