---
isChild: true
---

## Password Hashing {#password_hashing_title}

สำหรับนักพัฒนาโปรแกรม PHP แล้ว ก็จะมีวันหนี่งที่จะต้องสร้างโปรแกรม PHP ที่จะต้่องมีระบบ user login ในการ login นั้นคุณจะต้องมีการเก็บข้อมูล
usernames และ passwords ในฐานข้อมูลของคุณ และคุณก็จะต้องนำข้อมูลเหล่านี้มาใช้ในการ authenticate users เวลาที่เขา login ด้วย

ดังนั้น สิ่งที่สำคัญที่สุดคือการเก็บข้อมูลของ passwords ด้วย [_hash_][3] ให้ถูกต้อง ก่อนที่จะบันทึกลงในฐานข้อมูล สาเหตุที่เราใช้ hash ในการ
บันทึกข้อมูล passwords ก็เพราะว่าการ hashing นั้น เมื่อ hash ข้อมูลไปแล้วจะไม่สามารถที่จะหาข้อมูลเดิมก่อนที่จะ hash ได้ นั่นก็หมายความว่า
เราไม่สามารถที่จะทราบว่า passwords นั้นคืออะไร นอกจากนั้นเมื่อ hash ข้อมูลแล้ว เราก็จะได้ string ที่มีความยาวที่เท่ากันเสมอ
ดังนั้น คุณจึงสามารถที่จะเปรียบเทียบค่า hash สองค่าได้ว่ามาจาก string ตัวเดียวกันหรือเปล่า แต่คุณไม่สามารถที่จะหาค่า string เดิมนั้นได้
ถ้าคุณไม่ได้ทำการ hash passwords ไว้แล้ว และฐานข้อมูลของคุณนั้นได้ถูกจู่โจม ข้อมูลของ users ของคุณจะถูกขโมยไปได้ และเขาก็สามารถที่จะเห็น passwords
ของ users ของคุณได้ทันที และนอกจากนั้น users ส่วนมากก็จะใช้ password อันเดียวกันนี้กับที่อื่นๆด้วย ดังนั้นเราจะต้องคิดว่าความปลอดภัยเป็นสิ่งที่สำคัญมาก

**Hashing passwords ด้วย `password_hash`**

ใน PHP รุ่น 5.5 นั้นได้เพิ่มเติม `password_hash` ฟังก์ชั่นเข้ามา และในฟังก์ชั่นนี้ได้ใช้ BCrypt ซึ่งถือว่าเป็น algorithm ที่ปลอดภัยมากที่สุดในขณะนี้ที่ PHP รองรับ
แต่ PHP ก็จะคอยเพิ่มเติม algorithms ต่างๆเข้ามาในรุ่นต่อๆไป คุณยังสามารถใช้ `password_compat` library ได้ เพราะว่า library นี้รองรับตั้งแต่ PHP >= 5.3.7

ตัวอย่างข้างล่างนี้จะแสดงการ hash string และหลังจากนั้นจะทำการตรวจค่า hash กับ string อันใหม่นี้ แต่เมื่อค่า string สองค่านี้ต่างกัน
('secret-password' vs. 'bad-password') จึงทำให้การ login ไม่ประสบความสำเร็จ

{% highlight php %}
<?php
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    //Correct Password
} else {
    //Wrong password
}
{% endhighlight %}

* [เรียนรู้เกี่ยวกับ `password_hash`] [1]
* [`password_compat` สำหรับ PHP  >= 5.3.7 && < 5.5] [2]
* [เรียนรู้เกี่ยวกับ hashing ในหัวข้อของ cryptography] [3]
* [PHP `password_hash` RFC] [4]

[1]: http://us2.php.net/manual/en/function.password-hash.php
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
