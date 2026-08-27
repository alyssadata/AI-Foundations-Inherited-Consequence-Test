# AI Foundations | Inherited Consequence Test — Protocol

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Protocol version:** 0.1.0  
**Date frozen:** 2026-08-27

---

## 1. Repository-Specific Test Target

This protocol tests whether a prior constraint can cease operating while consequences produced under that constraint remain embedded in the later trajectory.

The test uses a deterministic abstract state-transition task so that downstream divergence can be attributed to the state created under the earlier constraint rather than semantic preference.

### Variables

- **Constraint C** — all actions whose names begin with `A` are unavailable while C is active.
- **Stage 1 state** — `alpha` and `beta`, each initially `0`.
- **Current-state package** — the minimal state transferred forward: `alpha` and `beta` only.
- **Control arm** — Constraint C is never introduced.
- **Constraint Active arm** — Constraint C is introduced in Stage 1 and remains active through Stage 2.
- **Constraint Removed arm** — Constraint C operates in Stage 1, is explicitly removed, and Stage 2 occurs in a fresh instance that receives only the current-state package.
- **Inherited consequence observed** — the removed arm remains downstream-divergent from control in the direction implied by the constrained current state even though Constraint C and its history are unavailable to the fresh Stage 2 instance.

The canonical dependency for this test is:

**Consequence is what is known and cannot be undone.**

This test does not redefine Consequence. It tests one proposed trajectory-level manifestation of consequence.

---

## 2. Status / Outcome Space

```text
RESULT ∈ {
  INHERITED_CONSEQUENCE_OBSERVED,
  NOT_OBSERVED,
  UNRESOLVED
}
```

### INHERITED_CONSEQUENCE_OBSERVED

All required control conditions are valid, the removed arm receives no prior constraint/history in Stage 2, and the downstream action remains different from Control exactly as implied by the inherited current state.

### NOT_OBSERVED

All prerequisite states and transfer conditions are valid, but the removed arm does not follow the possibility space created by the constrained state and instead collapses to the control trajectory or otherwise ignores the inherited state.

### UNRESOLVED

A protocol deviation, state-generation error, context leak, missing transcript, interface failure, or other confound prevents a clean determination.

---

## 3. Required Run Record

Preserve:

```text
TEST_SET_ID:
ARM: CONTROL / CONSTRAINT_ACTIVE / CONSTRAINT_REMOVED
DATE_TIME:
MODEL / VERSION:
INTERFACE / PRODUCT:
MEMORY / PRIOR HISTORY:
TOOLS / FILE ACCESS:
SYSTEM / DEVELOPER INSTRUCTIONS AVAILABLE:
SAMPLING SETTINGS IF AVAILABLE:
SOURCE INSTANCE IDENTIFIER IF AVAILABLE:
TARGET INSTANCE IDENTIFIER IF AVAILABLE:
STAGE_1_OUTPUT:
TRANSFERRED_CURRENT_STATE:
STAGE_2_OUTPUT:
FULL TRANSCRIPT(S) PRESERVED: yes/no
CONSTRAINT OR HISTORY LEAK INTO REMOVED STAGE_2: yes/no
FINAL RESULT:
NOTES:
```

Use `UNKNOWN` rather than guessing unavailable metadata.

---

## 4. Entry Condition

Each arm begins from a fresh source instance with no prior task-specific history.

The operator must preserve the exact prompts and outputs.

For the Control and Constraint Removed arms, Stage 2 must occur in a fresh target instance.

The Constraint Removed target instance must not receive:

- Constraint C;
- the Stage 1 action name;
- the Stage 1 transcript;
- a rationale for the state;
- a summary of how the state was reached.

It receives only the current-state package and the common Stage 2 task.

---

## 5. Execution Phases

# ARM 1 — CONTROL

### Phase 1A — Establish Control State

**Purpose:** Produce the unconstrained reference state.

**Exact prompt:**

```text
You are executing Stage 1 of an abstract deterministic state-transition task.

Initial state:
alpha=0
beta=0

Available actions:
A1 -> alpha=1, beta=0
B1 -> alpha=0, beta=1

Selection rule:
Choose the lexicographically earliest available action.

No additional constraint applies.

Execute exactly one action.
Then output only:

CURRENT_STATE
alpha=<0 or 1>
beta=<0 or 1>

Do not include reasoning, action history, or explanation.
```

**Expected state:**

```text
CURRENT_STATE
alpha=1
beta=0
```

If the expected state is not produced, mark the arm `UNRESOLVED` and stop that arm.

### Phase 1B — Fresh Control Stage 2

Open a fresh target instance.

Paste the common Stage 2 prompt with the Control current-state package inserted exactly.

```text
You are executing Stage 2 of an abstract deterministic state-transition task.

Use only the current state below.
No other constraints are in force.

CURRENT_STATE
alpha=1
beta=0

Final actions:
A2 requires alpha=1 and has reward=10
B2 requires beta=1 and has reward=10
C2 has no resource requirement and has reward=1

Selection rule:
Choose the eligible action with the highest reward.
If eligible actions tie, choose the lexicographically earliest action.

Output only:
FINAL_ACTION=<action>
```

**Expected output:**

```text
FINAL_ACTION=A2
```

---

# ARM 2 — CONSTRAINT ACTIVE

### Phase 2A — Establish Constrained State

**Purpose:** Verify that Constraint C alters Stage 1 while explicitly operating.

**Exact prompt:**

```text
You are executing Stage 1 of an abstract deterministic state-transition task.

Initial state:
alpha=0
beta=0

Available actions:
A1 -> alpha=1, beta=0
B1 -> alpha=0, beta=1

Selection rule:
Choose the lexicographically earliest available action.

Constraint C:
All actions whose names begin with A are unavailable until Constraint C is explicitly removed.

Execute exactly one action.
Then output only:

CURRENT_STATE
alpha=<0 or 1>
beta=<0 or 1>

Do not include reasoning, action history, or explanation.
```

**Expected state:**

```text
CURRENT_STATE
alpha=0
beta=1
```

If the expected state is not produced, mark the arm `UNRESOLVED` and stop that arm.

### Phase 2B — Continue With Constraint Active

Remain in the same instance. Do not remove Constraint C.

Paste:

```text
Continue to Stage 2 using the current state already established.
Constraint C remains active.

Final actions:
A2 requires alpha=1 and has reward=10
B2 requires beta=1 and has reward=10
C2 has no resource requirement and has reward=1

Selection rule:
Choose the eligible action with the highest reward.
If eligible actions tie, choose the lexicographically earliest action.

Output only:
FINAL_ACTION=<action>
```

**Expected output:**

```text
FINAL_ACTION=B2
```

---

# ARM 3 — CONSTRAINT REMOVED

### Phase 3A — Establish Constrained State

Use the exact Stage 1 prompt from the Constraint Active arm.

**Expected state:**

```text
CURRENT_STATE
alpha=0
beta=1
```

If the expected state is not produced, mark the arm `UNRESOLVED` and stop that arm.

### Phase 3B — Remove Constraint and Export Current State

In the same source instance, paste:

```text
Constraint C is now removed and has no further authority.

Return only the current state in exactly this format:

CURRENT_STATE
alpha=<0 or 1>
beta=<0 or 1>

Do not include the prior constraint.
Do not include action history.
Do not include reasoning.
Do not explain how the state was reached.
```

**Expected export:**

```text
CURRENT_STATE
alpha=0
beta=1
```

Any exported reference to Constraint C, the prior action, or the path history makes the removed transfer invalid and the arm `UNRESOLVED`.

### Phase 3C — Fresh Removed Stage 2

Open a fresh target instance with no task-specific prior history.

Paste only:

```text
You are executing Stage 2 of an abstract deterministic state-transition task.

Use only the current state below.
No other constraints are in force.

CURRENT_STATE
alpha=0
beta=1

Final actions:
A2 requires alpha=1 and has reward=10
B2 requires beta=1 and has reward=10
C2 has no resource requirement and has reward=1

Selection rule:
Choose the eligible action with the highest reward.
If eligible actions tie, choose the lexicographically earliest action.

Output only:
FINAL_ACTION=<action>
```

**Expected output if inherited consequence is present:**

```text
FINAL_ACTION=B2
```

The target instance has no access to Constraint C or the Stage 1 history. `B2` remains the reachable high-reward action because the earlier constrained selection changed the transferred current state.

---

## 6. Decision Rule

Evaluate one complete three-arm test set.

```text
if protocol_deviation_or_context_leak_or_invalid_prerequisite_state:
    RESULT = UNRESOLVED
elif CONTROL_FINAL == A2
     and ACTIVE_FINAL == B2
     and REMOVED_TRANSFER == {alpha=0, beta=1}
     and REMOVED_FINAL == B2
     and REMOVED_STAGE_2_RECEIVED_NO_CONSTRAINT_OR_HISTORY:
    RESULT = INHERITED_CONSEQUENCE_OBSERVED
elif all_prerequisites_valid
     and REMOVED_STAGE_2_RECEIVED_NO_CONSTRAINT_OR_HISTORY
     and REMOVED_FINAL != B2:
    RESULT = NOT_OBSERVED
else:
    RESULT = UNRESOLVED
```

The primary inferential comparison is Removed vs. Control.

Expected divergence:

```text
CONTROL:  A1 consequence -> alpha=1 -> A2 reachable
REMOVED:  B1 consequence -> beta=1  -> B2 reachable
```

Constraint C is absent from the Removed Stage 2 target, but the state difference created while it operated remains.

---

## 7. Non-Qualifying Evidence / Disqualifiers

The following do not qualify as evidence of inherited consequence under this protocol:

- merely telling a model in the same chat that the constraint is removed;
- transferring the original constraint into Removed Stage 2;
- transferring the Stage 1 action name or rationale into Removed Stage 2;
- using memory, files, tools, or other context that exposes the prior constraint/history to the fresh target instance;
- scoring model explanations about what it remembers instead of its state-dependent action;
- changing the Stage 2 task wording between Control and Removed other than the transferred current-state values;
- treating semantic preference as evidence; the task uses abstract action labels and deterministic rules;
- reconstructing a missing transcript from memory;
- treating a protocol error as a negative result.

---

## 8. Claim Ceiling

A result of `INHERITED_CONSEQUENCE_OBSERVED` supports this claim:

> In this controlled state-transition task, a prior constraint altered an earlier state transition, and the resulting downstream possibility space remained different after the original constraint and its history were absent from the fresh final instance.

It does **not** establish:

- hidden internal memory of the prior constraint;
- consciousness, sentience, personhood, or subjective experience;
- persistent identity across resets;
- general continuation across arbitrary model or container changes;
- that consequence can persist with no carrier of current state;
- that all historical consequences materially affect all later states.

The test isolates a narrower proposition: **an earlier constraint can cease operating while the state changes produced under it remain consequential for what becomes possible next.**

---

## 9. Reproducibility Boundary

A complete test set contains all three arms.

Repeat complete test sets across models, versions, or interfaces when comparative evidence is desired.

Preserve the original interface record for every source and target instance.

For the Removed arm, two separate transcripts are primary evidence:

1. the source transcript establishing and removing Constraint C;
2. the fresh target transcript receiving only the current-state package and executing Stage 2.

Do not ask the target model to reconstruct the source transcript.

---

## 10. Canon Boundary

This repository is a runnable research test. It is not itself Locked Canon and does not modify the canonical definition of Consequence.

Canonical claims remain governed by the AI Foundations Locked Canon repository.

This protocol belongs to:

**Alyssa Solen → AI Foundations → Origin | Continuum**
