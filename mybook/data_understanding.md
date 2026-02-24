---
title: Memahami Data
---

# Memahami Data

```{admonition} Tujuan Pembelajaran
:class: tip
Memahami:
- Jenis-jenis data
- Tipe atribut
- Distribusi normal
- Statistik deskriptif
- Visualisasi distribusi dengan Python
```

---

# 1️⃣ Macam-Macam Data

```{admonition} Jenis Data dalam Data Mining
:class: note
- Data Terstruktur
- Data Tidak Terstruktur
- Bahasa Alami (NLP)
- Machine Generated
- Audio / Video / Citra
- Streaming
- Graph-based
```

## ✅ Data Terstruktur
Data dalam bentuk tabel (baris & kolom).  
Mudah diproses dengan SQL / Excel.

## ❌ Data Tidak Terstruktur
Email, dokumen, teks bebas.

## 🗣 Bahasa Alami
Bahasa manusia yang diproses dengan NLP.

## ⚙ Machine Generated
Log server, IoT, sensor.

## 🎥 Multimedia
Audio, Video, Citra.

## 🔁 Streaming
Data mengalir terus-menerus (real-time).

## 🕸 Graph
Node & Edge (jejaring sosial).

---

# 2️⃣ Tipe Atribut

```{admonition} Jenis Atribut
:class: important
- Nominal
- Biner
- Ordinal
- Numerik (Interval & Rasio)
```

## Nominal
Kategori tanpa urutan.  
Contoh: warna rambut.

## Biner
0 dan 1 (True/False).  
Contoh: Merokok (1=Ya, 0=Tidak)

## Ordinal
Ada urutan tapi tidak ada jarak pasti.  
Contoh: kecil < sedang < besar.

## Numerik
### Interval → suhu (°C)
### Rasio → berat badan

---

# 3️⃣ Distribusi Normal (Gaussian)

```{admonition} Rumus Distribusi Normal
:class: note
$$
f(x) = \frac{1}{\sigma\sqrt{2\pi}} 
e^{-\frac{(x-\mu)^2}{2\sigma^2}}
$$

- $\mu$ = mean  
- $\sigma$ = standar deviasi  
- $\sigma^2$ = variansi
```

---

# 4️⃣ Statistik Deskriptif

## Mean

$$
\bar{x} = \frac{\sum_{i=1}^{N} x_i}{N}
$$

## Variansi

$$
\sigma^2 = \frac{1}{N}\sum_{i=1}^{N}(x_i - \bar{x})^2
$$

## Standar Deviasi

$$
\sigma = \sqrt{\sigma^2}
$$

## IQR

$$
IQR = Q_3 - Q_1
$$

Outlier jika:

$$
x < Q_1 - 1.5 \times IQR
$$

atau

$$
x > Q_3 + 1.5 \times IQR
$$

---

# 5️⃣ Contoh Implementasi Python

```python
import pandas as pd
from scipy import stats

df = pd.read_csv("data.csv", usecols=[0])  # asumsi kolom pertama NilaiPreTest

x = df["NilaiPreTest"]

print("Jumlah data      :", x.count())
print("Rata-rata (mean) :", x.mean())
print("Nilai minimum    :", x.min())
print("Q1 (25%)         :", x.quantile(0.25))
print("Q2 (median)      :", x.quantile(0.50))
print("Q3 (75%)         :", x.quantile(0.75))
print("Nilai maksimum   :", x.max())
print("Skewness         :", round(x.skew(), 6))
print("Std Deviasi      :", round(x.std(), 2))
print("Variansi         :", round(x.var(), 2))

mode = stats.mode(x, keepdims=True)
print(f"Modus            : {mode.mode[0]} (jumlah {mode.count[0]})")