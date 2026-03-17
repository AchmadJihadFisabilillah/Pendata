# Data Student

Dataset ini berisi data mahasiswa yang digunakan untuk merepresentasikan sebagian karakteristik akademik dan administratif mahasiswa dalam satu periode tertentu. Setiap baris merepresentasikan satu mahasiswa, sedangkan setiap kolom memuat atribut yang dapat digunakan untuk analisis deskriptif, eksplorasi data, maupun pemodelan sederhana.

Berdasarkan file dataset yang digunakan, data ini terdiri dari **50 mahasiswa** dengan **5 atribut**. Dataset memadukan **1 variabel numerik utama** dan **4 variabel kategorikal**, sehingga cocok untuk analisis data campuran, khususnya untuk melihat profil mahasiswa berdasarkan usia, tingkat kepuasan, status beasiswa, dan program studi.

Beberapa atribut yang terdapat dalam dataset ini antara lain:

- ID mahasiswa sebagai identitas unik
- Usia
- Tingkat kepuasan mahasiswa
- Status beasiswa
- Program studi

Variabel numerik dalam dataset ini meliputi **Usia**. Sementara itu, variabel kategorikal mencakup **Tingkat_Kepuasan**, **Status_Beasiswa**, dan **Program_Studi**. Kolom **ID** berfungsi sebagai penanda identitas unik dan tidak digunakan sebagai variabel analisis utama.

Dataset ini memungkinkan berbagai jenis analisis, seperti:

- Distribusi usia mahasiswa
- Komposisi mahasiswa berdasarkan program studi
- Perbandingan status beasiswa antar mahasiswa
- Analisis proporsi tingkat kepuasan mahasiswa

Karena tidak memiliki nilai kosong (*missing value*), dataset ini siap digunakan untuk analisis lebih lanjut maupun latihan pengolahan data.

```{code-cell} python
:tags: [hide-input]

import pandas as pd

df = pd.read_csv("dataset_mahasiswa_distance.csv")
df.head(20)
```

## Deskripsi Atribut

Berikut merupakan atribut/fitur yang terdapat dalam dataset mahasiswa:

| No | Atribut           | Deskripsi                                                |
| -- | ----------------- | -------------------------------------------------------- |
| 1  | ID                | Nomor identitas unik mahasiswa                           |
| 2  | Usia              | Usia mahasiswa (dalam tahun)                             |
| 3  | Tingkat_Kepuasan  | Tingkat kepuasan mahasiswa (Rendah, Sedang, Tinggi)      |
| 4  | Status_Beasiswa   | Status penerimaan beasiswa (Ya / Tidak)                  |
| 5  | Program_Studi     | Program studi/jurusan mahasiswa                          |

---

## Karakteristik Dataset

Dataset ini memiliki tipe data campuran (*mixed data*), yaitu:

* **Numerik**
  * Usia

* **Kategorikal Nominal**
  * ID
  * Status_Beasiswa
  * Program_Studi

* **Kategorikal Ordinal**
  * Tingkat_Kepuasan

---

## Informasi Umum Dataset

* **Jumlah Data (Baris)**: 50 mahasiswa
* **Jumlah Atribut (Kolom)**: 5 atribut
* **Jenis Data**: Campuran (Numerik dan Kategorikal)

---

## Statistik Deskriptif Singkat

## Variabel Numerik

| Atribut | Min | Max | Mean |
| ------- | --- | --- | ---- |
| Usia    | 18 | 25 | 21.50 |

## Variabel Kategorikal

### Tingkat_Kepuasan
- Rendah: 15
- Sedang: 19
- Tinggi: 16

### Status_Beasiswa
- Ya: 25
- Tidak: 25

### Program_Studi
- Akuntansi: 16
- Manajemen: 17
- Sistem Informasi: 17

---

## Missing Value

Berdasarkan pemeriksaan data:

* Tidak terdapat nilai kosong (*missing value*) pada seluruh atribut.
* Dataset dalam kondisi lengkap dan siap untuk analisis lebih lanjut.

---

## Outlier

* Pada variabel **Usia**, nilai berada dalam rentang **18–25** tahun, yang masih tergolong wajar untuk data mahasiswa.
* Dataset ini tidak menunjukkan nilai ekstrem yang mencolok berdasarkan pemeriksaan awal terhadap atribut numerik.

Secara umum, dataset ini tidak menunjukkan adanya outlier yang signifikan.

---