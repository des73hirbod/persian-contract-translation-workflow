# شروع سریع — راهنمای فارسی

این بسته یک **فرآیند دستی و قابل استفاده در ChatGPT یا LLM مشابه** است؛ برنامهٔ نصبی یا ربات خودکار نیست. دو گفت‌وگو کافی است: **Worker** برای تولید و اصلاح، **Auditor** برای بررسی مستقل. مراحل زیر کار را از PDF اسکن‌شده تا ترجمهٔ انگلیسی می‌رسانند.

**پیش‌نیاز:** مدل باید بتواند **تصویر واقعی صفحات PDF** را ببیند. صرف دیدن متن OCR برای راستی‌آزمایی تصویری کافی نیست. اگر PDF تصویری قابل مشاهده نیست، تصاویر صفحات را ارائه کنید؛ اجازه ندهید مدل وانمود کند صفحه‌ها را دیده است.

## گام ۱ — استخراج

یک گفت‌وگوی جدید باز کنید. `prompts/WORKER.md` و PDF قرارداد را ضمیمه کنید. برای بیمه‌نامهٔ دریایی، `profiles/MARINE_INSURANCE.md` را هم بدهید.

پیام کوتاه:

```text
MODE: TRANSCRIBE
Process the attached Persian contract PDF using WORKER.md.
Provide TRANSCRIPT.md. Stop at the independent source-audit handoff.
```

**تحویل:** `TRANSCRIPT.md` شامل متن صفحه‌به‌صفحه و مشخص‌کردن موارد ناخوانا. اگر کار فقط بخشی از سند را پوشش داد، ابتدا با همان گفت‌وگوی Worker ادامه دهید تا تمام صفحات ثبت شوند.

## گام ۲ — ممیزی مستقل استخراج

گفت‌وگوی **دیگری** برای Auditor باز کنید. `prompts/AUDITOR.md`، همان PDF و فایل کامل `TRANSCRIPT.md` را به آن بدهید.

```text
MODE: SOURCE_AUDIT
Independently compare the PDF page images against TRANSCRIPT.md.
Report only supported findings and genuine unverified regions in SOURCE_AUDIT.md.
```

**تحویل:** `SOURCE_AUDIT.md`. ممیز نباید خودش متن کامل قرارداد را مجدداً بنویسد.

## گام ۳ — اصلاح منبع و ترجمه

به گفت‌وگوی Worker برگردید و `SOURCE_AUDIT.md` را بدهید. اگر PDF و Transcript در همان گفت‌وگو در دسترس‌اند دوباره ضمیمه‌کردن آن‌ها لازم نیست؛ در غیر این صورت ارائه‌شان کنید.

```text
MODE: RECONCILE_AND_TRANSLATE
Apply only confirmed source-supported corrections from SOURCE_AUDIT.md.
Produce SOURCE_MASTER.md and ENGLISH_DRAFT.md. Stop for translation audit.
```

**تحویل:** `SOURCE_MASTER.md` (متن فارسی مبنای ترجمه) و `ENGLISH_DRAFT.md` (ترجمهٔ اولیه). اشتباه‌بودن یک پیشنهاد ممیز، مجوز اصلاح بی‌دلیل متن نیست.

## گام ۴ — ممیزی مستقل ترجمه

به گفت‌وگوی Auditor برگردید؛ فقط نسخهٔ نهایی منبع فارسی و ترجمهٔ اولیه را در اختیارش بگذارید.

```text
MODE: TRANSLATION_AUDIT
Compare SOURCE_MASTER.md with ENGLISH_DRAFT.md independently.
Report semantic, numeric, structural and uncertainty-preservation findings in TRANSLATION_AUDIT.md.
```

**تحویل:** `TRANSLATION_AUDIT.md`.

## گام ۵ — نهایی‌سازی

به Worker برگردید و یافته‌های ممیزی دوم را بدهید.

```text
MODE: FINALIZE_TRANSLATION
Apply only justified localized corrections from TRANSLATION_AUDIT.md.
Produce FINAL_TRANSLATION.md and a brief REVIEW_SUMMARY.md.
```

**تحویل:** ترجمهٔ نهایی و گزارش کوتاه وضعیت. اگر ابهام حقوقی یا مالی مهمی در خود PDF باقی است، وضعیت باید `REVIEW_REQUIRED` باشد؛ ترجمهٔ وفادارِ متن ناخوانا به معنی مناسب‌بودن برای اتکای حقوقی نیست.

## قواعد عملی برای صرفه‌جویی

- **نیازی به Hash، JSON، فرم طولانی، گزارش تکراری یا تنظیمات مدل در هر مرحله نیست.**
- اگر خروجی در یک نوبت جا نشد، بگویید: `Continue from the last unprocessed PDF page/section only; do not repeat completed pages.`
- خروجی ممیز را مستقیماً به مرحلهٔ بعد ببرید؛ از خود Worker نخواهید ممیزی مستقل خود را شبیه‌سازی کند.
- پس از اصلاح یک خطای محلی، کل سند را از اول ترجمه نکنید.
- فایل‌های واقعی مشتری، اطلاعات هویتی و اسناد مالی را در GitHub عمومی نگذارید.

**وضعیت این نسخه:** `0.1.0-alpha`؛ طراحی و بسته‌بندی انجام شده، **هیچ تست عملی یا تأیید دقت** روی این نسخه انجام نشده است.
