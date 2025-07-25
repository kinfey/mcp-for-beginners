<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4cc245e2f4ea5db5e2b8c2cd1dadc4b4",
  "translation_date": "2025-07-13T18:10:01+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "fa"
}
-->
در کد قبلی ما:

- کتابخانه‌ها را وارد کردیم
- یک نمونه از client ساختیم و با استفاده از stdio به عنوان روش انتقال به آن متصل شدیم.
- لیست پرامپت‌ها، منابع و ابزارها را گرفتیم و همه را فراخوانی کردیم.

همین است، یک client که می‌تواند با یک MCP Server ارتباط برقرار کند.

در بخش تمرین بعدی وقت می‌گذاریم تا هر قطعه کد را تجزیه و تحلیل کنیم و توضیح دهیم چه اتفاقی می‌افتد.

## تمرین: نوشتن یک client

همانطور که گفته شد، وقت می‌گذاریم تا کد را توضیح دهیم و اگر خواستید می‌توانید همراه با ما کدنویسی کنید.

### -1- وارد کردن کتابخانه‌ها

بیایید کتابخانه‌های مورد نیاز را وارد کنیم، ما به ارجاعاتی به client و پروتکل انتقال انتخابی‌مان، stdio، نیاز داریم. stdio پروتکلی است برای برنامه‌هایی که قرار است روی ماشین محلی شما اجرا شوند. SSE پروتکل انتقال دیگری است که در فصل‌های بعدی نشان خواهیم داد اما این گزینه دیگر شماست. فعلاً بیایید با stdio ادامه دهیم.

---

بیایید به مرحله نمونه‌سازی برویم.

### -2- نمونه‌سازی client و انتقال

ما باید یک نمونه از پروتکل انتقال و همچنین نمونه‌ای از client خود بسازیم:

---

### -3- لیست کردن ویژگی‌های سرور

حالا ما یک client داریم که می‌تواند به سرور متصل شود اگر برنامه اجرا شود. اما در واقع ویژگی‌های سرور را لیست نمی‌کند، پس بیایید این کار را انجام دهیم:

---

عالی است، حالا همه ویژگی‌ها را گرفته‌ایم. حالا سوال این است که چه زمانی از آن‌ها استفاده کنیم؟ خب، این client خیلی ساده است، ساده به این معنا که ما باید به صورت صریح ویژگی‌ها را وقتی می‌خواهیم فراخوانی کنیم. در فصل بعدی، یک client پیشرفته‌تر می‌سازیم که به مدل زبان بزرگ خودش (LLM) دسترسی دارد. فعلاً بیایید ببینیم چگونه می‌توانیم ویژگی‌های سرور را فراخوانی کنیم:

### -4- فراخوانی ویژگی‌ها

برای فراخوانی ویژگی‌ها باید مطمئن شویم که آرگومان‌های درست را مشخص کرده‌ایم و در برخی موارد نام چیزی که می‌خواهیم فراخوانی کنیم را نیز وارد کنیم.

---

### -5- اجرای client

برای اجرای client، دستور زیر را در ترمینال تایپ کنید:

---

## تمرین

در این تمرین، شما از آنچه یاد گرفته‌اید برای ساخت یک client استفاده می‌کنید اما یک client خودتان می‌سازید.

در اینجا یک سرور وجود دارد که می‌توانید از آن استفاده کنید و باید از طریق کد client خود به آن فراخوانی بزنید، ببینید آیا می‌توانید ویژگی‌های بیشتری به سرور اضافه کنید تا جذاب‌تر شود.

---

## راه‌حل

[راه‌حل](./solution/README.md)

## نکات کلیدی

نکات کلیدی این فصل درباره clientها به شرح زیر است:

- می‌توانند برای کشف و فراخوانی ویژگی‌ها روی سرور استفاده شوند.
- می‌توانند سرور را همزمان با شروع خودشان راه‌اندازی کنند (مثل این فصل) اما clientها می‌توانند به سرورهای در حال اجرا نیز متصل شوند.
- راه بسیار خوبی برای آزمایش قابلیت‌های سرور در کنار گزینه‌هایی مثل Inspector است که در فصل قبل توضیح داده شد.

## منابع اضافی

- [ساخت clientها در MCP](https://modelcontextprotocol.io/quickstart/client)

## نمونه‌ها

- [ماشین حساب جاوا](../samples/java/calculator/README.md)
- [ماشین حساب .Net](../../../../03-GettingStarted/samples/csharp)
- [ماشین حساب جاوااسکریپت](../samples/javascript/README.md)
- [ماشین حساب تایپ‌اسکریپت](../samples/typescript/README.md)
- [ماشین حساب پایتون](../../../../03-GettingStarted/samples/python)

## مرحله بعد

- بعدی: [ساخت client با LLM](../03-llm-client/README.md)

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نواقصی باشند. سند اصلی به زبان بومی خود باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچ گونه سوءتفاهم یا تفسیر نادرستی که از استفاده این ترجمه ناشی شود، نیستیم.