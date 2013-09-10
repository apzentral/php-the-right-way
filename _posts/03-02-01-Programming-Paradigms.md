---
title: ต้นแบบอย่างของภาษา
isChild: true
---

## ต้นแบบอย่างของภาษา {#programming_paradigms_title}

PHP เป็นภาษาที่มีความยืดหยุนสูง, เป็นภาษาไดนามิกที่รองรับเทคนิคในการเขียนโปรแกรมทุกรูปแบบ
PHP ได้รับการพัฒนาอย่างรวดเร็วในช่วงปีที่ผ่านมา โดยเฉพาะอย่างยิ่งได้เพิ่มเติมการเขียนโปรแกรมเชิงวัตถุที่
สมบูรณ์แบบใน PHP รุ่น 5.0 (2004) anonymous functions และ namespaces ใน PHP 5.3 (2009) และ
traits ใน PHP 5.4 (2012)

### การเขียนโปรแกรมเชิงวัตถุ

PHP ได้มีการรองรับการเขียนโปรแกรมเชิงวัตถุอย่างสมบูรณ์แบบ อย่างเช่น การใช้ classes, abstract classes,
interfaces, inheritance, constructors, cloning, exceptions, และอื่นๆ

* [ข้อมูลเพิ่มเติมของ Object-oriented ใน PHP][oop]
* [ข้อมูลเพิ่มเติมของ Traits][traits]

### การเขียนโปรแกรมเชิงฟังก์ชั่น

PHP สนับสนุน first-class ฟังก์ชั่น หมายความว่า เราสามารถที่จะนำฟังก์ชั่นมากำหนดค่าให้แด่ตัวแปลได้ นั้นคือ เราสามารถนำฟังก์ชั่นที่ผู้
เขียนโปรแกรมสร้างขึ้น หรือฟังก์ชั่นที่มากับ PHP นำมาอ้างอิงจากตัวแปลหรือเรียกใช้แบบไดนามิกได้ ฟังก์ชั่นสามารถที่จะส่งผ่านได้
แบบอาร์กิวเมนต์ไปยังฟังก์ชั่นอื่นๆได้ (ความสามารถนี้เรียกว่า Higher-order ฟังก์ชั่น) และฟังก์ชั่นก็สามารถที่จะคืนค่าฟังก์ชั่นอื่นได้อีกด้วย

Recursion เป็นคุณลักษณะที่ฟังก์ชั่นสามารถที่จะเรียกฟังก์ชั่นของตัวเองได้ แต่ภาษา PHP จะมุ่งเน้นการใช้ iteration มากกว่า

anonymous ฟังก์ชั่น (ที่สนับสนุน closures) ที่มาใหม่นั้นได้ มีตั้งแต่ PHP รุ่น 5.3 (2009)

ใน PHP 5.4 ได้เพิ่มความสามารถในการใช้ closures ในขอบเขตของวัตถุและได้เพิ่มความสามารถให้กับ callables โดยสามารถที่จะนำมาใช้สลับ
กับ anonymous ฟังก์ชั่น ได้เกือบทุกกรณี

* ข้อมูลเพิ่มเติมของ [การเขียนโปรแกรมเชิงฟังก์ชั่นใน PHP](/pages/Functional-Programming.html)
* [ข้อมูลเพิ่มเติมของ Anonymous ฟังก์ชั่น][anonymous-functions]
* [ข้อมูลเพิ่มเติมของ Closure คลาส][closure-class]
* [ข้อมูลเพิ่มเติมของ Closures RFC][closures-rfc]
* [ข้อมูลเพิ่มเติมของ Callables][callables]
* [ข้อมูลเพิ่มเติมของการเรียกใช้ฟังก์ชั่นแบบไดนามิกด้วย `call_user_func_array`][call-user-func-array]

### เมทาโปรแกรมมิง

PHP สนับสนุนรูปแบบการเขียนเมทาโปรแกรมผ่านทางกลไกอย่าง Reflection API และ Magic Methods PHP ได้มี Magic Methods มากมาย
อย่างเช่น `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()` และอื่นๆ ที่สามารถช่วยให้นักพัฒนาโปรแกรมเขียน hook
ในคลาสได้อย่างง่ายดาย นักพัฒนาภาษา Ruby ชอบบอกว่า PHP ขาดความสามารถ `method_missing` แต่แท้จริงแล้วมันคือ
`__call()` และ `__callStatic()`

* [ข้อมูลเพิ่มเติมของ Magic Methods][magic-methods]
* [ข้อมูลเพิ่มเติมของ Reflection][reflection]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[overloading]: http://php.net/manual/en/language.oop5.overloading.php
[oop]: http://www.php.net/manual/en/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/en/functions.anonymous.php
[closure-class]: http://php.net/manual/en/class.closure.php
[callables]: http://php.net/manual/en/language.types.callable.php
[magic-methods]: http://php.net/manual/en/language.oop5.magic.php
[reflection]: http://www.php.net/manual/en/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/en/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
