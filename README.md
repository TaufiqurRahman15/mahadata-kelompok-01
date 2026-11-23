# mahadata-kelompok-01
Proyek End-to-End _ Analisis Harga Komoditas Lampung


# Analisis Data Besar Harga Komoditas Cabai dan Bawang di Provinsi Lampung Menggunakan Apache Spark

**Mata Kuliah:** Mahadata (`IF25-40402`) — Institut Teknologi Sumatera (ITERA)  
**Kelompok:** Kelompok 01  
**Anggota:**
1. Rizky Patriawan (`123140112`)
2. Ahmad Mulia Saputra (`123140168`)
3. Taufiqur Rahman (`123140007`)
4. Ilyas Ramadhan (`123140016`)

---

## Ringkasan Proyek
Proyek ini membangun *pipeline* analitik data besar *end-to-end* berbasis **Apache Spark** dan **Spark MLlib** untuk memprediksi harga harian ($t+1$) serta mendeteksi anomali fluktuasi harga pada 4 komoditas hortikultura utama di Provinsi Lampung (**Bawang Merah, Bawang Putih, Cabai Merah, dan Cabai Rawit**) berdasarkan data historis PIHPS Bank Indonesia (2017–2026).

Keluaran *Gold Layer* disimpan dalam format kolumnar **Apache Parquet** (`lampung_commodity_decisions.parquet`) dan disajikan melalui dasbor interaktif **Streamlit** yang mengklasifikasikan kondisi pasar ke dalam 4 level peringatan dini (**Hijau, Kuning, Merah, dan Biru**) beserta rekomendasi kebijakan bagi TPID, distributor, dan petani/Bulog.

---

## Struktur Repositori
```text
mahadata-kelompok-01/
├── data/
│   └── processed/
│       └── lampung_commodity_decisions.parquet   # Keluaran Gold Layer dari Apache Spark
├── notebooks/
│   └── EDA_Kelompok01.ipynb                      # Notebook eksplorasi, pembersihan, & pemodelan Colab
├── src/
│   ├── __init__.py
│   ├── spark_pipeline.py                         # Modul kelas LampungCommodityPipeline (PySpark)
│   └── utils.py                                  # Modul pembacaan Parquet & fallback dataset
├── app.py                                        # Aplikasi web dashboard interaktif Streamlit
├── requirements.txt                              # Daftar dependensi & versi lingkungan
└── README.md                                     # Dokumentasi proyek
```

---

## Versi Lingkungan
- **Python:** 3.14 (Lokal) / 3.12 (Google Colab)
- **Apache Spark / PySpark:** 4.0.5
- **Streamlit:** >= 1.35.0
- **NumPy, Pandas & PyArrow:** 2.5.5 / >= 2.2.3 / >= 18.0.0
- **Plotly:** >= 5.20.0

---

## Cara Menjalankan Dasbor Web Secara Lokal
1. **Clone repositori ini:**
   ```bash
   git clone https://github.com/TaufiqurRahman15/mahadata-kelompok-01.git
   cd mahadata-kelompok-01
   ```
2. **Install seluruh pustaka yang dibutuhkan:**
   ```bash
   pip install -r requirements.txt
   ```
3. *(Opsional)* Salin folder/file `lampung_commodity_decisions.parquet` hasil eksekusi notebook Google Colab ke dalam direktori `data/processed/`. (Jika belum ada, aplikasi otomatis menjalankan mode pratinjau dengan skema data identik).
4. **Jalankan server Streamlit:**
   ```bash
   streamlit run app.py
   ```
