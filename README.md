# Sürücüsüz Metro Simülasyonu (Rota Optimizasyonu)

Bu proje, bir metro ağı üzerinde istasyonlar arası rotaların hesaplanmasını sağlar. BFS ve A* algoritmalarıyla en az aktarmalı ve en hızlı rotayı bulabilirsiniz.

## Kullanılan Teknolojiler ve Kütüphaneler

Bu projede PYTHON dili kullanılmıştır. Kullanılan kütüphaneler:

- **collections**: Python'ın standart kütüphanelerinden biridir ve veri yapıları (deque, defaultdict) sağlar. Bu kütüphane, özellikle BFS algoritmasında sıralı ve hızlı veri eklemeleri için kullanılır.
- **heapq**: Min-heap veri yapısını kullanarak A* algoritmasında en uygun rotayı bulmak için kullanılır. `heapq` ile verileri sıralayarak daha verimli bir arama işlemi yapılır.
- **typing**: Kodun daha anlaşılır olması ve tür denetimlerinin yapılabilmesi için kullanılır.

## Algoritmaların Çalışma Mantığı

### BFS Algoritması

BFS algoritması, bir graf üzerinde en kısa yolu bulmak için yaygın olarak kullanılır. Bu algoritma, her seviyedeki tüm komşu düğümleri kontrol eder ve hedefe ulaşmak için en az sayıda geçişi sağlar. Bu projede, **en az aktarmalı rota** için BFS kullanılmıştır.

**Çalışma Prensibi:**

1. Başlangıç noktasından başlayarak, her istasyonun komşuları sırayla ziyaret edilir.
2. Ziyaret edilen istasyonlar bir kuyruğa eklenir.
3. Kuyruktaki her istasyonun komşuları sırasıyla kontrol edilir.
4. Hedef istasyon bulunana kadar işlem devam eder.

### A* Algoritması

A* algoritması, en kısa yolu bulmada kullanılan bir diğer popüler algoritmadır. BFS'ten farklı olarak, A* algoritması, her adımda tahmin edilen bir "heuristic" değeri ekler ve daha akıllıca seçimler yaparak hedefe en hızlı şekilde ulaşmaya çalışır. Bu projede, **en hızlı rota** için A* algoritması kullanılmıştır.

**Çalışma Prensibi:**

1. Her istasyon için mevcut maliyet (g) ve tahmini maliyet (f) hesaplanır.
2. Her yeni istasyon, `g + h` (g=mevcut yol maliyeti, h=tahmini maliyet) değerine göre sıralanır.
3. En düşük f değeri olan istasyon sırayla işlenir.

## Neden Bu Algoritmaları Kullandık?

- **BFS**: Bu algoritma, "en az aktarmalı rota" için idealdir çünkü her istasyon yalnızca bir kez ziyaret edilir ve tüm komşular aynı seviyede keşfedilir. Bu sayede aktarma sayısı en aza indirilir.
- **A***: A* algoritması, daha hızlı bir rota bulma amacına hizmet eder. Heuristic fonksiyonlar sayesinde, gereksiz istasyonlar atlanır ve hedefe daha hızlı ulaşılır.

## Örnek Kullanım ve Test Sonuçları

Yapılan projedeki test sonuçları şu şekildedir:

### 1. AŞTİ'den OSB'ye
- **En az aktarmalı rota**: AŞTİ -> Kızılay -> Ulus -> Demetevler -> OSB
- **En hızlı rota (24 dakika)**: AŞTİ -> Kızılay -> Demetevler -> OSB

### 2. Batıkent'ten Keçiören'e
- **En az aktarmalı rota**: Batıkent -> Demetevler -> Gar -> Keçiören
- **En hızlı rota (21 dakika)**: Batıkent -> Demetevler -> Gar -> Keçiören

### 3. Keçiören'den AŞTİ'ye
- **En az aktarmalı rota**: Keçiören -> Gar -> Sıhhiye -> Kızılay -> AŞTİ
- **En hızlı rota (25 dakika)**: Keçiören -> Gar -> Sıhhiye -> Kızılay -> AŞTİ

## Projeyi Geliştirme Fikirleri

1. **Görselleştirilmiş Kullanıcı Arayüzü**: Kullanıcılara harita üzerinde rotalarını görselleştiren bir UI eklenebilir. Bu, kullanıcı deneyimini önemli ölçüde iyileştirebilir.
2. **Gerçek Zamanlı Trafik Durumu**: Gerçek zamanlı trafik verileri eklenerek, tıkanıklık veya aksama durumlarına göre rotalar güncellenebilir.
