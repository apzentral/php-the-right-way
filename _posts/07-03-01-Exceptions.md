---
isChild: true
---

## Exceptions {#exceptions_title}

Exceptions เป็นมาตรฐานของภาษาโปรแกรมส่วนใหญ่ แต่สำหรับนักพัฒนาภาษา PHP นั้นจะมากข้ามไป ภาษาอย่าง Ruby นั้นจะใช้ Exception อย่างมากมาย
ถ้าเกิดเหตุการณ์ที่ไม่คาดคิดเกิดขึ้นนั้น เช่น การเรียกใช้ HTTP ที่ผิดพลาด หรือการเชื่อมต่อกับฐานข้อมูลที่ผิดพลาด แม้กระทั้งการที่ไม่สามารถหา image asset ได้
Ruby (หรือ gems ที่กำลังใช้) จะ throw exception ให้กับผู้เรียกใช้ให้เห็นข้อผิดพลาดได้อย่างทันที

สำหรับ PHP นั้น จะไม่ได้ให้ความสำคัญกับการ throw exception มากนัก อย่างเช่น ถ้าคุณใช้ `file_get_contents()` จะให้ค่า `FALSE` และ warning
เท่านั้น โดยเฉพาะ PHP frameworks เก่าอย่าง CodeIgniter จะให้ค่า false เท่านั้น และจะทำการ log ข้อความเหล่านั้นใน logs และอาจจะให้คุณ
ตรวจสอบข้อผิดพลาดได้โดยใช้ `$this->upload->get_error()` แต่ปัญหาที่ใช้วิธีนี้นั้น คือคุณจะต้องตรวจสอบหาข้อผิดพลาดเองและต้องอ่านคู่มือวิธีการเรียกใช้
method เหล่านี้สำหรับ class นั้นๆ แทนที่จะมีมาตรฐานในการตรวจหาข้อผิดพลาดได้ทันที

ปัญหาอีกอย่างก็คือ ถ้า class นั้นทำการ throw ข้อผิดพลาดไปที่หน้าจอและหยุดการทำงานทันทีนั้นจะไม่ดีเท่าการที่จะสามารถจัดการข้อผิดพลาดเหล่านี้ได้ทันทีที่เกิดขี้น
และก็สามารถทำให้โปรแกรมทำงานต่อไปได้จนจบอย่างไม่มีการติดขัด เราสมควรที่จะ throw Exceptions เพื่อที่จะให้ผู้พัฒนาโปรแกรมสามารถที่จะทราบถึงข้อผิดพลาด
ได้ทันที และก็สามารถที่จะจัดการกับข้อผิดพลาดได้ด้วย ดังเช่น ตัวอย่างโปรแกรมนี้

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
finally
{
    // Use this to let user know email was sent
}
{% endhighlight %}

### SPL Exceptions

`Exception` class ที่มากับ PHP นั้นได้ให้ข้อความที่สามารถนำมาใช้ในการ debug ได้น้อยมาก แต่อย่างไรก็ตาม เราสามารถที่จะแก้และปรับปรุงที่จะสร้าง
`Exception` class ชนิดพิเศษได้ โดยการสร้าง class จาก `Exception` class ได้

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

นั้นก็หมายความว่า คุณสามารถที่จะมี catch blocks ได้หลายแบบ เพื่อที่จะคอยดักจับ Exceptions ต่างๆกันได้อย่างง่าย นั่นก็จะส่งผลให้เราสามารถที่จะสร้าง
Exceptions class <em>ได้อย่างมากมาย</em> แต่แท้จริงแล้ว เราสามารถใช้ SPL Exceptions แทนที่ได้ คุณสามารถที่จะเลือก
[SPL extension][splext] เพื่อนำมาใช้ได้เลย

ยกตัวอย่างเช่น ถ้าคุณใช้ Magic Method `__call()` และ ได้ส่งค่า method ที่ผิดไปนั้น PHP จะ `throw new BadFunctionCallException;` ให้เรา
ดังนั้นคุณก็ไม่จำเป็นที่จะต้องสร้าง custom Exception เพีื่อที่จะรองรับ Exception นี้ หรือเรียกใช้ Exception class เบื้องต้น ซึ้งไม่ได้บอกรายละเอียดของ
Exception ได้อย่างเจาะจงมากพอ

* [อ่านเพิ่มเติมเกี่ยวกับ Exceptions][exceptions]
* [อ่านเพิ่มเติมเกี่ยวกับ SPL Exceptions][splexe]
* [การ Nesting Exceptions ใน PHP][nesting-exceptions-in-php]
* [Exception Best Practices ใน PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/en/language.exceptions.php
[splexe]: http://php.net/manual/en/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
