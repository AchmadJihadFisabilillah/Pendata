# PENDAHULUAN

Kumpulan data bunga Iris adalah kumpulan data multivariat yang diperkenalkan oleh ahli statistik dan biologi Inggris, Ronald Fisher, dalam makalahnya tahun 1936 yang berjudul *“The use of multiple measurements in taxonomic problems”*. Kumpulan data ini juga dikenal sebagai **Iris Anderson** karena Edgar Anderson mengumpulkan data tersebut untuk mengukur variasi morfologi bunga Iris dari tiga spesies yang berkerabat.

Dataset ini terdiri dari **150 sampel** (50 sampel per kelas) dari tiga spesies:
- Iris-setosa
- Iris-versicolor
- Iris-virginica

Empat fitur diukur dari setiap sampel (dalam cm): **sepal_length, sepal_width, petal_length, petal_width**.

# DESKRIPSI DATA SET
## 2.1 struktur data
```{admonition}Dataset terdiri dari:
Jumlah observasi: 150 data
Jumlah variabel: 5 kolom
4 variabel numerik:
- sepal_length
- sepal_width
- petal_length
- petal_width

1 variabel kategorikal:
species
```


## Menampilkan Data Iris

Berikut adalah 5 baris pertama dataset Iris.

```python
:class: hide-input

import pandas as pd

df = pd.read_csv("mybook/tugas_iris/data/IRIS.csv")
df.head()
```

```{figure} image/iris.png
---
width: 600px
align: center
---
```

## Verifikasi Data di Database (MySQL - Laragon)

Data berhasil dimasukkan ke dalam database `irisdb` dan tabel `iris`.

```sql
SELECT COUNT(*) FROM iris;
SELECT * FROM iris LIMIT 5;
```

```{figure} image/sql.png
---
width: 600px
align: center
---

- Screenshot phpMyAdmin hasil `SELECT COUNT(*)`
```