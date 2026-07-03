# Macam-Macam Normalisasi Data pada Data Mining

Dalam Data Mining, normalisasi data adalah proses mengubah nilai data agar berada dalam rentang tertentu sehingga perbedaan skala antar atribut tidak mempengaruhi hasil analisis.

## 1. Min-Max Normalization
Metode ini mengubah nilai data ke dalam rentang tertentu, biasanya antara 0 sampai 1.

### Rumus
X' = (X - Xmin) / (Xmax - Xmin)

### Keterangan
- X = nilai data asli  
- Xmin = nilai minimum data  
- Xmax = nilai maksimum data  

### Contoh
Jika data memiliki nilai minimum 20 dan maksimum 80, maka normalisasi nilai 50 adalah:

X' = (50 - 20) / (80 - 20)  
X' = 30 / 60  
X' = 0.5

---

## 2. Z-Score Normalization (Standardization)
Metode ini menormalisasi data berdasarkan rata-rata (mean) dan standar deviasi.

### Rumus
X' = (X - μ) / σ

### Keterangan
- X = nilai data  
- μ = rata-rata (mean)  
- σ = standar deviasi  

### Hasil
- Mean = 0  
- Standar deviasi = 1  

Metode ini sering digunakan pada algoritma machine learning dan analisis statistik.

---

## 3. Decimal Scaling Normalization
Metode ini menormalisasi data dengan memindahkan titik desimal berdasarkan jumlah digit maksimum pada data.

### Rumus
X' = X / 10^j

### Keterangan
- X = nilai data  
- j = jumlah digit dari nilai maksimum  

### Contoh
Jika nilai maksimum adalah 987 maka:

X' = 987 / 10^3  
X' = 0.987

---

## 4. Mean Normalization
Metode ini menggunakan rata-rata dan rentang data untuk melakukan normalisasi.

### Rumus
X' = (X - mean) / (Xmax - Xmin)

### Keterangan
- X = nilai data  
- mean = rata-rata data  
- Xmax = nilai maksimum  
- Xmin = nilai minimum  

---

## Kesimpulan
Metode normalisasi yang umum digunakan dalam data mining adalah:

1. Min-Max Normalization  
2. Z-Score Normalization  
3. Decimal Scaling Normalization  
4. Mean Normalization