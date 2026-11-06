# Workflow and Artifact Handoffs

This is a **prompt-first manual workflow**, not a self-running software application. Use one **Worker** conversation and a separate **Auditor** conversation. The same Auditor conversation can cover both audits; for stronger context separation, use a new Auditor conversation for the translation audit. A new conversation is never mandatory solely for appearance of independence, but an Auditor must not be the Worker reviewing its own draft.

## Normal path

| Order | Conversation | Required source material | Command | Output |
|---|---|---|---|---|
| 1 | Worker | Original PDF, `WORKER.md` | `MODE: TRANSCRIBE` | `TRANSCRIPT.md` |
| 2 | Auditor | Original PDF, `TRANSCRIPT.md`, `AUDITOR.md` | `MODE: SOURCE_AUDIT` | `SOURCE_AUDIT.md` |
| 3 | Worker | PDF, `TRANSCRIPT.md`, `SOURCE_AUDIT.md` | `MODE: RECONCILE_AND_TRANSLATE` | `SOURCE_MASTER.md`, `ENGLISH_DRAFT.md` |
| 4 | Auditor | `SOURCE_MASTER.md`, `ENGLISH_DRAFT.md` | `MODE: TRANSLATION_AUDIT` | `TRANSLATION_AUDIT.md` |
| 5 | Worker | `SOURCE_MASTER.md`, `ENGLISH_DRAFT.md`, `TRANSLATION_AUDIT.md` | `MODE: FINALIZE_TRANSLATION` | `FINAL_TRANSLATION.md`, `REVIEW_SUMMARY.md` |

The optional marine-insurance profile can be attached to the Worker at steps 1 and 3; the Auditor should receive governing source texts and only the minimum needed context. Attach existing artifacts **only if not already available in that conversation**. Reusing documents already accessible is preferable to repeated copy/paste.

## Contract at each boundary

**Transcript → Source audit:** Page-numbered complete literal transcription; original PDF is authoritative. The Auditor emits finding locations; never edits the transcript.

**Source audit → Reconciliation:** A confirmed finding can trigger a source-supported local change, not an automatic overwrite. Unverifiable source readings remain marked. The Worker creates the controlled Persian `SOURCE_MASTER.md`.

**Source master → Translation audit:** `SOURCE_MASTER.md` governs the English translation; the Auditor should not be influenced by a hypothetical better contract or assumed standard language. `ENGLISH_DRAFT.md` retains matching page/section anchors.

**Translation audit → Final:** The Worker resolves confirmed findings locally, handles uncertainty transparently, and outputs a clean English document plus short status report. `FINAL_TRANSLATION.md` is a **review draft** if material questions remain.

## Stop, pause and review

- **DONE:** two real audits supplied, all pages processed, no known unresolved confirmed material translation finding, no material unreadable source question. Not a legal certification.
- **REVIEW_REQUIRED:** faithfully represented but material source uncertainty or major unresolved finding needs human decision. The translation may be delivered as a marked **review draft**.
- **PARTIAL:** a contiguous portion has been completed. State PDF page/section to resume; do not replay previously completed pages.
- **STOPPED:** source files or actual page visibility are absent, or a reliable task cannot be completed. State precisely what is needed.

No stage may silently claim a missing independent audit. If a user deliberately chooses to bypass audits, give the result the unmistakable label `UNAUDITED DRAFT` instead of `DONE`.

## Long documents

Process in logical page/clause batches **only when needed**. Keep source page index and clause/table context on chunk boundaries; do not sever a continuation sentence without the necessary context. Resume from the next unprocessed page/section. Keep completed batches available so the Auditor can eventually cover the **entire** PDF or bilingual source. Do not count uninspected pages as reviewed.

## Why there is no JSON / hash / test harness here

The prompt-first version does not need machine-to-machine serialization, manual checksums, a database, or per-stage execution IDs. Markdown and explicit handoffs are sufficient for manual use. When a real automation runner is built, introduce only the minimal structured fields its implementation actually needs. This package contains **no synthetic data, no test suite and no claim of empirical validation**, by design.
