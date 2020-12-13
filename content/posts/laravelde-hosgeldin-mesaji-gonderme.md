---
title: "Laravelde Hoşgeldin Mesajı Gönderme"
date: 2017-09-06T02:34:35+03:00
draft: false
---

Merhaba arkadaşlar, bu yazımda Laravel üzerinde giriş yapan kullanıcılara hoşgeldin mesajını nasıl göstereceğimizi anlatacağım. Yöntem basit ama nasıl kullandığımızı bilmekte fayda var.

**Kullandığımız Fonksiyon Hakkında:**

“redirectPath() fonksiyonu RedirectsUsers trait’ini referans almaktadır. Aynı zamanda RedirectsUsers, LoginController’da bulunan AuthenticatesUsers sınıfında kullanılmaktadır.“

Laravel‘in kendi oturum açma denetleyicisinde, ileti metnini gösterebilmek için,  trait’in yapısını bozmadan use içine bu class’a ait geçici bir metod oluşturuyoruz.Daha sonra aşağıda hazırladığım redirectPath() fonksiyonunu sınıf içerisine eklemeniz yeterli olacaktır. Son adım olarak mesajın çıkmasını istediğiniz yerede flash mesaj kodunu ekleyebilirsiniz.

**LoginController.php**
```php
use AuthenticatesUsers {
    redirectPath as customRedirectTo;
}
 
public function redirectPath()
{
    session()->flash('welcome_message', auth()->user()->name);
    return $this->customRedirectTo();
}
```

**Flash Mesaj:**
```php
@if (session()->has('welcome_message'))
        <div class="alert alert-success" id="welcome_message">
            Tekrar Hoşgeldin, <strong>{!! session('welcome_message') !!}</strong>
        </div>
@endif
```