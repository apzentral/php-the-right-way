---
isChild: true
---

## Behavior Driven Development {#behavior_driven_development_title}

ในการพัฒนาโปรแกรมแบบ Behavior-Driven Development (BDD) จะมีอยู่สองวิธีนั่นก็คือ SpecBDD และ StoryBDD
SpecBDD นั่นจะเน้นในเรื่องของพฤติกรรมทางเทคนิคหรือโปรแกรม โดย StoryBDD นั่นจะเน้นเรื่องของพฤติกรรมที่เกี่ยวข้องกับธุรกิจหรือพฤติกรรมที่สำคัญ
PHP ได้มี frameworks มากมายที่รองรับ BDD ทั้งสองแบบนี้

สำหรับ StoryBDD นั้น คุณสามารถที่จะเขียนเรื่องราวที่บุคคลทั่วไปอ่านได้ง่าย โดยเนื้อเรื่องนั้นจะอธิบายพฤติกรรมต่างๆของโปรแกรมของคุณ เรื่องที่คุณได้
เขียนขึ้นนั้นคุณสามารถที่จะนำมาใช้ในการทดสอบโปรแกรมของคุณได้อีกด้วย framework ที่ใช้ทดสอบโปรแกรมแบบ StoryBDD ใน PHP นั้น ก็คือ Behat โดย
ได้รับแนวคิดมาจากโครงการ [Cucumber](http://cukes.info/) จาก Ruby และได้ใช้ Gherkin DSL สำหรับการบรรยายพฤติกรรมที่สำคัญต่างๆ

สำหรับ SpecBDD นั้น คุณจะเขียนข้อกำหนดต่างๆของโปรแกรมว่าสมควรที่จะทำงานอย่างไร แทนที่จะทดสอบฟังก์ชั่นหรือ method คุณนั้นจะเขียนข้อกำหนดว่า
ฟังก์ชั่นหรือ method นั้นสมควรที่จะประพฤติอย่างไร PHP ได้มี PHPSpec framework สำหรับการทดสอบแบบนี้ framework นี้ได้รับแนวคิดมาจาก
[RSpec project](http://rspec.info/) สำหรับ Ruby

### BDD Links

* [Behat](http://behat.org/), StoryBDD framework สำหรับ PHP, ได้รับแนวคิดมาจากโครงการ [Cucumber](http://cukes.info/) ใน Ruby;
* [PHPSpec](http://www.phpspec.net/), SpecBDD framework สำหรับ PHP, ได้รับแนวคิดมาจากโครงการ [RSpec](http://rspec.info/) ใน Ruby;
* [Codeception](http://www.codeception.com) คือ full-stack testing framework ที่ใช้แนวคิดมาจาก BDD.
