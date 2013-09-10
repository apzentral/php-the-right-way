---
title: การติดตั้งบน Windows
isChild: true
---

## การติดตั้งบน Windows {#windows_setup_title}

PHP นั้นสามารถติดตั้งได้หลายวิธีบน Windows คุณสามารถ [download ไบนารี][php-downloads] และเมื่อไม่นานมานี้คุณสามารถใช้ '.msi' ในการติดตั้ง
แต่ว่าการใช้ '.msi' ในการติดตั้งนั้นได้ถูกหยุดพัฒนาใน PHP รุ่น 5.3.0

สำหรับผู้ที่ต้องการเรียนรู้หรือพัฒนาโปรแกรมในเครื่องคอมพิวเตอร์ของคุณนั้น คุณสามารถที่จะใช้ PHP รุ่น 5.4+ ซึ่งได้มีความสามารถที่จะใช้ webserver CLI ได้
ดังนั้นคุณไม่จำเป็นที่จะต้องเรียนรู้วิธีการติดตั้ง webserver
ถ้าคุณต้องการที่จะใช้ "all-in-one" แพคเกจที่รวบรวม webserver และ MySQL ไว้แล้วในตัว คุณสามารถใช้แพคเกจอย่างเช่น [Web Platform Installer][wpi],
[Zend Server CE][zsce], [XAMPP][xampp] และ [WAMP][wamp] แพคเกจเหล่านี้จะช่วยให้คุณสามารถที่จะเริ่มต้นใช้ภาษา PHP ได้อย่างรวดเร็ว
แต่คุณยังที่จะต้องระวังถึงความแตกต่างระหว่างสภาพแวดล้อม เวลาคุณต้องการที่จะนำโปรแกรมที่คุณพัฒนานั้นไปใช้งานจริง ยกตัวอย่างเช่น ถ้าคุณพัฒนาโปรแกรมบน
Windows แต่คุณต้องนำโปรแกรมนั้นไปใช้งานจริงใน Linux คุณจะต้องระวังสิ่งเหล่านี้ด้วย

ถ้าคุณต้องการใช้โปรแกรมที่คุณพัฒนาบน Windows คุณจะต้องใช้ IIS7 ซี่ง IIS7 จะทำให้โปรแกรมของคุณนั้นทำงานได้อย่างทีประสิทธิภาพมากที่สุด
คุณยังสามารถที่จะใช้ [phpmanager][phpmanager] (ปลั๊กอิน GUI สำหรับ IIS7) จะช่วยให้การดูแลระบบ PHP ของคุณอย่างง่ายดาย
IIS7 นั้นได้รวม FastCGI มาเรียบร้อย คุณเพียงแค่ตั้งค่าให้ PHP นั้นเป็นตัวจัดการ คุณสามารถหาข้อมูลเพิ้มเติมได้จาก [ข้อมูลสำหรับการใช้ IIS สำหรับ PHP ใน iis.net][php-iis]

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
