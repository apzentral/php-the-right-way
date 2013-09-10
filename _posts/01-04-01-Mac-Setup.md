---
title: การติดตั้งใน Mac
isChild: true
---

## การติดตั้งใน Mac {#mac_setup_title}

OSX ได้ติดตั้ง PHP มาเรียบร้อยแล้ว แต่จะไม่ได้เป็นรุ่นปัจจุบัน อาจจะเป็นรุ่นที่ล้าหลังนิดหน่อย อย่างเช่น Lion นั้นได้ติดตั้ง PHP รุ่น 5.3.6 และ Mountain Lion
นั้นมากับ PHP รุ่น 5.3.10

วิธีการ update PHP ใน OSX นั้นสามารถที่ทำได้โดยการติดตั้งผ่าน [package managers][mac-package-managers] ของ Mac ด้วย
[php-osx by Liip][php-osx-downloads] เป็นวิธีที่แนะนำ

อีกทางเลือกหนึ่งคือการ [compile PHP ด้วยตัวคุณเอง][mac-compile] โดยวิธีนี้คุณจะต้องมี Xcode หรือ ["Command Line Tools for Xcode"][apple-developer]
ที่จะสามารถนำมาใช่้แทน Xcode ได้ โปรแกรมเหล่านี้สามารถ download ได้จาก Apple's Mac Developer Center

ถ้่าคุณต้องการวิธีที่ง่ายที่สุด คือ "all-in-one" แพคเกจที่รวบรวม PHP, Apache web server และ MySQL database และยังมี GUI ที่สามารถควบคุมแพคเกจ
ได้อย่างง่ายดาย คุณสามารถ download ได้จาก [MAMP][mamp-downloads]

[mac-package-managers]: http://www.php.net/manual/en/install.macosx.packages.php
[mac-compile]: http://www.php.net/manual/en/install.macosx.compile.php
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
[apple-developer]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/index.html
[php-osx-downloads]: http://php-osx.liip.ch/
