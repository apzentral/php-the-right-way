---
title: Databases
---

# Databases {#databases_title}

เวลาคุณพัฒนาโปรแกรมภาษา PHP นั้น ส่วนมากเราจะต้องมีวิธีที่จะทำการเก็บข้อมูลไว้เพื่อที่จะนำมาใช้ได้อีก ดังนั้นคุณจำเป็นที่จะต้องใช้ฐานข้อมูล
คุณสามารถที่จะเลือกวิธีการติดต่อกับฐานข้อมูลได้ แต่เราแนะนำว่าวิธีการติดต่อกับฐานข้อมูลนั้นจนถึงรุ่น _PHP 5.1.0_ ควรที่จะใช้ native drivers อย่างเช่น
[mysql][mysql], [mysqli][mysqli], [pgsql][pgsql], และอื่นๆ.

Native drivers นั้นดีมากถ้าคุณเลือกที่จะใช้ฐานข้อมูลระบบเดียวเท่านั้นในโปรแกรมคุณ ถ้าคุณต้องทำการใช้ฐานข้อมูลทั้ง MySQL, MSSQL และ Oracle นั้น คุณจะต้อง
สามารถที่จะใช้ drivers ตัวเดียวกันได้ หรือแม้กระทั้งคุณจะต้องเรียนรู้วิธีการใช้ drivers เหล่านั้นสำหรับแต่ละฐานข้อมูล นั้นถือว่าเป็นทางเลือกที่ไม่ดี

และนอกจากนั้น mysql native drivers สำหรับ PHP นั้นได้เลิกทำการพัฒนาแล้ว และมาตรฐานของ PHP 5.4.0 นั้นสำหรับโครงการนี้คือ "Long term deprecation"
นั้นหมายความว่า PHP จะไม่นำ mysql native drivers มาอยู่ใน PHP แล้ว คาดว่า PHP รุ่น 5.6 (หรือรุ่นที่มาหลังจาก 5.5) อาจจะถูกนำออกไปแล้วก็ได้ ดังนั้นถ้าคุณใช้
`mysql_connect()` และ `mysql_query()` ในโปรแกรมของคุณนั้น คุณจะต้องแก้ไขโปรแกรมของคุณใหม่อย่างแน่นอน ดังนั้นทางเลือกที่ดีที่สุดคือ ใช้ mysqli หรือ PDO
ในโปรแกรมของคุณแทน คุณจะได้ไม่ต้องมาแก้ไขโปรแกรมของคุณในภายหลัง
_ถ้าคุณเริ่มโปรแกรมของคุณตั้งแต่ต้น คุณสมควรที่จะใช้ MySQLi หรือ PDO ห้ามใช้ mysql เด็ดขาด [อ่าน MySQLi extension เพิ่มเติม][mysqli],_

* [PHP: เลือกใช้ API สำหรับ MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)

## PDO

PDO เป็น database connection abstraction library &mdash; สร้างขึ้นสำหรับ PHP ตั้งแต่รุ่น 5.1.0 &mdash; ที่จะสามารถให้นำไปใช้ในการติดต่อกับฐานข้อมูล
ต่างๆมากมาย PDO จะไม่แปล SQL queries หรือช่วยเพิ่มเติมความสามารถให้ฐานข้อมูล PDO นั้นจะทำการติดต่อกับฐานข้อมูลต่่างๆเท่านั้น โดยใช้ API เดียวกันในการติดต่อ

แต่ที่สำคัญมากที่สุด `PDO` จะช่วยป้องกันข้อมูลภายนอกต่างๆที่จะเข้ามาในฐานข้อมูลของเราได้อย่างปลอดภัย หรือที่เรียกว่า database SQL injection attacks
เราสามารถป้องกันได้โดยเรียกใช้ PDO statements และ bound parameters

เรามายกตัวอย่างว่า เรามี PHP script ที่รับ ID ที่เป็นตัวเลขใน query นั้น ดังนั้น ID นี้สามารถที่จะเรียกหาข้อมูล user ในฐานข้อมูลได้
ตัวอย่างนี้ เป็นตัวอย่างที่`ผิด`ในการติดต่อฐานข้อมูล:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

ตัวอย่างโปรแกรมนี้เป็นสิ่งที่ผิดมาก! คุณเรียกใช้ `$_GET['id']` ใน SQL query แบบนี้ คุณจะสามารถโดนขโมยข้อมูลได้โดยง่าย
พวก hacker สามารถที่จะผ่านค่า ID ใน URL เข้าไปได้แบบนี้ `http://domain.com/?id=1%3BDELETE+FROM+users` ดังนั้น
`$_GET['id']` จะได้รับค่า `1;DELETE FROM users` คำสั่งนี้จะทำให้ฐานข้อมูลของคุณลบข้อมูลทุกอย่างใน users table!
วิธีการแก้นั้นสามารถทำได้โดยตรวจสอบ input และทำการแก้ไข input นั้น โดยใช้ PDO bound parameters

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- Automatically sanitized by PDO
$stmt->execute();
{% endhighlight %}

ตัวอย่างข้างบนนี้ถูกต้อง คุณได้เรียกใช้ bound parameter ใน PDO statement ดังนั้น PDO จะทำการ escapes input จาก ID ก่อนที่จะนำไปติดต่อกับฐานข้อมูล
เพื่อที่จะทำการป้องกัน SQL injection attacks!

* [เรียนรู้เพิ่มเติมเกี่ยวกับ PDO][1]

คุณควรที่จะทราบว่าการติดต่อฐานข้อมูลในแต่ละครั้งนั้นจะเรียกใช้ทรัพยากรอย่างมากและแต่ใน PHP นั้นเราจะไม่เคยได้ยินว่า ถ้าเราไม่เรียกปิดฐานข้อมูลเมื่อเลิกใช้นั้น
จะทำให้เกิดการเสียทรัพยากรได้ แต่ว่าเราจะพบเหตุการณ์นี้ได้ในภาษาอื่นๆ การใช้ PDO นั้นคุณสามารถที่จะทำการเลิกการเชื่อมต่อกับฐานข้อมูลได้โดยทำลาย PDO object
นั้นโดยการลบ references กับ PDO object ได้โดยการตั้งค่า NULL ถ้าคุณไม่ทำการตั้งค่านี้ให้เป็น NULL แล้วละก็ PHP จะทำการปิดการเชื่อมต่อกับฐานข้อมูลเมื่อ
โปรแกรม PHP ของคุณได้จบการทำงาน นอกจากคุณได้ทำการติดต่อด้วยวิธีแบบ persistent PHP จะไม่ทำการปิดฐานข้อมูลให้คุณ

* [เรียนรู้เกี่ยวกับการติดต่อกับฐานข้อมูลด้วย PDO][5]

## Abstraction Layers

Frameworks ส่วนมากจะได้ทำการ abstraction layer ร่วมกับ PDO มาแล้ว ดังนั้นจะสามารถที่จะใช้ PHP methods ในการเพิ่มเติมประสิทธิภาพให้แด่ฐานข้อมูล
ต่างๆให้ดีขึ้น ทำให้เกิดการ abstraction จากฐานข้อมูลโดยสิ้นเชิง แต่วิธีการนี้จะเพิ่ม overhead ให้กับโปรแกรมของเรา แต่ข้อดีคือ ถ้าคุณต้องการที่จะสร้างโปรแกรมที่รองรับ
ฐานข้อมูลต่่างๆ อย่างเช่น MySQL, PostgreSQL และ SQLite นั้น การเพิ่ม overhead เล็กน้อยเหล่านี้ย่อมที่จะคุ้มค่ากับโปรแกรมที่สามารถดูแลได้ง่ายขึ้น

abstraction layers บางตัวนั้นได้ถูกสร้างโดยใช้มาตรฐานแบบ PSR-0 namespace ดังนั้นคุณจึงสามารถนำมาใช้ในโครงการคุณได้อย่างง่ายดาย:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/en/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[5]: http://php.net/manual/en/pdo.connections.php
[6]: https://github.com/auraphp/Aura.Sql

[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
