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
> Dataset yang digunakan adalah data data_startup_saas.csv yang berisi informasi yang dapat dimanfaatkan untuk analisis bisnis , antara lain pendapatan tahunan perusahaan dan biaya langganan layanan. Variabel kunci dalam dataset ini meliputi `Pendapatan_Tahunan_Miliar_IDR`, `variabel_B`, dan `variabel_C`. Tujuan dari proyek ini adalah untuk memahami karakteristik data melalui statistik deskriptif, menguji hubungan antara `variabel_A` dan `variabel_B` melalui analisis korelasi, serta memprediksi `variabel_C` menggunakan `variabel_A` sebagai prediktor melalui analisis regresi.

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
    [Histogram Pendapatan Tahunan](results/Histogram 2.png)
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

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
