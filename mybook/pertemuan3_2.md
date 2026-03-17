# Distance in Student Data

**Perhitungan manual** menggunakan **2 mahasiswa dari dataset asli (baris pertama dan kedua dataset)**:

* Numerik → Normalisasi (range)
* Nominal → Simple Matching
* Ordinal → Ranking + Normalisasi
* Binary → Simple Matching

## **Data Dua Mahasiswa**

Diambil dari dataset yang dikirim:

| Atribut            | Mahasiswa 1 | Mahasiswa 2 |
|--------------------|------------|------------|
| ID                 | 1          | 2          |
| Usia               | 18         | 25         |
| Tingkat_Kepuasan   | Sedang     | Rendah     |
| Status_Beasiswa    | Tidak      | Ya         |
| Program_Studi      | Manajemen  | Sistem Informasi |

> Catatan: atribut **ID** hanya sebagai penanda data dan **tidak dihitung** dalam jarak.

## **Tentukan Rentang (Range) Numerik**

Dari dataset:

### Perhitungan Euclidean Distance

Rumus Euclidean Distance:

$$
d(x,y) = \sqrt{(x - y)^2}
$$

Untuk atribut **Usia**:

- Usia Mahasiswa 1 = 18  
- Usia Mahasiswa 2 = 25  

Perhitungan:

$$
d = \sqrt{(18 - 25)^2}
$$

$$
d = \sqrt{(-7)^2}
$$

$$
d = \sqrt{49}
$$

$$
d = 7
$$

Sehingga **jarak Euclidean untuk atribut usia adalah 7**.

![Foto Saya](images/euc1dan2.png)

## **Hitung Jarak Tiap Atribut**

### **A. Atribut Nominal (Simple Matching)**

#### **Program_Studi**

Berbeda → 1

### **B. Atribut Binary**

#### **Status_Beasiswa**

Berbeda (Tidak vs Ya) → 1

### **C. Atribut Ordinal**

#### **Konversi Ranking**

Tingkat_Kepuasan:

- Rendah = 1
- Sedang = 2
- Tinggi = 3

#### **Tingkat_Kepuasan**

Mahasiswa 1 = Sedang (2)  
Mahasiswa 2 = Rendah (1)  

Normalisasi:

$$
z = \frac{r - 1}{M - 1}
$$

Karena M = 3

Mahasiswa 1:

$$
(2 - 1)/(3 - 1) = 1/2 = 0.5
$$

Mahasiswa 2:

$$
(1 - 1)/(3 - 1) = 0/2 = 0.0
$$

Jarak:

$$
|0.5 - 0.0| = 0.5
$$

## **Hitung Total Jarak (Metode Campuran / Gower)**

Jumlah atribut yang dihitung = 4

$$
D = \frac{\text{Total seluruh jarak}}{4}
$$

#### **Total Seluruh Jarak**

$$
1.00 + 1 + 1 + 0.5 = 3.50
$$

#### **Hitung Nilai Akhir**

$$
D = \frac{3.50}{4}
$$

$$
D = 0.875
$$

## **Interpretasi**

Nilai dissimilarity:

$$
D = 0.875
$$

Karena nilainya **cukup tinggi**, maka kedua mahasiswa ini **cukup berbeda**.

Perbedaan terbesar terdapat pada:

- Usia
- Program Studi
- Status Beasiswa
- Tingkat Kepuasan

Artinya tingkat kemiripan keduanya relatif rendah berdasarkan atribut yang tersedia pada dataset.

## Implementasi Orange

![Foto Saya](images/visual.png)  

![Foto Saya](images/id1dan2.png)  

Perbedaan nilai jarak antara perhitungan manual dan hasil pada Orange dapat terjadi karena metode pengolahan atribut kategorikal bisa berbeda. Pada perhitungan manual di sini digunakan konsep **Gower Distance** untuk data campuran, sedangkan pada Orange hasil dapat dipengaruhi oleh proses transformasi data dan metrik jarak yang dipilih saat workflow dijalankan.