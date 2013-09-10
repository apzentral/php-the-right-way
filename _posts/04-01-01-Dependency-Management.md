# Dependency Management {#dependency_management_title}

PHP มี libraries, frameworks, และ components ให้นำมาใช้ได้อย่างมากมาย
โครงการในการเขียนโปรแกรมของคุณสามารถที่จะนำสิ่งเหล่านี้มาใช้ได้ การนำโปรแกรมย่อยต่างๆมาใช้ร่วมกัน
เราเรียกว่า "project dependencies" ก่อนหน้านี้ PHP ไม่ได้มีวิธีการที่จะสามารถจัดการ project dependencies ได้อย่างง่าย
ทำให้คุณจะต้องทำการควบคุม project dependencies ด้วยตัวคุณเอง นอกจากนั้นคุณจะต้องดูแลการนำ project dependencies
มาใช้ในโปรแกรมของคุณ (autoloaders) แต่ในเวลานี้เราได้มีวิธีการควบคุมจัดการ project dependencies ได้

ในขณะนี้เรามีวิธีการจัดการ project dependencies หรือที่เรียกว่า "package management systems"
โดย package management systems ที่ใช้กันในอยู่ขณะนี้มีอยู่สองวิธี คือ "Composer" และ "PEAR" ทั้งสองแบบนี้แตกต่างกันอย่างไร?
เรามาเปรียบเทียบได้ว่า

* ใช้ **Composer** ถ้าคุณใช้ควบคุม dependencies สำหรับโครงการเดียว
* ใช้ **PEAR** ถ้าคุณใช้ควบคุม dependencies สำหรับ PHP ทั้งระบบของคุณ

โดยทั้วไป Composer แพคเกจจะสามารถใช้ได้ในเฉพาะโครงการที่คุณได้กำหนดค่าเอาไว้เท่านั้น
แต่ PEAR แพคเกจจะสามารถใช้ได้ในทุก PHP โครงการที่อยู่บนระบบเดียวกัน
คุณคงคิดว่าการใช้ PEAR น่าจะดีกว่า เพราะว่าคุณไม่ต้องมาคอยกำหนดค่า dependencies ทุกๆโครงการ
แต่แท้จริงแล้ว การใช้ Composer หรือ กำหนดค่า dependencies ที่ละโครงการจะมีข้อได้เปรียบมากกว่า
