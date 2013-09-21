---
isChild: true
---

## Frameworks {#frameworks_title}

ผู้พัฒนาโปรแกรมภาษา PHP ส่วนมากได้ใช้ frameworks ในการสร้างโปรแกรมสำหรับเว็บแทนที่จะต้องมาสร้าง framework ใช้เอง Frameworks นั้นจะทำการรวบรวม
สิ่งที่มีประโยชน์และเครื่องมือต่างๆให้คุณได้นำมาใช้ในการเขียนโปรแกรมของคุณได้ง่ายมากขึ้น

คุณไม่จำเป็นที่จะต้องใช้ framework ในทุกโครงการของคุณ ในบางครั้งเพียงแค่ PHP โปรแกรมธรรมดาก็สามารถที่จะนำไปใช้งานได้แล้ว แต่ถ้าคุณต้องการที่จะใช้ framework นั้น
ก็จะแบ่งได้เป็นสามจำพวก:

* Micro Frameworks
* Full-Stack Frameworks
* Component Frameworks

Micro-frameworks ส่วนมากจะทำการ route HTTP request ไปยังโปรแกรมของคุณ ผ่านทาง callback, controller, method, และอื่นๆ ให้รวดเร็วที่สุด ในบางครั้ง
อาจจะมี libraries อยู่ด้วย เพื่อมาช่วยในการพัฒนาโปรแกรม อย่างเช่น database wrappers อย่างง่ายๆ ส่วนมากจะนำมาใช้ในใน remote HTTP services

แต่ frameworks ส่วนมากก็จะเพิ่มความสามารถให้มากขึ้นไปอีกมากกว่า micro-framework นั้นก็จะทำให้กลายเป็น Full-Stack Frameworks โดยจะได้มี ORMs,
Authentication packages และ อื่นๆอีก

Component-based frameworks นั้นจะเป็นการนำ libraries ต่างๆที่มีหน้าที่เดียวนำมารวมกันให้กลายเป็น framework และเราก็สามารถนำ component-based frameworks
มารวมกันเพื่อให้กลายเป็น micro- หรือ full-stack framework

* [PHP Frameworks ที่เป็นที่นิยม](https://github.com/codeguy/php-the-right-way/wiki/Frameworks)