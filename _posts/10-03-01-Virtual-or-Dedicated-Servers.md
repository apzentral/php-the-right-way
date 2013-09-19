---
isChild: true
---

## Virtual หรือ Dedicated Servers {#virtual_or_dedicated_servers_title}

ถ้าคุณมีความสามารถที่จะบริหารและจัดการ หรืออยากที่จะเรียนรู้ ดังนั้นการใช้ virtual หรือ dedicated servers จะทำให้คุณสามารถที่จะควบคุมและจัดการ
สภาพแวดล้อมของโปรแกรมของคุณได้

### nginx และ PHP-FPM

PHP, ที่เรียกใช้ผ่าน PHP's built-in FastCGI Process Manager (FPM) นั้นสามารถนำมาใช้คู่กับ [nginx](http://nginx.org) ได้อย่างดี โดย
[nginx](http://nginx.org) เป็นเว็บเซิร์ฟเวอร์มีคุณสมบัติที่เล็กและประสิทธิภาพสูง nginx นั้นจะใช้หน่วยความจำที่น้อยมากกว่า Apache และสามารถที่จะ
มีระบบจัดการ concurrent requests ที่ดีกว่า สิ่งนี้เป็นสิ่งที่สำคัญมากบน virtual servers ที่ไม่ได้มีหน่วยความจำมากพอที่จะนำมาแบ่งใช้ได้

* [อ่านเพิ่มเติมเกี่ยวกับ nginx](http://nginx.org)
* [อ่านเพิ่มเติมเกี่ยวกับ PHP-FPM](http://php.net/manual/en/install.fpm.php)
* [อ่านเพิ่มเติมเกี่ยวกับการติดตั้ง nginx และ PHP-FPM อย่างปลอดภัย](https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/)

### Apache and PHP

PHP และ Apache นั้นได้ทำการร่วมกันมายาวนานมาก Apache นั้นสามารถที่จะเพิ่มเติม [modules](http://httpd.apache.org/docs/2.4/mod/) ต่างๆเพื่อเพิ่ม
ความสามารถได้อย่างง่าย สำหรับ shared servers แล้ว Apache นั้นได้ถือว่าเป็นที่นิยมอย่างมาก และก็สามารถที่จะติดตั้ง PHP frameworks และ open source โปรแกรม
อย่าง WordPress ได้ง่าย แต่ข้อเสียนั้น Apache จะใช้ทรัพยากรที่มากกว่า nginx และไม่สามารถที่จะรองรับการเรียกใช้จากหลายผู้เรียกใช้ได้พร้อมกัน

Apache นั้นได้มีการติดตั้งได้หลายรูปแบบเพื่อที่จะเรียกใช้ PHP วิธีที่ง่ายและใช้กันอย่างมากที่สุดก็คือการใช้
[prefork MPM](http://httpd.apache.org/docs/2.4/mod/prefork.html) ด้วย mod_php5 การใช้ระบบการติดตั้งแบบนี้นั้นจะไม่ได้เป็นระบบติดตั้งที่บริหาร
ทรัพยากรได้ดีที่สุด แต่วิธีนี้เป็นวิธีที่ง่ายที่สุดที่ทำให้ใช้ PHP ได้อย่างง่าย ถ้าคุณไม่ต้องการที่จะจัดการ server ด้วยตัวคุณเอง วิธีนี้ก็ถือว่าเป็นวิธีที่ดีที่สุด คำเตือนถ้าคุณใช้
mod_php5 คุณจะต้องใช้ prefork MPM ด้วย

อีกทางเลือกหนึ่งก็คือ ถ้าคุณต้องการที่จะเพิ่มประสิทธิภาพและความเสถียรให้กับ Apache นั้น คุณก็สมควรที่จะใช้ระบบ FPM ดังที่ nginx ใช้ และเรียกใช้
[worker MPM](http://httpd.apache.org/docs/2.4/mod/worker.html) หรือ [event MPM](http://httpd.apache.org/docs/2.4/mod/event.html)
ด้วย mod_fastcgi หรือ mod_fcgid การตั้งค่าเหล่านี้นั้นรับรองว่าจะทำให้ Apache ใช้หน่วยความจำได้อย่างมีประสิทธิภาพที่มากขึ้นและรวดเร็วขึ้น แต่คุณจะต้องทราบวิธีใน
การติดตั้งและจะใช้เวลาในการติดตั้งนานกว่า

* [อ่านเพิ่มเติมเกี่ยวกับ Apache](http://httpd.apache.org/)
* [อ่านเพิ่มเติมเกี่ยวกับ Multi-Processing Modules](http://httpd.apache.org/docs/2.4/mod/mpm_common.html)
* [อ่านเพิ่มเติมเกี่ยวกับ mod_fastcgi](http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html)
* [อ่านเพิ่มเติมเกี่ยวกับ mod_fcgid](http://httpd.apache.org/mod_fcgid/)
