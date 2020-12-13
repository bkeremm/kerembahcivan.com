---
title: "Ionic Androidmanifest Xml Duplicate Hatası"
date: 2018-03-25T02:55:13+03:00
draft: false
---

Bir önceki yazım ionic üzerineydi ve bu yazımda da yine ionic üzerinden yazmaya devam ediyorum. **AndroidManifest.xml Duplicate** hatası çok sık olmasada build alırken karşımıza çıkabilecek hatalardan biri olabilmektedir.

**Hatanın Oluşma Nedeni**
Uygulamanıza eklediğiniz eklentiler AndroidManifest.xml dosyasına iki kere yazıldığında bu hata meydana gelir veya daha önce bir eklenti kurdunuz bu eklentiyi tam olarak kaldıramadan tekrar kurmaya kalktığınızda xml dosyasına yine iki kere yazabilmektedir.
Örn: Eğer plugin-barcodescanner eklentisini kullanıyorsanız bu hata ile karşılaşma olasılığınız yüksektir.

**Hatanın Çözümü**
Bu hatadan temiz bir şekilde sıyrılmanın en iyi yolu uygulamadaki platform, node_modules, plugins klasörlerini silip tekrar kurmamız gerekiyor.
```
ionic cordova platform rm android
ionic cordova platform rm ios
``` 
Eğer hatanız bir eklenti kaynaklı ise onuda kaldırmanız gerekiyor. Ben yukarıda verdiğim örnekteki gibi barcodescanner'ı kaldırıyorum.
```
ionic cordova plugin rm phonegap-plugin-barcodescanner
rm -r plugins
rm -r node_modules
rm package-lock.json
```

İşlemleri tamamladıktan sonra tekrar kurulumlarımızı yapıyoruz.
```
npm install
ionic cordova platform add android
ionic cordova platform add ios
```
Varsa eklentimizide en son kuruyoruz.
```
ionic cordova plugin add phonegap-plugin-barcodescanner

ionic cordova build android
```

Son olarak dikkat edilmesi gereken bir nokta var. Bu hatayı özel olarak tetikleyen bir eklentiniz varsa eklentiyi silme ve yükleme işlemlerine dahil ediyorsunuz. Uygulamanızdaki bütün eklentileri tek tek kaldırıp silmiyorsunuz.

İyi Kodlamalar 🙂