---
title: "PhpStorm Could not Create FTP directory Hatası ve Çözümü"
date: 2017-01-17T12:34:26+03:00
draft: false
ShowReadingTime: true
---

Phpstorm’da yakın zamanda karşılaştığım bir sorun beni ve işlerimi bir hayli aksattı. Yerel depodan uzak sunucuya dosya kaydetmeye çalışırken sürekli **“Could not Create FTP directory”** diye hata almaya başladım. Yabancı forumlarda biraz araştırma yaptıktan sonra sorunun Passive Modu etkinleştirmeyle düzeldiğini söylüyorlardı ancak bu çözüm bende en azından direkt işe yaramadı.

Bu sorunu çözmemiz için ilk öncelikle Phpstormu  bilgisayarınızdan tamamen kaldırmamız gerekiyor. Tekrar temiz kurulum yaptıktan sonra herhangi bir projeyi açıyoruz ve File menüsünden **Invalidate Caches / Restart** seçeneğine tıklayarak önbelleği devre dışı bırakıp yeniden başlatıyoruz. Son olarak başta söylediğim; ftp gelişmiş ayarlarından Passive Modu etkinleştiriyorsunuz ve sorun çözülmüş oluyor. Bu adımdan sonra Phpstormu tekrar kullanmaya başlayabilirsiniz 🙂