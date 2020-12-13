---
title: "Ionic Error Cannot Find Module Build Alma Sorunu"
date: 2018-02-24T02:54:47+03:00
draft: false
---

Selam arkadaşlar, hali hazırda cross platform araçları arasından Ionic ile mobil uygulamalar geliştirmekteyim. Dün başladığım bir uygulamada build almaya çalışırken sürekli aşağıdaki hatayı almaktaydım.

`	
Error: Cannot find module '../cordova/platform_metadata'
`

Biraz araştırma ve sürüm incelemesi sonrasında sorunun Cordova CLI sürümünden kaynaklandığını tespit ettim. Yaklaşık 1 hafta önce uzun zamandır yaptığım npm güncellemesini yapmıştım ve Cordova CLI sürümü 8.0’a yükselmiş. Build esnasında eğer sizde yukarıdaki hatayı alıyorsanız sürüm düşürme yaparak sorunu giderebilirsiniz. Bunun için sırası ile aşağıdaki komutları uygulamanız yeterli olacaktır.


Öncelikle Cordova'yı kaldırıyoruz.
```
npm uninstall -g cordova
```
Cordova CLI 7 sürümünü tekrar kuruyoruz.
```
npm install -g cordova@7.1.0
``` 
Platformlarımızı silip tekrar ekliyoruz.Yapmazsanız yine hata alıcaksınız muhtemelen.
```
cordova platform remove ios
cordova platform remove android
cordova platform add ios
cordova platform add android
```

Bu işlemlerden sonra yazılımsal bir sorununuz yoksa artık build alabileceksiniz.
Not: OSX ve Linux kullananlar için terminal’de npm komutlarını çalıştırırken ERROR verirse komutların başına **sudo** ekleyerek yönetici yetkisi veriniz.