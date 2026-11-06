# راهنمای انتشار عمومی در GitHub — نسخهٔ 0.1.0-alpha

این راهنما برای کسی نوشته شده که تجربهٔ زیادی با GitHub ندارد. **این پروژه یک باندل پرامپت است، نه نرم‌افزار نصب‌شونده یا سیستم خودکار تست‌شده.** ساخت باندل و آماده‌سازی فایل‌ها انجام شده؛ اجرای ترجمه یا آزمون عملکردی انجام نشده است.

## ۱. مشخصات پیشنهادی Repository

| گزینه | مقدار |
|---|---|
| Owner | حساب GitHub خودتان |
| Repository name | `persian-contract-translation-workflow` |
| Description | `Prompt-first workflow for faithful Persian contract transcription and English translation with independent LLM audits.` |
| Visibility | **Public** |
| Add a README | **Off / Do not initialize**؛ فایل `README.md` از قبل در باندل وجود دارد |
| Add .gitignore | **None**؛ فایل `.gitignore` از قبل وجود دارد |
| Choose a license | **None** هنگام ساخت Repository؛ فایل `LICENSE` پیشنهادی MIT از قبل در باندل وجود دارد |
| Template | **No template** |

**Topics** (در قسمت About بعد از ساخت): `llm`, `prompt-engineering`, `persian`, `farsi`, `contract-translation`, `document-processing`, `transcription`, `translation`, `quality-assurance`, `marine-insurance`.

Website URL: خالی بماند، مگر آنکه واقعاً وب‌سایتی برای این پروژه ساخته شده باشد.

## ۲. ساخت Repository

1. به https://github.com/new بروید و وارد حساب شوید.
2. Owner را حساب خود انتخاب کنید.
3. Repository name و Description بالا را درج کنید.
4. Visibility را روی **Public** قرار دهید.
5. **Add README** را فعال نکنید؛ `.gitignore` و License جدید هم از فرم GitHub نسازید، چون در فایل‌ها موجودند.
6. **Create repository** را بزنید.

## ۳. بارگذاری فایل‌ها — نه فقط ZIP

1. ZIP دریافتی را در رایانه Extract کنید.
2. پوشهٔ `persian-contract-translation-workflow` را باز کنید. باید `README.md`, `START_HERE_FA.md`, `LICENSE`, `.gitignore`, `CHANGELOG.md` و سه پوشهٔ `prompts`, `profiles`, `docs` را ببینید.
3. در Repository تازه و خالی، روی `uploading an existing file` کلیک کنید. اگر این گزینه نبود، از **Add file → Upload files** استفاده کنید.
4. **محتویات داخل پوشه** را بکشید و در قسمت Upload رها کنید. فولدرهای `prompts`, `profiles`, `docs` باید همراه با مسیر زیرپوشه‌هایشان حفظ شوند. توجه کنید فایل `.gitignore` نیز بارگذاری شود.
5. بررسی کنید `README.md` در ریشهٔ Repository باشد؛ یعنی در `your-username/persian-contract-translation-workflow/README.md`، نه در یک پوشهٔ اضافه.
6. Commit message را `Initial public alpha release` بگذارید و فایل‌ها را Commit کنید.
7. در تب Code باید README نمایش داده شود و پوشه‌های `prompts`, `profiles`, `docs` قابل مشاهده باشند.

**ZIP را فقط به‌عنوان یک فایل در بخش Code بارگذاری نکنید.** در آن صورت GitHub محتویات را به‌صورت فایل‌های قابل مرور Repository نمایش نمی‌دهد. ZIP برای فایل پیوست بخش Releases مناسب است.

## ۴. About / Topics

در صفحهٔ اصلی Repository، کنار بخش **About** روی آیکن چرخ‌دنده کلیک کنید. Topics را از جدول مرحلهٔ اول وارد و Save کنید. Website را خالی بگذارید. Description اگر هنگام ساخت وارد شده، نیازی به تکرار ندارد.

## ۵. Release اختیاری اما توصیه‌شده

بعد از قرارگرفتن فایل‌ها در Code:

1. روی **Releases** → **Draft a new release** بزنید.
2. یک Tag جدید به نام `v0.1.0-alpha` بسازید.
3. Release title: `v0.1.0-alpha — Experimental Prompt Bundle`.
4. Release notes پیشنهادی:

```text
Initial public alpha release of a prompt-first Persian contract transcription and English translation workflow.
Includes separate Worker and Auditor prompts, an optional marine-insurance profile, and Persian setup instructions.
No empirical accuracy tests, benchmarking, client data, or legal certification are included.
This is a manual workflow, not an automated translation service.
```

5. گزینهٔ **This is a pre-release** را فعال کنید.
6. فایل ZIP را در قسمت Release assets پیوست کنید (اختیاری) و سپس **Publish release** را بزنید.

## ۶. مجوز و مسئولیت انتشار

فایل `LICENSE` پیشنهادی از نوع **MIT** است. این مجوز امکان استفاده، تغییر، بازنشر و استفادهٔ تجاری توسط دیگران را می‌دهد، به شرط حفظ اعلان مجوز. پیش از Public کردن Repository، تأیید کنید که حق انتشار و اعطای مجوز نسبت به تمام محتوا را دارید و چنین اختیاری را قصد دارید بدهید. اگر صرفاً می‌خواهید فایل‌ها در GitHub **قابل مشاهده باشند** و فعلاً اجازهٔ بازاستفاده ندهید، فایل `LICENSE` را **پیش از انتشار حذف کنید** و بخش Licensing در README را مطابق آن ویرایش کنید. Public بودن به‌تنهایی مجوز بازاستفاده صادر نمی‌کند.

باندل **بدون تست** آماده شده و نباید به‌عنوان محصول تأییدشدهٔ حقوقی، دارای دقت تضمین‌شده، یا ابزار خودکار معرفی شود.

## ۷. انتشار امن

- هیچ PDF واقعی، اطلاعات مشتری، شناسهٔ شخصی یا خروجی محرمانه‌ای را به Repository عمومی وارد نکنید.
- باندل فعلی فاقد PDF قرارداد و نتایج واقعی است.
- `.gitignore` برای کار با Git محلی محافظت مفیدی ایجاد می‌کند، ولی جایگزین بازبینی انتخاب فایل در آپلود مرورگری نیست.
- هنگام اولین انتشار نیازی به Actions، Projects، Wiki، Pages، API token یا محیط استقرار ندارید.
- هر زمان نسخهٔ جدیدی آماده شد، فایل‌های مربوط را در همان Repository به‌روزرسانی کنید؛ برای هر نسخه Repository جدید نسازید.
