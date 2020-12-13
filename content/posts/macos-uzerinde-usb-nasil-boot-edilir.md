---
title: "macOS Üzerinde Usb Nasıl Boot Edilir"
date: 2017-08-27T01:07:44+03:00
draft: false
---

Birkaç gün önce usb üzerine boot edilmiş windows ve ubuntu kalıplarına ihtiyacım vardı. Windows işletim sistemli bilgisayarım olmadığı için osx üzerinde nasıl yapıldığını araştırdım ve buldum. Mac kullanıcıların işine yarar diye adımları sırasıyla paylaşıyorum.

1. diskutil list
2. distutil unmountDisk /dev/disk2 (Siz hangi diskinizi silecekseniz onu yazın)
3. sudo dd if=”iso kalıbın yolu” bs=1m
4. diskutil eject /dev/disk2

![alt text](/media/macos-uzerinde-usb-nasil-boot-edilir.png "Macos Uzerinde Usb Nasil Boot Edilir")
