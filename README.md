# İkinci El Telefon Fiyat Tahmini: Doğrusal ve Polinom Regresyon Analizi

Telefon yaşına bağlı doğrusal olmayan değer kaybını analiz ederek ikinci el telefon fiyatlarını Doğrusal Regresyon ve Polinom Regresyon (2. ve 3. derece) modelleriyle karşılaştırmalı olarak tahmin eden makine öğrenmesi çalışması.

![Python](https://img.shields.io/badge/Python-3.13-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Veri%20Analizi-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Sayısal%20Hesaplama-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Görselleştirme-11557C?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Makine%20Öğrenmesi-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)

---

## Projenin Amacı ve Çözdüğü Problem

Elektronik cihazlarda, özellikle akıllı telefonlarda değer kaybı zamanla sabit bir oranda gerçekleşmez; ilk yıllarda fiyat hızla düşerken ilerleyen yıllarda düşüş eğimi yavaşlar. Bu nedenle basit doğrusal modeller bu eğrisel yapıyı yakalamakta yetersiz kalabilir.

Bu proje, 0 ile 5 yıl arasındaki 30 adet ikinci el telefon ilan verisi üzerinde:
- Temel tanımlayıcı istatistiklerin hesaplanmasını,
- Telefon yaşı ile ikinci el fiyatı arasındaki doğrusal olmayan ilişkinin görselleştirilmesini,
- Doğrusal Regresyon ile 2. ve 3. dereceden Polinom Regresyon modellerinin hata payı (MSE) ve açıklayıcılık ($R^2$) açısından karşılaştırılmasını amaçlar.

---

## Öne Çıkan Özellikler ve Proje Bulguları

### 1. Veri Seti Özeti ve Tanımlayıcı İstatistikler
Analizde kod içerisinde tanımlanan 30 gözlemlik (`Telefon yaşı (yıl)` ve `İkinci el fiyatı (TL)`) veri seti kullanılmıştır:

| Metrik | Değer |
| :--- | :--- |
| Gözlem Sayısı | 30 |
| Telefon Yaşları Ortalaması | 2.51 yıl |
| En Düşük Fiyat | 13,000.00 TL |
| En Yüksek Fiyat | 40,000.00 TL |
| Medyan (Ortanca) Fiyat | 19,750.00 TL |
| Aritmetik Ortalama Fiyat | 22,070.00 TL |
| Fiyat Standart Sapması | 7,853.45 TL |

### 2. Model Parametreleri ve Performans Karşılaştırması
Aynı veri seti üzerinde eğitilen üç farklı regresyon modelinin performans sonuçları aşağıdaki gibidir:

| Model | MSE (Ortalama Kare Hata) | $R^2$ Skoru |
| :--- | :---: | :---: |
| **Doğrusal Regresyon (Linear Regression)** | 5,316,321.26 | 0.9108 |
| **Polinom Regresyon (Degree = 2)** | 528,617.92 | 0.9911 |
| **Polinom Regresyon (Degree = 3)** | 93,649.07 | 0.9984 |

- **Doğrusal Model Denklemi:** Eğim (Coef) = `-4912.24`, Sabit Terim (Intercept) = `34416.09`
- **2. Derece Polinom Modeli:** Katsayılar (Coef) = `[0, -10430.42, 1086.27]`, Sabit Terim (Intercept) = `38978.70`
- Polinom derece 1'den 2'ye çıkarıldığında hata payı (MSE) yaklaşık **10 kat azalmış**, $R^2$ skoru `0.9108`'den `0.9911`'e yükselmiştir. 3. derecede ise $R^2$ skoru `0.9984` olarak ölçülmüştür.

### 3. Örnek Tahmin Karşılaştırması (2.5 Yıllık Telefon)
Veri setinde 2.5 yaşındaki telefonun gerçek ilan fiyatı **19,500.00 TL** iken modellerin ürettiği tahminler:
- **Doğrusal Model Tahmini:** `22,135.50 TL`
- **Polinom Model Tahmini (Degree = 2):** `19,691.83 TL`

Bu çıktı, telefon fiyatındaki eğrisel değer kaybını polinom modelin gerçek piyasa değerine çok daha yakın biçimde yakaladığını göstermektedir.

---

## Kullanılan Teknolojiler ve Araçlar

- **Programlama Dili:** Python 3.13
- **Geliştirme Ortamı:** Jupyter Notebook
- **Veri İşleme ve İstatistik:** `pandas`, `numpy`
- **Veri Görselleştirme:** `matplotlib`
- **Makine Öğrenmesi:** `scikit-learn` (`LinearRegression`, `PolynomialFeatures`, `mean_squared_error`, `r2_score`)

---

## Proje Klasör ve Dosya Yapısı

```text
ikinci-el-telefon-fiyat-tahmini/
├── telefon_fiyat_tahmini.ipynb             # Veri oluşturma, EDA, modelleme, görselleştirme ve tahminlerin bulunduğu ana Jupyter Notebook              
├── .gitignore                              # Git tarafından takip edilmeyecek geçici dosya ve klasör kuralları
└── README.md                               # Proje dokümantasyonu
```

---

## Kurulum ve Çalıştırma

Projeyi kendi bilgisayarınızda çalıştırmak için aşağıdaki adımları izleyin:

### 1. Repoyu Klonlayın
```bash
git clone https://github.com/esmanuryavuz908/ikinci-el-telefon-fiyat-tahmini.git
cd ikinci-el-telefon-fiyat-tahmini
```

### 2. Gerekli Kütüphaneleri Yükleyin
```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

### 3. Jupyter Notebook'u Başlatın
```bash
jupyter notebook
```
Tarayıcıda açılan arayüzden `telefon_fiyat_tahmini.ipynb` dosyasını seçin ve hücreleri sırayla çalıştırın.

> **Not:** Veri seti doğrudan notebook içerisindeki ilk hücrede Python sözlüğü olarak tanımlandığı için harici bir `.csv` dosyası indirmenize gerek yoktur.

---
