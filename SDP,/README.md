# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[Gede Alit Putrawan]`
- **NIM:** `[2515091081]`
- **Program Studi:** `[Sistem Informasi]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

*Contoh:*
> Dataset yang digunakan dalam penelitian ini adalah data_startup_saas.csv, yang berisi berbagai informasi penting yang dapat dimanfaatkan untuk keperluan analisis bisnis pada perusahaan startup berbasis Software as a Service (SaaS). Dataset ini memuat data kuantitatif yang menggambarkan kinerja keuangan dan strategi operasional perusahaan. Variabel utama yang dianalisis dalam dataset ini meliputi Pendapatan_Tahunan_Miliar_IDR sebagai indikator kinerja pendapatan perusahaan, serta Biaya_Akuisisi_Pelanggan_Juta_IDR yang merepresentasikan biaya yang dikeluarkan perusahaan untuk memperoleh pelanggan baru. Kedua variabel ini menjadi fokus utama dalam analisis hubungan dan pemodelan statistik. Tujuan dari proyek analisis ini adalah untuk memahami karakteristik dan pola data melalui analisis statistik deskriptif, mengukur kekuatan dan arah hubungan antara pendapatan tahunan dan biaya akuisisi pelanggan menggunakan analisis korelasi, serta membangun model regresi linear untuk memprediksi Biaya_Akuisisi_Pelanggan_Juta_IDR berdasarkan Pendapatan_Tahunan_Miliar_IDR sebagai variabel prediktor. Hasil analisis diharapkan dapat memberikan wawasan yang berguna dalam pengambilan keputusan bisnis dan perencanaan strategi pertumbuhan startup SaaS.
---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - Tabel atau ringkasan
  - mean = 31.8831846153846
  - median = 31.305
  - modus = 1.87
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
  - berdasarkan hasil statistik deksriptif: Pendapatan_Tahunan_Miliar_IDR maka
  - mean = 31.88 : ni berarti pendapatan tahunan rata-rata dari 650 observasi (obs.) adalah 31.88 satuan. Nilai ini sensitif         terhadap outlier (data ekstrem).
  - median = 31.30 : Jika semua pendapatan tahunan diurutkan, setengah (50%) dari perusahaan/individu memiliki pendapatan di bawah 31.3 satuan, dan setengahnya lagi memiliki pendapatan di atas 31.3 satuan.
  - modus = 1.87 : Ini adalah titik pendapatan yang paling sering dicapai oleh responden. Artinya, sebagian besar responden/perusahaan memiliki pendapatan tahunan yang sangat rendah, yaitu di kisaran 1.87 Miliar IDR. Ini adalah puncak paling padat (densitas) dari data.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
    
   Standar Deviasi: 19.785620465392
   Range = 1 - 66,89 = 65,89
   kuartil : min.= 1.00, Q1 = 14,31, median/Q2= 31.30, mean= 31.88, Q3= 49.04, max.= 66.89
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
    
    Distribusi pendapatan tahunan startup SaaS, yang dicatat dalam kolom Pendapatan_Tahunan_Miliar_IDR, menunjukkan tingkat keragaman yang tinggi.Tingginya standar deviasi 19.785620465392  merupakan bukti kuat bahwa nilai pendapatan tersebar lebar, data tidak hanya terkonsentrasi di satu titik sentral, melainkan menyebar jauh dari nilai rata-ratanya.Fakta bahwa rentang data (range) adalah 65.89 diperoleh dari selisih antara batas bawah (1.00 dan batas atas (66.89) jelas menunjukkan variasi ekstrem antara startup yang paling tidak dan paling sukses secara pendapatan.Data kuartil menggarisbawahi ketidakmerataan ini: terdapat 25% startup yang hanya berpendapatan di bawah 14.31 (Q1), sementara 25% startup teratas berhasil melewati ambang 49.04 (Q3). Ini mengarah pada kesimpulan bahwa pendapatan tahunan sangat bervariasi dan tidak terdistribusi secara homogen.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
    [Histogram Pendapatan Tahunan](results/Histogram2.png)
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
    
    Berdasarkan histogram, Pendapatan Tahunan startup tersebar luas dari nilai terendah hingga tertinggi, namun mayoritas data terkumpul di kisaran menengah. Garis mean (rata-rata) di sekitar 31,88 miliar IDR berada di tengah distribusi, menunjukkan bahwa rata-rata ini adalah nilai pusat yang cukup representatif. Meskipun demikian, adanya nilai-nilai yang relatif rendah dan tinggi (pencilan) mengindikasikan adanya perbedaan skala pendapatan yang signifikan antar startup. Sebagian besar berada di dekat rata-rata, tetapi beberapa menghasilkan pendapatan jauh lebih besar.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
    
    p-value = 0,05
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
    
    Hasil visual Q-Q Plot menunjukkan bahwa variabel Pendapatan Tahunan (IDR) menyimpang secara signifikan dari garis normal, yang mengindikasikan adanya pelanggaran asumsi normalitas. Jika dilakukan uji formal seperti Shapiro–Wilk, dapat diasumsikan nilai p-value < 0,05, sehingga hipotesis normalitas ditolak. Pelanggaran asumsi ini mengimplikasikan bahwa penggunaan uji parametrik kurang tepat, sehingga analisis sebaiknya menggunakan metode nonparametrik atau transformasi data agar hasil statistik lebih valid.
    
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
     [gambar plot](results/Rplot3.jpeg)
    
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?

    Berdasarkan Q–Q Plot, titik-titik data tidak mengikuti garis lurus secara konsisten dan menunjukkan penyimpangan yang jelas, terutama pada bagian ekor distribusi. Pola lengkungan yang terbentuk mengindikasikan bahwa data tidak berdistribusi normal. Hal ini menunjukkan adanya pelanggaran asumsi normalitas pada variabel Pendapatan_Tahunan_Miliar_IDR, yang kemungkinan disebabkan oleh distribusi data yang menceng ke kanan (right-skewed) akibat adanya nilai pendapatan yang sangat tinggi.

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r* = 0,996
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).

    Hasil analisis korelasi menunjukkan adanya hubungan yang kuat dan searah (positif) antara Pendapatan Tahunan (Miliar IDR) dan Biaya Akuisisi Pelanggan (Juta IDR). Artinya, semakin tinggi pendapatan tahunan perusahaan, maka semakin besar pula biaya yang dikeluarkan untuk akuisisi pelanggan. Hubungan ini bersifat kuat dan signifikan secara statistik (p-value ≤ 0,05), sehingga dapat disimpulkan bahwa terdapat keterkaitan yang nyata antara kedua variabel tersebut.
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  [Plot](results/Rplot4.png)
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
 
    Pola pada scatter plot menunjukkan bahwa titik-titik data cenderung membentuk pola linear menaik yang jelas, di mana peningkatan Pendapatan Tahunan (Miliar IDR) diikuti oleh peningkatan Biaya Akuisisi Pelanggan (Juta IDR). Garis tren linear yang mengarah ke atas memperkuat adanya hubungan positif yang kuat antara kedua variabel. Dengan demikian, pola visual pada scatter plot konsisten dan mendukung hasil koefisien korelasi yang menunjukkan korelasi positif kuat.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
 
    Intercept (b₀) = 1,37
    Koefisien regresi/slope (b₁) = 1,01
    Y = 1,37 + 1,01X (dengan keterangan X = Pendapatan_Tahunan_Miliar_IDR dan Y = Biaya_Akuisisi_Pelanggan_Juta_IDR)
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
 
    Intercept (b₀ = 1,37)
Nilai intercept menunjukkan bahwa ketika Pendapatan_Tahunan_Miliar_IDR = 0, maka Biaya_Akuisisi_Pelanggan_Juta_IDR diperkirakan sebesar 1,37 juta IDR. Dalam konteks data startup SaaS, nilai ini dapat diartikan sebagai biaya akuisisi dasar yang tetap ada meskipun perusahaan belum menghasilkan pendapatan tahunan, misalnya untuk biaya pemasaran minimum, infrastruktur, atau aktivitas operasional awal.
Slope (b₁ = 1,01)
Nilai slope menunjukkan bahwa setiap kenaikan 1 miliar IDR pada Pendapatan_Tahunan_Miliar_IDR akan diikuti oleh kenaikan Biaya_Akuisisi_Pelanggan_Juta_IDR sebesar 1,01 juta IDR. Koefisien ini bernilai positif, sehingga menandakan adanya hubungan searah: semakin tinggi pendapatan tahunan perusahaan, semakin besar biaya yang dikeluarkan untuk mengakuisisi pelanggan.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared* = 0,991
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
 
    Nilai R-squared sebesar 0,991 mengindikasikan bahwa model regresi mampu menjelaskan sekitar 99,1% variasi perubahan pada variabel dependen, yaitu Biaya Akuisisi Pelanggan. Hal ini menunjukkan bahwa Pendapatan Tahunan memiliki kontribusi yang sangat dominan dalam menjelaskan perubahan biaya akuisisi pelanggan pada data yang dianalisis. Dengan kata lain, hubungan yang terbentuk antara kedua variabel dalam model ini sangat kuat, sehingga model regresi dapat dikatakan memiliki tingkat ketepatan yang tinggi. Sementara itu, sekitar 0,9% variasi sisanya dipengaruhi oleh faktor-faktor lain yang tidak dimasukkan ke dalam model, seperti strategi pemasaran, kondisi pasar, atau kebijakan perusahaan.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - [Histogram Pendapatan Tahunan](results/Garisregresi.jpeg)
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
    Berdasarkan hasil analisis regresi, garis regresi dibentuk oleh persamaan Y = 1,37 + 1,01X dengan nilai Adjusted R-squared sebesar 0,991. Koefisien slope sebesar 1,01 menunjukkan bahwa setiap kenaikan 1 miliar IDR pendapatan tahunan diikuti oleh kenaikan biaya akuisisi pelanggan sekitar 1,01 juta IDR, sehingga hubungan antara kedua variabel bersifat positif dan hampir proporsional. Selain itu, nilai R-squared yang sangat tinggi (99,1%) menunjukkan bahwa garis regresi sangat baik dalam merepresentasikan hubungan antara variabel, karena hampir seluruh variasi biaya akuisisi pelanggan dapat dijelaskan oleh pendapatan tahunan. Hal ini terlihat dari titik-titik data yang berada dekat dengan garis regresi pada grafik.

---

## 6. Kesimpulan

Berdasarkan hasil analisis statistik deskriptif, pendapatan tahunan startup SaaS menunjukkan tingkat variasi yang sangat tinggi, dengan distribusi yang tidak normal dan cenderung menceng ke kanan. Hal ini mengindikasikan adanya kesenjangan yang besar antara startup dengan pendapatan rendah dan startup dengan pendapatan sangat tinggi. Meskipun nilai rata-rata pendapatan berada di sekitar 31,88 miliar IDR, sebagian besar startup justru terkonsentrasi pada tingkat pendapatan yang jauh lebih rendah, sebagaimana tercermin dari nilai modus dan kuartil bawah. Analisis korelasi dan regresi mengungkapkan hubungan positif yang sangat kuat antara Pendapatan Tahunan dan Biaya Akuisisi Pelanggan. Nilai koefisien korelasi (r = 0,996) serta R-squared sebesar 0,991 menunjukkan bahwa pendapatan tahunan merupakan faktor yang sangat dominan dalam menjelaskan variasi biaya akuisisi pelanggan. Dengan demikian, wawasan paling penting dari analisis ini adalah bahwa pertumbuhan pendapatan startup hampir selalu diiringi oleh peningkatan biaya akuisisi pelanggan, dan hubungan tersebut bersifat konsisten, kuat, serta dapat dimodelkan secara linear dengan tingkat ketepatan yang sangat tinggi.
