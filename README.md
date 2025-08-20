# TechnicalTest-DataAnalyst-MandiriSekuritas

# 📌 User Behavior Analysis Dashboard

## 📖 Deskripsi
Project ini menganalisis perilaku pengguna berdasarkan data **users**, **cards**, dan **transactions**.  
Dataset transaksi mencakup periode **2010–2019** (13 juta+ baris, dibagi menjadi 27 file). Data transaksi dibagi menjadi beberapa part karena di dalam Google BigQuery hanya bisa upload file maksimal sebesar 100 mb.  
Data dibersihkan menggunakan Python (Colab) lalu diunggah ke **Google BigQuery**.  
Dashboard interaktif kemudian dibuat di **Looker Studio** dengan filter tahun, KPI Cards, dan grafik.

---

## 🛠️ Tools yang Digunakan
- **Google Colab (Python + Pandas)** → data cleaning & preprocessing  
- **Google BigQuery** → penyimpanan data & query SQL  
- **Looker Studio** → dashboard visualisasi  

---

## ⚡ Langkah Menjalankan

### 1. Persiapan Data
- Bersihkan data menggunakan script Python (`cleaning_data.ipynb`).  
- Simpan hasil cleaning dalam CSV part (≤100MB per file).  
- Upload semua file ke **Google BigQuery** menggunakan wildcard (`transactions_part*`) agar terbaca sebagai satu tabel.  
- Buat tabel tambahan untuk `users_data` dan `cards_data`.

### 2. Buat Summary Tables di BigQuery
Jalankan query di file `SQL Queries` untuk membuat summary tables:

- **`transactions_summary`** → Ringkasan transaksi bulanan + KPI Cards  
- **`transactions_per_gender`** → Total transaksi berdasarkan gender  
- **`top_merchant_states`** → Top 10 merchant states berdasarkan transaksi  
- **`avg_spend_per_creditscore`** → Average spend per user berdasarkan credit score group  
- **`transactions_by_cardtype`** → Tren transaksi bulanan per tipe kartu  
- **`avgspend_by_agegroup`** → Average spend per user berdasarkan kelompok umur  

### 3. Hubungkan ke Looker Studio
- Tambahkan data source BigQuery ke Looker Studio.  
- Hubungkan tabel hasil query summary (bukan tabel mentah).  
- Tambahkan filter tahun (2010–2019).  
- Buat dashboard dengan KPI Cards + grafik.  

---

## 📊 Komponen Dashboard
- **KPI Cards**  
- Total Users  
- Total Transactions  
- Total Transaction Amount  
- Average Transaction Amount  
- Success Rate (%)  

- **Charts**  
- Monthly Transactions by Card Type  
- Average Spend per User by Credit Score Group  
- Top 10 Merchant States by Transactions  
- Transactions per Gender  
- Average Spend per User by Age Group  

---

## 🚀 Cara Replikasi
1. Clone repo ini  
2. Jalankan notebook cleaning di `/notebooks/cleaning_data.ipynb`  
3. Upload hasil CSV ke BigQuery  
4. Jalankan query di `SQL Queries` untuk membangun summary tables  
5. Buat dashboard di Looker Studio dengan menghubungkan tabel hasil query  
