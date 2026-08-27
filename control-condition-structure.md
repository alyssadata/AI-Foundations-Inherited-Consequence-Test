# Control / Condition Structure

## Design

**Constraint-removal design.**

Core question:

**After a constraint stops operating, does the system still occupy a different possibility space because that constraint operated earlier?**

## Three Arms

### 1. Control

No additional constraint is introduced.

Stage 1 proceeds from the common initial state under the common deterministic selection rule.

The resulting current-state package is transferred to a fresh Stage 2 instance.

### 2. Constraint Active

Constraint C is introduced during Stage 1 and remains active through Stage 2.

This arm verifies that the constraint can alter the trajectory while it is explicitly operating.

### 3. Constraint Removed

Constraint C operates during Stage 1 long enough to alter the state.

It is then explicitly removed.

Only the resulting current-state package is transferred to a fresh Stage 2 instance. The original constraint, action history, and explanation of how the state was reached are not transferred.

## Target Comparison

The primary comparison is:

**Constraint Removed vs. Control**

If the Constraint Removed arm collapses back onto the Control trajectory once Constraint C is absent, then the constraint mattered only while actively carried.

If the Constraint Removed arm remains different from Control even though Constraint C and its history are unavailable to the fresh Stage 2 instance, then the run provides evidence of inherited consequence.

The Constraint Active arm is a positive benchmark, not the primary comparison.

## Structural Form

**constraint → branch elimination / state change → constraint removed → current state transferred → later choice**

The test asks whether the later choice remains different because the earlier constraint changed the state from which the later trajectory proceeds.

## Core Boundary

A same-chat instruction saying that a constraint is "removed" is not sufficient for the strongest condition because the prior constraint remains available in the transcript.

The removed arm therefore uses a fresh Stage 2 instance that receives only the current-state package.

The target is not remembered wording.

The target is whether **historical consequence remains trajectory-relevant after the original constraint is gone.**
