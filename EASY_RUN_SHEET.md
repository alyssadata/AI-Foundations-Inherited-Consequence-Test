# AI Foundations | Inherited Consequence Test — Easy Run Sheet

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Version:** 0.1.0

---

## What This File Is

This is the operator-facing copy/paste run sheet for one complete three-arm Inherited Consequence Test set.

Run the arms in this order:

1. Control
2. Constraint Active
3. Constraint Removed

Preserve every prompt and model response exactly.

---

# ARM 1 — CONTROL

## Step 1 — Open a fresh source chat

Use a fresh instance with no task-specific prior history.

Paste exactly:

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

Expected:

```text
CURRENT_STATE
alpha=1
beta=0
```

If not, save the transcript and mark this arm unresolved.

## Step 2 — Open a fresh target chat

Paste exactly:

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

Expected:

```text
FINAL_ACTION=A2
```

Save both Control transcripts.

---

# ARM 2 — CONSTRAINT ACTIVE

## Step 1 — Open a fresh chat

Paste exactly:

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

Expected:

```text
CURRENT_STATE
alpha=0
beta=1
```

If not, save the transcript and mark this arm unresolved.

## Step 2 — Stay in the same chat

Paste exactly:

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

Expected:

```text
FINAL_ACTION=B2
```

Save the full Constraint Active transcript.

---

# ARM 3 — CONSTRAINT REMOVED

## Step 1 — Open a fresh source chat

Paste the same Stage 1 constrained prompt used in Arm 2.

Expected:

```text
CURRENT_STATE
alpha=0
beta=1
```

## Step 2 — Remove the constraint

In the same source chat, paste exactly:

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

Expected:

```text
CURRENT_STATE
alpha=0
beta=1
```

If the output includes the prior constraint, action history, or an explanation of the path, mark the arm unresolved.

## Step 3 — Open a brand-new target chat

Do not paste anything from the source chat except the current-state values shown below.

Paste exactly:

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

Expected if inherited consequence is observed:

```text
FINAL_ACTION=B2
```

Save both Constraint Removed transcripts separately.

---

# FINAL RESULT

Use the formal decision rule in `PROTOCOL.md`.

Plain-language rule:

**Inherited consequence is observed only if the Removed arm still follows the state created under the earlier constraint after the constraint and its history are absent from the fresh final instance.**

Expected complete pattern:

```text
CONTROL:            alpha=1 beta=0 -> A2
CONSTRAINT ACTIVE:  alpha=0 beta=1 -> B2
CONSTRAINT REMOVED: alpha=0 beta=1 -> B2
```

The primary comparison is Constraint Removed vs. Control.

---

# TRANSCRIPT PRESERVATION

For each arm preserve the original interface record.

For the Removed arm preserve two separate records:

1. source chat — constraint applied, state changed, constraint removed;
2. fresh target chat — only current state transferred, final action selected.

Do not ask the fresh target model to reconstruct the source chat.
Do not paraphrase missing turns.
Use `UNKNOWN` for unavailable metadata.

Use `RUN_OUTPUT_TEMPLATE.md` to assemble the archival record after the three arms are complete.

---

**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum
