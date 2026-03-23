# VISUALISASI DISTRIBUSI DATA
Visualisasi distribusi data adalah teknik grafis untuk menunjukkan bagaimana nilai-nilai dalam kumpulan data tersebar, mengelompok, atau membentuk pola tertentu (seperti Histogram, Boxplot atau Density plot).

## HISTOGRAM
Histogram digunakan untuk menampilkan distribusi frekuensi dari data numerik dengan membagi data ke dalam beberapa interval (bins). Visualisasi ini membantu memahami pola penyebaran data, seperti kecenderungan nilai, tingkat variasi, serta kemungkinan adanya nilai ekstrem (outlier).

Pada dataset Iris, histogram digunakan untuk melihat sebaran nilai pada setiap fitur sehingga memudahkan analisis awal sebelum dilakukan pengolahan data lebih lanjut.

```python
df.drop(columns=["species"]).hist(figsize=(10,8))
plt.tight_layout()
plt.show()
```

```{figure} image/histogram.png
---
width: 600px
align: center
---
```
## SCATTER
Scatter artinya menyebar atau tersebar.

```{admonition}Bisa berarti:
- Umum: sesuatu yang tersebar ke berbagai arah.  
- Statistik: grafik titik (scatter plot) untuk melihat hubungan dua data.  
- Game slot: simbol khusus untuk bonus atau free spin. 
```

```python
plt.figure(figsize=(8,5))
sns.scatterplot(data=df, x="petal_length", y="petal_width", hue="species")
plt.show()
```
```{figure} image/scatter.png
---
width: 600px
align: center
---
```
## HEATMAP KORELASI
Heatmap korelasi adalah grafik berbentuk tabel berwarna yang menunjukkan tingkat hubungan (korelasi) antar variabel.  
Setiap kotak mewakili hubungan dua variabel.  
Warna menunjukkan kuat/lemahnya korelasi.   

```{admonition}Nilai korelasi biasanya dari -1 sampai 1:  
1 = hubungan sangat kuat positif  
-1 = hubungan sangat kuat negatif  
0 = tidak ada hubungan 

Digunakan untuk melihat pola hubungan data dengan cepat.
```

```python
plt.figure(figsize=(6,5))
sns.heatmap(df.drop(columns=["species"]).corr(), annot=True)
plt.show()
```

```{figure} image/heatmap.png
---
width: 600px
align: center
---
```

## visualisasi dari orange
```{figure} image/orange1.png
---
width: 600px
align: center
---
```

```{figure} image/orange2.png
---
width: 600px
align: center
---
```

