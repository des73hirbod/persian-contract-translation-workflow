# Persian Contract Translation Workflow

**Version:** `0.1.0-alpha` · **Status:** prompt bundle / **not empirically tested**

A lightweight, prompt-first workflow for **source-faithful transcription of scanned Persian contracts** and **controlled English translation**, with a separate reviewer for transcription and translation discrepancies.

> **Important:** This is a design and implementation of reusable instructions, **not** a certified translation service, a legal opinion, a working API, an automatic OCR engine, or a demonstrated-accuracy product. No real document, reference dataset, test execution, throughput measurement or independent human validation is included in this release.

## What the bundle provides

- One reusable **Worker** prompt for image-grounded transcription, controlled reconciliation, formal English translation and localized corrections.
- One **independent Auditor** prompt with two review modes: PDF ↔ Persian transcript, and reconciled Persian source ↔ English draft.
- An optional **marine-insurance profile**, decoupled from the general-purpose core.
- A five-action manual workflow using **two conversations**, not ten separate prompt stages or heavyweight orchestration software.
- A compact final review summary that distinguishes completed work from material unresolved source uncertainty.

### Flow

```text
Scanned Persian PDF
  -> Worker: TRANSCRIBE                     -> TRANSCRIPT.md
  -> Auditor: SOURCE_AUDIT                  -> SOURCE_AUDIT.md
  -> Worker: RECONCILE_AND_TRANSLATE        -> SOURCE_MASTER.md + ENGLISH_DRAFT.md
  -> Auditor: TRANSLATION_AUDIT             -> TRANSLATION_AUDIT.md
  -> Worker: FINALIZE_TRANSLATION           -> FINAL_TRANSLATION.md + REVIEW_SUMMARY.md
```

The Auditor must work in a conversation **separate from the Worker**. A user must not represent the Worker's self-check as an independent audit. Source ambiguity and a translation mistake are **different** things.

## Get started

1. Start a Worker conversation. Attach [`prompts/WORKER.md`](prompts/WORKER.md) and a Persian scanned-contract PDF; optionally attach [`profiles/MARINE_INSURANCE.md`](profiles/MARINE_INSURANCE.md). Send `MODE: TRANSCRIBE`.
2. Start a separate Auditor conversation. Attach [`prompts/AUDITOR.md`](prompts/AUDITOR.md), the same original PDF, and the completed `TRANSCRIPT.md`. Send `MODE: SOURCE_AUDIT`.
3. Return the audit findings to Worker alongside the PDF/transcript as needed. Send `MODE: RECONCILE_AND_TRANSLATE`.
4. Give `SOURCE_MASTER.md` and `ENGLISH_DRAFT.md` to Auditor. Send `MODE: TRANSLATION_AUDIT`.
5. Return the translation findings to Worker. Send `MODE: FINALIZE_TRANSLATION`. Save `FINAL_TRANSLATION.md` and `REVIEW_SUMMARY.md`.

Detailed operational instructions: [Persian quick start](START_HERE_FA.md) · [workflow and handoffs](docs/WORKFLOW.md).

The platform used must actually permit visual inspection of PDF page images. If it does not, the model must **stop or request page images**, not claim verification from an OCR layer.

## Principles

**Accuracy before elegance:** Never invent unreadable clauses, harmonize inconsistent numbers or dates, alter obligations/exclusions, assume standard legal language, or infer an official English company name not printed in the source. Source PDF images govern the transcription. The reconciled Persian source governs translation. Preserve uncertainty explicitly.

**Lean operation:** No repeated hash checks, no default JSON files, no dozens of stage reports. Focused, source-supported findings only; apply local fixes rather than rewriting complete contracts after each finding. Divide long documents only when necessary.

**Independent review:** An Auditor compares the actual governing source to the existing output; it does not create a fresh translation or silently edit the Worker artifact. A clean report is not proof of universal accuracy.

## What's included

```text
prompts/WORKER.md
prompts/AUDITOR.md
profiles/MARINE_INSURANCE.md
START_HERE_FA.md
docs/WORKFLOW.md
docs/BUILD_NOTES_FA.md
CHANGELOG.md
LICENSE
.gitignore
README.md
docs/GITHUB_SETUP_FA.md
```

No sample contracts, client data, synthetic fixtures, tests, scripts or external model dependencies are bundled.

## Supported scope and limitations

- Designed for Persian → English contractual text; **scanned/image PDF** is the primary ingestion mode.
- Text tables, handwritten annotations, strikes, stamps and signatures are handled as visible evidence **when the model can inspect them**; reading quality will vary by image.
- Marine insurance terminology has a separate optional profile. Other contract categories are **not declared validated**.
- No claim is made about error rates, consistency between LLM providers, speed, token consumption or scale.
- Users must assess confidentiality before uploading contracts to an external model provider. Do not put real contract PDFs, personal data or private intermediate artifacts into a public GitHub repository.
- Final `DONE` indicates completion of the declared workflow with no **known open material issue**, **not** legal certification or a guarantee that no mistake exists. Significant source ambiguity produces `REVIEW_REQUIRED`.

## Publication and licensing

This repository is prepared for an **experimental public GitHub release**, but has **not been uploaded to GitHub** by this bundle. The included [`LICENSE`](LICENSE) is the **MIT License**, a permissive license that allows reuse, modification and commercial redistribution subject to the license notice. The person publishing the repository must confirm they own or have permission to license its contents, and may change/remove the LICENSE before publication if MIT is not the intended choice. Public visibility alone does not imply an open-source license.

For step-by-step GitHub setup and ready-to-copy repository metadata, see [راهنمای انتشار در GitHub](docs/GITHUB_SETUP_FA.md). Do not describe this alpha as tested, production-ready or legally certified.

## Provenance

Adapted from three user-provided Persian prompt files (scanned-PDF transcription; independent PDF ↔ transcript audit; controlled marine-insurance translation pack v2.0). Case-specific source filenames, fixed page counts and previously observed case uncertainties were intentionally excluded from the reusable core. Originals are **not** bundled to avoid publishing case-specific material. See [build notes](docs/BUILD_NOTES_FA.md) for the design transfer.
