---
isChild: true
---

## Command Line Interface {#command_line_interface_title}

PHP ได้ถูกสร้่างขื้นมาเพื่อสร้่างโปรแกรมบนเว็บ แต่ PHP นั้นยังสามารถนำมาสร้างโปรแกรมสคริปต์ command line interface (CLI)
CLI สำหรับ PHP สามารถช่วยคุณสร้างโปรแกรมอัตโนมัติอย่างเช่น ทดสอบโปรแกรม, การติดตั้งโปรแกรมสำหรับไปใช้งานจริง,
และ โปรแกรมสำหรับควบคุมระบบ

โปรแกรม CLI สำหรับ PHP นั้นมีความสามารถมาก เพราะว่าคุณสามารถที่จะใช้งานได้โดยตรง คุณไม่จำเป็นที่จะต้องมาสร้าง GUI และคอยดูแล
ความปลอดภัยของเว็บ แค่อย่านำ CLI โปรแกรมไปติดตั้งไว้ในเว็บไดเรกทอรีที่สามารถเรียกได้โดยตรงจากเว็บไซต์!

ลองใช้ PHP CLI จาก command line:

{% highlight bash %}
> php -i
{% endhighlight %}

ตัวเลือก `-i` จะทำการแสดงค่าติดตั้งของ PHP เหมือนกับการเรียกใช้ฟังก์ชั่น [`phpinfo`][phpinfo]

ตัวเลือก `-a` จะทำให้ PHP เข้าสู่ interactive shell เหมือนกับ Ruby's IRB หรือ Python's interactive shell ยังมีตัวเลือกอื่นๆอีกมากที่มี
ประโยชน์ [ตัวเลือก command line][cli-options]

เรามาลองเขียน CLI โปรแกรมง่ายๆกันดีกว่าด้วย "Hello, $name" ถ้าจะลองโปรแกรมนี้ สร้างไฟล์ว่า `hello.php` ให้เหมือนกับไฟล์ข้างล่าง

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP ได้มีตัวแปลพิเศษสองตัวแปล ที่จะรับอาร์กิวเมนต์เข้ามาในสคริปต์ [`$argc`][argc] เป็นตัวแปล integer ที่จะบอกจำนวนอาร์กิวเมนต์ที่มี
ในสคริปต์ และ [`$argv`][argv] เป็นตัวแปล array ที่มีค่าของอาร์กิวเมนต์ที่อยู่ในสคริปต์ อาร์กิวเมนต์แรกจะเป็นชื่อของ PHP สคริปต์เสมอ
ในตัวอย่างนี้คือ `hello.php`

เมื่อใช้ `exit()` ร่วมกับจำนวนตัวเลขที่ไม่ใช่ศูนย์ จะเป็นการบอก shell ให้ทราบว่า PHP สคริปต์นี้ล้มเหลว มาตรฐานการใช้ตัวเลขกับ `exit()`
นี้สามารถอ้างอิงได้จาก[ที่นี่][exit-codes]

การเรียกใช้โปรแกรมจาก command line:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [เรียนรู้การเรียกใช้ PHP จาก command line][php-cli]
 * [เรียนรู้การติดตั้ง PHP command line ใน Windows][php-cli-windows]

[phpinfo]: http://php.net/manual/en/function.phpinfo.php
[cli-options]: http://www.php.net/manual/en/features.commandline.options.php
[argc]: http://php.net/manual/en/reserved.variables.argc.php
[argv]: http://php.net/manual/en/reserved.variables.argv.php
[php-cli]: http://php.net/manual/en/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/en/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
