---
title: "Brew Unable to determine linked PHP Hatası"
date: 2018-06-02T02:56:10+03:00
draft: false
---
Bilgisayarınızda Valet kullanıyor ve yukarıdaki hatayı alıyorsanız aşağıdaki komutları çalıştırarak sorundan kurtulabilirsiniz.

```
brew unlink php && brew link php
brew services restart --all
composer global update
```