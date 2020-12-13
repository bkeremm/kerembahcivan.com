---
title: "Ionic Could Not Find Intellij Core Jar Hatası"
date: 2018-10-25
draft: false
---
Uzun bir aradan sonra yine bir hata-çözüm yazısıyla karşınızdayım. 
Ionic ile yeni bir projeye başlarken baktım Ionic CLI sürümü eski görünüyordu bende güncellemeye karar verdim. (Keşke güncellemeseydim :) )

Not: Ionic 3 sürümünü kullanmaktayım.

CLI’ı normal bir şekilde güncelledikten sonra uygulamayı geliştirip ilk build almaya başladığım anda daha önce karşıma çıkmayan bir hatayla karşılaştım. 

**Hatanın tam adı:**
```print
Error:Could not find intellij-core.jar (com.android.tools.external.com-intellij:intellij-core:26.0.1).
```

**Bu hatanın tam sebebiyet verdiği olayı açıklamak gerekirse;**
Bildiğiniz gibi android üzerinde build alırken eklentiler dahil olmak üzere dışarıdan çok sayıda açık kaynak paketlerini kullanmaktadır. Bu paketlerin listelendiği siteye göz atmak isterseniz https://maven.google.com  adresinden bakabilirsiniz. **Gradle** ise bu paketleri alıp geliştirme aşamalarını tamamlayan bir build sistemidir. Ionic üzerinde build alırken gradle kullanılmaktadır. Bunu anlatıyorum çünkü hatada gradle’dan da bahsediyor ama bizim asıl odaklanmamız gereken nokta paketlerin yüklenememesi.


### Peki nasıl çözeriz?
Projeye android platformunu ekledikten sonra platforms/android/CordovaLib içerisindeki build.gradle dosyasını açıyoruz.

![alt text](/media/ionic-could-not-find-intellij-core-jar-hatasi-1.png "Ionic Could Not Find Intellij Core Jar Hatası")

Dosya içerisindeki repositories alanında gördüğünüz gibi jcenter() maven’in üstünde yer alıyor. Biz bunu aşağıdaki gibi değiştiriyoruz ve kaydediyoruz.

![alt text](/media/ionic-could-not-find-intellij-core-jar-hatasi-2.png "Ionic Could Not Find Intellij Core Jar Hatası")

#### Peki neden böyle birşey yaptık?
Hatanın temel sebebi paketleri çekemeden yüklemeye çalışmasıdır. Uzun uzun anlatıyorum çünkü; hatanın çözümünü direkt yazmaktan çok işleyişin nasıl olduğunu ve hatanın neyden kaynaklandığını anlatmaktı.
Sonrasında “ionic cordova build android” diyerek build alabilirsiniz.

Bir sonraki yazıda görüşmek üzere 🙂