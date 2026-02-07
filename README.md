# ogrenci_yerlestirme_simulasyonu
Öğrencilerin GNO ve tercihlerine  göre firmalara yerleştirilmesini Python ile optimizde eden, algoritmik bir İMEP simülasyonudur.

# Öğrenci Yerleştirme Simülasyonu (İMEP)

Bu proje, Bursa Teknik Üniversitesi İMEP kapsamında verilen **stajyer yerleştirme problemine** yönelik geliştirilmiş Python tabanlı bir simülasyon sistemidir.

Amaç; firmaların sınırlı kontenjanları ve minimum Genel Not Ortalaması (GNO) şartları altında öğrencilerin firmalara yerleştirilmesini sağlamak ve farklı algoritmik stratejileri karşılaştırmalı olarak analiz etmektir.

---

## 📌 Proje Özeti

Stajyer yerleştirme süreci şu şekilde modellenmiştir:

- Firmaların belirli kontenjanları bulunmaktadır.
- Firmalar minimum GNO şartı belirleyebilir.
- Öğrenciler 5 firmadan oluşan tercih listesi oluşturur.
- Yerleştirme işlemi iteratif (tur bazlı) yürütülür.
- Firmalar belirli bir olasılıkla öğrencileri reddedebilir.
- Yerleşemeyen öğrenciler sonraki turlarda tekrar değerlendirilir.
- Tercih listeleri tıkanırsa ek kontenjan mekanizması devreye girer.

Bu yapı, gerçek hayattaki stajyer kabul süreçlerine yakın dinamik bir simülasyon ortamı sunmaktadır.

---

## 🧠 Kullanılan Algoritmalar

### ✅ Greedy (Açgözlü) Algoritma

- Öğrenciler GNO değerine göre büyükten küçüğe sıralanır.
- Her öğrenci tercih listesindeki ilk uygun firmaya yerleştirilir.
- Hızlı çalışır ancak her zaman maksimum memnuniyet sağlamaz.

**Avantaj:** Daha kısa çözüm süresi  
**Dezavantaj:** Daha düşük toplam memnuniyet oluşabilir

---

### 🤖 Heuristik (Sezgisel) Algoritma

Greedy’den farklı olarak her öğrenci için uygun firmalar skorlanır ve en yüksek puanlı firma seçilir.

Skor hesaplama formülü:
Skor = (Tercih_Puanı × 10) + (GNO × 2)

Tercih puanları:

- 1. tercih → 5
- 2. tercih → 4
- 3. tercih → 3
- 4. tercih → 2
- 5. tercih → 1

**Avantaj:** Daha dengeli ve tercih odaklı yerleştirme  
**Dezavantaj:** Daha fazla işlem maliyeti

---

### 🔄 Local Search (Yerel Arama) İyileştirmesi

Heuristik çözüm sonrasında toplam memnuniyet puanını artırmak için:

- Rastgele iki öğrenci seçilir
- Firmaları takas edilir
- Memnuniyet artarsa değişiklik korunur

Bu sayede çözüm kalitesi iyileştirilmeye çalışılır.

---

## ❌ Firma Red Mekanizması

Simülasyonda firmalar yerleşen öğrencileri belirli bir olasılıkla reddedebilir:

- Reddedilen öğrenci açıkta kalır
- Firma kontenjanı geri artırılır
- Öğrenci sonraki turda yeniden değerlendirilir
- İterasyonlar ilerledikçe red oranı azaltılır

Bu mekanizma simülasyonu daha gerçekçi hale getirir.

---

## 📂 Veri Dosyaları

### Firmalar — `firmalar.csv`

Her firma için:

- Firma adı
- Minimum GNO şartı
- Kontenjan
- Kalan kontenjan

📌 Firma sayısı: **30–50**

---

### Öğrenciler — `ogrenciler.json`

Her öğrenci için:

- Öğrenci adı
- GNO
- 5 firma tercihi
- Atanan firma
- Yerleştiği tur bilgisi

📌 Öğrenci sayısı: **100–150**

---

## ▶️ Projeyi Çalıştırma

1. Repoyu klonlayın:

```bash
git clone https://github.com/ismihankrmz/ogrenci_yerlestirme_simulasyonu.git

2.Gerekli kütüphaneleri yükleyin:

pip install pandas

3.Simülasyonu çalıştırın:

python imep_ogrenci_yerlestirme_simulasyonu.py

📊 Performans Karşılaştırması

Algoritmalar şu kriterlerle değerlendirilmiştir:

Toplam memnuniyet puanı
Çözüm süresi
İşlem sayısı
İterasyon (tur) sayısı

Sonuçlar
Greedy algoritma daha hızlı ve düşük işlem maliyetlidir.
Heuristik algoritma daha dengeli ve tercih odaklı yerleştirme sağlar.
Local Search adımı heuristik çözümü iyileştirmeye yardımcı olur.

🛠️ Kullanılan Teknolojiler
Python
Pandas
CSV / JSON veri yapıları
Simülasyon tabanlı optimizasyon

👩‍💻 Geliştiriciler

İsmihan Kırmızıoğlan
Melike Dal
Bursa Teknik Üniversitesi — Bilgisayar Mühendisliği

📌 Lisans
Bu proje eğitim amaçlı geliştirilmiştir.
