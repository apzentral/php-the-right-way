---
isChild: true
---

## Error Reporting {#error_reporting_title}

การบันทึกข้อผิดพลาดนั้นจะมีประโยชน์อย่างมากในการหาข้อผิดพลาดในโปรแกรมของคุณ แต่ข้อเสียนั้นก็คืออาจจะเป็นเผยข้อมูลเกี่ยวกับโครงสร้างโปรแกรมของคุณสู่โลกภายนอกได้
ดังนั้นการที่จะปกป้องโปรแกรมของคุณจากปัญหาที่อาจจะเกิดขึ้นได้จากการแสดงข้อผิดพลาดเหล่านั้น คุณจะต้องทำการกำหนดค่าของเซิร์ฟเวอร์แตกต่างกันระหว่างกำลังพัฒนา
และนำไปใช้งานจริงใน production

### ระหว่างการพัฒนา

สำหรับการแสดงข้อผิดพลาดระหว่างการ<strong>พัฒนา</strong>นั้น เราต้องการที่จะแสดงข้อผิดพลาดทุกอย่างออกมาทั้งหมด, เราสามารถที่จะตั้งค่าเหล่านี้ได้ใน `php.ini`:

    display_errors = On
    display_startup_errors = On
    error_reporting = -1
    log_errors = On

> การผ่านค่า `-1` เข้าไป จะทำให้ PHP แสดงค่าผิดพลาดต่างๆออกมา ไม่ว่าจะเป็นค่าใหม่ๆที่จะได้รับเพิ่มเติมเข้ามา PHP รุ่นอนาคต การใช้ค่าคงที่ `E_ALL` ใน PHP รุ่น
5.4 ก็จะเป็นเหมือนกัน - [php.net](http://php.net/manual/function.error-reporting.php)

การตั้งค่า `E_STRICT` ในการแสดงข้อผิดพลาดนั้น ได้เริ่มใช้ใน PHP รุ่น 5.3.0 และค่านี้จะไม่ได้รวมอยู่ใน `E_ALL` ด้วย แต่ในรุ่น 5.4.0 นั้น จะถูกรวมอยู่ใน `E_ALL`
ด้วย นั่นก็หมายความว่า ถ้าคุณได้ใช้ PHP รุ่น 5.3 นั้นและคุณต้องการที่จะแสดงข้อผิดพลาดทั้งหมดแล้วละก็จะต้องใช้คำสั่ง `-1` หรือ `E_ALL | E_STRICT`

**รวมรวมค่าที่ใช้ในการแสดงข้อผิดพลาดทั้งหมดโดยแยกตามรุ่นของ PHP**

* &lt; 5.3 `-1` หรือ `E_ALL`
* &nbsp; 5.3 `-1` หรือ `E_ALL | E_STRICT`
* &gt; 5.3 `-1` หรือ `E_ALL`

### Production

สำหรับการใช้การแสดงข้อผิดพลาดใน production นั้น คุณสมควรที่ซ่อนข้อผิดพลาดโดยการตั้งค่าเหล่านี้ใน `php.ini`:

    display_errors = Off
    display_startup_errors = Off
    error_reporting = E_ALL
    log_errors = On

โดยการตั้งค่าเหล่านั้นใน production ข้อผิดพลาดทั้งหลายก็ยังคงเก็บไว้ใน error logs ในเว็บเซิร์ฟเวอร์ของคุณ แต่ข้อผิดพลาดเหล่านี้จะไม่แสดงออกมาให้ผู้ใช้
โปรแกรมของคุณได้เห็น, สำหรับข้อมูลเพิ่มเติมเกี่ยวการตั้งค่าเหล่านี้ คุณสามารถอ่านได้จากคู่มือของ PHP:

* [error_reporting](http://php.net/manual/errorfunc.configuration.php#ini.error-reporting)
* [display_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-errors)
* [display_startup_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-startup-errors)
* [log_errors](http://php.net/manual/errorfunc.configuration.php#ini.log-errors)
