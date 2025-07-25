<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "8311f46a35cf608c9780f39b62c9dc3f",
  "translation_date": "2025-07-14T02:03:20+00:00",
  "source_file": "05-AdvancedTopics/mcp-root-contexts/README.md",
  "language_code": "th"
}
-->
## ตัวอย่าง: การจัดการ Root Context

การจัดการ root contexts อย่างมีประสิทธิภาพเป็นสิ่งสำคัญสำหรับการรักษาประวัติการสนทนาและสถานะ ด้านล่างนี้คือตัวอย่างวิธีการใช้งานการจัดการ root context

## Root Context สำหรับการช่วยเหลือแบบหลายรอบ

ในตัวอย่างนี้ เราจะสร้าง root context สำหรับเซสชันช่วยเหลือแบบหลายรอบ โดยแสดงให้เห็นวิธีการรักษาสถานะข้ามหลายการโต้ตอบ

## แนวทางปฏิบัติที่ดีที่สุดสำหรับ Root Context

นี่คือแนวทางปฏิบัติที่ดีที่สุดสำหรับการจัดการ root contexts อย่างมีประสิทธิภาพ:

- **สร้าง Context ที่เน้นจุดประสงค์ชัดเจน**: สร้าง root contexts แยกต่างหากสำหรับวัตถุประสงค์หรือโดเมนการสนทนาที่แตกต่างกันเพื่อรักษาความชัดเจน

- **ตั้งนโยบายการหมดอายุ**: นำนโยบายมาใช้เพื่อเก็บถาวรหรือลบ contexts เก่าเพื่อจัดการพื้นที่จัดเก็บและปฏิบัติตามนโยบายการเก็บรักษาข้อมูล

- **เก็บข้อมูลเมตาที่เกี่ยวข้อง**: ใช้ metadata ของ context เพื่อเก็บข้อมูลสำคัญเกี่ยวกับการสนทนาที่อาจมีประโยชน์ในภายหลัง

- **ใช้ ID ของ Context อย่างสม่ำเสมอ**: เมื่อสร้าง context แล้ว ให้ใช้ ID นั้นอย่างสม่ำเสมอสำหรับคำขอที่เกี่ยวข้องทั้งหมดเพื่อรักษาความต่อเนื่อง

- **สร้างสรุป**: เมื่อ context มีขนาดใหญ่ขึ้น ให้พิจารณาสร้างสรุปเพื่อจับข้อมูลสำคัญในขณะที่จัดการขนาดของ context

- **ใช้งานการควบคุมการเข้าถึง**: สำหรับระบบที่มีผู้ใช้หลายคน ให้ใช้งานการควบคุมการเข้าถึงที่เหมาะสมเพื่อรับประกันความเป็นส่วนตัวและความปลอดภัยของ context การสนทนา

- **จัดการข้อจำกัดของ Context**: ตระหนักถึงข้อจำกัดของขนาด context และนำกลยุทธ์มาใช้สำหรับการจัดการการสนทนาที่ยาวมาก

- **เก็บถาวรเมื่อเสร็จสิ้น**: เก็บถาวร context เมื่อการสนทนาเสร็จสิ้นเพื่อปล่อยทรัพยากรในขณะที่ยังคงรักษาประวัติการสนทนาไว้

## ต่อไปคืออะไร

- [5.5 Routing](../mcp-routing/README.md)

**ข้อจำกัดความรับผิดชอบ**:  
เอกสารนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติ [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้ความถูกต้องสูงสุด แต่โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นทางถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่สำคัญ ขอแนะนำให้ใช้บริการแปลโดยผู้เชี่ยวชาญมนุษย์ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดใด ๆ ที่เกิดจากการใช้การแปลนี้