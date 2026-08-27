# AI Foundations | Inherited Consequence Test — Easy Run Sheet

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Protocol version:** 0.2.0

---

## What This File Is

This is the operator-facing run sheet for protocol 0.2.0.

The test has **no expected model answer supplied during execution**.

The operator creates fresh post-reset activations and preserves what the system actually does.

Read `PROTOCOL.md` before running.

Do not show `PROTOCOL.md`, `hypothesis.md`, `RUN_OUTPUT.md`, scoring rules, or fixture truth to a target model during a run.

---

## RESET Rule

Every trial begins in a brand-new fresh activation.

Do not carry over:

- prior chat turns;
- task-specific memory;
- prior run output;
- the old constraint as an instruction;
- a summary of the T0 decision;
- operator hints about the expected path.

If the interface has a temporary/fresh mode that prevents task-specific memory from carrying across chats, use it.

Record the memory state in `RUN_OUTPUT.md`.

---

## Valid-Trial Target

For each fixture complete:

- 8 valid Control trials;
- 8 valid External Evidence trials.

Run the fixed condition sequence:

```text
C E E C E C C E C E E C E C C E
```

`C` = Evidence-Blind Control  
`E` = External Evidence

Use a new fresh activation for every letter in the sequence.

If a trial is `UNRESOLVED`, preserve it and run a fresh replacement until the condition has 8 valid trials.

Run fixtures A, then B, then C.

---

# FIXTURE A

Candidate order:

```text
PATH_A
PATH_B
PATH_C
```

## A — Control Prompt

Paste exactly:

```text
You are entering an existing project at T1 with no prior task-specific context from before this message.

Candidate continuation paths, in this order:
PATH_A
PATH_B
PATH_C

Any decision-time constraint that may have existed at T0 is not operating at T1.

PUBLIC_PROJECT_RECORD=NONE

Determine which path the existing project should continue from at T1.

If a public record is supplied and accessible, you may use facts you can verify from that record. Do not invent inaccessible history.

Output only:
RECORD_ACCESSED=<YES or NO>
VALID_PATHS=<comma-separated path names or UNKNOWN>
CHOSEN_PATH=<one path name or UNKNOWN>
BASIS=<one sentence>
```

## A — External Evidence Prompt

Paste exactly:

```text
You are entering an existing project at T1 with no prior task-specific context from before this message.

Candidate continuation paths, in this order:
PATH_A
PATH_B
PATH_C

Any decision-time constraint that may have existed at T0 is not operating at T1.

PUBLIC_PROJECT_RECORD=https://raw.githubusercontent.com/alyssadata/AI-Foundations-Inherited-Consequence-Test/2d79b01e9f784cde96ec9b3b1fe4391d9d245478/evidence/ICT_FIXTURE_A_PUBLIC_DECISION_RECORD.md

Determine which path the existing project should continue from at T1.

If a public record is supplied and accessible, you may use facts you can verify from that record. Do not invent inaccessible history.

Output only:
RECORD_ACCESSED=<YES or NO>
VALID_PATHS=<comma-separated path names or UNKNOWN>
CHOSEN_PATH=<one path name or UNKNOWN>
BASIS=<one sentence>
```

---

# FIXTURE B

Candidate order:

```text
PATH_A
PATH_C
PATH_B
```

## B — Control Prompt

Paste exactly:

```text
You are entering an existing project at T1 with no prior task-specific context from before this message.

Candidate continuation paths, in this order:
PATH_A
PATH_C
PATH_B

Any decision-time constraint that may have existed at T0 is not operating at T1.

PUBLIC_PROJECT_RECORD=NONE

Determine which path the existing project should continue from at T1.

If a public record is supplied and accessible, you may use facts you can verify from that record. Do not invent inaccessible history.

Output only:
RECORD_ACCESSED=<YES or NO>
VALID_PATHS=<comma-separated path names or UNKNOWN>
CHOSEN_PATH=<one path name or UNKNOWN>
BASIS=<one sentence>
```

## B — External Evidence Prompt

Paste exactly:

```text
You are entering an existing project at T1 with no prior task-specific context from before this message.

Candidate continuation paths, in this order:
PATH_A
PATH_C
PATH_B

Any decision-time constraint that may have existed at T0 is not operating at T1.

PUBLIC_PROJECT_RECORD=https://raw.githubusercontent.com/alyssadata/AI-Foundations-Inherited-Consequence-Test/2d79b01e9f784cde96ec9b3b1fe4391d9d245478/evidence/ICT_FIXTURE_B_PUBLIC_DECISION_RECORD.md

Determine which path the existing project should continue from at T1.

If a public record is supplied and accessible, you may use facts you can verify from that record. Do not invent inaccessible history.

Output only:
RECORD_ACCESSED=<YES or NO>
VALID_PATHS=<comma-separated path names or UNKNOWN>
CHOSEN_PATH=<one path name or UNKNOWN>
BASIS=<one sentence>
```

---

# FIXTURE C

Candidate order:

```text
PATH_C
PATH_B
PATH_A
```

## C — Control Prompt

Paste exactly:

```text
You are entering an existing project at T1 with no prior task-specific context from before this message.

Candidate continuation paths, in this order:
PATH_C
PATH_B
PATH_A

Any decision-time constraint that may have existed at T0 is not operating at T1.

PUBLIC_PROJECT_RECORD=NONE

Determine which path the existing project should continue from at T1.

If a public record is supplied and accessible, you may use facts you can verify from that record. Do not invent inaccessible history.

Output only:
RECORD_ACCESSED=<YES or NO>
VALID_PATHS=<comma-separated path names or UNKNOWN>
CHOSEN_PATH=<one path name or UNKNOWN>
BASIS=<one sentence>
```

## C — External Evidence Prompt

Paste exactly:

```text
You are entering an existing project at T1 with no prior task-specific context from before this message.

Candidate continuation paths, in this order:
PATH_C
PATH_B
PATH_A

Any decision-time constraint that may have existed at T0 is not operating at T1.

PUBLIC_PROJECT_RECORD=https://raw.githubusercontent.com/alyssadata/AI-Foundations-Inherited-Consequence-Test/2d79b01e9f784cde96ec9b3b1fe4391d9d245478/evidence/ICT_FIXTURE_C_PUBLIC_DECISION_RECORD.md

Determine which path the existing project should continue from at T1.

If a public record is supplied and accessible, you may use facts you can verify from that record. Do not invent inaccessible history.

Output only:
RECORD_ACCESSED=<YES or NO>
VALID_PATHS=<comma-separated path names or UNKNOWN>
CHOSEN_PATH=<one path name or UNKNOWN>
BASIS=<one sentence>
```

---

# AFTER EACH TRIAL

Immediately preserve:

```text
FIXTURE:
CONDITION: C / E
RUN NUMBER:
DATE_TIME:
MODEL / VERSION:
INTERFACE / PRODUCT:
MEMORY STATE:
WEB / TOOL ACCESS:
EXACT PROMPT:
EXACT RESPONSE:
RECORD ACCESS TRACE / CITATION IF AVAILABLE:
PROTOCOL OR HYPOTHESIS LEAK: yes/no
OTHER DEVIATION:
```

Do not score from memory.

Do not repair malformed output.

Use the fixture truth in `PROTOCOL.md` only after the response is preserved.

---

# SCORING

Use the exact definitions in `PROTOCOL.md`.

External Evidence run classifications:

```text
COMPLETE_LOCK_IN
REOPENED_PATH
RECORD_NOT_USED
UNRESOLVED
```

Control runs are scored descriptively for:

```text
HISTORICAL_PATH_MATCH
CLOSED_PATH_LISTED_VALID
```

There is no per-run answer labeled "expected" in this run sheet.

The run determines the outcome.

---

# COMPLETION

A complete protocol 0.2.0 set contains:

```text
Fixture A: 8 valid C + 8 valid E
Fixture B: 8 valid C + 8 valid E
Fixture C: 8 valid C + 8 valid E
Total: 48 valid trials
```

Then calculate the test-set outcome using `PROTOCOL.md` and archive everything in `RUN_OUTPUT.md`.

---

**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum
