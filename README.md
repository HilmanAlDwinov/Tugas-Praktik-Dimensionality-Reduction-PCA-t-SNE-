# 🍇 Dimensionality Reduction Analysis: PCA vs t-SNE

Repositori ini dibuat untuk memenuhi **Tugas Praktik Pertemuan 25 - Fundamen Sains Data (Kelas A)** mengenai implementasi dan analisis perbandingan metode reduksi dimensi menggunakan **Principal Component Analysis (PCA)** dan **t-Distributed Stochastic Neighbor Embedding (t-SNE)**.

---

## 👥 Anggota Kelompok
* Hilman Al Dwinov - 24523216

---

1. Deskripsi Kasus & Dataset

* **Kasus Penggunaan:** Eksplorasi Cluster dan Visualisasi Data Berdimensi Tinggi.
* **Dataset:** *Wine Dataset* (diambil secara otomatis via `sklearn.datasets`). Dataset ini terdiri dari **178 sampel** dengan **13 fitur kimia** hasil analisis laboratorium terhadap 3 jenis kultivar anggur (*Class 0, Class 1, dan Class 2*).
* **Masalah yang Dihadapi:** Sangat sulit bagi manusia untuk memvisualisasikan data dan melihat pola pengelompokan alami secara langsung dalam ruang berdimensi 13.
* **Mengapa Reduksi Dimensi Dibutuhkan:** Reduksi fitur ke dalam ruang 2 dimensi (2D) sangat diperlukan untuk membantu proses analisis visual (*Exploratory Data Analysis*) guna mengetahui apakah karakteristik kimia tersebut secara alami memisahkan ketiga jenis anggur secara signifikan sebelum dilanjutkan ke tahap pemodelan klasifikasi atau clustering.

---

2. Ringkasan Metode

### A. PCA (Principal Component Analysis)
PCA adalah teknik reduksi dimensi linier yang berfokus pada maksimisasi varians data. Metode ini bekerja dengan mencari arah vektor baru yang disebut *Principal Components* (PC) yang mampu menangkap penyebaran data terbesar dari ruang berdimensi tinggi ke dimensi rendah secara ortogonal.

### B. t-SNE (t-Distributed Stochastic Neighbor Embedding)
t-SNE adalah teknik reduksi dimensi non-linier probabilistik yang sangat andal untuk visualisasi data. Metode ini bekerja dengan mempertahankan struktur lokal data—artinya, objek yang serupa di ruang dimensi tinggi akan dipetakan sedekat mungkin di ruang dimensi rendah, sedangkan objek yang tidak mirip akan dipisahkan sejauh mungkin.

---

3. Analisis Hasil

### A. Makna Hasil PCA
PCA mentransformasikan 13 dimensi fitur asli menjadi 2 komponen linier baru (PC1 dan PC2) dengan mempertahankan **~55%** total varians seluruh data. Pada grafik PCA, terlihat bahwa `class_0` terpisah dengan sangat jelas di sebelah kanan. Namun, terdapat daerah *overlap* (tumpang tindih) yang cukup tipis antara `class_1` dan `class_2` di area tengah. Hal ini terjadi karena PCA berfokus mempertahankan varians global secara linier, sehingga detail hubungan non-linier yang rumit antar tetangga data bisa sedikit terabaikan.

### B. Pola Cluster t-SNE
Berbeda dengan PCA, t-SNE berhasil memetakan data ke dalam 3 kelompok cluster yang **sangat tegas dan terpisah secara eksklusif**. Batas antar klaster terlihat sangat kontras, dan tidak ditemukan adanya *overlap* antar kelas anggur. Pola ini membuktikan bahwa struktur kemiripan lokal (tetangga terdekat) pada dimensi tinggi berhasil dipertahankan dengan sangat baik di dimensi rendah melalui pendekatan non-linier.

---

4. Kesimpulan: Metode Mana yang Lebih Sesuai?

1. **Untuk Kasus Eksplorasi & Visualisasi Data (Kasus Saat Ini):** **t-SNE jauh lebih sesuai.** Alasannya, t-SNE mampu mengelompokkan data sejenis secara rapat dan memisahkan antar kelas secara bersih tanpa ambiguitas visual, sehingga mempermudah proses analisis klastering secara langsung.
2. **Untuk Kasus Preprocessing Sebelum Modeling ML (Opsi Lain):** Jika data ini nantinya digunakan untuk dilatih ke model *Machine Learning*, **PCA akan lebih cocok** karena komputasinya cepat, bersifat pasti (deterministik), dan mempertahankan struktur varians data global tanpa risiko *overfitting*.

---

5. Isi Repositori
* `Dimensionality_Reduction.ipynb` : Notebook Python berisi kode implementasi lengkap (Standardization, PCA, t-SNE, dan Visualisasi).
* `README.md` : Dokumentasi lengkap dan narasi analisis proyek.
