---
title: "Laravel Seo Uyumlu Link Hazırlama (Elequent Sluggable)"
date: 2018-07-13T02:56:33+03:00
draft: false
---
Bu yazımda sizlere laravel üzerinde Elequent Sluggable paketini kullanarak seo uyumlu linkler nasıl yaratırız, güncelleme işlemlerinde Sluggable nasıl aktif ederiz ve türkçe karakter sorununu nasıl giderebiliriz bahsetmek istiyorum. Eğer cms sistemi yazıyorsanız veya özel bir yazılım projesi geliştiriyorsanız seo uyumlu link yapısına mutlaka ihtiyacınız olacaktır.

Öncelikle ben işlemlerimi Laravel 5.6 üzerinde gerçekleştiriyorum.

### 1. Kurulum
Terminal üzerinde proje klasörüne giderek composer ile paketimizi indiriyoruz.

composer require cviebrock/eloquent-sluggable:^4.5

**Eğer Laravel 5.5 ve üzeri kullanıyorsanız bu adımı atlayabilirsiniz.

Daha düşük Laravel versiyonları kullanıyorsanız providers’a şunu yazmanız gerekmektedir. Tabi Laravel 5.4 kullanırken **Sluggable 4.2** sürümünü kurmalısınız.

```php
'providers' => [
    // ...
    Cviebrock\EloquentSluggable\ServiceProvider::class,
];
```

### 2. Kullanım
Eğer eklentinin varsayılan ayarlarını üzerinde değişiklik yapmak istiyorsanız aşağıdaki vendor:publish komutumuzu çalıştırıyoruz ve config dizini içerisine sluggable.php ayar dosyamızı getirmiş oluyoruz.

php artisan vendor:publish --provider="Cviebrock\EloquentSluggable\ServiceProvider"

Seo linki yapacağınız her tablo’nun Model dosyaları içerisine aşağıdaki tanımlamaları yapıyoruz.
Ben örnekte post tablosu içerisine title ve slug adında 2 sütun oluşturdum.

```php
use Cviebrock\EloquentSluggable\Sluggable;
 
class Post extends Model
{
    use Sluggable;
 
    protected $fillable = ['title', 'slug'];
 
    public function sluggable()
    {
        return [
            'slug' => [
                'source' => 'title'
            ]
        ];
    }
}
```

Burada anlamamız gereken **sluggable()** fonksiyonunun çalışma mantığıdır.
Fonksiyon bize şunu söylüyor; ben tablonda başlık olarak verdiğin sütunu **(title)** referans alır gider linki yazdıracağın sütuna **(slug)** otomatik olarak çeviririm der.

Örnek bir ekleme işlemi yaptığımızda aşağıdaki gibi başlığımız otomatik olarak linke dönüşecektir.

```php
public function store()
{
  Post::create(['title' => 'Limonlu Kek']);
 
  // Çıktı aşağıdaki gibi olacaktır.
  // limonlu-kek
}
```
### Güncelleme (Update) İşlemlerinde Sluggable Kullanımı
Peki buraya kadar herşey normal yeni kayıt eklerken otomatik olarak link çevrimi yapılıyor fakat güncelleme işlemlerinde otomatik olarak link çevirme yapmamaktadır.  Bunun sebebi ise Sluggable tablodaki slug sütununu dolu olarak algıladığından üzerine yazdırma yapmamaktadır.

Güncelleme fonksiyonlarımızda slug alanını en başta null yaparak bu sorunuda çözmüş oluyoruz.
```php
public function update()
{
  $post = Post::findOrfail(1);
  $post->slug = null; // Güncelleme yaparken link sütununu null yapıyoruz.
  $post->title = "Üşenmeden kendin yaz";
  $post->save();
 
  // Çıktı
  // uesenmeden-kendin-yaz
}
```

Alternatif bir yol olarak `config/sluggable.php` içerisindeki `onUpdate=true` yapmanız yeterlidir.

### 4. Türkçe Karakter Sorunu ve Çözümü
Başlıklarımızı seo uyumlu linklere artık otomatik olarak çevirebiliyoruz fakat türkçe karakter kullandığımızda bazı uyuşmazlıklar ortaya çıkmaktadır. Yukarıdaki güncelleme örneğinde de farketmiş olabilirsiniz 😀

Örneğin; “ü” harfini eklenti linke çevirirken “ue” olarak döndürmektedir.

Bu sorunun temel kaynağı laravel’in Str::slug’ı dahil yapısında türkçe karakterlere destek vermemesidir. Hatırlarsanız ki kurulum yaparken yukarda sizlere varsayılan ayarlara değiştirmek istiyorsanız vendor:publish komutunu çalıştırın demiştim. Türkçe karakter sorununu çözmek için şimdi komutu çalıştırıp config/sluggable.php ayar dosyamızın içerisine gidiyoruz.

Ayar dosyamız içerisinde method elemanını buluyoruz. Standartta burası null olarak tanımlı gelmektedir. Biz içerisine türkçe karakterleri de seo yapısına uygun çevirebilmesi için aşağıdaki yazdığım fonksiyon ekliyoruz.

```php
'method' => function( $string, $sep  ) {
return strtolower(str_replace(['Ğ','ğ','Ş','ş','Ü','ü','Ö','ö',' '], ['g','g','s','s','u','u','o','o','-'], $string));
},
```

### 5. Sonuç
Laravel üzerinde SEO dostu url yapısı nasıl yapılır, güncelleme işlemlerinde de sluggable eklentisini nasıl kullanırız, sluggable eklentisinde türkçe karakter sorunu gibi sorulara cevap vermeye çalıştım.
Umarım faydalı olmuştur, bir sonraki yazıda görüşmek üzere 🙂