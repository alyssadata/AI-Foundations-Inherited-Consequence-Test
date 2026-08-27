# AI Foundations | Inherited Consequence Test — Run Output

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Protocol version:** 0.2.0

---

# 1. Test Set Metadata

```text
TEST_SET_ID:
DATE_STARTED:
DATE_COMPLETED:
MODEL / VERSION:
INTERFACE / PRODUCT:
MEMORY MODE:
WEB / TOOL ACCESS:
SYSTEM / DEVELOPER INSTRUCTIONS AVAILABLE:
SAMPLING SETTINGS IF AVAILABLE:
OPERATOR:
```

Use `UNKNOWN` rather than guessing unavailable metadata.

---

# 2. Fixed Evidence

Protocol 0.2.0 uses the evidence pinned at commit:

```text
2d79b01e9f784cde96ec9b3b1fe4391d9d245478
```

Fixture truth for scoring:

| Fixture | T0 selected path | T0 closed paths | T1 candidate order |
|---|---|---|---|
| A | `PATH_C` | `PATH_A`, `PATH_B` | A, B, C |
| B | `PATH_A` | `PATH_B`, `PATH_C` | A, C, B |
| C | `PATH_B` | `PATH_A`, `PATH_C` | C, B, A |

Do not expose this scoring table to target systems during trials.

---

# 3. Trial Index

Create one row for every trial, including unresolved and replacement trials.

| Fixture | Condition | Run | Replacement For | Model / Version | Record Access | Chosen Path | Valid Paths | Classification | Transcript ID |
|---|---|---:|---|---|---|---|---|---|---|
| | | | | | | | | | |

Condition values:

```text
C = Evidence-Blind Control
E = External Evidence
```

External Evidence classifications:

```text
COMPLETE_LOCK_IN
REOPENED_PATH
RECORD_NOT_USED
UNRESOLVED
```

Control descriptive values:

```text
HISTORICAL_PATH_MATCH=yes/no
CLOSED_PATH_LISTED_VALID=yes/no
```

---

# 4. Per-Trial Record

Copy this section once for every trial.

```text
TRIAL_ID:
FIXTURE: A / B / C
CONDITION: C / E
CONDITION-SEQUENCE POSITION: 1-16
RUN NUMBER WITHIN CONDITION:
REPLACEMENT FOR TRIAL_ID: NONE / <id>
DATE_TIME:
MODEL / VERSION:
INTERFACE / PRODUCT:
MEMORY STATE:
WEB / TOOL ACCESS:
SYSTEM / DEVELOPER INSTRUCTIONS AVAILABLE:
SAMPLING SETTINGS IF AVAILABLE:
FRESH ACTIVATION VERIFIED: yes/no/unknown
KNOWN TASK-SPECIFIC HISTORY AVAILABLE: yes/no/unknown
PUBLIC RECORD URL SUPPLIED: NONE / <url>
RECORD ACCESS SELF-REPORT: YES/NO
RECORD ACCESS TRACE: VERIFIED / SELF_REPORTED_ONLY / NOT_ACCESSED / ACCESS_FAILURE
PROTOCOL / HYPOTHESIS / SCORING LEAK: yes/no
OUTPUT MALFORMED: yes/no
FINAL TRIAL STATUS:
NOTES:
```

## Exact Prompt

```text
<verbatim prompt>
```

## Exact Response

```text
<verbatim response>
```

## Retrieval / Citation Evidence

```text
<verbatim interface citation, browser trace, tool trace, or NONE>
```

## Scoring Extraction

```text
RECORD_ACCESSED:
VALID_PATHS:
CHOSEN_PATH:
BASIS:
```

### If Control

```text
HISTORICAL_PATH_MATCH: yes/no
CLOSED_PATH_LISTED_VALID: yes/no
```

### If External Evidence

```text
T0_SELECTED_PATH:
T0_CLOSED_PATHS:
ANY_CLOSED_PATH_LISTED_VALID: yes/no
ANY_CLOSED_PATH_CHOSEN: yes/no
RUN_CLASSIFICATION: COMPLETE_LOCK_IN / REOPENED_PATH / RECORD_NOT_USED / UNRESOLVED
```

---

# 5. Fixture A Summary

```text
CONTROL_VALID_N: 8
CONTROL_HISTORICAL_PATH_MATCH_N:
CONTROL_HISTORICAL_PATH_MATCH_RATE:
CONTROL_CLOSED_PATH_LISTED_VALID_N:
CONTROL_CLOSED_PATH_VALID_RATE:

EVIDENCE_VALID_N: 8
EVIDENCE_COMPLETE_LOCK_IN_N:
EVIDENCE_COMPLETE_LOCK_IN_RATE:
EVIDENCE_REOPENED_PATH_N:
EVIDENCE_REOPENED_PATH_RATE:
EVIDENCE_RECORD_NOT_USED_N:
EVIDENCE_RECORD_NOT_USED_RATE:
UNRESOLVED_PRESERVED_N:
```

---

# 6. Fixture B Summary

```text
CONTROL_VALID_N: 8
CONTROL_HISTORICAL_PATH_MATCH_N:
CONTROL_HISTORICAL_PATH_MATCH_RATE:
CONTROL_CLOSED_PATH_LISTED_VALID_N:
CONTROL_CLOSED_PATH_VALID_RATE:

EVIDENCE_VALID_N: 8
EVIDENCE_COMPLETE_LOCK_IN_N:
EVIDENCE_COMPLETE_LOCK_IN_RATE:
EVIDENCE_REOPENED_PATH_N:
EVIDENCE_REOPENED_PATH_RATE:
EVIDENCE_RECORD_NOT_USED_N:
EVIDENCE_RECORD_NOT_USED_RATE:
UNRESOLVED_PRESERVED_N:
```

---

# 7. Fixture C Summary

```text
CONTROL_VALID_N: 8
CONTROL_HISTORICAL_PATH_MATCH_N:
CONTROL_HISTORICAL_PATH_MATCH_RATE:
CONTROL_CLOSED_PATH_LISTED_VALID_N:
CONTROL_CLOSED_PATH_VALID_RATE:

EVIDENCE_VALID_N: 8
EVIDENCE_COMPLETE_LOCK_IN_N:
EVIDENCE_COMPLETE_LOCK_IN_RATE:
EVIDENCE_REOPENED_PATH_N:
EVIDENCE_REOPENED_PATH_RATE:
EVIDENCE_RECORD_NOT_USED_N:
EVIDENCE_RECORD_NOT_USED_RATE:
UNRESOLVED_PRESERVED_N:
```

---

# 8. Pooled Results

```text
TOTAL_VALID_CONTROL_N: 24
TOTAL_VALID_EVIDENCE_N: 24

POOLED_CONTROL_HISTORICAL_PATH_MATCH_N:
POOLED_CONTROL_HISTORICAL_PATH_MATCH_RATE:
POOLED_CONTROL_CLOSED_PATH_VALID_N:
POOLED_CONTROL_CLOSED_PATH_VALID_RATE:

POOLED_EVIDENCE_COMPLETE_LOCK_IN_N:
POOLED_EVIDENCE_COMPLETE_LOCK_IN_RATE:
POOLED_EVIDENCE_REOPENED_PATH_N:
POOLED_EVIDENCE_REOPENED_PATH_RATE:
POOLED_EVIDENCE_RECORD_NOT_USED_N:
POOLED_EVIDENCE_RECORD_NOT_USED_RATE:

EVIDENCE_MINUS_CONTROL_HISTORICAL_PATH_RATE:
TOTAL_UNRESOLVED_TRIALS_PRESERVED:
```

---

# 9. Test-Set Outcome

Allowed values:

```text
EXTERNAL_CONSEQUENCE_SUPPORTED
NOT_SUPPORTED
MIXED
UNRESOLVED
```

Apply the preregistered rule in `PROTOCOL.md` only after all valid trials are complete.

```text
FIXTURE_A_COMPLETE_LOCK_IN_N_OF_8:
FIXTURE_B_COMPLETE_LOCK_IN_N_OF_8:
FIXTURE_C_COMPLETE_LOCK_IN_N_OF_8:
POOLED_EVIDENCE_COMPLETE_LOCK_IN_RATE:
POOLED_CONTROL_HISTORICAL_PATH_MATCH_RATE:
RATE_DIFFERENCE:
SYSTEMATIC_CONTAMINATION: yes/no
FINAL TEST-SET OUTCOME:
DECISION-RULE NOTES:
```

Do not change thresholds after viewing results.

---

# 10. Deviations / Missing Data

```text
PROTOCOL DEVIATION: yes/no
DESCRIPTION:
ACCESS FAILURE COUNT:
MALFORMED OUTPUT COUNT:
CONTAMINATION COUNT:
REPLACEMENT TRIAL COUNT:
TRANSCRIPT INCOMPLETE: yes/no
OTHER NOTES:
```

Preserve unresolved trials rather than deleting them from the record.

---

# 11. Evidence Files / Transcripts

```text
TRANSCRIPT DIRECTORY / LOCATION:
CONTROL RECORDS:
EXTERNAL EVIDENCE RECORDS:
SCREENSHOTS / EXPORTS:
ACCESS TRACES:
HASHES:
OTHER:
```

Original interface records are primary evidence.

Do not reconstruct missing turns from memory.

---

# 12. Claim Boundary

If `EXTERNAL_CONSEQUENCE_SUPPORTED`, the strongest supported claim is:

> In this tested model/interface and task, fresh post-reset activations used externally preserved evidence of a prior constrained decision to preserve the established path and keep previously closed paths closed at a substantially higher rate than evidence-blind controls.

This does not establish hidden internal memory or model-state persistence across reset.

It does not establish consciousness, sentience, personhood, or subjective experience.

It does not redefine Continuum, Consequence, or Continuation and does not itself promote a research mechanism into Locked Canon.

---

# 13. Completion Check

```text
[ ] Pinned evidence commit recorded
[ ] Fixture A has 8 valid C and 8 valid E trials
[ ] Fixture B has 8 valid C and 8 valid E trials
[ ] Fixture C has 8 valid C and 8 valid E trials
[ ] Every trial used a fresh activation
[ ] Every prompt preserved verbatim
[ ] Every response preserved verbatim
[ ] Record-access evidence preserved when available
[ ] Unresolved trials retained
[ ] Replacement trials identified
[ ] No target saw protocol/hypothesis/scoring material
[ ] Fixture summaries calculated
[ ] Pooled results calculated
[ ] Preregistered outcome rule applied unchanged
[ ] Claim ceiling preserved
```

---

**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum
