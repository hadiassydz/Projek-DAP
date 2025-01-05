# Analisis Data Groceries dengan "Association" Rules RStudio 
## Buat Rules dengan Apriori
Sekarang kita akan membuat rules menggunakan algoritma Apriori. Kita pake nilai support 0,01 dan confidence 0,25.

Oke, kita bahas sedikit kenapa milih nilai support dan confidence nya segitu?? :
- Support = 0.01 : kita tetap dapat menemukan item yang kurang populer tetapi mungkin memiliki hubungan menarik.
- Confidence = 0.25 : jika confidence terlalu tinggi (misalnya 0.8), hanya aturan sangat kuat yang akan muncul, dan bisa melewatkan pola menarik lainnya.

Nah "inspect" ini berfungsi buat menampilkan hasil dari objek association_rules.

```r
# Membuat Rules menggunakan algoritma Apriori
association_rules <- apriori(
  Groceries,
  parameter = list(support = 0.01, confidence = 0.25)
)
inspect(association_rules)
```

#### Output
Dari output berikut dapat dilihat jumlah rules yang dihasilkan, yaitu 171 rule beserta nilai support, confidence, coverage, lift, dan count.

<img src="../gambar/rules1.png" width="500">

## Eksperimen dengan nilai support & confidence lebih kecil
Kita bahas kenapa milih nilai support dan confidence nya segitu?? :
- Support = 0.005 : aturan dengan item yang jarang muncul (tapi mungkin menarik) tetap akan dipertimbangkan.
- Confidence = 0,2 : hubungan antara LHS dan RHS cukup lemah karena confidence-nya rendah.
  
```r
# Eksperimen dengan parameter support dan confidence yang lebih kecil
experiment_rules <- apriori(
  Groceries,
  parameter = list(support = 0.005, confidence = 0.2)
)
inspect(experiment_rules)
```

#### Output
Nah, kalo dari output eksperimen ini tuh beberapa ada rule yang punya nilai lif < 1, beda sama rule sebelumnya yang cuma menghasilkan 1 rule dengan lift < 1.

<img src="../gambar/eksperimen.png" width="500">
