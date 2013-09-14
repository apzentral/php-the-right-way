---
title: วันและเวลา
isChild: true
---

## วันและเวลา {#date_and_time_title}

PHP ได้มี class ที่ชื่อว่า DateTime เพื่อที่จะช่วยคุณในการอ่าน, เขียน, เทียบและคำนวนค่าต่างๆที่เกี่ยวกับวันและเวลา PHP ยังมี functions อื่นๆอีกมากมาย
ที่เกี่ยวกับวันและเวลานอกจาก class DateTime แต่ class DateTime จะมี interface ที่สามารถนำมาใช้ได้ในการแก้ปัญหาต่างๆทั่วไป ยังสามารถที่จะนำมาแก้
เวลาใน zones ต่างๆทั่วโลก แต่เราจะไม่นำมาอธิบายในบทความนี้

การเริ่มต้นใช้ DateTime นั้น เราจะต้องแปลงค่าวันและเวลาจาก string ไปเป็น object ด้วย `createFromFormat()` factory method หรือใช้ `new \DateTime`
สำหรับการตั้งค่าเวลาในปัจจุบัน และใช้ `format()` method ในการเปลี่ยนค่าจาก object ไปเป็น string สำหรับการแสดงค่า output

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('m/d/Y') . "\n";
{% endhighlight %}

การคำนวนค่าของ DateTime นั้นสามารถทำได้โดยใช้ DateInterval class DateTime จะมี methods อย่างเช่น `add()` และ `sub()` แต่จะใช้ DateInterval
เป็น argument อย่าเขียนโปรแกรมที่คำนวนเวลาโดยใช้วินาทีในการคำนวนทุกๆวัน เพราะว่า daylight saving และ timezone จะทำให้การคำนวนนี้ผิดพลาดได้
คุณสมควรที่จะใช้ date intervals แทน การคำนวนวันเวลาที่แตกต่างกันนั้น ใช้`diff()` method จะคืนค่า new DateInterval และสามารถที่จะนำมาแสดงได้อย่างง่ายดาย

{% highlight php %}
<?php
// create a copy of $start and add one month and 6 days
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Difference: 1 month, 6 days (total: 37 days)
{% endhighlight %}

ใน DateTime objects นั้นคุณสามารถใช้การเปรียบเทียบพื้นฐานได้:

{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}

ตัวอย่างสุดท้ายนี้จะแสดงการใช้ DatePeriod class ซี้งจะนำมาใช้ในการหาค่าเหตุการณ์ที่เหมือนกัน class นี้จะรับค่า DateTime objects สองค่า
(ค่าเริ่มต้นและค่าสุดท้าย) และระยะเวลาที่เราต้องการให้ class นี้คืนค่าเหตุการณ์ในระหว่างนั้น

{% highlight php %}
<?php
// output all thursdays between $start and $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('m/d/Y') . ' ';
}
{% endhighlight %}

* [อ่านเพิ่มเติมเกี่ยวกับ DateTime][datetime]
* [อ่านเพิ่มเติมเกี่ยวกับการแสดงค่าจาก DateTime][dateformat] (รับค่าตัวเลือก date format string)

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
