---
title: "Laravel Homestead ile Birden Fazla Projeyle Çalışmak"
date: 2017-01-02T03:55:05+03:00
draft: false
ShowReadingTime: true
---

Homestead üzerinde laravel ile bir proje geliştiriyorsunuz fakat ikinci bir projeyi kurduğunuzda ve 192.168.10.10 üzerinden eriştiğinizde oluşturduğumuz proje gelmeyecektir. (Burada Homestead.yaml dosyasındaki ayarları yaptığınızı varsayıyorum)

Sanal sunucunuzun bulunduğu klasörde kaç tane laravel projesi oluşturursanız oluşturun hep ilk oluşturduğunuz proje ekrana gelecektir. Bunun sebebi Homestead projelerinizi otomatik olarak birbirinden ayrıştırmıyor olması. **Aşağıdaki adımları yapmadan önce homestead.yaml dosyasında projenin yolunu göstermeniz gerekmektedir.**

Sorunun çözümü için terminal’imizi açıyoruz ve sanal sunucu klasörünün içerisine girerek `vagrant up` komutu ile vagrantımızı çalıştırıyoruz. Eğer sizde açıksa tekrar yazmanıza gerek yok.

Daha sonra terminalde `vagrant global-status` komutunu yazıyoruz ve açık olan sunucuları görüyoruz. Benim homestead dosyamda laravel2 olarak sunucu adı tanımlı. Tanımlı olan sunucu id’sini kopyalıyoruz ve terminal ekranımıza `vagrant provision sunucuId` yazarak çalıştırıyoruz. Homestead burda kendini tekrar optimize edicek ve çalıştıracak sayfayı yenilediğinizde artık projeler birbirinden bağımsız olacaktır.

![alt text](/media/laravelbirdenfazlaprojeilecalismak.jpg "Laravel Homestead ile Birden Fazla Projeyle Çalışmak")
