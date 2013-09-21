---
isChild: true
---

## Bytecode Cache {#bytecode_cache_title}

เมื่อ PHP ไฟล์ได้ทำการเรียกใช้ การทำงานของ PHP ในระบบนั้นแล้ว จะเริ่มจาก compiled ลงเป็น bytecode (หรือที่เรียกว่า opcode) และคอมพิวเตอร์ก็จะนำ bytecode
เหล่านี้ไปใช้ในการทำงาน ถ้า PHP ไฟล์ไม่ได้ถูกแก้ไขแล้ว bytecode นี้ก็จะเหมือนเดิม นั่นก็หมายความว่าการ compilation นั้นจะทำให้เสียทรัพยากรเวลาของ CPU

นั้นก็ถึงเวลาที่ bytecode cache ได้เข้ามามีส่วนช่วยเหลือทำให้ bytecode ที่ได้ถูก compiled ก่อนหน้านี้แล้ว สามารถที่จะถูกเก็บให้อยู่ในหน่วยความจำได้และก็สามารถที่จะ
bytecode เหล่านี้มาใช้ได้อีกต่อๆไปเมื่อถูกเรียกใช้ การติดตั้ง bytecode cache นั้นใช้เวลาไม่นาน และโปรแกรมของคุณก็จะทำงานได้เร็วมากขึ้นด้วย นั่นจึงไม่มีเหตุผลเลย
ที่คุณจะไม่ใช้ bytecode cache ในโครงการของคุณ

ตั้งแต่ PHP รุ่น 5.5, ได้มี bytecode cache ที่ได้ติดตั้งมาอยู่ใน PHP อยู่แล้ว นั่นก็คือ [OPcache](http://php.net/manual/en/book.opcache.php)
แต่ PHP รุ่นก่อนหน้านี้ก็สามารถที่จะนำ OPcache มาใช้ได้

Bytecodes caches ที่เป็นที่นิยม:

* [APC](http://php.net/manual/en/book.apc.php) (PHP 5.4 และรุ่นก่อนหน้านี้)
* [XCache](http://xcache.lighttpd.net/)
* [Zend Optimizer+](http://www.zend.com/products/server/) (ได้อยู่ร่วมกับ Zend Server package)
* [WinCache](http://www.iis.net/download/wincacheforphp) (extension สำหรับ MS Windows Server)
