---
title: "Bulanık mantık ile stratejik planlama ve kâr/zarar tahmini"
date: 2018-02-11T02:40:21+03:00
draft: false
---
Kısa bir aradan sonra tekrar merhabalar, üniversite ve iş yoğunluğundan dolayı bir süredir blogumda yazılar paylaşamıyordum. Her seferinde tamam bugün paylaşacağım desemde kısmet bugüneymiş :))

Bu yazımda sizlere bir anlatımdan çok Yapay Zeka dersi için **Bulanık Mantık** ile hazırlamış olduğum matlab projesini paylaşıyorum. Bilgisayar Mühendisliği okuyan arkadaşlar için olmazsa olmaz bir derstir.

#### Üyelik Fonksiyonları

**Kriterler:** İlin nüfusu,  arsanın merkeze yakınlığı,  arsa fiyatı, arsa büyüklüğü.
* İlin nüfusü ne kadar fazla ise o kadar iyi,
* ildeki arsanın merkeze yakınlığı ne kadar az ise o kadar iyi,
* Arsa fiyatı ne kadar az ise o kadar iyi,
* Arsanın ideal büyüklüğü 2500 metrekare  bu değerden uzaklaştıkça kötü.

Bu kriterlere göre iller 0-10 arası puan almaktadır. 0 en kötü, 10 en iyi puan olarak baz alınmaktadır.

A İli, 30.000 nüfuslu, arsanın merkeze uzaklığı 3km mesafe, arsa fiyatı 2.000.000 TL ve 1800 metrekare.

B İli, 190.000 nüfuslu, arsanın merkeze uzaklığı 1 km mesafe, arsa fiyatı 1.000.000 TL ve 3000 metrekare.

C İli, 90.000 nüfuslu, arsanın merkeze uzaklığı 3 km mesafe, arsa fiyatı 3.000.000 TL ve 2450 metrekare.

**Tanımlı Kurallar**
![alt text](/media/bulanik-mantik-ile-stratejik-planlama-kar-zarar-tahmini.png "Bulanık mantık ile stratejik planlama ve kâr/zarar tahmini")

Proje dosyalarını Github'a yükledim.

[Github Proje Linki](https://github.com/kerembahcivan/FuzzyLogic)
