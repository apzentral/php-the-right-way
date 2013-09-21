---
isChild: true
---

## Object Caching {#object_caching_title}

ในบางครั้งการที่เราสามารถที่ cache objects ในโปรแกรมของเรานั้นก็จะมีประโยชน์กับโปรแกรมของเราได้ อย่างเช่นการที่เราต้องการเรียกใช้ข้อมูล
ที่จะต้องใช้เวลานานในการติดต่ออย่างเช่น การติดต่อกับฐานข้อมูล ซึ่งข้อมูลที่เราได้รับมานั้นจะมีโอกาศที่จะเปลี่ยนได้น้อยมาก คุณจึงสามารถที่จะใช้โปรแกมในการ
object caching ได้ในหน่วยความจำที่รวดเร็วที่เราสามารถนำมาใช้ได้ต่อไป ถ้าคุณได้ทำการเก็บข้อมูลใน cache หลังจากที่คุณได้รับมาจากฐานข้อมูลแล้ว
ก็จะสามารถเพิ่มความเร็วได้อย่างมากในการเรียกใช้ครั้งต่อๆไป และยังลดการเรียกใช้ติดต่อกับฐานข้อมูลอีกด้วย

นอกจากนี้ bytecode caching ต่างๆที่เป็นที่นิยมนั้น ยังสามารถที่จะช่วยคุณ cache ข้อมูลได้อีกด้วย นั้นก็หมายความว่าเราสามารถนำมาใช้ได้เลย
APCu, XCache, และ WinCache ต่างก็ได้มี APIs ที่ใช้ในการเก็บข้อมูลจากโปรแกรม PHP ของคุณเข้าไปใช้ใน cache ของหน่วยความจำอีกด้วย

APCu และ memcached ได้เป็นที่นิยมมากที่สุด APCu นั้นได้เหมาะสมอย่างมากในการใช้ object caching, ได้มี API ที่ใช้งานได้ง่ายในการเพิ่มข้อมูลของ
คุณเข้าไปในหน่วยความจำ และยังมีการติดตั้งที่ง่ายและใช้งานได้ง่ายอีกด้วย แต่ APCu นั้นได้มีข้อจำกัดอยู่ที่เซิร์ฟเวอร์ที่ได้ติดตั้งเท่านั้น ส่วน Memcached นั้นจะติดตั้ง
เป็น service และสามารถที่จะนำมาเรียกใช้ได้ในเครือข่ายของคุณ นั้นก็หมายความว่า คุณสามารถที่จะเก็บข้อมูลได้ในหน่วยความจำที่ไวมากที่สุดและก็ให้ระบบต่างๆ
นั้นเรียกใช้ข้อมูลได้ทันที

แต่ถ้าคุณได้ใช้ PHP ในการทำงานแบบ (Fast-)CGI ในเว็บเซิร์ฟเวอร์ของคุณแล้วละก็ PHP process จะมี cache ในตัวของ PHP process เอง นั้นก็หมายความว่า
ข้อมูลจาก APCu นั้นจะไม่สามารถนำมาใช้ระหว่าง processes ต่างๆได้ ในกรณีนี้นั้น คุณจะต้องพิจารณาใช้ memcached แทน เพราะว่า memcached จะไม่เกี่ยวข้องกับ
PHP processes

ในการใช้ในเครือข่ายนั้น APCu จะมีความรวดเร็วในการเข้าถึงข้อมูลกว่า memcached แต่ memcached นั้นสามารถที่จะ scale ได้มากและรวดเร็วกว่า ถ้าคุณไม่ได้ใช้
เว็บเซิร์ฟเวอร์หลายๆอันในการใช้โปรแกรมของคุณแล้วละก็ APCu น่าจะเป็นตัวเลือกที่ดีกว่า สำหรับ object caching

ตัวอย่างโปรแกรมในการเรียกใช้ APCu:

{% highlight php %}
<?php
// check if there is data saved as 'expensive_data' in cache
$data = apc_fetch('expensive_data');
if ($data === false) {
    // data is not in cache; save result of expensive call for later use
    apc_add('expensive_data', $data = get_expensive_data());
}

print_r($data);
{% endhighlight %}

โปรดทราบว่าใน PHP รุ่นก่อน 5.5 นั้น, APC ได้มีระบบ object cache และ bytecode cache แต่โครงการ APCu นั้นได้สร้่างขึ้นเพื่อนำมาใช้ในรุ่น 5.5 เป็นต้นไป
เพราะว่า PHP ได้มี bytecode cache ติดตั้งอยู่แล้วในตัวเอง (OPcache)

เรียนรู้เกี่ยวกับระบบการ object caching ที่เป็นที่นิยม:

* [APCu](https://github.com/krakjoe/apcu)
* [APC Functions](http://php.net/manual/en/ref.apc.php)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache APIs](http://xcache.lighttpd.net/wiki/XcacheApi)
* [WinCache Functions](http://www.php.net/manual/en/ref.wincache.php)
