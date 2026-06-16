# 🏠 Airbnb Seattle Investment Dashboard
> Proyek akhir dari seri tutorial Tableau — membangun dashboard analisis data untuk membantu investor menemukan peluang terbaik di pasar Airbnb Seattle.

---

## 📌 Deskripsi Proyek

Dashboard ini dibangun menggunakan **Tableau Public** dengan dataset Airbnb Seattle (2016). Tujuannya adalah menjawab pertanyaan seorang investor:

> *"Di mana saya harus membeli properti, kapan waktu terbaik menyewakannya, dan tipe properti apa yang paling menguntungkan?"*

---

## 📂 Dataset

**Sumber:** [Seattle Airbnb Open Data — Kaggle](https://www.kaggle.com/datasets/airbnb/seattle)

Dataset terdiri dari **3 tabel (CSV)** yang digabungkan menjadi satu Excel workbook:

| Tabel | Deskripsi |
|---|---|
| `listings` | Data properti: lokasi, tipe, jumlah kamar, harga per malam/minggu/bulan |
| `calendar` | Data ketersediaan & harga harian per listing (2016) |
| `reviews` | Ulasan tamu per listing |

> **Catatan:** Data dari tahun 2016. Untuk data terbaru, kunjungi [Inside Airbnb](http://insideairbnb.com/get-the-data/).

---

## 🔗 Cara Menghubungkan Data (JOIN)

Tabel dihubungkan di Tableau menggunakan **Inner Join** pada field berikut:

```
listings.id  →  calendar.listing_id
listings.id  →  reviews.listing_id
```

> ⚠️ **Penting:** Jangan gunakan field `id` di tabel `reviews` — itu adalah ID ulasan, bukan ID listing. Kesalahan join ini bisa mengurangi data dari 23 juta menjadi hanya 2.555 baris.

---

## 📊 Visualisasi yang Dibangun

### 1. Bar Chart — Harga per Zip Code
Menampilkan rata-rata harga per malam untuk setiap wilayah (zip code), diurutkan dari tertinggi ke terendah, dilengkapi warna unik per zip code.

**Insight:** Zip code `98134` memiliki rata-rata tertinggi di **$206/malam**.

---

### 2. Peta — Sebaran Lokasi & Harga
Visualisasi geografis semua zip code di Seattle dengan warna yang sinkron dengan bar chart, dilengkapi label harga rata-rata di tiap area.

**Insight:** Memudahkan investor melihat secara spasial area mana yang paling premium.

---

### 3. Time Series — Pendapatan per Minggu
Line chart dari data `calendar` yang menampilkan tren total pendapatan Airbnb per minggu sepanjang tahun 2016.

**Insight:**
- 📈 Puncak: **musim panas** dan **November–Desember** (liburan)
- 📉 Terendah: **Januari–Februari**

---

### 4. Bar Chart — Harga Rata-rata per Jumlah Kamar
Menampilkan hubungan antara jumlah kamar (`bedrooms`) dengan harga rata-rata per malam.

**Insight:** Properti dengan **5–6 kamar** menghasilkan harga per malam tertinggi, jauh di atas properti 1–2 kamar.

---

### 5. Bar Chart — Jumlah Listing per Jumlah Kamar
Menampilkan berapa banyak properti yang tersedia untuk tiap kategori jumlah kamar (tingkat kompetisi).

**Insight:**

| Jumlah Kamar | Jumlah Listing | Kompetisi |
|---|---|---|
| 1 kamar | 1.800+ | Sangat tinggi |
| 2 kamar | 783 | Tinggi |
| 3 kamar | 206 | Sedang |
| 4 kamar | 55 | Rendah |
| 5 kamar | 20 | Sangat rendah |
| 6 kamar | 5 | Minimal |

---

## 💡 Insight Kunci untuk Investor

| Aspek | Rekomendasi |
|---|---|
| 📍 **Lokasi terbaik** | Zip code `98134` — rata-rata $206/malam |
| 🗓️ **Waktu terbaik sewa** | Musim panas & November–Desember |
| 🏠 **Tipe properti ideal** | 5–6 kamar: harga tinggi + kompetisi rendah = ROI optimal |

---

## 🛠️ Tools & Teknologi

- **Tableau Public** — visualisasi & dashboard
- **Microsoft Excel** — penggabungan dataset CSV
- **Kaggle** — sumber dataset

---

## 📁 Struktur File

```
airbnb-tableau-project/
│
├── data/
│   └── airbnb_seattle_combined.xlsx   # Dataset gabungan (listings + calendar + reviews)
│
├── dashboard/
│   └── airbnb_dashboard.twbx          # File Tableau workbook
│
└── README.md
```

---

## 🚀 Cara Menjalankan

1. Download dataset dari link GitHub (tersedia di deskripsi video) atau dari [Kaggle](https://www.kaggle.com/datasets/airbnb/seattle).
2. Buka **Tableau Public** dan connect ke file `airbnb_seattle_combined.xlsx`.
3. Buat join antar tabel sesuai panduan di atas.
4. Ikuti langkah pembuatan visualisasi satu per satu.
5. Gabungkan semua sheet ke dalam satu **Dashboard**.

---

## 📝 Catatan Tambahan

- Dataset ini dari tahun **2016** — cocok untuk latihan, namun untuk analisis nyata gunakan data terbaru.
- Ada **30–40+ field** lain di dataset yang belum dieksplorasi, seperti: weekly price, monthly price, cleaning fee, review scores, dan lainnya.
- Proyek ini dapat dikembangkan lebih lanjut dengan menambahkan filter interaktif, analisis review bintang, atau perbandingan tipe properti.

---

## 🙌 Kredit

Proyek ini merupakan bagian dari **Tableau Tutorial Series** (video ke-5 dari 5). Dataset berasal dari Kaggle Seattle Airbnb Open Data.
