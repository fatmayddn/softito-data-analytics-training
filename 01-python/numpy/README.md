# NumPy Pratik: Öğrenci Performans Analizi

NumPy'nin temel kavramlarını (array oluşturma, indeksleme, dilimleme, boolean maskeleme, istatistiksel fonksiyonlar, broadcasting, reshape ve rastgele örnekleme) gerçek boyutlu bir veri seti üzerinde uygulamalı olarak gösteren bir pratik/öğrenim notebook'u.

## İçindekiler

- [Veri Seti](#veri-seti)
- [Kurulum](#kurulum)
- [Kullanım](#kullanım)
- [Notebook İçeriği](#notebook-i̇çeriği)
- [Öğrenilen NumPy Kavramları](#öğrenilen-numpy-kavramları)
- [Proje Yapısı](#proje-yapısı)
- [Lisans](#lisans)

## Veri Seti

Notebook, `Student_Performance.csv` adlı bir öğrenci performans veri setini kullanır (25.000 öğrenci kaydı). Veri setinde şu sütunlar bulunur:

| Sütun | Açıklama |
|---|---|
| `student_id` | Öğrenci kimliği |
| `age` | Yaş |
| `gender` | Cinsiyet |
| `school_type` | Okul türü |
| `parent_education` | Ebeveyn eğitim düzeyi |
| `study_hours` | Günlük çalışma saati |
| `attendance_percentage` | Devam yüzdesi |
| `internet_access` | İnternet erişimi |
| `travel_time` | Okula ulaşım süresi |
| `extra_activities` | Ekstra faaliyet katılımı |
| `study_method` | Çalışma yöntemi |
| `math_score` | Matematik notu |
| `science_score` | Fen notu |
| `english_score` | İngilizce notu |
| `overall_score` | Genel başarı skoru |
| `final_grade` | Harf notu (a–f; `f` = kaldı) |

> Veri setini kendi CSV dosyanızla değiştirmek isterseniz, notebook'un 3. hücresindeki sütun indekslerini kendi dosyanızın sütun sırasına göre güncellemeniz yeterlidir.

## Kurulum

```bash
git clone <bu-repo-url>
cd <repo-klasörü>
pip install numpy jupyter
```

`Student_Performance.csv` dosyasını notebook ile aynı klasöre yerleştirin.

## Kullanım

```bash
jupyter notebook numpy_pratik_ogrenci_performans.ipynb
```

Hücreleri sırasıyla çalıştırarak (Shift+Enter) her adımın çıktısını görebilirsiniz.

## Notebook İçeriği

Notebook 17 hücreden oluşur ve şu sırayla ilerler:

1. **Kurulum** — NumPy ve csv modüllerinin içe aktarılması
2. **Veri okuma** — CSV dosyasının satır satır okunması
3. **Array dönüşümü** — Sayısal ve kategorik sütunların NumPy array'lerine çevrilmesi
4. **Array özellikleri** — `shape`, `ndim`, `size`, `dtype`
5. **2D matris oluşturma** — `np.column_stack` ile ders notlarının birleştirilmesi
6. **İndeksleme ve dilimleme** — 1D/2D array'lerde eleman ve aralık seçimi
7. **Boolean maskeleme (tek koşul)** — Belirli bir eşiği geçen öğrencilerin filtrelenmesi
8. **Boolean maskeleme (çoklu koşul)** — `&` ve `|` operatörleriyle birleşik koşullar
9. **Maske ile başka array filtreleme** — Çalışma saatine göre başarı karşılaştırması
10. **Kategorik filtreleme** — Harf notuna göre devam yüzdesi karşılaştırması
11. **Temel istatistikler** — `mean`, `min`, `max`, `std`, `median`
12. **Axis bazlı işlemler** — Satır/sütun yönünde ortalama hesaplama
13. **`argmax`** — En yüksek skora sahip öğrencinin bulunması
14. **Broadcasting ve `np.clip`** — Tüm notlara puan ekleme ve sınırlama
15. **Ağırlıklı ortalama** — Matris-vektör çarpımıyla ağırlıklı hesaplama
16. **`reshape`** — 1D array'i 2D matrise dönüştürme
17. **Rastgele örnekleme** — `np.random.choice` ile tekrarsız örneklem seçimi

## Öğrenilen NumPy Kavramları

- Array oluşturma ve temel özellikler (`shape`, `ndim`, `size`, `dtype`)
- 1D ve 2D array indeksleme / dilimleme
- Boolean maskeleme ve mantıksal operatörler (`&`, `|`)
- İstatistiksel fonksiyonlar (`mean`, `std`, `median`, `min`, `max`, `argmax`)
- `axis` parametresi ile satır/sütun bazlı işlemler
- Broadcasting
- `np.clip`, `np.round`, `np.column_stack`, `reshape`
- `np.random.seed` ile tekrarlanabilir rastgele örnekleme

## Proje Yapısı

```
.
├── numpy_pratik_ogrenci_performans.ipynb   # Ana notebook
├── Student_Performance.csv                  # Veri seti (repoya dahil değilse ayrıca indirilmeli)
└── README.md
