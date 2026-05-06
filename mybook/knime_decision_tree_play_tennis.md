# Panduan Lengkap Decision Tree di KNIME - Dataset Play Tennis

Dokumen ini menjelaskan langkah-langkah membuat model **Decision Tree** di KNIME menggunakan dataset **Play Tennis**.

Tujuan model: memprediksi kolom **`PlayTennis`** berdasarkan kondisi cuaca seperti **Outlook**, **Temperature**, **Humidity**, dan **Wind**.

---

## 1. Struktur Dataset

Dataset yang digunakan memiliki kolom berikut:

| Kolom | Keterangan | Digunakan untuk Model? |
|---|---|---|
| `Day` | ID atau penanda hari | Tidak |
| `Outlook` | Kondisi cuaca: Sunny, Overcast, Rain | Ya |
| `Temperature` | Suhu: Hot, Mild, Cool | Ya |
| `Humidity` | Kelembapan: High, Normal | Ya |
| `Wind` | Kondisi angin: True, False | Ya |
| `PlayTennis` | Target/class: Yes, No | Ya, sebagai target |

Kolom **`Day`** sebaiknya dihapus karena hanya berfungsi sebagai ID, bukan variabel prediksi.

---

## 2. Alur Workflow KNIME

Workflow akhir yang digunakan:

```text
CSV Reader
   ↓
Column Filter
   ↓
Table Partitioner
   ├── Output atas → Decision Tree Learner ┐
   └── Output bawah ───────────────────────→ Decision Tree Predictor
                                              ↓
                                            Scorer
```

Gambar workflow akhir:

![Workflow final KNIME](images/07_workflow_final.png)

---

## 3. Node 1 - CSV Reader

### Fungsi

Node **CSV Reader** digunakan untuk membaca file CSV ke dalam KNIME.

### Pengaturan

Pastikan data sudah terbaca menjadi beberapa kolom, bukan satu kolom panjang.

Pengaturan utama:

| Bagian | Nilai |
|---|---|
| File | `data_sampel_play_tennis_knime.csv` |
| Column delimiter | `,` |
| Has column header | Aktif |
| Row delimiter | Line break |

Gambar pengaturan CSV Reader:

![Pengaturan CSV Reader](images/01_csv_reader_settings.png)

### Hasil yang Benar

Preview harus menampilkan kolom seperti ini:

```text
Day | Outlook | Temperature | Humidity | Wind | PlayTennis
```

Jika semua data masuk ke satu kolom, berarti delimiter masih salah.

---

## 4. Node 2 - Column Filter

### Fungsi

Node **Column Filter** digunakan untuk menghapus kolom yang tidak diperlukan.

Dalam dataset ini, kolom yang dihapus adalah:

```text
Day
```

Karena `Day` hanya ID, maka tidak perlu dipakai untuk membuat model Decision Tree.

### Pengaturan

| Bagian | Nilai |
|---|---|
| Exclude | `Day` |
| Include | `Outlook`, `Temperature`, `Humidity`, `Wind`, `PlayTennis` |

Gambar ilustrasi pengaturan Column Filter:

![Pengaturan Column Filter](images/02_column_filter_settings.png)

### Output Setelah Column Filter

Kolom yang tersisa:

```text
Outlook | Temperature | Humidity | Wind | PlayTennis
```

---

## 5. Node 3 - Table Partitioner

### Fungsi

Node **Table Partitioner** digunakan untuk membagi data menjadi dua bagian:

1. **Training data** untuk melatih model.
2. **Testing data** untuk menguji model.

### Pengaturan

| Bagian | Nilai |
|---|---|
| First partition type | Relative (%) |
| Relative size | 70 |
| Sampling strategy | Random |
| Fixed random seed | Aktif |

Gambar pengaturan Table Partitioner:

![Pengaturan Table Partitioner](images/03_table_partitioner_settings.png)

### Arti Output

| Output | Fungsi |
|---|---|
| Output atas | 70% data training |
| Output bawah | 30% data testing |

Catatan: jika tersedia, **Stratified sampling** dengan kolom `PlayTennis` bisa digunakan agar jumlah data Yes dan No lebih seimbang di training dan testing.

---

## 6. Node 4 - Decision Tree Learner

### Fungsi

Node **Decision Tree Learner** digunakan untuk membangun model Decision Tree dari data training.

### Koneksi

Hubungkan:

```text
Output atas Table Partitioner → Decision Tree Learner
```

### Pengaturan

| Bagian | Nilai |
|---|---|
| Class column | `PlayTennis` |
| Quality measure | Gini index |
| Pruning method | No pruning |
| Reduced Error Pruning | Aktif |
| Min number records per node | 2 |

Gambar pengaturan Decision Tree Learner:

![Pengaturan Decision Tree Learner](images/04_decision_tree_learner_settings.png)

### Catatan

- **Class column** wajib diisi dengan `PlayTennis` karena itu adalah target yang ingin diprediksi.
- **Gini index** adalah ukuran yang umum digunakan pada Decision Tree.
- Jika tugas meminta metode entropy, ubah **Quality measure** ke pilihan yang berkaitan dengan **Information Gain** atau **Entropy**, jika tersedia di versi KNIME yang digunakan.

---

## 7. Melihat Hasil Pohon Keputusan

Setelah **Decision Tree Learner** berhasil dieksekusi, klik kanan node lalu pilih tampilan Decision Tree.

Contoh hasil pohon:

![Decision Tree View](images/05_decision_tree_view.png)

Dari contoh hasil tersebut, model membagi data berdasarkan kolom:

```text
Temperature
```

Aturan yang terbentuk:

| Kondisi | Prediksi |
|---|---|
| `Temperature = Hot` | `PlayTennis = No` |
| `Temperature = Mild` | `PlayTennis = Yes` |
| `Temperature = Cool` | `PlayTennis = Yes` |

Interpretasi:

- Jika suhu **Hot**, model memprediksi **No**.
- Jika suhu **Mild**, model memprediksi **Yes**.
- Jika suhu **Cool**, model memprediksi **Yes**.

---

## 8. Node 5 - Decision Tree Predictor

### Fungsi

Node **Decision Tree Predictor** digunakan untuk menerapkan model Decision Tree ke data testing.

### Koneksi

Node ini membutuhkan dua input:

```text
Decision Tree Learner → Decision Tree Predictor
Output bawah Table Partitioner → Decision Tree Predictor
```

Keterangan:

| Input | Sumber |
|---|---|
| Model input | Decision Tree Learner |
| Data input | Output bawah Table Partitioner |

### Pengaturan

Biasanya pengaturan default sudah cukup.

Output node ini akan menambahkan kolom baru, misalnya:

```text
Prediction (PlayTennis)
```

Gambar ilustrasi pengaturan Decision Tree Predictor:

![Pengaturan Decision Tree Predictor](images/06_decision_tree_predictor_settings.png)

---

## 9. Node 6 - Scorer

### Fungsi

Node **Scorer** digunakan untuk mengevaluasi hasil prediksi model.

Node ini membandingkan:

- Kolom aktual: `PlayTennis`
- Kolom prediksi: `Prediction (PlayTennis)`

### Koneksi

Hubungkan:

```text
Decision Tree Predictor → Scorer
```

### Pengaturan

| Bagian | Nilai |
|---|---|
| Actual class column | `PlayTennis` |
| Predicted class column | `Prediction (PlayTennis)` |

Gambar ilustrasi pengaturan Scorer:

![Pengaturan Scorer](images/08_scorer_settings.png)

### Output yang Dilihat

Setelah node Scorer dieksekusi, lihat:

1. **Confusion Matrix**
2. **Accuracy Statistics**

Confusion Matrix menunjukkan jumlah prediksi benar dan salah.

Accuracy menunjukkan persentase prediksi yang benar.

---

## 10. Urutan Eksekusi Node

Jalankan node secara berurutan:

```text
1. CSV Reader
2. Column Filter
3. Table Partitioner
4. Decision Tree Learner
5. Decision Tree Predictor
6. Scorer
```

Semua node yang berhasil dijalankan akan memiliki indikator lampu hijau.

---

## 11. Penjelasan Singkat Decision Tree

Decision Tree adalah metode klasifikasi yang membuat aturan keputusan dalam bentuk pohon.

Contoh aturan dari dataset Play Tennis:

```text
Jika Temperature = Hot  → PlayTennis = No
Jika Temperature = Mild → PlayTennis = Yes
Jika Temperature = Cool → PlayTennis = Yes
```

Kelebihan Decision Tree:

- Mudah dipahami.
- Hasilnya bisa dibaca sebagai aturan IF-THEN.
- Cocok untuk data kategori seperti dataset Play Tennis.

---

## 12. Masalah yang Sering Terjadi

### Masalah 1 - Data CSV Masuk ke Satu Kolom

Penyebab:

```text
Delimiter salah
```

Solusi:

Gunakan delimiter:

```text
,
```

Pastikan preview menampilkan kolom terpisah.

---

### Masalah 2 - Kolom PlayTennis Tidak Muncul di Decision Tree Learner

Penyebab:

- CSV belum terbaca dengan benar.
- Kolom `PlayTennis` tidak ada atau namanya berbeda.

Solusi:

- Cek lagi CSV Reader.
- Pastikan `Has column header` aktif.
- Pastikan kolom target bernama `PlayTennis`.

---

### Masalah 3 - Scorer Error

Penyebab:

Kolom aktual dan prediksi salah dipilih.

Solusi:

Gunakan:

```text
Actual column    : PlayTennis
Predicted column : Prediction (PlayTennis)
```

---

### Masalah 4 - Akurasi Berubah-ubah

Penyebab:

Dataset Play Tennis sangat kecil, sehingga pembagian training dan testing sangat memengaruhi hasil.

Solusi:

- Gunakan fixed random seed.
- Coba pembagian 70:30 atau 80:20.
- Jika perlu, gunakan cross validation.

---

## 13. Kesimpulan

Workflow Decision Tree untuk dataset Play Tennis sudah benar jika memenuhi syarat berikut:

| Bagian | Status yang Benar |
|---|---|
| CSV Reader | Kolom terbaca terpisah |
| Column Filter | Kolom `Day` dihapus |
| Table Partitioner | Data dibagi 70% training dan 30% testing |
| Decision Tree Learner | Class column = `PlayTennis` |
| Decision Tree Predictor | Menerima model dan data testing |
| Scorer | Membandingkan `PlayTennis` dan `Prediction (PlayTennis)` |

Dengan workflow ini, KNIME dapat membuat model Decision Tree dan menghitung performa prediksi menggunakan Scorer.
