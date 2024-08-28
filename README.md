# Tugas1-VDI RA-RESUME-121450101

# Teknik Visualisasi Data

## Ikhtisar
Dokumen ini merangkum artikel **"Making Data Visualization More Efficient and Effective: A Survey"** dan menawarkan contoh praktis menggunakan Altair/Vega-Lite untuk membuat visualisasi yang disesuaikan.

## 1. Ringkasan Artikel

Artikel berjudul "Making Data Visualization More Efficient and Effective: A Survey" membahas berbagai teknik yang digunakan untuk membuat visualisasi data menjadi lebih efisien dan efektif. Artikel ini mengidentifikasi tiga arah utama dalam pengembangan visualisasi data:

### 1.1 Spesifikasi Visualisasi

- **Bahasa Spesifikasi Visualisasi:**
  - Bahasa Level Rendah: Memerlukan pengguna untuk menentukan semua detail pemetaan.
  - Bahasa Level Tinggi: Menyederhanakan proses dengan menyembunyikan detail teknis.
- tujuan unguk membantu pengguna menentukan apa yang ingin divisualisasikan dengan cara yang lebih terstruktur.

### 1.2 Pendekatan Efisien untuk Visualisasi Data

Artikel ini membahas berbagai teknik untuk membuat proses visualisasi lebih efisien, seperti:
  - Menerjemahkan query visualisasi menjadi query SQL.
  - Menggunakan penyimpanan berbasis kolom untuk meningkatkan kinerja.
  - Menerapkan teknik prefetching dan prediksi untuk mempercepat eksplorasi visualisasi.
- Tujuan untuk Membuat proses visualisasi lebih efisien dan cepat.

### 1.3 Rekomendasi Visualisasi

- **Sistem Rekomendasi:**
  - Memberikan saran visualisasi yang relevan berdasarkan spesifikasi yang tidak lengkap atau perilaku dan preferensi pengguna dImana untuk mmbantu pengguna menentukan visualisasi yang tepat.

### Tinjauan Literatur

Artikel ini juga mencakup tinjauan terhadap literatur yang ada, menyoroti teknik-teknik yang digunakan dalam berbagai survei terkait visualisasi grafik, visualisasi data berdimensi tinggi, dan visualisasi data temporal. Melalui survei ini, artikel ini menyediakan panduan komprehensif tentang bagaimana visualisasi data dapat ditingkatkan dari segi efisiensi dan efektivitas.


## Menyesuaikan Visualisasi dengan Altair/Vega-Lite

### 2.1 Menyesuaikan Visualisasi
Secara default, Altair/Vega-Lite otomatis menetapkan beberapa properti visualisasi. Namun, Anda dapat menyesuaikan tampilan visualisasi dengan:

- Menentukan Judul Sumbu: Menggunakan atribut axis dari kelas channel.
- Mengubah Properti Skala: Menggunakan atribut scale.
- Menentukan Warna Tanda: Mengatur parameter color pada metode Chart.mark_* dengan string warna CSS yang valid.

- **Contoh Kode:**
  ```python
  import altair as alt
  import pandas as pd

  # DataFrame Contoh
  df = pd.DataFrame({
      'precip': [1, 2, 3, 4],
      'city': ['A', 'B', 'C', 'D']
  })

  # Grafik yang Disesuaikan
  chart = alt.Chart(df).mark_point(color='firebrick').encode(
    alt.X('precip', scale=alt.Scale(type='log'), axis=alt.Axis(title='Nilai Log-Scaled')),
    alt.Y('city', axis=alt.Axis(title='Kategori')),
  )

#### Hasil visualisasinya:
![Visualisasi Data](https://github.com/nadiaftryani/Tugas-1-VDI-RESUME/blob/main/visualization.png)


### 2.2. Multiple Views

- **Example Code:**
  ```python
  import altair as alt

  # Sample DataFrame
  cars = pd.DataFrame({'Year': [1970, 1972, 1974, 1976, 1978, 1980, 1982],'Miles_per_Gallon': [5, 10, 15, 20, 25, 30, 35]})

  # Line Chart
  line_chart = alt.Chart(cars).mark_line().encode(alt.X('Year'), alt.Y('average(Miles_per_Gallon)'))

  # Circle Mark for Each Data Point
  circle_mark = alt.Chart(cars).mark_circle().encode(alt.X('Year'), alt.Y('average(Miles_per_Gallon)'))

  # Combined View
  combined_chart = line_chart + circle_mark

Untuk menambahkan plot ini, kita mungkin ingin menambahkan tanda lingkaran untuk setiap titik data yang dirata-ratakan. (Tanda lingkaran hanyalah singkatan yang nyaman untuk tanda titik yang menggunakan lingkaran terisi.)

#### Hasil visualisasinya:
![Visualisasi Data 2](https://github.com/nadiaftryani/Tugas-1-VDI-RESUME/blob/main/visualization2.png)
