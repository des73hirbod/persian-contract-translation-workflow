# Optional domain profile — Persian Marine Insurance / Vessel Policy

**Use only when the actual document is a marine-insurance or vessel-insurance contract.** This is a domain vocabulary and attention guide, **not** a reference contract or authority over the words visible in the source. Do not use it to fill unreadable text. Do not insert its terms or example values unless they occur in the document.

## Domain attention

Pay special attention when present to:
- Insurer, policyholder, insured, beneficiary, subject matter insured; identity of legal parties.
- Vessel name, type, flag, registration and IMO identifiers; year built, shipbuilder, hull and machinery, dimensions, GT, NT, classification society, navigation area and seaworthiness.
- Coverage limits, insured values, rates, premiums, tax, installment terms and currency/exchange-rate statements.
- Total and partial loss, deductibles, exclusions, claims duties, notification periods, cancellation, termination, automatic termination, liability, arbitration and dispute clauses.
- Hull and Machinery provisions, Institute Time Clauses references, version years and clause numbers. Source inconsistencies in years or clause references must be preserved, not silently fixed.

## Terminology starting points (context controls final choice)

| Persian source term | Possible conservative English equivalent | Note |
|---|---|---|
| بیمه‌نامه | insurance policy | Preserve named-policy distinctions |
| بیمه‌گر | insurer | |
| بیمه‌گذار | policyholder | Distinguish from insured |
| بیمه‌شده | insured | If present |
| ذی‌نفع | beneficiary | Context may require named beneficiary |
| مورد بیمه | subject matter insured | Or insured subject, depending on sentence |
| شناور | vessel | |
| بدنه و ماشین‌آلات | hull and machinery | |
| خسارت کلی | total loss | |
| خسارت جزئی | partial loss | |
| فرانشیز | deductible | Verify actual structure and meaning from source |
| سرمایه مورد بیمه | sum insured / insured value | Do not assume identical meanings |
| حق بیمه | insurance premium | |
| فسخ | termination / cancellation | Choose by source context, do not harmonize |
| انفساخ | automatic termination | Only if that is supported by text |
| داوری | arbitration | |
| قابلیت دریانوردی | seaworthiness | |
| مؤسسه رده‌بندی | classification society | |

## Already-English expressions

When present in the **actual source**, retain existing English proper terms and abbreviations accurately; examples from prior design include `IMO`, `GPS`, `ITC`, `P&I`, `Hull & Machinery`, `Oil Tanker`, `Bureau Veritas`, `lay-up`, and `Bareboat`. They are **not** required contents of a new translation.

## Names and clause references

- Never invent the official registered English name of an Iranian company or organization. Prefer the English name **actually printed in the document**, otherwise use consistent conservative transliteration, with a note where official spelling is unestablished.
- Do not silently substitute a known template or external standard clause for a locally printed provision.
- Preserve observed clause numbers/versions, including apparent contradictions (e.g. references to different ITC years).
- Do not convert Solar Hijri dates to Gregorian, or Iranian rials to another currency, without an explicit separate authorization outside this faithful-translation workflow.

## Important: no case-specific hardcoding

This profile intentionally excludes the former source-file name, fixed four-page assumption, example vessel name, policy-specific values, and four source uncertainties labeled HR-01 to HR-04. Such details belong only to the **actual document being processed**, never to reusable instructions.
