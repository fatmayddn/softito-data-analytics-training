# Pandas ile Veri Temizleme

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/fatmayddn/pandas-data-cleaning/blob/main/pandas_veri_temizleme.ipynb)

Bir perakende satış veri seti üzerinde, ham veriden analize hazır veriye giden temizleme sürecinin uçtan uca uygulandığı bir Pandas çalışması. Her adım önce tespit (sorun var mı?), sonra düzeltme mantığıyla ilerliyor; son bölümde tüm adımlar tek bir fonksiyonda toplanıyor.

## Veri Seti

`retail_store_sales.csv` — 12.575 satır, 11 sütun. Bilinçli olarak "kirli" bırakılmış bir perakende işlem kaydı veri seti (eksik değerler, tutarsız veri tipleri).

| Sütun | Açıklama |
|---|---|
| `Transaction ID` | İşlem kimliği |
| `Customer ID` | Müşteri kimliği |
| `Category` | Ürün kategorisi (8 kategori) |
| `Item` | Ürün kodu |
| `Price Per Unit` | Birim fiyat |
| `Quantity` | Miktar |
| `Total Spent` | Toplam tutar |
| `Payment Method` | Ödeme yöntemi (Cash / Credit Card / Digital Wallet) |
| `Location` | Satış kanalı (In-store / Online) |
| `Transaction Date` | İşlem tarihi |
| `Discount Applied` | İndirim uygulandı mı |

## İçerik

1. Veriyi yükleme ve ilk bakış
2. Genel veri sağlığı kontrolü (`info`, `isnull`, `duplicated`)
3. Eksik değerlerin tespiti ve giderilmesi
4. Yinelenen (duplicate) kayıt kontrolü
5. Veri tiplerinin düzeltilmesi (tarih sütunu)
6. Mantıksal hata / aykırı değer tespiti ve düzeltilmesi
7. Kategori tutarlılığı kontrolü
8. İndeks düzenleme
9. Temizlenmiş veriyi kaydetme
10. Uçtan uca temizleme fonksiyonu

## Temizleme Sürecinde Çıkan Bulgular

| Kontrol | Sonuç |
|---|---|
| Eksik `Item` | 1.213 satır → `"Bilinmiyor"` ile dolduruldu |
| Eksik `Price Per Unit` / `Quantity` | 609 / 604 satır |
| Eksik `Discount Applied` | 4.199 satır |
| Tam yinelenen satır | 0 |
| Müşteri + tarih + ürün bazında yinelenen | 40 kayıt |
| `Transaction Date` tipi | `object` → `datetime64[ns]` (çevrilemeyen kayıt yok) |
| Negatif / sıfır miktar veya fiyat | 0 (düzeltme yöntemi yine de örneklendi) |
| Kategorik sütunlarda boşluk / yazım tutarsızlığı | 0 (standartlaştırma yine de uygulandı) |

Tarih dönüşümünün ardından `islem_yili` ve `islem_ayi` sütunları türetilerek veri, zaman bazlı analizlere hazır hale getirildi.

## Uçtan Uca Fonksiyon

Tüm adımlar `veriyi_temizle(df_ham)` fonksiyonunda toplanıyor. Ham DataFrame'i alır, temizlenmiş bir kopyasını döndürür:

```python
df_ham = pd.read_csv("retail_store_sales.csv")
df_temiz = veriyi_temizle(df_ham)
```

Fonksiyon sırasıyla eksik `Item` değerlerini doldurur, tarih sütununu dönüştürür, negatif miktar/fiyatları düzeltip `Total Spent` değerini yeniden hesaplar, alt küme bazında yinelenen kayıtları siler, kategorik sütunları standartlaştırır ve indeksi sıfırlar.

## Çalıştırma

**Colab:** Yukarıdaki rozete tıklamanız yeterli. Veri setini çalışma dizinine yükleyip yoldaki `/content/` kısmını gerekirse güncelleyin.

**Yerel:**

```bash
git clone https://github.com/fatmayddn/pandas-data-cleaning.git
cd pandas-data-cleaning
pip install pandas numpy jupyter
jupyter notebook pandas_veri_temizleme.ipynb
```

## Gereksinimler

- Python 3.8+
- pandas
- numpy

## Dosyalar

```
pandas_veri_temizleme.ipynb    # Ana not defteri
retail_store_sales.csv         # Ham veri
retail_store_sales_temiz.csv   # Temizlenmiş çıktı
```


