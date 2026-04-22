# DESKRIPTIF DATA

## Contoh Implementasi Python

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
```

```python
Jumlah data      : 150
Rata-rata        : 5.843333333333334
Nilai minimum    : 4.3
Q1               : 5.1
Median (Q2)      : 5.8
Q3               : 6.4
Nilai maksimum   : 7.9
Modus            : 5.0
Frekuensi modus  : 10
Standar deviasi  : 0.828066127977863
Variansi         : 0.6856935123042507
```

```{admonition} Keterangan
- Jumlah data menunjukkan banyaknya sampel yang dianalisis.  
- Rata-rata (mean) merupakan nilai pemusatan data.  
- Nilai minimum dan maksimum menunjukkan rentang data.  
- Q1, Median (Q2), dan Q3 membagi data menjadi empat bagian sama besar.  
- Modus adalah nilai yang paling sering muncul dalam data.  
- Standar deviasi menunjukkan tingkat penyebaran data dari rata-rata.  
- Variansi merupakan kuadrat dari standar deviasi.  
```