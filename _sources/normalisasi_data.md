# Normalisasi Data

## Pengertian Normalisasi Data

Normalisasi data adalah proses **mengubah nilai atribut ke dalam skala yang sama** agar tidak ada atribut yang memiliki pengaruh lebih besar dalam proses perhitungan.  

Normalisasi sering digunakan pada algoritma **data mining dan machine learning**, terutama yang berbasis perhitungan jarak seperti:

- KNN (K-Nearest Neighbor)
- WKNN (Weighted KNN)
- Clustering
- Cosine Similarity

---

## Data Contoh

| Atribut | Produk 1 | Produk 2 | Produk 3 | Produk 4 |
|---|---|---|---|---|
| Harga | 15000 | 50000 | 25000 | 75000 |
| Rating | 3.5 | 4.8 | 4.0 | 4.5 |
| Jumlah_Terjual | 120 | 80 | 200 | 60 |
| Diskon | 10 | 25 | 5 | 30 |
| Berat | 200 | 500 | 300 | 700 |
| Kategori | Makanan | Elektronik | Fashion | Elektronik |
| Brand | Lokal | Brand A | Brand B | Brand A |
| Status_Gratis_Ongkir | Ya | Tidak | Ya | Tidak |

Pada proses normalisasi biasanya **hanya atribut numerik yang dinormalisasi**, seperti:

- Harga  
- Rating  
- Jumlah_Terjual  
- Diskon  
- Berat  

---

# 1. Min-Max Normalization

Min-Max Normalization digunakan untuk **mengubah nilai data ke dalam rentang 0 sampai 1**.

## Rumus

X' = (X - Xmin) / (Xmax - Xmin)

---

## Contoh pada atribut Harga

- Xmin = 15000  
- Xmax = 75000  

| Produk | Perhitungan | Hasil |
|---|---|---|
| 1 | (15000 − 15000) / (75000 − 15000) | 0 |
| 2 | (50000 − 15000) / (75000 − 15000) | 0.58 |
| 3 | (25000 − 15000) / (75000 − 15000) | 0.17 |
| 4 | (75000 − 15000) / (75000 − 15000) | 1 |

---

## Hasil Normalisasi Min-Max

| Atribut | Produk 1 | Produk 2 | Produk 3 | Produk 4 |
|---|---|---|---|---|
| Harga | 0 | 0.58 | 0.17 | 1 |
| Rating | 0 | 1 | 0.38 | 0.77 |
| Jumlah_Terjual | 0.43 | 0.14 | 1 | 0 |
| Diskon | 0.2 | 0.8 | 0 | 1 |
| Berat | 0 | 0.6 | 0.2 | 1 |

---

# 2. Z-Score Normalization (Standardization)

Z-Score Normalization mengubah data berdasarkan **rata-rata (mean)** dan **standar deviasi**.

## Rumus

Z = (X - μ) / σ

---

## Contoh pada atribut Harga

Data: 15000, 50000, 25000, 75000  

Mean = 41250  
Standar Deviasi ≈ 22361  

| Produk | Hasil |
|---|---|
| 1 | -1.17 |
| 2 | 0.39 |
| 3 | -0.73 |
| 4 | 1.51 |

---

# 3. Decimal Scaling Normalization

## Rumus

X' = X / (10^j)

---

## Contoh pada atribut Harga

| Produk | Hasil |
|---|---|
| 1 | 0.15 |
| 2 | 0.50 |
| 3 | 0.25 |
| 4 | 0.75 |

---

# 4. Mean Normalization

## Rumus

X' = (X - mean) / (max - min)

---

## Contoh pada atribut Harga

| Produk | Hasil |
|---|---|
| 1 | -0.44 |
| 2 | 0.15 |
| 3 | -0.27 |
| 4 | 0.56 |

---

# Kesimpulan

Normalisasi data bertujuan untuk menyamakan skala antar atribut agar tidak ada atribut yang mendominasi dalam perhitungan.

Metode yang digunakan:
- Min-Max Normalization
- Z-Score Normalization
- Decimal Scaling
- Mean Normalization