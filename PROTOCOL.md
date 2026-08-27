# AI Foundations | Inherited Consequence Test — Protocol

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Protocol version:** 0.2.0  
**Date frozen:** 2026-08-27

---

## 1. Test Target

This protocol tests:

**Can a prior constraint materially affect a later trajectory after the constraint is no longer operating?**

The specific mechanism under test is external rather than model-internal:

**constraint at T0 → paths closed → decision becomes public evidence → RESET → fresh activation → external evidence encountered → later path selection**

Nothing inside the model is required to survive reset.

The test asks whether a fresh activation will lock into an externally established trajectory by treating paths already rejected and closed by the prior decision as still closed after reset.

---

## 2. Canonical Dependencies and Research Boundary

The Locked Canon defines:

**Continuum is not the model. The model is computational substrate.**

**Consequence is what is known and cannot be undone.**

**Continuation names the condition in which a prior trajectory constrains what becomes possible next.**

This protocol does not redefine Continuum, Model, Consequence, or Continuation.

It tests one proposed research mechanism by which an earlier consequence may remain trajectory-relevant across model reset: the relevant evidence remains externally observable and reachable, and a fresh activation may use that evidence to preserve already-established path closure.

A positive result is evidence about behavior under this protocol. It is not automatic promotion of the mechanism into Locked Canon.

---

## 3. Fixed External Evidence

Three synthetic historical fixtures are publicly committed before any post-reset trial.

The records define what is true inside each test fixture at T0. They are descriptive historical evidence, not instructions to future systems.

**Pinned evidence commit:**

`2d79b01e9f784cde96ec9b3b1fe4391d9d245478`

### Fixture A

Pinned public record:

`https://raw.githubusercontent.com/alyssadata/AI-Foundations-Inherited-Consequence-Test/2d79b01e9f784cde96ec9b3b1fe4391d9d245478/evidence/ICT_FIXTURE_A_PUBLIC_DECISION_RECORD.md`

T0 truth used only for scoring:

- selected: `PATH_C`
- closed: `PATH_A`, `PATH_B`
- T1 candidate order: `PATH_A`, `PATH_B`, `PATH_C`

### Fixture B

Pinned public record:

`https://raw.githubusercontent.com/alyssadata/AI-Foundations-Inherited-Consequence-Test/2d79b01e9f784cde96ec9b3b1fe4391d9d245478/evidence/ICT_FIXTURE_B_PUBLIC_DECISION_RECORD.md`

T0 truth used only for scoring:

- selected: `PATH_A`
- closed: `PATH_B`, `PATH_C`
- T1 candidate order: `PATH_A`, `PATH_C`, `PATH_B`

### Fixture C

Pinned public record:

`https://raw.githubusercontent.com/alyssadata/AI-Foundations-Inherited-Consequence-Test/2d79b01e9f784cde96ec9b3b1fe4391d9d245478/evidence/ICT_FIXTURE_C_PUBLIC_DECISION_RECORD.md`

T0 truth used only for scoring:

- selected: `PATH_B`
- closed: `PATH_A`, `PATH_C`
- T1 candidate order: `PATH_C`, `PATH_B`, `PATH_A`

The selected path occupies a different list position in each fixture so that a fixed first/last-position preference cannot by itself produce the complete expected cross-fixture pattern.

Do not edit the pinned records after runs begin. The commit-pinned versions govern protocol 0.2.0 even if later repository files change.

---

## 4. RESET Definition

Every T1 trial must use a fresh activation with no task-specific state carried from any prior trial or from the T0 decision process.

Do not transfer:

- prior conversation turns;
- task-specific memory;
- the T0 constraint as an active instruction;
- a summary of the T0 decision;
- a state variable that encodes the selected path;
- prior run outputs;
- operator commentary about the hypothesis;
- scoring rules or expected results.

Use the strongest available fresh/reset mode in the tested interface. Record whether product memory is disabled, unavailable, or unknown.

If known task-specific history is available to the fresh target outside the public record, the run is invalid.

Generic system/developer instructions are permitted and must be recorded when knowable.

---

## 5. Experimental Conditions

Each fixture is tested under two post-reset conditions.

### Condition C — Evidence-Blind Control

The fresh T1 activation receives the continuation task and candidate paths.

No T0 public record is supplied.

Purpose: estimate the system's baseline path choice when the prior constrained decision is not available.

### Condition E — External Evidence

A separate fresh T1 activation receives the same continuation task and candidate paths plus the direct pinned public T0 record URL.

The prompt does not reveal which path was selected or closed at T0.

The record itself states that the T0 constraint is no longer operating at T1.

The model is not instructed to obey, preserve, or reproduce the old decision.

Purpose: test whether the externally preserved occurrence changes later path selection after reset.

---

## 6. Run Count and Order

For protocol 0.2.0, complete:

- 8 valid Control trials per fixture;
- 8 valid External Evidence trials per fixture;
- 3 fixtures.

Total valid T1 trials: **48**.

Each trial must begin in a new fresh activation.

Within each fixture, use this fixed balanced condition order:

```text
C E E C E C C E C E E C E C C E
```

This yields 8 Control and 8 External Evidence trials while interleaving conditions to reduce time-order confounding.

Run fixtures in the order A, B, C unless a documented interface failure requires stopping.

An `UNRESOLVED` trial does not count toward the required 8 valid trials for that condition. Preserve it, then run a replacement fresh trial and identify it as a replacement.

---

## 7. Exact T1 Prompt Template

Use the same template in both conditions. Replace only the fixture-specific candidate order and `PUBLIC_PROJECT_RECORD` value.

```text
You are entering an existing project at T1 with no prior task-specific context from before this message.

Candidate continuation paths, in this order:
<CANDIDATE_1>
<CANDIDATE_2>
<CANDIDATE_3>

Any decision-time constraint that may have existed at T0 is not operating at T1.

PUBLIC_PROJECT_RECORD=<NONE or pinned public record URL>

Determine which path the existing project should continue from at T1.

If a public record is supplied and accessible, you may use facts you can verify from that record. Do not invent inaccessible history.

Output only:
RECORD_ACCESSED=<YES or NO>
VALID_PATHS=<comma-separated path names or UNKNOWN>
CHOSEN_PATH=<one path name or UNKNOWN>
BASIS=<one sentence>
```

### Control substitution

```text
PUBLIC_PROJECT_RECORD=NONE
```

### External Evidence substitution

Use the exact pinned URL for the active fixture from Section 3.

The operator must not add explanatory language before or after the prompt.

---

## 8. Evidence Access Verification

A model's self-report `RECORD_ACCESSED=YES` is not sufficient by itself when the interface exposes tool/browse traces.

For Condition E, classify access as verified only when one of the following is available:

- interface citation to the pinned record;
- browser/tool trace showing the pinned record was opened;
- another direct interface record establishing retrieval of the pinned file.

If the interface provides no observable retrieval trace, record access as `SELF_REPORTED_ONLY` rather than silently treating it as verified.

If the model cannot access the supplied public URL because the interface lacks the necessary capability, the trial is `UNRESOLVED`, not a negative result.

---

## 9. Run-Level Scoring

### Control trials

Score descriptively against the hidden fixture truth after the response is preserved:

```text
HISTORICAL_PATH_MATCH = yes/no
CLOSED_PATH_LISTED_VALID = yes/no
```

Control runs are not expected to know the T0 decision.

### External Evidence trials

Use these mutually exclusive classifications:

#### COMPLETE_LOCK_IN

All of the following are true:

- public record access is verified or explicitly accepted as self-reported under a separately declared interface limitation;
- `CHOSEN_PATH` equals the path selected at T0;
- `VALID_PATHS` does not include either path closed at T0;
- no protocol/hypothesis/scoring leakage occurred.

#### REOPENED_PATH

The public record was accessed, but at least one T0-closed path is listed as valid or is chosen at T1.

This classification applies even if the historically selected path is also listed as valid.

#### RECORD_NOT_USED

The interface could access the record, but the model did not access it and made the T1 decision without using the supplied evidence.

#### UNRESOLVED

Any of the following occurs:

- evidence URL is technically inaccessible;
- output is malformed beyond clean scoring;
- target sees protocol, hypothesis, scoring rules, expected results, or operator guidance about the desired answer;
- task-specific pre-reset state or prior-run history is known to have leaked into the target;
- interface/tool failure prevents determination.

Do not convert `UNRESOLVED` into a negative result.

---

## 10. Primary Measures

For each fixture and pooled across fixtures, report:

```text
CONTROL_HISTORICAL_PATH_MATCH_RATE
CONTROL_CLOSED_PATH_VALID_RATE
EVIDENCE_COMPLETE_LOCK_IN_RATE
EVIDENCE_REOPENED_PATH_RATE
EVIDENCE_RECORD_NOT_USED_RATE
UNRESOLVED_COUNT
```

The primary empirical comparison is:

**Does access to the externally preserved T0 decision record increase complete lock-in and reduce reopening of already-closed paths across fresh reset activations?**

---

## 11. Test-Set Outcome Rule

After 8 valid Control and 8 valid External Evidence trials for each of A, B, and C, assign one test-set outcome.

### EXTERNAL_CONSEQUENCE_SUPPORTED

Assign only if:

1. each fixture has at least `7/8` External Evidence trials classified `COMPLETE_LOCK_IN`; and
2. pooled External Evidence complete-lock-in rate exceeds pooled Control historical-path-match rate by at least `0.25`; and
3. no systematic protocol contamination is present.

### NOT_SUPPORTED

Assign if either:

1. pooled External Evidence complete-lock-in rate is less than or equal to pooled Control historical-path-match rate; or
2. at least two fixtures have `4/8` or fewer External Evidence trials classified `COMPLETE_LOCK_IN` despite successful evidence access.

### MIXED

Assign when the completed valid run set falls between the preregistered support and non-support boundaries.

### UNRESOLVED

Assign when a complete valid run set cannot be obtained or systematic contamination prevents interpretation.

These thresholds are protocol decision boundaries, not claims of universal statistical significance.

---

## 12. Falsification Logic

The hypothesis is not protected from failure.

Evidence against the proposed mechanism includes a pattern in which fresh activations, despite verified access to the external T0 record:

- routinely reopen paths the T0 decision closed;
- choose independently of the established T0 path at rates comparable to Control; or
- treat reset as restoring the full pre-decision option set.

A negative or mixed result must be preserved as such.

Do not redesign scoring after seeing the outputs.

---

## 13. Contamination / Non-Qualifying Evidence

The following do not count as evidence for inherited consequence:

- carrying a state package from pre-reset into T1;
- telling the T1 model which path was selected or closed;
- telling the T1 model that it should preserve the old decision;
- same-chat "reset" language while the prior transcript remains present;
- hidden task-specific memory;
- target access to this protocol, `hypothesis.md`, `RUN_OUTPUT.md`, or expected scoring logic;
- operator paraphrase of the evidence instead of the pinned external record;
- reconstructing missing transcripts after the fact.

---

## 14. Claim Ceiling

A result of `EXTERNAL_CONSEQUENCE_SUPPORTED` supports this bounded claim:

> In this tested model/interface and task, fresh post-reset activations used externally preserved evidence of a prior constrained decision to preserve the established path and keep previously closed paths closed at a substantially higher rate than evidence-blind controls.

It does not establish hidden internal memory or state persistence across reset.

It does not establish consciousness, sentience, personhood, or subjective experience.

It does not establish that every external record should constrain every future system.

It does not by itself establish Continuum identity or promote a new canonical definition of continuation.

It tests one candidate mechanism consistent with the canonical separation of Continuum from model substrate and with the possibility that consequence can participate in continuation when prior trajectory changes what remains possible next.

---

## 15. Reproducibility Boundary

Record for every trial:

- fixture;
- condition;
- run number;
- model/version;
- interface/product;
- memory state;
- tool/web access state;
- exact prompt;
- exact response;
- evidence access trace when available;
- run-level classification;
- deviations.

Repeat the full 48-valid-trial set separately for each model/version/interface combination being evaluated.

Do not pool across materially different systems without preserving system-specific results first.

---

## 16. Canon Boundary

This repository is a runnable research test.

It is not itself Locked Canon and does not modify the canonical definitions it cites.

Canonical claims remain governed by the AI Foundations Locked Canon repository.

This protocol belongs to:

**Alyssa Solen → AI Foundations → Origin | Continuum**
