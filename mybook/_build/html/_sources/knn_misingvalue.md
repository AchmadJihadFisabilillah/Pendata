# KNN Missing Value

Contoh ini menunjukkan cara menentukan **nilai usia yang hilang pada data ke-10** menggunakan metode **K-Nearest Neighbor (KNN)**.

## Atribut pada dataset

- Usia
- Tingkat_Kepuasan
- Status_Beasiswa
- Program_Studi

Untuk memprediksi **Usia**, atribut pembanding yang digunakan:

- Tingkat_Kepuasan
- Status_Beasiswa
- Program_Studi

---

# Perhitungan Missing Value Menggunakan Euclidean Distance

## Data Mahasiswa

| Data ke | Usia | Tingkat_Kepuasan | Status_Beasiswa | Program_Studi |
|--------|------|------------------|-----------------|---------------|
| 1 | 30 | Tinggi | Ya | Teknik Informatika |
| 2 | 35 | Rendah | Tidak | Desain Komunikasi Visual |
| 3 | 28 | Sedang | Ya | Arsitektur |
| 4 | 26 | Tinggi | Tidak | Teknik Mesin |
| 5 | 32 | Sedang | Ya | Manajemen |
| 6 | 29 | Rendah | Tidak | Teknik Kimia |
| 7 | 34 | Tinggi | Ya | Sistem Informasi |
| 8 | 31 | Sedang | Tidak | Teknik Elektro |
| 9 | 33 | Rendah | Ya | Matematika |
| 10 | ? | Tinggi | Tidak | Teknik Informatika |

---

Pada data ke-10 terdapat **missing value pada atribut Usia**, sehingga perlu dilakukan estimasi nilai menggunakan **Euclidean Distance** dengan pendekatan **KNN**.

---

# Transformasi Data Kategorikal

## Tingkat Kepuasan

| Kategori | Nilai |
|----------|------|
| Rendah | 1 |
| Sedang | 2 |
| Tinggi | 3 |

## Status Beasiswa

| Kategori | Nilai |
|----------|------|
| Tidak | 0 |
| Ya | 1 |

## Program Studi

| Program Studi | Nilai |
|---------------|------|
| Teknik Informatika | 1 |
| Desain Komunikasi Visual | 2 |
| Arsitektur | 3 |
| Teknik Mesin | 4 |
| Manajemen | 5 |
| Teknik Kimia | 6 |
| Sistem Informasi | 7 |
| Teknik Elektro | 8 |
| Matematika | 9 |

---

# Data Setelah Transformasi

| Data | Usia | Kepuasan | Beasiswa | Prodi |
|-----|------|---------|---------|------|
| 1 | 30 | 3 | 1 | 1 |
| 2 | 35 | 1 | 0 | 2 |
| 3 | 28 | 2 | 1 | 3 |
| 4 | 26 | 3 | 0 | 4 |
| 5 | 32 | 2 | 1 | 5 |
| 6 | 29 | 1 | 0 | 6 |
| 7 | 34 | 3 | 1 | 7 |
| 8 | 31 | 2 | 0 | 8 |
| 9 | 33 | 1 | 1 | 9 |
| 10 | ? | 3 | 0 | 1 |

---

# Rumus Euclidean Distance

d(p,q) = √((x₁-x₁)² + (x₂-x₂)² + (xₙ-xₙ)²)

Atribut yang digunakan:

- Kepuasan
- Beasiswa
- Prodi

---

# Perhitungan Jarak Data ke-10 dengan Data Lain

### Data 1
d = √((3-3)² + (0-1)² + (1-1)²) = 1  

### Data 2
d = √((3-1)² + (0-0)² + (1-2)²) = √5 = 2.23  

### Data 3
d = √((3-2)² + (0-1)² + (1-3)²) = √6 = 2.45  

### Data 4
d = √((3-3)² + (0-0)² + (1-1)²) = 0  

### Data 5
d = √((3-1)² + (0-1)² + (1-2)²) = √6 = 2.45  

### Data 6
d = √((3-2)² + (0-0)² + (1-3)²) = √5 = 2.23  

### Data 7
d = √((3-3)² + (0-1)² + (1-1)²) = 1  

### Data 8
d = √((3-2)² + (0-0)² + (1-2)²) = √2 = 1.41  

### Data 9
d = √((3-1)² + (0-1)² + (1-3)²) = √9 = 3  

---

# Hasil Perhitungan Jarak

| Data | Usia | Jarak |
|-----|------|------|
| 4 | 26 | 0 |
| 1 | 30 | 1 |
| 7 | 34 | 1 |
| 8 | 31 | 1.41 |
| 2 | 35 | 2.23 |
| 6 | 29 | 2.23 |
| 3 | 28 | 2.45 |
| 5 | 32 | 2.45 |
| 9 | 33 | 3 |

---

# Menentukan Nilai K

Misalkan digunakan **K = 3**.

Data terdekat:

| Data | Usia | Jarak |
|-----|------|------|
| 4 | 26 | 0 |
| 1 | 30 | 1 |
| 7 | 34 | 1 |

---

# Menghitung Estimasi Usia

Usia = (26 + 30 + 34) / 3  
Usia = 90 / 3  
Usia = 30  

---

# Hasil Imputasi Missing Value

Nilai **Usia pada data ke-10** adalah:

**Usia = 30**

---

# Data Setelah Perbaikan

| Data ke | Usia | Tingkat_Kepuasan | Status_Beasiswa | Program_Studi |
|--------|------|------------------|-----------------|---------------|
| 10 | 30 | Tinggi | Tidak | Teknik Informatika |