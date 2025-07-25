<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "cd973a4e381337c6a3ac2443e7548e63",
  "translation_date": "2025-07-14T02:31:37+00:00",
  "source_file": "05-AdvancedTopics/mcp-scaling/README.md",
  "language_code": "he"
}
-->
## ארכיטקטורה מבוזרת

ארכיטקטורות מבוזרות כוללות מספר צמתים של MCP שעובדים יחד כדי לטפל בבקשות, לשתף משאבים ולספק גיבוי. גישה זו משפרת את היכולת להרחבה ואת העמידות בפני תקלות על ידי מתן אפשרות לצמתים לתקשר ולתאם דרך מערכת מבוזרת.

בואו נבחן דוגמה לאופן יישום ארכיטקטורת שרת MCP מבוזרת באמצעות Redis לתיאום.

## מה הלאה

- [5.8 אבטחה](../mcp-security/README.md)

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לקחת בחשבון כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי-דיוקים. המסמך המקורי בשפת המקור שלו נחשב למקור הסמכותי. למידע קריטי מומלץ להשתמש בתרגום מקצועי על ידי מתרגם אנושי. אנו לא נושאים באחריות לכל אי-הבנה או פרשנות שגויה הנובעת משימוש בתרגום זה.