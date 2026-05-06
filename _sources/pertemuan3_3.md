# Prediksi Nilai Usia yang Hilang Menggunakan KNN

Contoh ini menunjukkan cara menentukan **nilai usia yang hilang pada
data ke‑10** menggunakan metode **K‑Nearest Neighbor (KNN)**.

Atribut pada dataset:

-   Usia
-   Tingkat_Kepuasan
-   Status_Beasiswa
-   Program_Studi

Untuk memprediksi **Usia**, atribut pembanding yang digunakan:

-   Tingkat_Kepuasan
-   Status_Beasiswa
-   Program_Studi

------------------------------------------------------------------------

# Data Mahasiswa

## Data ke-10 (Usia Hilang)

| Data ke | Usia | Tingkat_Kepuasan | Status_Beasiswa | Program_Studi |
|--------|------|------------------|-----------------|---------------|
| 10 | ? | Sedang | Ya | Manajemen |

---

## Data Pembanding (1–9)

| Data ke | Usia | Tingkat_Kepuasan | Status_Beasiswa | Program_Studi |
|--------|------|------------------|-----------------|---------------|
| 1 | 18 | Sedang | Tidak | Manajemen |
| 2 | 25 | Rendah | Ya | Sistem Informasi |
| 3 | 20 | Tinggi | Tidak | Akuntansi |
| 4 | 21 | Sedang | Ya | Manajemen |
| 5 | 19 | Rendah | Tidak | Sistem Informasi |
| 6 | 22 | Tinggi | Ya | Akuntansi |
| 7 | 23 | Tinggi | Tidak | Manajemen |
| 8 | 24 | Sedang | Ya | Sistem Informasi |
| 9 | 20 | Rendah | Tidak | Akuntansi |

# Rumus Jarak (Simple Matching)

Untuk atribut kategorikal digunakan **Simple Matching Distance**.

Jika atribut sama:

$$
d = 0
$$

Jika atribut berbeda:

$$
d = 1
$$

Total jarak dihitung dengan:

$$
d(i,j) = \sum_{k=1}^{n} \delta(x_{ik}, x_{jk})
$$

dengan:

-   $x_{ik}$ = nilai atribut ke‑k pada data i\
-   $x_{jk}$ = nilai atribut ke‑k pada data j

------------------------------------------------------------------------

# Perhitungan Jarak

### Data 1 ke Data 10

Sedang = Sedang → 0\
Tidak ≠ Ya → 1\
Manajemen = Manajemen → 0

$$
d(1,10) = 0 + 1 + 0 = 1
$$

------------------------------------------------------------------------

### Data 2 ke Data 10

Rendah ≠ Sedang → 1\
Ya = Ya → 0\
Sistem Informasi ≠ Manajemen → 1

$$
d(2,10) = 1 + 0 + 1 = 2
$$

------------------------------------------------------------------------

### Data 3 ke Data 10

Tinggi ≠ Sedang → 1\
Tidak ≠ Ya → 1\
Akuntansi ≠ Manajemen → 1

$$
d(3,10) = 1 + 1 + 1 = 3
$$

------------------------------------------------------------------------

### Data 4 ke Data 10

Sedang = Sedang → 0\
Ya = Ya → 0\
Manajemen = Manajemen → 0

$$
d(4,10) = 0 + 0 + 0 = 0
$$

------------------------------------------------------------------------

### Data 5 ke Data 10

$$
d(5,10) = 1 + 1 + 1 = 3
$$

------------------------------------------------------------------------

### Data 6 ke Data 10

$$
d(6,10) = 1 + 0 + 1 = 2
$$

------------------------------------------------------------------------

### Data 7 ke Data 10

$$
d(7,10) = 1 + 1 + 0 = 2
$$

------------------------------------------------------------------------

### Data 8 ke Data 10

$$
d(8,10) = 0 + 0 + 1 = 1
$$

------------------------------------------------------------------------

### Data 9 ke Data 10

$$
d(9,10) = 1 + 1 + 1 = 3
$$

------------------------------------------------------------------------

# Tabel Hasil Jarak
## Tabel Hasil Jarak

| Data ke | Usia | Jarak |
|--------|------|------|
| 1 | 18 | 1 |
| 2 | 25 | 2 |
| 3 | 20 | 3 |
| 4 | 21 | 0 |
| 5 | 19 | 3 |
| 6 | 22 | 2 |
| 7 | 23 | 2 |
| 8 | 24 | 1 |
| 9 | 20 | 3 |

------------------------------------------------------------------------

# Menentukan Nilai K

Misalkan:

$$
K = 3
$$

Tetangga terdekat:
## Tetangga Terdekat (K = 3)

| Data | Usia |
|------|------|
| 4 | 21 |
| 1 | 18 |
| 8 | 24 |

------------------------------------------------------------------------

# Prediksi Nilai Usia

Karena **Usia adalah atribut numerik**, maka digunakan **rata‑rata**.

$$
Usia_{prediksi} = \frac{21 + 18 + 24}{3}
$$

$$
Usia_{prediksi} = \frac{63}{3}
$$

$$
Usia_{prediksi} = 21
$$

------------------------------------------------------------------------

# Kesimpulan

Berdasarkan metode **K‑Nearest Neighbor (KNN)** dengan **K = 3**, maka
nilai **Usia pada data ke‑10 diprediksi sebesar 21 tahun**. 