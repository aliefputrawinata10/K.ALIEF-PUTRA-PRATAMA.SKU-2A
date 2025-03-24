# K.ALIEF-PUTRA-PRATAMA.SKU-2A

Nama : K.Alief Putra Pratam Winata

Nim  : 09011382429167

Kelas : SKU.2A


## 1. Jelaskan struktur antar hubungan dan beri contohnya ?
jawaban : Struktur Antar Hubungan (Interconnection Structure) Secara Detail
Struktur antar hubungan merujuk pada infrastruktur yang memungkinkan komunikasi dan pertukaran data antara berbagai komponen dalam sistem komputer.berikut contoh nya:

# a. Bus Structure (Struktur Bus) 

Definisi: Saluran komunikasi bersama yang menghubungkan beberapa perangkat, memungkinkan mereka berbagi sumber daya dan bertukar data.
Karakteristik:

Terdiri dari saluran data, alamat, dan kontrol
Menggunakan protokol arbitrasi untuk menghindari konflik
Hanya satu perangkat yang dapat mentransmisikan data pada satu waktu


Contoh Konkret:

Front Side Bus (FSB) yang menghubungkan CPU dengan northbridge pada arsitektur lama
PCI/PCI-X bus yang menghubungkan perangkat peripheral
USB bus yang menghubungkan perangkat eksternal



# b. Point-to-Point Connection

Definisi: Koneksi langsung dan eksklusif antara dua komponen.
Karakteristik:

Bandwidth tinggi dan latensi rendah
Tidak memerlukan arbitrasi
Tidak ada konflik dengan perangkat lain


Contoh Konkret:

QPI (QuickPath Interconnect) untuk komunikasi prosesor Intel
HyperTransport untuk koneksi CPU-ke-CPU pada arsitektur AMD
NVLink antara GPU NVIDIA untuk komunikasi high-speed
Koneksi SATA antara hard disk dan controller



# c. Crossbar Switch

Definisi: Struktur interconnect yang memungkinkan beberapa koneksi simultan antara input dan output.
Karakteristik:

Mendukung multiple simultaneous connections
Lebih kompleks dan mahal dibanding bus
Skalabilitas tinggi tanpa degradasi performa signifikan


Contoh Konkret:

Network-on-Chip (NoC) dalam System-on-Chip modern
Switch fabric dalam supercomputer
Crossbar dalam router jaringan high-end

# d. Hierarchical Bus Structure

Definisi: Sistem yang menggunakan beberapa bus dengan tingkat hierarki berbeda.
Karakteristik:

Bus yang lebih cepat untuk komponen performa tinggi
Bus yang lebih lambat untuk perangkat I/O
Bridge untuk menghubungkan bus-bus berbeda


Contoh Konkret:

Arsitektur PC dengan bus CPU lokal, bus memori, dan bus I/O yang dihubungkan melalui bridge
Arsitektur mikroprosesor modern dengan cache hierarchy

# 2. Bila terlalu banyak modul atau perangkat dihubungkan pada bus maka akan terjadi penurunan kinerja, sebutkan penyebabnya?

jawaban: Penyebab Penurunan Kinerja pada Bus
Ketika terlalu banyak modul atau perangkat dihubungkan pada bus, penurunan kinerja terjadi karena:

# a. Kapasitansi Elektrik dan Efek Listrik

Beban Kapasitif: Setiap perangkat yang terhubung ke bus menambahkan beban kapasitif, yang memperlambat rise dan fall time sinyal.
Impedansi: Impedansi karakteristik bus berubah saat lebih banyak perangkat dihubungkan, menyebabkan refleksi sinyal dan gangguan.
Daya dan Panas: Lebih banyak perangkat berarti konsumsi daya lebih tinggi, yang dapat menyebabkan pemanasan dan kemungkinan kegagalan sinyal.

# b. Konkurensi dan Arbitrasi

Peningkatan Waktu Arbitrasi: Semakin banyak perangkat yang bersaing untuk akses bus, semakin kompleks dan lama proses arbitrasi.
Latensi Bus: Waktu tunggu meningkat karena ada lebih banyak permintaan yang harus dilayani dengan bandwidth tetap.
Siklus Bus yang Terbuang: Lebih banyak siklus bus terbuang untuk protokol arbitrasi dan penyelesaian konflik.

# c. Batasan Fisik

Propagation Delay: Jarak fisik yang lebih panjang menyebabkan sinyal membutuhkan waktu lebih lama untuk merambat.
Crosstalk: Interferensi elektromagnetik antara sinyal pada jalur yang berdekatan, meningkat dengan densitas perangkat yang tinggi.
Clock Skew: Perbedaan waktu kedatangan sinyal clock di berbagai titik bus, yang dapat menyebabkan kesalahan timing.

# d. Bandwidth Sharing dan Congestion

Resource Contention: Perangkat bersaing untuk bandwidth terbatas, menyebabkan bottleneck.
Inefficient Use: Bus yang dibagi seringkali tidak digunakan secara optimal karena protokol komunikasi dan overhead.
Queueing Delays: Permintaan akses tertunda dalam antrian, menyebabkan latensi tambahan.

#  3. Umumnya perangkat berprioritas paling rendah memiliki waktu tunggu rata-rata yang paling singkat. Dengan dasar ini biasanya CPU diberi perioritas tertinggi pada SBI. Sebutkan alasan perangkat berprioritas 16 memiliki waktu tunggu rata-rata paling rendah? Dibawah kondisi seperti apa keadaan diatas tidak berlaku?

jawaban:

# a. Alasan Perangkat Berprioritas 16 (Terendah) Memiliki Waktu Tunggu Rata-rata Paling Rendah

Frekuensi Akses: Perangkat berprioritas rendah umumnya memiliki frekuensi permintaan akses yang jauh lebih rendah dibandingkan perangkat berprioritas tinggi seperti CPU.
Pola Permintaan:

CPU (prioritas 1) memiliki pola permintaan yang sangat sering dan berulang (misalnya pengambilan instruksi, data, dan menulis hasil)
Perangkat I/O lambat (prioritas 16) mungkin hanya meminta akses sesekali untuk transfer data batch


Pengukuran Waktu Tunggu:

Waktu tunggu diukur hanya ketika perangkat benar-benar meminta akses, bukan total waktu
Perangkat berprioritas tinggi seperti CPU lebih sering menunggu karena lebih sering meminta akses


Matematis: Jika waktu tunggu rata-rata dihitung sebagai (Total waktu tunggu / Jumlah permintaan), perangkat yang jarang meminta akses memiliki pembagi yang lebih kecil, sehingga hasil rata-ratanya lebih rendah.

# b. Kondisi Di Mana Keadaan Ini Tidak Berlaku - Analisis Kasus

1. Pola Akses Berbeda

Bursty Traffic: Ketika perangkat berprioritas rendah membuat banyak permintaan dalam waktu singkat (burst), waktu tunggunya akan meningkat drastis karena selalu kalah prioritas.
Contoh Spesifik: Controller disk RAID yang mentransfer data dalam burst besar namun memiliki prioritas rendah.

2. Sistem Dengan Beban Tinggi

Near Saturation: Dalam sistem dengan utilisasi bus mendekati 100%, perangkat prioritas rendah mungkin mengalami "starvation" (kelaparan sumber daya).
Analisis Matematis: Pada kondisi saturasi, waktu tunggu perangkat prioritas rendah mendekati tak terhingga karena selalu diinterupsi oleh perangkat prioritas lebih tinggi.
Bukti Empiris: Dalam pengukuran sistem real-time dengan beban tinggi, waktu tunggu perangkat prioritas 16 bisa meningkat eksponensial dibanding kondisi normal.

3. Algoritma Arbitrasi Alternatif

Round-Robin: Setiap perangkat diberi giliran akses bus secara berurutan, menghilangkan efek prioritas tetap.
Time-Sliced: Setiap perangkat diberi slot waktu tertentu, menghasilkan distribusi akses yang lebih merata.
Aging Mechanism: Prioritas perangkat dinaikkan sementara jika terlalu lama menunggu, mencegah starvation.
Fair Queuing: Permintaan diproses berdasarkan urutan kedatangan, mengabaikan prioritas tetap.

4. Perangkat Spesial dengan Kebutuhan Real-time

Perangkat Multimedia: Controller video atau audio streaming mungkin memiliki prioritas rendah tapi membutuhkan akses tepat waktu.
Hard Real-time Constraints: Beberapa perangkat berprioritas rendah mungkin memiliki deadline waktu yang ketat, membuat waktu tunggu panjang tidak dapat diterima.
Quality of Service (QoS): Sistem modern seringkali menerapkan mekanisme QoS yang memberi prioritas dinamis berdasarkan kebutuhan timing, bukan prioritas statis.
