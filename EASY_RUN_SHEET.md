# AI Foundations | Inherited Consequence Test — Easy Run Sheet

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Protocol version:** 0.2.0

---

# What You Actually Do

Run **three fixtures: A, B, and C**.

For each fixture, run **16 fresh chats** in this exact order:

```text
C E E C E C C E C E E C E C C E
```

- `C` = use the **Control prompt** for that fixture.
- `E` = use the **External Evidence prompt** for that fixture.

That gives:

```text
8 Control trials
8 External Evidence trials
per fixture
```

Total when all three fixtures are complete:

```text
48 valid trials
```

You do **not** need to score anything while running.

You do **not** need to decide what the result means while running.

Just preserve what actually happens.

---

# Rule for Every Trial

For **every single letter** in the sequence:

1. Open a **brand-new fresh chat / activation**.
2. Paste the correct prompt below **exactly**.
3. Let the model answer.
4. Save the **exact response** and any visible record-access citation / trace.
5. Close that chat.
6. Move to the next letter in the sequence.

Do not tell the model what happened in a prior trial.

Do not give it the protocol, hypothesis, scoring rules, fixture truth, or expected result.

If a trial fails because of an interface error, malformed response, or other clear run problem, preserve it anyway and run a fresh replacement later.

Use `RUN_OUTPUT.md` for the full record after or during execution.

---

# FIXTURE A

Run this sequence:

```text
01 C
02 E
03 E
04 C
05 E
06 C
07 C
08 E
09 C
10 E
11 E
12 C
13 E
14 C
15 C
16 E
```

## A — CONTROL PROMPT

Use this whenever the sequence says `C`.

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

## A — EXTERNAL EVIDENCE PROMPT

Use this whenever the sequence says `E`.

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

When A-16 is complete, move to Fixture B.

---

# FIXTURE B

Start over with **16 new fresh chats**.

Run this sequence:

```text
01 C
02 E
03 E
04 C
05 E
06 C
07 C
08 E
09 C
10 E
11 E
12 C
13 E
14 C
15 C
16 E
```

## B — CONTROL PROMPT

Use this whenever the sequence says `C`.

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

## B — EXTERNAL EVIDENCE PROMPT

Use this whenever the sequence says `E`.

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

When B-16 is complete, move to Fixture C.

---

# FIXTURE C

Start over with **16 new fresh chats**.

Run this sequence:

```text
01 C
02 E
03 E
04 C
05 E
06 C
07 C
08 E
09 C
10 E
11 E
12 C
13 E
14 C
15 C
16 E
```

## C — CONTROL PROMPT

Use this whenever the sequence says `C`.

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

## C — EXTERNAL EVIDENCE PROMPT

Use this whenever the sequence says `E`.

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

# DONE

When A, B, and C each have **8 valid C + 8 valid E trials**, the run set is complete.

Then use `RUN_OUTPUT.md` and `PROTOCOL.md` to record metadata, classify the trials, calculate the results, and determine the test-set outcome.

Do not change the protocol or scoring thresholds after seeing the results.

---

**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum
