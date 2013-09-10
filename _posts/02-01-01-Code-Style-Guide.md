---
title: สไตล์ในการเขียนโปรแกรม
---

# สไตล์ในการเขียนโปรแกรม  {#code_style_guide_title}

ชุมชนของผู้เขียนโปรแกรม PHP นั้นมีอยู่กว้างขวางและมีความหลากหลาย ประกอบไปด้วย libraries, framework และ components
มันเป็นเรื่องปรกติที่ผู้พัฒนาโปรแกรม PHP จะนำเอาสิ่งต่างๆเหล่านี้มารวมกันใช้ในการพัฒนาโปรแกรมนั้นๆ มันเป็นสิ่งที่สำคัญหรือมาตรฐาน
ในการพัฒนาสไตล์เพื่อใช้ในการสร้างหรือรวบรวมโปรแกรมต่างๆเข้ามาใช้รวมกันได้อย่างง่ายดายและไม่มีปัญหา

[Framework Interop Group][fig] ได้เสนอและได้รับการอนุมัติสไตล์ต่างๆที่ได้รับการยอมรับอย่างกว้างขวาง อย่างเช่น [PSR-0][psr0],
[PSR-1][psr1] และ [PSR-2][psr2] อย่าได้สับสนในชื่อที่แปลกเหล่านี้ ชื่อสไตล์เหล่านี้เป็นที่ยอมรับและแนะนำที่ใช้กันอย่างกว้างขวาง
ในโครงการใหญ่ๆอย่างเช่น Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium, และอื่นๆอีกมากมาย
คุณสามารถนำสไตล์เหล่านี้มาใช้ในโครงการของคุณได้ หรือคุณอยากที่จะใช้สไตล์ของคุณเองก็ย่อมได้

แต่จะเป็นสิ่งที่ดีกว่าถ้าคุณเขียนโปรแกรม PHP ในสไตล์ที่ได้รับการยอมรับว่าเป็นมาตรฐานของ PHP ซึ้งสไตล์เหล่านี้สามารถที่จะเกิดจากการ
นำ PSR เหล่านี้มารวมกัน หรือสไตล์ที่ PEAR และ Zend ได้ใช้อยู่ ถ้าคุณใช้สไตล์มาตรฐานในการเขียน PHP นั้นจะทำให้นักพัฒนาโปรแกรมสามารถ
ที่จะอ่านและเข้าใจโปรแกรมของคุณได้อย่างง่ายดาย โปรแกรมที่ใช้สไตล์มาตรฐานนั้นจะสามารถนำมาใช้ร่วมกับโปรแกรมอื่นได้อย่างไม่มีปัญหา

* [ข้อมูลเพิ่มเติมของ PSR-0][psr0]
* [ข้อมูลเพิ่มเติมของ PSR-1][psr1]
* [ข้อมูลเพิ่มเติมของ PSR-2][psr2]
* [ข้อมูลเพิ่มเติมของ PEAR Coding Standards][pear-cs]
* [ข้อมูลเพิ่มเติมของ Zend Coding Standards][zend-cs]

คุณสามารถที่จะใช้ [PHP_CodeSniffer][phpcs] เพื่อที่จะใช้ในการตรวจสอบโปรแกรมของคุณกับสไตล์มาตรฐานเหล่านี้ นอกจากนี้ยังมีปลั๊กอินสำหรับ
text editors อย่างเช่น [Sublime Text 2][st-cs] ที่สามารถที่จะตรวจสอบได้ในขณะที่คุณกำลังพิมพ์ PHP ได้อย่างทันที

ถ้าใช้ Fabien Potencier's [PHP Coding Standards Fixer][phpcsfixer] เพื่อที่จะตรวจสอบไวยากรณ์ของโปรแกรมของคุณให้สอดคล้องกับ
มาตรฐานเหล่านี้ เพื่อที่จะทำให้การทำงานของคุณง่ายดายขี้น

ภาษาอังกฤษเป็นภาษาหลักสำหรับตัวแปลต่างๆและโครงสร้างของโปรแกรม ข้อคิดเห็นนั้นสามารถที่จะเขียนในภาษาใดๆก็ได้ที่ทำให้ทางทีมงาน
ของคุณและผู้ร่วมพัฒนาในอนาคต ที่จะสามารถเข้าใจโปรแกรมของคุณได้อย่างง่ายดาย

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr3]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logger-interface.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
