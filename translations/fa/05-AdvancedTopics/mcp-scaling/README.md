<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "cd973a4e381337c6a3ac2443e7548e63",
  "translation_date": "2025-07-14T02:27:25+00:00",
  "source_file": "05-AdvancedTopics/mcp-scaling/README.md",
  "language_code": "fa"
}
-->
## معماری توزیع‌شده

معماری‌های توزیع‌شده شامل چندین گره MCP است که با هم کار می‌کنند تا درخواست‌ها را پردازش کنند، منابع را به اشتراک بگذارند و افزونگی فراهم کنند. این رویکرد با اجازه دادن به گره‌ها برای ارتباط و هماهنگی از طریق یک سیستم توزیع‌شده، مقیاس‌پذیری و تحمل خطا را افزایش می‌دهد.

بیایید نگاهی به نمونه‌ای از پیاده‌سازی معماری سرور MCP توزیع‌شده با استفاده از Redis برای هماهنگی بیندازیم.

## مرحله بعد

- [5.8 امنیت](../mcp-security/README.md)

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نواقصی باشند. سند اصلی به زبان بومی خود باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچ گونه سوءتفاهم یا تفسیر نادرستی که از استفاده این ترجمه ناشی شود، نیستیم.