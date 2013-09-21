---
isChild: true
---

## Building และ Deploying โปรแกรมของคุณ {#build_title}

ถ้าคุณได้ค้นพบว่า คุณได้ทำการเปลี่ยนโครงสร้างของฐานข้อมูลหรือทำการทดสอบโปรแกรมด้วยตัวของคุณเอง ลองคิดดูให้ดีว่าการที่คุณต้องทำกระบวนการเหล่านี้
ด้วยตัวเองนั้น ยิ่งมีกระบวนการที่มากเท่าไหร่ ก็ยิ่งมีโอกาศเสี่ยงต่อข้อผิดพลาดได้มากขึ้นเท่านั้น ไม่ว่าคุณจะต้องการที่จะอัพเดตไ​​ฟล์ง่ายๆเพียงนั้น คุณสมควรที่จะ
ใช้กระบวนการ build หรือ continuous integration strategy ดังนั้น [build automation](http://en.wikipedia.org/wiki/Build_automation)
คือสิ่งที่คุณสมควรใช้

นอกเหนือจากที่ได้กล่าวมาข้างต้นแล้ว หัวข้อเหล่านี้ก็สมควรที่จะเรียกใช้อัตโนมัติเช่นกัน

* การควบคุม dependency
* Compilation, minification สำหรับ assets ต่างๆ
* เรียกใช้โปรแกรม tests
* การสร้างคู่มือต่างๆ
* Packaging
* Deployment

### Build Automation Tools

Build tools สามารถเรียกได้ว่าเป็นศูนย์รวมสคริปต์ต่างๆที่สามารถที่จะรองรับงานทั่วไปในการพัฒนาโปรแกรม build tool นั้นไม่ได้เป็นส่วนหนึ่งของโปรแกรม
แต่เป็นเครื่องมือที่จะช่วยในการทำงานต่างๆในโปรแกรมของคุณแทนที่คุณ

สำหรับเครื่องมือในการ build automation นั้นได้มีโครงการ open source อยู่มากมาย มีบางโครงการได้เขียนโดยใช้ PHP และบางโครงการก็ใช้ภาษาอื่นแทน
แต่ถ้าการที่ build tools ที่ไม่ได้เขียนในภาษา PHP นั้นได้มีความสามารถที่ดีกว่า คุณก็อย่านำจุดนั้นมาเป็นข้ออ้างที่จะไม่ใช้เครื่องมือนั้นในโปรแกรมของคุณ
นี้คือตัวอย่างเครื่องมือเหล่านั้น:

[Phing](http://www.phing.info/) เป็นวิธีที่ง่ายที่สุดที่จะเริ่มต้นการใช้ automated deployment ในโลกของ PHP โดยการใช้ Phing นั้น คุณสามารถควบคุม
กระบวนการเหล่านี้ packaging, deployment และ testing จาก build XML ไฟล์ได้อย่างง่าย Phing (ได้แนวคิดมาจาก [Apache Ant](http://ant.apache.org/))
นั้นได้มีคำสั่งมากมายที่เราสามารถนำมาใช้ในการติดตั้งหรือเพิ่มเติมโปรแกรมของคุณและสามารถที่จะเพิ่มเติมคำสั่งต่างๆที่คุณต้องการได้อีกด้วย เขียนด้วยภาษา PHP

[Capistrano](https://github.com/capistrano/capistrano/wiki) เป็นระบบสำหรับ *intermediate-to-advanced programmers* เพื่อที่จะเรียกใช้
คำสั่งที่เป็นโครงสร้าง, เหมือนๆกันในหนึ่งหรือหลายๆเครื่อง เครื่องมือนี้ได้ตั้งค่ามาเพื่อสำหรับการติดตั้งโปรแกรม Ruby on Rails, แต่อย่างไรก็ตาม ผู้ใช้เครื่องมือนี้
ก็สามารถที่จะ **ติดตั้งระบบ PHP ได้สำเร็จ** การที่จะใช้เครื่องมือนี้ได้อย่างดีนั้น คุณจะต้องมีพื้นฐานของ Ruby และ Rake

Dave Gardner's blog post [PHP Deployment with Capistrano](http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/)
เป็นจุดเริ่มต้นการศึกษาที่ดีสำหรับผู้พัฒนาภาษา PHP ที่ต้องการที่จะใช้ Capistrano

[Chef](http://www.opscode.com/chef/) เป็นมากกว่าเครื่องมือในการติดตั้ง ยังเป็นเครื่องมือของระบบ Ruby ที่นอกจากทำการติดตั้งโปรแกรมของคุณแล้วยังช่วยในการ
ติดตั้งสภาพแวดล้อมของ server ของคุณและยังสามารถติดตั้งระบบ virtual ได้อีกด้วย

ข้อมูลสำหรับ Chef เพื่อนักพัฒนาภาษา PHP:

* [blog series สามตอนที่จะสอนการติดตั้งโปรแกรมใน LAMP ด้วย Chef, Vagrant, และ EC2](http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/)
* [Chef Cookbook ที่จะสอนการติดตั้งและตั้งค่า PHP 5.3 และ PEAR ระบบ package management](https://github.com/opscode-cookbooks/php)

อ่านเพิ่มเติม:

* [การใช้ Apache Ant ในการจัดการโครงการอัตโนมัติ](http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/)
* [Maven](http://maven.apache.org/), build framework ที่ใช้แนวคิดจาก Ant และ [การนำมาใช้ใน PHP](http://www.php-maven.org/)

### Continuous Integration

> Continuous Integration นั้นคือรูปแบบของการพัฒนาโปรแกรมที่สมาชิกของทีมจะต้องของนำงานที่เขาได้ทำมารวมกันในโครงการอยู่บ่อยๆ อย่างน้อยคุณจะต้องนำงาน
> ที่คุณทำอยู่นั้นมารวมในโครงการวันละครั้ง ในทึ่สุดก็ในผู้ร่วมทำงานของคุณก็จะนำงานเข้ามาในโครงการบ่อยมากขึ้น สาเหตุที่ต้องนำงานที่คุณทำเข้ามารวมในโครงการบ่อยๆ
> นั้น ก็เพราะว่าจะช่วยลดปัญหาการที่โปรแกรมเหล่านั้นมาทำงานร่วมกัน และยังทำให้ผู้ร่วมงานของคุณได้ร่วมพัฒนาโปรแกรมที่ทำงานร่วมกันได้อย่างดีมาก

*-- Martin Fowler*

สำหรับ PHP แล้วนั้นได้มีวิธีมากมายในการใช้หลักการ continuous integration เมื่อไม่นานมานี้ [Travis CI](https://travis-ci.org/) ได้ช่วยให้การ
ใช้ continuous integration นั้นใช้งานได้จริงแม้ว่าจะเป็นโครงการเล็กๆก็ตาม Travis CI เป็น host สำหรับ open source project ที่ใช้
continuous integration และยังได้ทำงานร่วมกับ GitHub และได้มีการสนับสนุนให้ความช่วยเหลือสำหรับภาษาต่างๆ รวมถึง PHP อีกด้วย

อ่านเพิ่มเติม:

* [Continuous Integration ด้วย Jenkins](http://jenkins-ci.org/)
* [Continuous Integration ด้วย PHPCI](http://www.phptesting.org/)
* [Continuous Integration ด้วย Teamcity](http://www.jetbrains.com/teamcity/)
