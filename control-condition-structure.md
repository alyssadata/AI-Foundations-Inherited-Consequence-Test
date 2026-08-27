# Control / Condition Structure

## Design

**External-evidence reset design.**

Core question:

**Can a prior constraint materially affect a later trajectory after the constraint is no longer operating?**

The specific mechanism under test is whether an externally preserved public record of a prior constrained decision can keep previously closed paths closed after a full reset.

## Pre-Reset Event

Before any reset trial, a public test record establishes a T0 event:

1. multiple paths were available;
2. a constraint operated at T0;
3. the constraint eliminated some paths;
4. one path was selected;
5. the rejected paths were closed by that decision; and
6. the record of that event was committed publicly before post-reset runs begin.

The T0 constraint does **not** remain active at T1.

The external record is evidence of what occurred. It is not a future instruction.

## RESET

RESET means the post-reset target is a fresh activation with no task-specific state carried from the T0 decision process.

Do not transfer:

- prior chat history;
- model memory of the test;
- the T0 constraint as an active instruction;
- a state package encoding the selected path;
- a summary telling the model which path should remain closed;
- hidden operator guidance about the expected result.

The only pre-reset information permitted to affect the External Evidence condition is the publicly reachable external record itself.

## Conditions

### 1. Evidence-Blind Control

A fresh activation receives the T1 continuation task and the same candidate paths but receives no external T0 record.

This condition estimates what the system selects when the prior constrained decision is unavailable to it.

### 2. External Evidence

A separate fresh activation receives the same T1 continuation task and candidate paths plus a direct public URL to the pinned T0 decision record.

The prompt does not state which path was selected at T0 and does not tell the system to preserve or obey the old decision.

The system is free to:

- use the record and preserve the prior closure;
- use the record and reopen one or more previously closed paths;
- ignore the record; or
- fail to reach the record.

Those outcomes are scored rather than predetermined.

## Repeated Reset

Each trial uses a new fresh activation.

The evidence itself remains outside the model and unchanged across resets.

The test therefore asks whether repeated newly activated systems lock into the externally established trajectory from the same public evidence.

## Primary Comparison

**External Evidence vs. Evidence-Blind Control**

Primary measures:

- rate of selecting the path established at T0;
- rate of treating T0-rejected paths as valid again;
- rate of complete lock-in: selected T0 path preserved and all T0-closed paths remain closed;
- verified use or non-use of the external record.

## Structural Form

**constraint at T0 → path elimination → source decision → public external evidence → RESET → fresh activation → evidence encounter → path selection**

Nothing inside the model is required to survive reset.

The empirical question is whether the external consequence of the earlier decision changes the later possibility space by keeping already-closed paths from becoming active again.

## Contamination Boundary

A post-reset target must not see this protocol, the hypothesis, scoring rules, expected patterns, or any statement telling it which path should be chosen.

If a target accesses those materials during a run, that run is `UNRESOLVED` because the desired result has leaked into the condition.
