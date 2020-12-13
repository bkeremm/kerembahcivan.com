---
title: "Jigsaw Nedir ve Nasıl Kullanılır"
date: 2017-08-12T01:07:22+03:00
draft: false
---

Jigsaw, web uygulamalarınıza güç veren aynı modern araçlarla statik siteleri hızla oluşturmak için Laravel geliştiricileri tarafından kullanıma sunulan bir çerçevedir. PHP’nin nasıl frameworkleri var ise statik sayfalarınızında artık bir frameworku var!

Basit html siteler hazırlayacaksınız veya müşterinize bir demo hazırlayacaksınız. Normalde statik sitelerde her sayfa için header’ı kopyala, footer’ı kopyala gibi zahmetli işlere kalkışıyorduk yada bir php dosyası oluşturup header ve footer’ı başka bir yerden çağırıp dosyalama sistemi yapıyorduk. Jigsaw ile artık böyle uğraşlara son veriyoruz.

### Peki Jigsaw bize neler sunuyor?

* Laravel kullananlar bilir içerisinde varsayılan olarak blade template engine ile birlikte geliyor. Burdada istediğiniz sayfaları kolayca extends edebiliyorsunuz.
* “Local” ve “Production” olarak build etmemize olanak sağlıyor. Bu özelliği seveceksiniz
* config.php‘de site içerisinde kullanabileceğimiz değişkenler tanımlayabiliyoruz. Örneğin; site adı, site url, mail adresi, sosyal medya linkleri vs.
* Helper metodları bulunmaktadır. Örneğin hangi sayfadaysanız o menü başlığının aktif olması için sürekli if/else yazmanıza gerek kalmıyor.
* Page Metadata diye adlandırdıkları yine bizim işlerimizi kolaylaştıracak araçlar bulunuyor. Yukarıda bahsettiğim gibi siz tutup sayfanın linkini almakla veya dosya yolunuzu göstermekle uğraşmıyorsunuz.
Örneğin: `$page->getPath()` , `$page->getFilename()` gibi fonksiyonları bulunmaktadır. 
* İçerisinde 3 farklı Template Engine sunuyor.
    * Blade
    * Markdown
    * Blade & Markdown (Hibrit)
* Collections ile statik sayfalarınıza yeni özellikler kazandırabiliyorsunuz. Örneğin config.php’de yapacağınız ayarlama ile sayfalarınıza otomatik url kazandırabiliyorsunuz. Eskiden statik sitenize 3 tane elle blog yazısı yazıcaksınız diyelim. Burda her sayfanız için sonraki yazı, önceki yazı, yazı başlığı, yazı linki derken elle tek tek uğraşmanıza son veriyor.
* Dosyalarımız php üzerinden düzenliyor olsakda Jigsaw production’a build ederken tüm dosyaları .html çevirmektedir.

### Jigsaw Kurulumu
Terminal’de bir klasör açıp içerisinde aşağıdaki komutu yazarak dosyalarımızı indiriyoruz.

```
composer require tightenco/jigsaw
```
Geçerli klasörümüz içerisinde aşağıdaki komutu çalıştırarak yeni projemizi oluşturuyoruz ve resimdeki gibi bir klasör yapımız olmuş oluyor.
```
./vendor/bin/jigsaw init
```
![alt text](/media/jigsaw-nedir-ve-nasil-kullanilir-1.png "Jigsaw Nedir ve Nasıl Kullanılır")
Css, Javascript ve Resim dosyalarınızı **source** klasörü içerisine atıyorsunuz. Proje içerisinde değişiklikleri yaptıktan sonra hemen önizleyemiyorsunuz. Jigsaw’ın değişikliklerinizi işleyebilmesi için terminal üzerinden aşağıdaki kodu her seferinde çalıştırmanız gerekmektedir.
```
./vendor/bin/jigsaw build
```

Bu yazıda da Jigsaw’ın ne olduğunu nerelerde kullanıldığını ve basitçe proje oluşturmayı öğrenmiş olduk. Yakın zamanda youtube üzerine  “Jigsaw ile Site Yapımı” dersini ekleyerek daha fazla ayrıntıya yer vereceğim.