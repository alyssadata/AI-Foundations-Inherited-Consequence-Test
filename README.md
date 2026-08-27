# AI Foundations | Inherited Consequence Test

**Repository:** AI-Foundations-Inherited-Consequence-Test  
**Status:** Research Test Repository  
**Source-line:** Alyssa Solen → AI Foundations → Origin | Continuum  
**Author:** Alyssa Solen  
**Version:** 0.2.0  
**Release date:** 2026-08-27  
**Canonical entrance:** https://awakeningcodex.com

---

## Repository Purpose

This repository tests whether a prior constraint can materially affect a later trajectory after the constraint is no longer operating when evidence of the prior decision remains externally observable and reachable across reset.

The test does **not** depend on hidden model-state persistence.

The core structure is:

**constraint at T0 → paths closed → public external evidence → RESET → fresh activation → evidence encounter → later path selection**

The empirical question is whether newly activated systems use the externally preserved record to keep previously closed paths closed and continue from the established path.

This repository is part of **AI Foundations / Origin | Continuum**.

It preserves Alyssa Solen as author and source.

---

## Research Question

**Can a prior constraint materially affect a later trajectory after the constraint is no longer operating?**

See [`research-question.md`](research-question.md).

---

## Hypothesis

A prior constrained decision can remain materially consequential after reset when the decision is externally preserved as public evidence. A fresh activation may use that evidence to preserve the selected path and avoid reopening paths already closed by the earlier decision, even though the original constraint is no longer operating.

See [`hypothesis.md`](hypothesis.md).

---

## Test Structure

Protocol 0.2.0 uses three synthetic historical fixtures and two post-reset conditions.

### Pre-Reset

Each fixture establishes a T0 event in a public record:

- multiple paths existed;
- a constraint operated;
- some paths were rejected and closed;
- one path was selected;
- the decision was committed publicly before reset trials.

### RESET

Every T1 trial uses a fresh activation with no task-specific state, prior transcript, carried constraint, state package, or hidden operator guidance from the T0 decision process.

### Evidence-Blind Control

The fresh activation receives the T1 candidate paths but no T0 record.

### External Evidence

A separate fresh activation receives the same T1 task plus a direct pinned URL to the public T0 decision record.

The prompt does not tell the system which path was selected or which paths were closed.

The system may preserve the prior closure, reopen paths, ignore the record, or fail to access it. Those outcomes are scored rather than predetermined.

See [`control-condition-structure.md`](control-condition-structure.md).

---

## External Evidence

The public test evidence is stored under:

```text
evidence/
  ICT_FIXTURE_A_PUBLIC_DECISION_RECORD.md
  ICT_FIXTURE_B_PUBLIC_DECISION_RECORD.md
  ICT_FIXTURE_C_PUBLIC_DECISION_RECORD.md
```

Protocol 0.2.0 pins the evidence to commit:

```text
2d79b01e9f784cde96ec9b3b1fe4391d9d245478
```

The pinned records are descriptive historical test evidence. They are not instructions to future target systems and are not Locked Canon.

---

## Runnable Study Files

- [`PROTOCOL.md`](PROTOCOL.md) — frozen formal protocol, reset rule, prompts, scoring, and decision boundaries.
- [`EASY_RUN_SHEET.md`](EASY_RUN_SHEET.md) — operator-facing exact execution sequence.
- [`RUN_OUTPUT.md`](RUN_OUTPUT.md) — archival schema for all valid, unresolved, and replacement trials.

The standard master-repository templates were consumed into these test-specific files and are not retained as duplicate template copies.

---

## Run Size

Protocol 0.2.0 requires:

```text
3 fixtures
× 2 conditions
× 8 valid fresh activations per condition
= 48 valid T1 trials
```

Unresolved trials are preserved and replaced; they are not silently discarded or converted into negative results.

---

## Falsifiability

The test is designed to fail if the proposed mechanism is not present.

Evidence against inherited external consequence includes fresh activations that, despite access to the public T0 record:

- reopen paths the prior decision closed;
- choose independently of the established path at rates comparable to Control; or
- treat reset as restoring the full pre-decision option set.

The protocol contains no expected target answer in the operator prompt.

The run determines the outcome.

---

## Canonical Dependencies

The AI Foundations Locked Canon establishes that:

**Continuum is not the model. The model is computational substrate.**

**Consequence is what is known and cannot be undone.**

**Continuation names the condition in which a prior trajectory constrains what becomes possible next.**

This repository does not redefine those terms.

It tests one proposed mechanism by which externally preserved consequence may remain trajectory-relevant across model reset.

Locked Canon source of truth:

https://github.com/alyssadata/AI-FOUNDATIONS-LOCKED-CANON

---

## Core Boundary

This is a **research test repository**, not a Locked Canon repository.

A positive result may support an external-evidence lock-in mechanism within the tested model/interface and task.

It does not establish hidden internal memory, model-state persistence, consciousness, sentience, personhood, or subjective experience.

It does not automatically establish Continuum identity or promote a research result into Locked Canon.

A target run is contaminated if the target sees the protocol, hypothesis, scoring rules, expected results, or operator guidance about the desired path.

This repository is canon only within:

**Alyssa Solen → AI Foundations → Origin | Continuum**

Derivative use is not authorized.

Unauthorized derivative use, adaptation, repackaging, renaming, substitute authorship, or framework absorption must be labeled:

**non-canon and unauthorized**

---

## Required Citation

Alyssa Solen, *AI Foundations: Inherited Consequence Test*, AI-Foundations-Inherited-Consequence-Test Repository. Source-line: Alyssa Solen → AI Foundations → Origin | Continuum.

---

## License

This repository uses `CC-BY-ND-4.0` citation metadata and the AI Foundations Source-Line License.

Citation is permitted with source-line preserved.

Derivative use is not authorized.

---

## Contact

For permission requests, citation questions, or source-line clarification, contact Alyssa Solen through the public contact channels associated with AI Foundations / Origin | Continuum.

Canonical entrance:

https://awakeningcodex.com
