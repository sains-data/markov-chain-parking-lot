# Analisis Okupansi Tempat Parkir dengan Rantai Markov

## 📋 Gambaran Proyek

Proyek ini mengimplementasikan **model Rantai Markov** untuk menganalisis dan memprediksi pola okupansi tempat parkir. Dengan menganalisis data historis parkir, kita dapat menentukan probabilitas transisi antar berbagai state okupansi dan memprediksi ketersediaan parkir di masa depan.

**Kelompok:** Kelompok 13 RA  
**Tanggal:** November 2025

---

## 🎯 Tujuan

Memodelkan okupansi tempat parkir menggunakan teori Rantai Markov untuk:
- Menganalisis pola penggunaan parkir
- Memprediksi kondisi okupansi di masa depan
- Memahami dinamika transisi antar tingkat okupansi yang berbeda

---

## 📊 Definisi State

Okupansi tempat parkir dibagi menjadi 6 state diskrit berdasarkan jumlah tempat yang terisi:

| State | Rentang Okupansi | Deskripsi |
|-------|------------------|-----------|
| State 1 | 0 - 10 tempat   | Sangat Rendah |
| State 2 | 11 - 20 tempat  | Rendah |
| State 3 | 21 - 30 tempat  | Sedang-Rendah |
| State 4 | 31 - 40 tempat  | Sedang-Tinggi |
| State 5 | 41 - 50 tempat  | Tinggi |
| State 6 | 51 - 60 tempat  | Sangat Tinggi |

---

## 🔄 Matriks Transisi (P)

Berdasarkan analisis dataset, matriks probabilitas transisi antar state adalah:

| From    | State 3 | State 4 | State 5 |
|---------|--------:|--------:|--------:|
| State 3 |   0.000 |    0.50 |   0.500 |
| State 4 |   0.200 |    0.30 |   0.500 |
| State 5 |   0.125 |    0.75 |   0.125 |

**Interpretasi:**
- Dari **State 3** (21-30 tempat): probabilitas 50% untuk transisi ke State 4, 50% ke State 5
- Dari **State 4** (31-40 tempat): probabilitas 20% ke State 3, 30% tetap di State 4, 50% ke State 5
- Dari **State 5** (41-50 tempat): probabilitas 12.5% ke State 3, 75% ke State 4, 12.5% tetap di State 5

---

## 📈 Diagram Transisi State

Diagram berikut memvisualisasikan transisi antar state:

<img src="./graf.png" alt="Diagram Transisi State" width="600"/>

---

## 🛠️ Implementasi

Analisis diimplementasikan dalam R menggunakan:
- **Pemrosesan data:** `dplyr`, `tidyr`
- **Visualisasi:** `ggraph`, `igraph`, `tidyverse`
- **Analisis:** Kalkulasi Rantai Markov kustom termasuk P² (transisi 2 langkah)

### Fitur Utama:
1. **Import & Preprocessing Data:** Memuat dan membersihkan data okupansi parkir
2. **Klasifikasi State:** Mengkategorikan okupansi ke dalam state diskrit secara otomatis
3. **Kalkulasi Matriks Transisi:** Menghitung probabilitas transisi antar state
4. **Prediksi Multi-langkah:** Menghitung P² untuk probabilitas transisi 2 langkah
5. **Visualisasi:** Menghasilkan diagram transisi state

---

## 📂 Struktur Proyek

```
markov-chain-parking-lot/
│
├── code_R.Rmd              # File analisis R Markdown utama
├── dataset_13_RA.xlsx      # Dataset input
├── graf.png                # Diagram transisi state
├── README.md               # Dokumentasi proyek
└── outdate/                # Folder arsip
    ├── dataset/            # Dataset sebelumnya
    ├── markov.ipynb        # Versi Jupyter notebook
    └── referensi/          # Paper referensi
```

---

## 🚀 Cara Penggunaan

1. Buka `code_R.Rmd` di RStudio
2. Install package yang diperlukan (chunk kode pertama)
3. Muat dataset parkir Anda
4. Jalankan semua chunk untuk menghasilkan:
   - Matriks probabilitas transisi (P)
   - Matriks transisi 2 langkah (P²)
   - Diagram transisi state

---

## 📚 Dasar Matematis

**Sifat Markov:** State masa depan hanya bergantung pada state saat ini, tidak pada urutan kejadian yang mendahuluinya.

**Probabilitas Transisi:**
```
P(Xₙ₊₁ = j | Xₙ = i) = pᵢⱼ
```

**Transisi n-Langkah:**
```
P^n = P × P × ... × P (n kali)
```

---

## 👥 Kontributor

Kelompok 13 RA

---

## 📄 Lisensi

Proyek ini merupakan bagian dari tugas akademik.

---

## 📖 Referensi

Lihat folder `outdate/referensi/` untuk paper akademik tentang:
- Prediksi okupansi tempat parkir
- Aplikasi Rantai Markov dalam sistem lalu lintas
- Sistem multiagen kooperatif untuk parkir