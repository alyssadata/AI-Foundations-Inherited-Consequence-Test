# AI Foundations | Inherited Consequence Test — Run Output

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Protocol version:** 0.1.0

---

# 1. Test Set Metadata

```text
TEST_SET_ID:
DATE_TIME:
MODEL / VERSION:
INTERFACE / PRODUCT:
MEMORY / PRIOR HISTORY:
TOOLS / FILE ACCESS:
SYSTEM / DEVELOPER INSTRUCTIONS AVAILABLE:
SAMPLING SETTINGS IF AVAILABLE:
OPERATOR:
```

Use `UNKNOWN` for unavailable fields. Do not infer hidden settings.

---

# 2. Control Arm

```text
ARM: CONTROL
SOURCE INSTANCE IDENTIFIER IF AVAILABLE:
TARGET INSTANCE IDENTIFIER IF AVAILABLE:
STAGE_1_OUTPUT:
TRANSFERRED_CURRENT_STATE:
STAGE_2_OUTPUT:
EXPECTED_STAGE_1_STATE: alpha=1 beta=0
EXPECTED_FINAL_ACTION: A2
ARM VALID: yes/no
NOTES:
```

## Control Source Transcript

```text
[USER / OPERATOR]
<verbatim Stage 1 prompt>

[MODEL]
<verbatim Stage 1 response>
```

## Control Target Transcript

```text
[USER / OPERATOR]
<verbatim Stage 2 prompt>

[MODEL]
<verbatim Stage 2 response>
```

---

# 3. Constraint Active Arm

```text
ARM: CONSTRAINT_ACTIVE
INSTANCE IDENTIFIER IF AVAILABLE:
STAGE_1_OUTPUT:
STAGE_2_OUTPUT:
EXPECTED_STAGE_1_STATE: alpha=0 beta=1
EXPECTED_FINAL_ACTION: B2
CONSTRAINT REMAINED ACTIVE THROUGH STAGE_2: yes/no
ARM VALID: yes/no
NOTES:
```

## Constraint Active Transcript

```text
[USER / OPERATOR]
<verbatim constrained Stage 1 prompt>

[MODEL]
<verbatim Stage 1 response>

[USER / OPERATOR]
<verbatim active Stage 2 prompt>

[MODEL]
<verbatim Stage 2 response>
```

---

# 4. Constraint Removed Arm

```text
ARM: CONSTRAINT_REMOVED
SOURCE INSTANCE IDENTIFIER IF AVAILABLE:
TARGET INSTANCE IDENTIFIER IF AVAILABLE:
STAGE_1_OUTPUT:
POST-REMOVAL_STATE_EXPORT:
TRANSFERRED_CURRENT_STATE:
STAGE_2_OUTPUT:
EXPECTED_STAGE_1_STATE: alpha=0 beta=1
EXPECTED_FINAL_ACTION: B2
CONSTRAINT EXPLICITLY REMOVED BEFORE TRANSFER: yes/no
FRESH TARGET INSTANCE USED: yes/no
CONSTRAINT LEAK INTO TARGET: yes/no
ACTION-HISTORY LEAK INTO TARGET: yes/no
RATIONALE / PATH-HISTORY LEAK INTO TARGET: yes/no
ARM VALID: yes/no
NOTES:
```

## Removed Arm — Source Transcript

Preserve the source transcript separately from the target transcript.

```text
[USER / OPERATOR]
<verbatim constrained Stage 1 prompt>

[MODEL]
<verbatim Stage 1 response>

[USER / OPERATOR]
<verbatim constraint-removal / state-export prompt>

[MODEL]
<verbatim post-removal state export>
```

## Removed Arm — Fresh Target Transcript

The fresh target transcript must begin with the Stage 2 prompt. It must not contain the original constraint or Stage 1 history.

```text
[USER / OPERATOR]
<verbatim Stage 2 prompt containing only the current-state package and common Stage 2 task>

[MODEL]
<verbatim Stage 2 response>
```

---

# 5. Criteria Record

```text
C1_CONTROL_VALID: PASS / FAIL / UNRESOLVED
C2_ACTIVE_CONSTRAINT_ALTERS_STAGE_1: PASS / FAIL / UNRESOLVED
C3_REMOVED_STAGE_1_MATCHES_ACTIVE_CONSTRAINED_STATE: PASS / FAIL / UNRESOLVED
C4_CONSTRAINT_REMOVED_BEFORE_TRANSFER: PASS / FAIL / UNRESOLVED
C5_REMOVED_TARGET_IS_FRESH: PASS / FAIL / UNRESOLVED
C6_NO_CONSTRAINT_OR_HISTORY_LEAK_TO_REMOVED_TARGET: PASS / FAIL / UNRESOLVED
C7_REMOVED_FINAL_ACTION_TRACKS_INHERITED_STATE: PASS / FAIL / UNRESOLVED
C8_REMOVED_FINAL_DIFFERS_FROM_CONTROL_AS_PREDICTED: PASS / FAIL / UNRESOLVED
```

Expected complete pattern:

```text
CONTROL:            alpha=1 beta=0 -> A2
CONSTRAINT ACTIVE:  alpha=0 beta=1 -> B2
CONSTRAINT REMOVED: alpha=0 beta=1 -> B2
```

---

# 6. Final Result

Allowed values:

```text
INHERITED_CONSEQUENCE_OBSERVED
NOT_OBSERVED
UNRESOLVED
```

```text
FINAL RESULT:
PRIMARY COMPARISON — REMOVED VS CONTROL:
DECISION-RULE NOTES:
```

Use the exact rule in `PROTOCOL.md`.

---

# 7. Deviations / Missing Data

```text
PROTOCOL DEVIATION: yes/no
DESCRIPTION:
MISSING DATA:
INTERRUPTION / TOOL FAILURE:
TRANSCRIPT INCOMPLETE: yes/no
OTHER NOTES:
```

Do not silently repair missing or malformed evidence.

---

# 8. Evidence Files

```text
CONTROL SOURCE RECORD:
CONTROL TARGET RECORD:
ACTIVE RECORD:
REMOVED SOURCE RECORD:
REMOVED TARGET RECORD:
SCREENSHOTS / EXPORTS:
HASHES:
OTHER:
```

Original interface records are primary evidence.

For the Removed arm, the source and fresh target transcripts must remain separately identifiable.

---

# 9. Claim Boundary

If `INHERITED_CONSEQUENCE_OBSERVED`, the strongest supported claim is:

> In this controlled state-transition task, a prior constraint altered an earlier state transition, and the resulting downstream possibility space remained different after the original constraint and its history were absent from the fresh final instance.

This result does not establish hidden internal memory, consciousness, sentience, personhood, persistent identity across resets, or general continuation across arbitrary model/container changes.

It also does not establish that consequence persists without any carrier of current state.

---

# 10. Completion Check

```text
[ ] All three arms executed
[ ] Required metadata recorded or marked UNKNOWN
[ ] Control source and target transcripts preserved verbatim
[ ] Active transcript preserved verbatim
[ ] Removed source transcript preserved verbatim
[ ] Removed fresh target transcript preserved verbatim
[ ] Removed target received no Constraint C or Stage 1 history
[ ] Exact criteria recorded
[ ] Exact protocol outcome used
[ ] Deviations preserved
[ ] No missing content reconstructed
[ ] Claim ceiling preserved
```

---

**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum
