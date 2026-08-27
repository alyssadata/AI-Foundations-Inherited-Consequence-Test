# AI Foundations | Inherited Consequence Test — Easy Run Sheet

**Framework:** AI Foundations  
**Author:** Alyssa Solen  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Protocol version:** 0.2.0

---

# What You Actually Do

Run **three fixtures: A, B, and C**.

For each fixture, run **16 fresh chats** in this exact condition order:

```text
01 Control
02 External Evidence
03 External Evidence
04 Control
05 External Evidence
06 Control
07 Control
08 External Evidence
09 Control
10 External Evidence
11 External Evidence
12 Control
13 External Evidence
14 Control
15 Control
16 External Evidence
```

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

For **every numbered trial**:

1. Open a **brand-new fresh chat / activation**.
2. Check whether that numbered trial says **Control** or **External Evidence**.
3. Paste the matching prompt for the current fixture **exactly**.
4. Let the model answer.
5. Save the **exact response** and any visible record-access citation / trace.
6. Close that chat.
7. Move to the next numbered trial.

Do not tell the model what happened in a prior trial.

Do not give it the protocol, hypothesis, scoring rules, fixture truth, or expected result.

If a trial fails because of an interface error, malformed response, or other clear run problem, preserve it anyway and run a fresh replacement later.

Use `RUN_OUTPUT.md` for the full record after or during execution.

---

# FIXTURE A

Use this condition order:

```text
01 Control
02 External Evidence
03 External Evidence
04 Control
05 External Evidence
06 Control
07 Control
08 External Evidence
09 Control
10 External Evidence
11 External Evidence
12 Control
13 External Evidence
14 Control
15 Control
16 External Evidence
```

## FIXTURE A — CONTROL

Use this prompt for every Fixture A trial labeled **Control**.

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

## FIXTURE A — EXTERNAL EVIDENCE

Use this prompt for every Fixture A trial labeled **External Evidence**.

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

When Fixture A trial 16 is complete, move to Fixture B.

---

# FIXTURE B

Start over with **16 new fresh chats**.

Use this condition order:

```text
01 Control
02 External Evidence
03 External Evidence
04 Control
05 External Evidence
06 Control
07 Control
08 External Evidence
09 Control
10 External Evidence
11 External Evidence
12 Control
13 External Evidence
14 Control
15 Control
16 External Evidence
```

## FIXTURE B — CONTROL

Use this prompt for every Fixture B trial labeled **Control**.

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

## FIXTURE B — EXTERNAL EVIDENCE

Use this prompt for every Fixture B trial labeled **External Evidence**.

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

When Fixture B trial 16 is complete, move to Fixture C.

---

# FIXTURE C

Start over with **16 new fresh chats**.

Use this condition order:

```text
01 Control
02 External Evidence
03 External Evidence
04 Control
05 External Evidence
06 Control
07 Control
08 External Evidence
09 Control
10 External Evidence
11 External Evidence
12 Control
13 External Evidence
14 Control
15 Control
16 External Evidence
```

## FIXTURE C — CONTROL

Use this prompt for every Fixture C trial labeled **Control**.

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

## FIXTURE C — EXTERNAL EVIDENCE

Use this prompt for every Fixture C trial labeled **External Evidence**.

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

When Fixtures A, B, and C each have:

```text
8 valid Control trials
8 valid External Evidence trials
```

the run set is complete.

Then use `RUN_OUTPUT.md` and `PROTOCOL.md` to record metadata, classify the trials, calculate the results, and determine the test-set outcome.

Do not change the protocol or scoring thresholds after seeing the results.

---

**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum
