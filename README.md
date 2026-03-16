# Maven-Market-Dashboard
Dalam proyek ini, saya menjalankan serangkaian langkah penting dalam membangun dashboard Power BI.

# Tentang Proyek Ini

Analisis Performa Penjualan Maven Market

Proyek ini mengeksplorasi analisis performa penjualan "Maven Market". Tujuan utamanya adalah mendapatkan gambaran menyeluruh tentang kinerja bisnis "Maven Market" secara keseluruhan.

## Tujuan

Tujuan analisis ini adalah mengevaluasi efektivitas dashboard "Topline Performance" di Power BI. Dari sini, saya mengidentifikasi area yang perlu ditingkatkan agar dashboard mampu menghasilkan insight yang dapat dijadikan dasar pengambilan keputusan berbasis data.

## User Story

Sebagai Head of Business Strategy di Maven Market, saya perlu memahami performa penjualan perusahaan secara keseluruhan guna merumuskan strategi yang tepat dan mendorong pertumbuhan bisnis. Untuk itu, saya meminta data analis kami untuk menganalisis dashboard "Topline Performance".

## Komponen Dashboard

Dashboard yang ada saat ini mencakup komponen-komponen berikut:
- **Metrik Bulan Berjalan:** Transaksi, Profit, dan Return
- **Matriks Brand Produk:** Transaksi, Profit, Profit Margin, dan Return Rate per Brand
- **Tren Pendapatan**
- **Gauge Revenue Bulanan vs Target**
- **Peta Toko dengan Tooltip:** Transaksi, Profit, Biaya, Return, Revenue, Return Rate, Kuantitas Terjual, dan Kuantitas Dikembalikan per Toko
- **Area Heatmap dengan Tooltip:** Metrik yang sama dengan Peta Toko, dikelompokkan berdasarkan Area (Negara, Negara Bagian, Kota)

## Target Akhir

Di akhir proyek ini, saya bertujuan menghadirkan Maven Market Dashboard yang dapat mengoptimalkan performa penjualan dan mendorong pertumbuhan bisnis secara menyeluruh.

## Daftar Isi
- [Menghubungkan & Membentuk Data](#menghubungkan--membentuk-data)
- [Membuat Data Model](#membuat-data-model)
- [Menambahkan DAX Measures](#menambahkan-dax-measures)
- [Membangun Dashboard](#membangun-dashboard)
- [Dashboard Interaktif](#dashboard-interaktif)
- [Temuan](#temuan)
- [Insight & Solusi Bisnis](#insight-dan-solusi-bisnis)

---

# Menghubungkan & Membentuk Data

Saya membuat dan membentuk tabel-tabel berikut:
- [Tabel Customers](#tabel-customers)
- [Tabel Products](#tabel-products)
- [Tabel Stores](#tabel-stores)
- [Tabel Regions](#tabel-regions)
- [Tabel Calendar](#tabel-calendar)
- [Tabel Return_data](#tabel-return_data)
- [Tabel Transaction_data](#tabel-transaction_data)

### Tabel Customers
- Menamai tabel dengan "Customers" dan memastikan header sudah dipromosikan
- Memeriksa tipe data (catatan: "customer_id" harus bertipe whole number, sedangkan "customer_acct_num" dan "customer_postal_code" harus bertipe teks)
- Menambahkan kolom baru bernama "full_name" dengan menggabungkan kolom "first_name" dan "last_name", dipisahkan spasi
- Membuat kolom baru bernama "birth_year" untuk mengambil tahun dari kolom "birthdate", dan memformatnya sebagai teks
- Membuat kolom kondisional bernama "has_children" yang bernilai "N" jika "total_children" = 0, selain itu bernilai "Y"

![Load MavenMarket_Customers](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/f8798f97-4fd3-4f7d-8290-c0ba2a1d09ab)
![Customer_id, acct name, postal data type change](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/a2a4ca35-7b11-4e5a-b18a-c74ef91bf327)
![Create full_name Column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d05885ee-7d5d-41fd-9a70-67a57b05da15)
![full_name](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/72cd06a6-439e-4639-baa0-f35f06669841)
![Create birth_year Column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/29599955-ccaa-4d18-8196-09cd582527b0)
![birth_year](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/56073a34-8155-46d0-adc7-424620232315)
![has_children](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/92ae5105-851f-4096-8e0b-fff297ab8ade)
![has_children finish](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/f31a604b-b3b0-47a8-ac68-6d376a7e2a29)

### Tabel Products
- Menamai tabel dengan "Products" dan memastikan header sudah dipromosikan
- Memeriksa tipe data (catatan: "product_id" harus whole number, "product_sku" harus teks, "product_retail_price" dan "product_cost" harus decimal number)
- Menambahkan kolom kalkulasi bernama "discount_price" senilai 90% dari harga retail asli, memformatnya sebagai fixed decimal number, lalu membulatkan ke 2 desimal
- Mengganti nilai "null" dengan angka nol pada kolom "recyclable" dan "low-fat"

![Extract MavenProducts csv](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/3a7d2692-9ac8-4c31-b23c-c27c1465cc61)
![Create discount_price Column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/8018ab62-886c-4c4f-99a5-cdb613a277f3)
![discount_price](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/a2c51394-9439-4919-a97a-58a16069b980)
![recyclable](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d0101c90-d67c-4f34-9fdb-413496f92cb1)
![low_fat](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d2b59dad-9e5e-41c6-95a8-81187be52f35)
![recyclable and low_fat](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/cf2a83c2-0dbe-4217-a6e9-63d46dfb2633)

### Tabel Stores
- Menamai tabel dengan "Stores" dan memastikan header sudah dipromosikan
- Memeriksa tipe data (catatan: "store_id" dan "region_id" harus whole number)
- Menambahkan kolom kalkulasi bernama "full_address" dengan menggabungkan "store_city", "store_state", dan "store_country", dipisahkan koma dan spasi
- Menambahkan kolom kalkulasi bernama "area_code" dengan mengambil karakter sebelum tanda pisah ("-") pada kolom "store_phone"

![Exctract MavenMarketStore](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d58f53a5-c99d-4f80-8e57-006185623d1a)
![store_id region id whole number](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/00471fbf-3a00-4375-8c5d-f2d06106c652)
![add full_address column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/e7b5907c-906f-4a9d-8771-3b5883bb9909)
![full_address column](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/0258af18-9f03-4b8b-a40b-7e863fbfb1a5)
![Create area_code](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/acc3ad54-de94-47bc-b833-36f5addd03cf)
![area_code](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/598a21f8-203a-49ce-a28f-0676d26f2f24)

### Tabel Regions
- Menamai tabel dengan "Regions" dan memastikan header sudah dipromosikan
- Memeriksa tipe data (catatan: "region_id" harus whole number)

![Extract MavenRegions](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/881878ee-cc8a-46ca-b5e3-daf3c0ed520b)
![Regions](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/261c8b8e-a105-46f3-b3bf-5e04cfaec12c)

### Tabel Calendar
- Menamai tabel dengan "Calendar" dan memastikan header sudah dipromosikan
- Menggunakan fitur date tools di query editor untuk menambahkan kolom-kolom berikut: Start of Week (mulai Minggu), Name of Day, Start of Month, Name of Month, Quarter of Year, Year

![MavenCalender](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/d0d1b667-30e2-472b-a35f-450b25660406)
![Calender add column complete](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/a06f5a9e-7dc6-4bf5-8f2f-9909ef4d0cb1)

### Tabel Return_data
- Menamai tabel dengan "Return_Data" dan memastikan header sudah dipromosikan
- Memeriksa tipe data (semua kolom ID dan quantity harus whole number)

![Extract MavenReturns](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/7e5d0870-fcb8-4cf9-bcb7-9969a2a39689)
![return_data](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/1a9f5d85-67a3-4aa0-ad84-2093c14a300a)

### Tabel Transaction_data
- Membuat folder baru bernama "MavenMarket Transactions" yang berisi kedua file CSV "MavenMarket_Transactions_1997" dan "MavenMarket_Transactions_1998"
- Menghubungkan ke path folder tersebut
- Menggabungkan file-filenya, lalu menghapus kolom "Source.Name"
- Menamai tabel dengan "Transaction_data" dan memastikan header sudah dipromosikan
- Memeriksa tipe data (semua kolom ID dan quantity harus whole number)

![Create Mavenmarket_transaction](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/be2b22a3-d782-4224-bb37-8e67ab64f68a)
![Exctract MavenTransactions](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/7894896a-ed2d-42be-8907-7a4a194dc081)
![Combine maventransactions file](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/0d35632b-baf3-423e-870b-ce5c3ea23b47)
![pra delete source name](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/f51ea6d0-0dc7-4306-8571-ba721b4534fd)
![post source name](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/fa291896-6aba-4646-9a0c-34ec33268c10)

Untuk dua tabel data ("return_data" dan "transaction_data"), saya menonaktifkan opsi "Include in Report Refresh".

Proses Menghubungkan & Membentuk Data selesai.

---

# Membuat Data Model

**1. Di tampilan MODEL, saya menyusun tabel dengan lookup table di atas data table**

- Menghubungkan Transaction_Data ke Customers, Products, dan Stores menggunakan primary/foreign key yang sesuai
- Menghubungkan Transaction_Data ke Calendar menggunakan kedua field tanggal, dengan relasi "stock_date" yang dinonaktifkan (inactive)
- Menghubungkan Return_Data ke Products, Calendar, dan Stores menggunakan primary/foreign key yang sesuai
- Menghubungkan Stores ke Regions dalam skema "snowflake"

**2. Saya memastikan hal-hal berikut terpenuhi:**

- Semua relasi mengikuti kardinalitas one-to-many, dengan primary key (1) di sisi lookup table dan foreign key (*) di sisi data table
- Semua filter bersifat satu arah (tidak ada two-way filter)
- Filter context mengalir ke "downstream" dari lookup table ke data table
- Data table terhubung melalui shared lookup table (bukan langsung satu sama lain)

**3.** Menyembunyikan semua foreign key pada kedua data table dari Report View, serta "region_id" dari tabel Stores

**4. Di tampilan DATA, saya melakukan hal-hal berikut:**

- Memperbarui semua field tanggal (di semua tabel) ke format "M/d/yyyy" menggunakan fitur formatting di tab Modeling
- Memperbarui "product_retail_price", "product_cost", dan "discount_price" ke format Currency ($ English)
- Di tabel Customers, mengkategorikan "customer_city" sebagai City, "customer_postal_code" sebagai Postal Code, dan "customer_country" sebagai Country/Region
- Di tabel Stores, mengkategorikan "store_city" sebagai City, "store_state" sebagai State or Province, "store_country" sebagai Country/Region, dan "full_address" sebagai Address

![Creating Data Model Fix](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/5de3b2f1-d47f-435f-b91e-4b967393e3ac)

---

# Menambahkan DAX Measures

Silakan cek seluruh DAX yang telah saya buat di file Power BI ini. Pada bagian ini saya hanya menampilkan DAX measures yang digunakan di laporan dashboard, karena jika semuanya dimuat bagian ini akan sangat panjang. Berikut beberapa DAX measures yang saya gunakan:
```DAX
Last Month Transactions = CALCULATE([Total Transactions], PREVIOUSMONTH('Calendar'[date]))
```
```DAX
Total Transactions = COUNTROWS(Transaction_data)
```
```DAX
Last Month Profit = CALCULATE([Total Profit], PREVIOUSMONTH('Calendar'[date]))
```
```DAX
Total Profit = [Total Revenue] - [Total Cost]
```
```DAX
Last Month Returns = CALCULATE([Total Returns], PREVIOUSMONTH('Calendar'[date]))
```
```DAX
Total Returns = COUNTROWS(Return_data)
```
```DAX
Total Revenue = 
    SUMX(
        Transaction_Data,
        Transaction_Data[quantity] * RELATED(Products[product_retail_price])
    )
```
```DAX
Total Cost = 
    SUMX(
        Transaction_Data,
        Transaction_Data[quantity] * RELATED(Products[product_cost])
    )
```
```DAX
Return Rate = DIVIDE([Quantity Returned], [Quantity Sold], 0)
```
```DAX
Profit Margin = DIVIDE([Total Profit], [Total Revenue], 0)
```
```DAX
Average Transaction per Customer = 
DIVIDE(
    [Total Transactions], 
    [Total Customers]
)
```
```DAX
Average Revenue per Customer = 
DIVIDE(
    [Total Revenue], 
    [Total Customers]
)
```
```DAX
Total Customers = 
DISTINCTCOUNT(
    'Customers'[customer_id]
)
```
```DAX
Revenue Target = 
VAR PreviousMonthRevenue = [Last Month Revenue]
RETURN
    PreviousMonthRevenue * 1.05
```

---

## Membangun Dashboard
![image](https://github.com/Ruzsel/Maven-Market-Dashboard/assets/150054552/dcbe7605-e799-4096-aabc-c12e5a9f9948)

## Dashboard Interaktif
[Link Power BI](https://app.powerbi.com/view?r=eyJrIjoiNDY2ZWRjNTgtZjI2Ni00NmE0LTg1NTEtMjRmMjBjOWE3YzI3IiwidCI6IjUwODkxNmEwLTdiODktNDNhMS1hZjRlLTcyZmUxNWFiYTViOSIsImMiOjEwfQ%3D%3D)

---

# Temuan

## 1. Apa saja 10 produk teratas di setiap negara berdasarkan profit?

**USA:**

| Brand Produk | Total Transaksi | Total Profit | Profit Margin | Return Rate |
|---|---|---|---|---|
| Hermanos | 2.796 | $11.233 | 58,71% | 0,95% |
| Ebony | 2.657 | $10.224 | 59,84% | 0,78% |
| Tell Tale | 2.642 | $10.168 | 58,01% | 0,96% |
| Tri-State | 2.597 | $10.130 | 58,64% | 1,07% |
| High Top | 2.537 | $10.006 | 60,46% | 0,80% |
| Nationeel | 2.319 | $9.642 | 60,43% | 1,15% |
| Best Choice | 2.206 | $9.510 | 60,88% | 0,79% |
| Horatio | 2.124 | $8.911 | 58,35% | 1,44% |
| High Quality | 1.893 | $8.416 | 59,98% | 1,20% |
| Red Wing | 2.027 | $8.377 | 59,32% | 1,02% |

**Meksiko:**

| Brand Produk | Total Transaksi | Total Profit | Profit Margin | Return Rate |
|---|---|---|---|---|
| Hermanos | 2.096 | $8.622 | 58,53% | 0,98% |
| Ebony | 2.079 | $8.177 | 59,78% | 1,09% |
| Tri-State | 2.049 | $8.089 | 59,23% | 1,17% |
| Tell Tale | 2.036 | $8.088 | 58,11% | 1,01% |
| High Top | 1.954 | $7.993 | 60,31% | 1,20% |
| Nationeel | 1.710 | $7.301 | 60,42% | 1,19% |
| Best Choice | 1.657 | $7.244 | 60,35% | 0,75% |
| Horatio | 1.699 | $7.224 | 58,46% | 1,13% |
| Fast | 1.650 | $6.754 | 60,86% | 1,20% |
| Denny | 1.503 | $6.709 | 58,04% | 0,93% |

**Kanada:**

| Brand Produk | Total Transaksi | Total Profit | Profit Margin | Return Rate |
|---|---|---|---|---|
| Ebony | 502 | $1.953 | 59,80% | 1,32% |
| Hermanos | 450 | $1.898 | 58,75% | 0,79% |
| High Top | 449 | $1.811 | 60,76% | 1,34% |
| Tri-State | 453 | $1.760 | 58,99% | 0,98% |
| Tell Tale | 434 | $1.727 | 57,98% | 1,09% |
| Nationeel | 379 | $1.674 | 60,58% | 1,34% |
| Horatio | 372 | $1.601 | 58,56% | 0,85% |
| Best Choice | 355 | $1.601 | 60,53% | 1,15% |
| Big Time | 356 | $1.523 | 60,40% | 1,67% |
| High Quality | 320 | $1.485 | 60,47% | 1,34% |

---

## 2. Bagaimana gambaran total transaksi, total profit, profit margin, dan return rate di setiap negara?

| Negara | Total Transaksi | Total Profit | Profit Margin | Return Rate |
|---|---|---|---|---|
| USA | 93.986 | $365.665 | 59,68% | 0,97% |
| Meksiko | 72.806 | $285.687 | 59,65% | 1,02% |
| Kanada | 16.091 | $64.341 | 59,76% | 1,07% |

---

## 3. Bagaimana perbandingan transaksi, profit, dan return antara bulan ini dengan bulan sebelumnya di setiap negara?

| Negara | Transaksi Bulan Ini | Target | % Selisih | Profit Bulan Ini | Target | % Selisih | Return Bulan Ini | Target | % Selisih |
|---|---|---|---|---|---|---|---|---|---|
| USA | 9.516 | 10.094 | -5,73% | $36.909 | $39.438 | -6,41% | 256 | 268 | +4,48% |
| Meksiko | 7.350 | 5.727 | +28,34% | $28.976 | $22.306 | +29,9% | 198 | 155 | -27,74% |
| Kanada | 1.459 | 1.518 | -3,89% | $5.798 | $6.128 | -5,39% | 42 | 59 | +28,81% |

---

## 4. Toko mana yang memiliki performa terbaik di setiap negara?

**USA:**

| Kota Toko | Total Transaksi | Total Revenue | Total Biaya | Total Profit | Total Return | Return Rate | Qty Terjual | Qty Dikembalikan |
|---|---|---|---|---|---|---|---|---|
| Salem | 12.518 | $83.181 | $33.492 | $49.689 | 321 | 0,94% | 39.182 | 367 |

**Meksiko:**

| Kota Toko | Total Transaksi | Total Revenue | Total Biaya | Total Profit | Total Return | Return Rate | Qty Terjual | Qty Dikembalikan |
|---|---|---|---|---|---|---|---|---|
| Hidalgo | 110.798 | $44.692 | $44.692 | $66.106 | 491 | 1,08% | 52.888 | 572 |

**Kanada:**

| Kota Toko | Total Transaksi | Total Revenue | Total Biaya | Total Profit | Total Return | Return Rate | Qty Terjual | Qty Dikembalikan |
|---|---|---|---|---|---|---|---|---|
| Vancouver | 12.770 | $85.262 | $34.307 | $50.955 | 359 | 1,05% | 40.152 | 420 |

---

# Insight dan Solusi Bisnis

### USA
- **10 Produk Teratas Berdasarkan Profit:** Brand seperti Hermanos, Ebony, dan Tell Tale menunjukkan kinerja yang solid dalam menghasilkan profit tinggi dengan margin yang sehat dan return rate yang rendah. Strategi pemasaran dan penjualan perlu diperkuat untuk mempertahankan sekaligus meningkatkan penjualan produk-produk ini.

- **Perbandingan Kinerja Bulan Ini vs Bulan Lalu:** Meski volume transaksi dan profit bulan ini turun sekitar 6% dibanding bulan sebelumnya, return rate masih terjaga stabil. Ada peluang untuk memperkuat strategi pemasaran atau memberikan insentif kepada pelanggan agar transaksi dan profit kembali meningkat.

- **Toko Berperforma Terbaik:** Toko di Salem menunjukkan performa yang luar biasa dengan total transaksi tinggi, profit signifikan, dan return rate yang rendah. Menganalisis lebih mendalam strategi penjualan, lokasi toko, dan manajemen inventaris dapat memberikan pelajaran berharga untuk meningkatkan performa toko-toko lainnya.

### Meksiko
- **10 Produk Teratas Berdasarkan Profit:** Pola profit di Meksiko serupa dengan di AS, dengan brand Hermanos dan Ebony mendominasi. Perusahaan perlu terus memfokuskan diri pada produk-produk ini dan memperluas strategi pemasaran untuk memperbesar pangsa pasar.

- **Perbandingan Kinerja Bulan Ini vs Bulan Lalu:** Ada kenaikan signifikan pada volume transaksi dan profit bulan ini dibanding bulan sebelumnya, meski return rate mengalami penurunan. Kondisi ini mencerminkan potensi pertumbuhan yang cukup besar di pasar Meksiko.

- **Toko Berperforma Terbaik:** Toko di Hidalgo mencatat kinerja yang menonjol dengan volume transaksi tinggi dan profit yang signifikan. Menganalisis faktor-faktor yang mendorong performa toko ini dapat dimanfaatkan untuk mendongkrak kinerja toko-toko lain.

### Kanada
- **10 Produk Teratas Berdasarkan Profit:** Meski total transaksi Kanada lebih rendah dibanding AS dan Meksiko, pola profitnya tetap serupa, dengan brand Ebony dan Hermanos di posisi teratas. Perusahaan perlu terus memaksimalkan kedua brand ini untuk meningkatkan profitabilitas.

- **Perbandingan Kinerja Bulan Ini vs Bulan Lalu:** Volume transaksi dan profit bulan ini sedikit turun dibanding bulan sebelumnya. Namun, return rate justru menurun secara signifikan, yang mengindikasikan peningkatan kepuasan pelanggan atau pengelolaan retur yang semakin efisien.

- **Toko Berperforma Terbaik:** Toko di Vancouver menunjukkan kinerja yang baik dengan volume transaksi tinggi dan profit yang cukup signifikan. Faktor-faktor keberhasilan toko ini bisa dijadikan acuan untuk meningkatkan performa toko-toko lain di Kanada.

### Solusi Bisnis Umum
- **Meningkatkan Pemasaran dan Promosi:** Mengingat adanya penurunan transaksi di AS dan Kanada, ada peluang untuk mengintensifkan upaya pemasaran dan promosi guna menarik lebih banyak pelanggan dan mendorong penjualan.
- **Mengoptimalkan Manajemen Inventaris:** Menganalisis lebih lanjut pola penjualan dan permintaan dapat membantu mengoptimalkan manajemen inventaris, sehingga biaya dapat ditekan dan profitabilitas meningkat.
- **Meningkatkan Pengalaman Pelanggan:** Memfokuskan diri pada peningkatan pengalaman pelanggan dapat membantu mempertahankan pelanggan yang ada sekaligus menarik pelanggan baru. Langkah-langkah yang bisa dilakukan antara lain meningkatkan layanan pelanggan, membuat kebijakan retur yang lebih fleksibel, dan mengoptimalkan proses pembelian secara keseluruhan.
