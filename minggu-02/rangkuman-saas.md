# LATIHAN 1
## Apa perbedaan antara IaaS, SaaS, dan Paas?
[Artikel 1 : perbedaan antara IaaS, SaaS, dan Paas](https://www.quora.com/What-is-the-difference-between-IaaS-SaaS-and-Paas)
##### Mari saya tunjukkan perbedaan antara IaaS, PaaS, dan SaaS dengan cara yang mudah dan dengan kata-kata sederhana:
### SaaS: Perangkat Lunak sebagai Layanan

##### Ini berarti menjalankan aplikasi di cloud publik. Pengguna menggunakan aplikasi ini melalui Internet. Aplikasi ini dikelola oleh Penyedia Layanan. Beberapa mis., Penyedia Layanan, adalah SalesForce, Microsoft (Office 365), Oracle, Google (Google Apps), dll.
##### Salesforce adalah perusahaan pertama yang mengubah dunia Saas, dan sejak saat itu, perusahaan lain telah melihat potensi di pasar ini dan meluncurkan aplikasi mereka.
### Iaas: Infrastruktur sebagai Layanan

##### Ini memberikan lingkungan bagi pengembang untuk membangun aplikasi yang dapat digunakan pengguna. IaaS meliputi:
1. Pengguna membuat mesin virtual (VM) sesuai permintaan.
2. Dari perpustakaan gambar VM.
### PaaS: Platform sebagai Layanan
##### Ini agak mirip dengan IaaS tetapi perbedaannya adalah:
1. Pengembang menyediakan aplikasi yang dijalankan platform.
2. Mereka tidak secara langsung membuat VM.

##### Jika Anda mempertimbangkan untuk mengalihkan bisnis e-commerce Anda ke cloud, berikut adalah model yang harus Anda perhitungkan:
+ IaaS
+ PaaS
+ SaaS

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-02/allvs.jpg)
##### Mereka adalah kategori inti dari komputasi awan. Model-model ini adalah cara untuk menggambarkan bagaimana Anda dapat menggunakan cloud untuk perusahaan Anda, yaitu hosting, menyimpan, mengelola, dan memproses data online.
##### Di sini Anda dapat melihat ringkasan fitur utama dari setiap kategori, di mana On-Premise adalah perangkat lunak yang diinstal di gedung yang sama dengan bisnis Anda.

##### ```IaaS (infrastruktur-sebagai-layanan)``` adalah yang termudah dari semua kategori. Ini mengacu pada layanan berbasis cloud, seperti penyimpanan pay-as-you-go, jaringan, dan virtualisasi. Model ini menyediakan teknologi dan ruang lingkup yang sama dengan pusat data tradisional. Perbedaannya adalah Anda tidak dapat memelihara atau mengelolanya secara fisik menggunakan solusi offline.
##### IaaS membantu perusahaan membuat dan mengelola data mereka saat mereka berskala, membayar ruang server yang mereka gunakan untuk mengembangkan perangkat keras atau perangkat lunak. Contoh paling umum adalah Amazon Web Services, Microsoft Azure, dll.

##### ```PaaS (platform-as-a-service)``` mengacu pada layanan platform berbasis cloud yang memberi para pengembang kerangka kerja yang dapat mereka gunakan untuk membuat aplikasi khusus. Model ini menyediakan programmer dengan platform yang digunakan untuk membuat perangkat lunak yang dikirimkan melalui Internet. Semua server, penyimpanan, dan jaringan dapat dikontrol oleh bisnis atau penyedia pihak ketiga.
##### PaaS membuat proses pengembangan, pengujian, dan penyebaran cepat, mudah, dan hemat biaya. Dibandingkan dengan SaaS, PaaS menyediakan platform untuk pembuatan perangkat lunak, bukan perangkat lunaknya. Contoh yang paling dikenal adalah Windows Azure, Google App Engine, dll.

##### ```SaaS (perangkat lunak sebagai layanan)``` adalah perangkat lunak berbasis cloud yang tersedia untuk pembelian secara berlangganan. Ini sebagian besar digunakan untuk aplikasi yang membutuhkan akses web dan seluler. Produk SaaS tidak perlu diunduh dan diinstal pada perangkat individu. Sebagian besar dapat dijalankan langsung dari browser web. Harus diperhitungkan bahwa pelanggan tidak bertanggung jawab atas pembaruan perangkat keras dan perangkat lunak.
##### Selain itu, dengan SaaS, vendor mengelola semua masalah teknis potensial, seperti data, middleware, server, dan penyimpanan. Ini memungkinkan bisnis untuk merasionalisasi pemeliharaan dan dukungan mereka.

## Arsitektur Platform SAAS (Perangkat Lunak sebagai Layanan)
[Artikel 2 : Arsitektur Platform SAAS](https://hackernoon.com/saas-software-as-a-service-platform-architecture-757a432270f5)
##### SaaS adalah model pengiriman umum untuk banyak aplikasi bisnis, termasuk perangkat lunak perkantoran dan pesan, perangkat lunak manajemen, virtualisasi dll. Ini adalah bagian dari nomenklatur komputasi awan, bersama dengan infrastruktur sebagai layanan (IaaS), platform sebagai layanan (PaaS) , desktop sebagai layanan (DaaS).

##### Ini terkait dengan penyedia layanan aplikasi (ASP) yang menyediakan aplikasi "shrink-wrap" untuk pengguna bisnis melalui Internet. Perangkat lunak yang dikirimkan melalui Internet lebih awal memiliki fitur yang mirip dengan aplikasi di tempat dibandingkan dengan aplikasi SaaS. Karena ini awalnya dibangun sebagai aplikasi penyewa tunggal, kemampuan mereka untuk berbagi data terbatas. Aplikasi SaaS adalah instance tunggal, arsitektur multi-tenant yang memberikan pengalaman kaya fitur yang kompetitif dengan aplikasi on-premise. Aggregator menggabungkan penawaran SaaS dari vendor yang berbeda dan menawarkannya sebagai bagian dari platform aplikasi terpadu.

##### Penyedia SaaS menyimpan aplikasi dan data secara terpusat - tambalan penyebaran. Mereka meningkatkan ke aplikasi secara transparan, memberikan akses ke pengguna akhir melalui Internet. Banyak vendor menyediakan API yang digunakan pengembang untuk membuat aplikasi komposit. Ini berisi berbagai mekanisme keamanan untuk keamanan data selama transmisi dan penyimpanan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-02/A2.jpg)

### Arsitektur SAAS:

##### Dengan model ini, satu versi aplikasi, dengan satu konfigurasi digunakan untuk semua pelanggan. Aplikasi ini diinstal pada banyak mesin untuk mendukung skalabilitas (disebut penskalaan horizontal). Apakah multitenancy merupakan komponen yang diperlukan untuk perangkat lunak-sebagai-layanan adalah topik kontroversi.
##### Ada dua varietas utama SaaS:
+ SaaS Vertikal
+ Perangkat Lunak yang menjawab kebutuhan industri tertentu (mis. Perangkat lunak untuk kesehatan, pertanian, real estat, industri keuangan)
+ SaaS Horisontal
+ Produk-produk yang berfokus pada kategori perangkat lunak (pemasaran, penjualan, alat pengembang, SDM) tetapi agnostik industri.

### Manfaat SAAS:

##### Integrasi dapat direncanakan dan dilaksanakan dengan upaya minimal, menciptakan salah satu interval waktu-ke-nilai sesingkat mungkin untuk investasi TI utama. Ini juga memungkinkan sejumlah vendor SaaS untuk menawarkan "test drive" bebas risiko (dan seringkali secara harfiah gratis) dari perangkat lunak mereka untuk periode terbatas, seperti 30 hari. Memberi pelanggan kesempatan untuk mencoba perangkat lunak sebelum mereka membelinya membantu menghilangkan banyak risiko seputar pembelian perangkat lunak.

### Dampak pada Peran dan Tanggung Jawab TI

##### Menambahkan SaaS dapat menyebabkan perubahan mendasar dalam peran departemen TI sebagai penyedia layanan informasi. Di masa lalu, sifat penyebaran perangkat lunak telah menempatkan petugas informasi kepala dalam peran penjaga gerbang. Mereka dapat melakukan veto dengan menyatakan bahwa mereka tidak akan meng-host-nya di pusat data. Dengan SaaS, kontrol pusat data tidak harus sama dengan kontrol atas seluruh lingkungan komputasi perusahaan. Ini dapat menyebabkan penjaga gerbang takut kehilangan kendali.

### Kesimpulan

##### Perusahaan sebaiknya mempertimbangkan fleksibilitas dan implikasi manajemen risiko dalam menambahkan SaaS ke portofolio layanan TI mereka. Integrasi dan komposisi adalah komponen penting dalam strategi arsitektur Anda untuk menggabungkan SaaS dengan sukses sebagai anggota yang berpartisipasi penuh dari infrastruktur TI Anda yang berfokus pada layanan. Kami percaya bahwa masa depan komputasi perusahaan tidak akan murni di tempat. Sebaliknya, mereka akan ada dalam harmoni simbiosis.

## Arsitektur Platform SAAS (Perangkat Lunak sebagai Layanan)
[Artikel 3 : Arsitektur Platform SAAS](https://www.devteam.space/blog/saas-software-as-a-service-platform-architecture/)
### Apa itu Platform SaaS?
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-02/A2.jpg)
##### SaaS juga merupakan salah satu pilar utama komputasi awan. Sebuah ledakan dalam komputasi Cloud, didorong oleh penyedia cloud seperti Microsoft dengan Azure atau Amazon dengan AWS, telah melihat pertumbuhan produk dan layanan lain yang disampaikan melalui internet seperti:
+ Infrastruktur sebagai Layanan
+ Platform sebagai Layanan
+ Pembelajaran Mesin sebagai Layanan
### Mengapa Menggunakan Arsitektur SaaS?
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-02/A3.jpg)
##### Seperti yang disebutkan dalam pendahuluan, perangkat lunak telah didistribusikan kepada pelanggan dalam berbagai saluran selama beberapa dekade terakhir. Jadi mengapa Anda mungkin ingin menggunakan produk yang telah dikirim "sebagai layanan"?

### Konsumen
##### Dari perspektif konsumen, produk SaaS adalah salah satu cara termudah untuk menggunakan layanan atau produk digital. Anda cukup mengaksesnya melalui web, membayar layanan dan menggunakannya! Dalam beberapa tahun terakhir kami telah melihat kemunculan ribuan produk SaaS yang ditargetkan untuk konsumen seperti:
+ Netflix
+ Microsoft Office 365
+ Amazon Prime
+ Indonesia
+ Facebook
+ Google Documents
##### Mampu mengaktifkan atau menonaktifkan produk SaaS sesuai permintaan adalah faktor lain yang menarik bagi konsumen, Anda tidak perlu lagi menjatuhkan ratusan dolar pada lisensi perangkat lunak. Sebagian besar produk SaaS memungkinkan Anda membayar langganan bulanan dengan opsi dan membatalkan kapan pun Anda mau.

### Bisnis

##### Beberapa manfaat lain dari penerapan arsitektur SaaS dalam bisnis termasuk, tetapi tidak terbatas pada:
+ Mengurangi waktu ke pasar
+ Biaya perawatan lebih rendah
+ Pembaruan yang lebih mudah

### Fitur dan Manfaat Utama dari Platform SaaS
##### Solusi SaaS memiliki fitur berbeda dengan aplikasi yang lebih tradisional yang diinstal pada desktop Anda misalnya, berikut adalah beberapa manfaat lain yang dapat diberikan oleh penggunaan produk berbasis SaaS.

+ Kesederhanaan
    Aplikasi perangkat lunak yang dirancang sebagai solusi SaaS biasanya diakses melalui web melalui berbagai jenis perangkat. Kemajuan dalam bahasa pemrograman sisi klien seperti JavaScript telah menghasilkan antarmuka web yang lebih intuitif dan karenanya, membuat penggunaan aplikasi yang dikirim melalui internet mudah digunakan seperti rekan-rekan desktop mereka.

+ Ekonomis
    Model pembayaran biaya subskrip bulanan atau tahunan memudahkan bisnis untuk menganggarkan dana, ditambah dengan ini tanpa biaya pemasangan infrastruktur, mudah untuk melihat bagaimana memilih menggunakan solusi SaaS dapat menghemat uang bisnis.

+ Keamanan
    Keamanan adalah aspek penting dari solusi pengembangan perangkat lunak dan platform SaaS tidak berbeda. Sebagai konsumen aplikasi yang dirancang menggunakan SaaS, Anda tidak perlu khawatir dengan bagaimana data Anda dikunci. Itu dipegang dengan aman di awan!

+ Kesesuaian
    Dengan penginstalan perangkat lunak tradisional, pembaruan dan tambalan terkadang membutuhkan banyak waktu dan uang. Ini terutama benar dalam perusahaan. Selain itu, perbedaan versi antara anggota tim dari tenaga kerja Anda dapat menyebabkan masalah kompatibilitas dan bahkan lebih banyak waktu terbuang. Namun, dengan SaaS, pelanggan dapat log-on ke layanan yang sudah ditingkatkan.
### Kemampuan Solusi SaaS
##### Platform SaaS memiliki beragam kemampuan. Terutama ketika digabungkan dengan penawaran cloud lainnya seperti IaaS (Infrastructure as a Service) dan PaaS (Platform as a Service).
##### Solusi SaaS dapat digunakan untuk lingkungan ini dan, secara teori, menawarkan semua jenis layanan yang dapat dikembangkan sebagai aplikasi perangkat lunak yang dapat mencakup, tetapi tidak terbatas pada:
+ Aplikasi kantor
+ Email dan pesan instan
+ Media sosial
+ Mengekspos API Pihak Ketiga
+ Keamanan dan otentikasi
+ Pembelajaran mesin
+ Kecerdasan buatan
+ Layanan Lokasi
+ Streaming data dan layanan pencarian
