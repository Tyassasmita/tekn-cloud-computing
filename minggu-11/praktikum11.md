### Stage Setup

```git clone https://github.com/ibnesayeed/linkextractor.git```

#### Pada perintah tersebut melakukan clone Link Extractor dari github. Link Extractor sendiri merupakan aplikasi yang akan melakukan scraping link dari suatu halaman web.

```cd linkextractor```

```git checkout demo```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/1.jpg)

### Step 0: Basic Link Extractor Script

```git checkout step0```

#### Pada proses tersebut melakukan checkout file step0 yang berada di dalam repo linkextractor. Perintah checkout tersebut saat dilakukan maka semua file akan dikembalikan seperti keadaan pada nomer commit yang dilakukan.

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/2.jpg)

```cat linkextractor.py```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/3.jpg)

```./linkextractor.py http://example.com/```

#### Menjalankan link extractor dengan http://example.com/, namun gagal karena permasalahan hak akses.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/4.jpg)

```ls -l linkextractor.py```

#### Perintah tersebut menghasilkan -rw-r--r--, yang menandakan bahwa skrip  linkextractor.py tidak bisa dijalankan dan harus diubah.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/5.jpg)

```python linkextractor.py```
#### hasil dari eksekusi perintah tersebut terdapat error karena tida terdapat modul beautifulsoup4 di bagian import pada file linkextractor.py

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/6.jpg)

### Step 1: Containerized Link Extractor Script

```git checkout step1```

#### Pada proses tersebut melakukan checkout file step1 yang berada di dalam repo linkextractor. Perintah checkout tersebut saat dilakukan maka semua file akan dikembalikan seperti keadaan pada nomer commit yang dilakukan pada step1.

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/7.jpg)

```cat Dockerfile```

#### Pada Dockerfile tersebut berisi perintah yang akan mengimport dari python 3 dengan label Sawood Alam. Dockerfile tersebut akan menjalankan perintah instalasi dengan menggunakan pip yang akan melakukan install modul beautifulsoup4 dan requests dengan menggunakan pip. Untuk direktory proses tersebut dilokasikan pada /app. Selanjutnya Dockerfile akan menjalankan copy file linkextractor.py dan menjalankan chmod a+x linkextractor.py.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/8.jpg)

```docker image build -t linkextractor:step1 .```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/9.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/10.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/11.jpg)

#### Penjelasan 
#### Step 1/8, dari image python:3, akan melakukan pull dari library python
#### Step 2/8, akan menjalankan container  perantara dengan kode 8678496664bf
#### Step 3/8, akan menjalankan perintah untuk instalasi beautifulsoup4
#### Step 4/8, akan menjalankan perintah untuk instalasi requests
#### Step 5/8, akan mengalokasikan apk direktory proses tersebut yang dilokasikan pada /app
#### Step 6/8, akan mencopy apa yang dibutuhkan pada proses build container, yaitu Dockerfile akan menjalankan copy file linkextractor.py
#### Step 7/8, akan menjalankan chmod a+x linkextractor.py
#### Step 8/8, mengatur entrypoint ubtuj linkextractor

```docker image ls```
#### pada perintah tersebut melakukan cek repositori yang telah dibuat.
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/12.jpg)

#### ```docker container run -it --rm linkextractor:step1 http://example.com/``` akan menjalankan container untuk pertama kalinya

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/13.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/71.jpg)

```docker container run -it --rm linkextractor:step1 https://training.play-with-docker.com/```

#### akan menjalankan container dengan menggunakan link https://training.play-with-docker.com/. Pada output terdapat stage 1,2, dan 3 dilakukan secara perulangan dengan diikuti beberapa proses untuk convert link dari twitter, facebook, google plus, linkedin, dockercon, docker, dan github

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/14.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/15.jpg)

### Step 2: Link Extractor Module with Full URI and Anchor Text

```git checkout step2```

#### Pada proses tersebut melakukan checkout file step2 yang berada di dalam repo linkextractor. Perintah checkout tersebut saat dilakukan maka semua file akan dikembalikan seperti keadaan pada nomer commit yang dilakukan pada step2.

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/16.jpg)

```cat linkextractor.py```

#### Pada file tersebut logika ektrasi link akan dilakukan abstraksi menjadi fungsi extract_links yang akan menerima URL sebagai parameter dan akan mengembaalikan object list yang berisi anchor text dan hiperlink yang dinormalisasi. Selanjutnya fungsi tersebut dapat diimport ke skrip lain yang dijadikan dalam bentuk modul.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/17.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/18.jpg)

```docker image build -t linkextractor:step2 .```

#### Pada proses build tersebut yang sama dengan proses sebelumnya,pada proses yang ini telah bisa melakukan import linkextractor dalam bentuk modul dan menjalankannya

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/19.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/20.jpg)

```docker image ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/21.jpg)

```docker container run -it --rm linkextractor:step2 https://training.play-with-docker.com/```

#### Pada proses menjalankan container tersebut, Pada output yang terdapat stage 1,2, dan 3 dengan diikuti beberapa proses untuk convert link dari twitter, facebook, google plus, linkedin, dockercon, docker, dan github sudah terdapat keterangan stepnya setelah berhasil melakukan import, yang antara lain Stage 1: The Basics, Stage 2: Digging Deeper, Stage 3: Moving to Production, Stage 1: The Basics, Stage 2: Digging Deeper, Stage 3: Moving to Staging. Lalu pada link yang diconvert terdapat keterangan bahwa semua tersebut adalah image.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/22.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/23.jpg)

```docker container run -it --rm linkextractor:step1 https://training.play-with-docker.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/24.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/25.jpg)

### Step 3: Link Extractor API Service

```git checkout step3```

####  Pada proses tersebut melakukan checkout file step3 yang berada di dalam repo linkextractor. Perintah checkout tersebut saat dilakukan maka semua file akan dikembalikan seperti keadaan pada nomer commit yang dilakukan pada step3.

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/26.jpg)

```cat Dockerfile```

#### Pada Dockerfile tersebut berisi perintah yang akan mengimport dari python 3 dengan label Sawood Alam. Dockerfile tersebut akan menjalankan perintah untuk menambahkan script server main.py yang menggunakan modul ekstrak link yang ditulis pada langkah terakhir. Lalu Dockerfile diperbarui untuk merujuk ke file main.py, Server dapat diakses sebagai API WEB di http: // <hostname> [: <prt>] / api / <url>, se;anjutnya dependensi dipindahkan ke file requirement.txt.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/27.jpg)

```cat main.py```

#### Pada file main.py berisi script untuk keperluan server. Script tersebut memerlukan import modul flask framework, modul request, jsonify, dan import fungsi dari file linkextractor yaitu fungsi extract_links. Pada fungsi index akan mengembalikan nilai "Usage: http://<hostname>[:<prt>]/api/<url>". [ada fungsi api berisi beberapa perintah request seperti url dan mengembalikan links. Huntuk host appnya adalah 0.0.0.0

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/28.jpg)

```docker image build -t linkextractor:step3 .```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/52.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/53.jpg)

#### Penjelasan
#### Step 1/8, dari image python:3, akan melakukan pull dari library python
#### Step 2/8, akan menjalankan container  perantara dengan kode 8678496664bf
#### Step 3/8, akan mengalokasikan apk direktory proses tersebut yang dilokasikan pada /app
#### Step 4/8, akan menjalankan perintah untuk melakukan copy file requirements.txt
#### Step 5/8, akan menjalankan perintah untuk instalasi requests dengan melakukan copy file requirements.txt. yaitu dengan mendownload dan install modul beautifulsoup4, flask framework, requests, jsonify, dan import fungsi dari file linkextractor
#### Step 6/8, akan mencopy apa yang dibutuhkan pada proses build container, yaitu Dockerfile akan menjalankan copy file linkextractor.py
#### Step 7/8, akan menjalankan chmod a+x linkextractor.py yang dimana perintah tersebut akan mengubah perizinan hak akses untuk semua pengguna pada file/Direktori
#### Step 8/8, mengatur entrypoint ubtuj linkextractor

```docker container run -d -p 5000:5000 --name=linkextractor linkextractor:step3```

#### akan menjalankan container baru dengan nama container linkextractor dari step3 dengan port 5000:5000 pada Daemon mode.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/54.jpg)

#### ```docker container ls``` sudah terdapat container dengan nama image linkextractor:step3

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/55.jpg)

```curl -i http://localhost:5000/api/http://example.com/```

#### perintah curl -i http://localhost:5000/api/http://example.com/akan membuat host menjadi terhubung dengan container linkextractor. Hasilnya akan menampilkan struktur kode interface image linkextractor.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/56.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/72.jpg)

```docker container logs linkextractor```

#### Docker container logs akan menjalankan perintah untuk melihat catatan aktivitas yang terjadi pada container yang berjalan. Antara lainmenjalankan flask app main, beralih ke user mysql, inisialisasi file database, lalu terdapat warning memberi tahu bahwa Jangan gunakan server pengembangan di lingkungan produksi. Selanjutnya terdapat aktivitas inisialisasi file database dan menjalankan server sementara, dan rerakhir terdapat warning bahwa tidak bisa memuat file iso3166.tab dmode debug dan berjalan pada  http://0.0.0.0:5000.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/57.jpg)

#### ```docker container rm -f linkextractor``` akan menghapus container linkextractor pada step 3

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/58.jpg)

### Step 4: Link Extractor API and Web Front End Services

```git checkout step4```

#### Pada proses tersebut melakukan checkout file step4 yang berada di dalam repo linkextractor. Perintah checkout tersebut saat dilakukan maka semua file akan dikembalikan seperti keadaan pada nomer commit yang dilakukan pada step4.

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/30.jpg)

```cat docker-compose.yml```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/31.jpg)

```cat www/index.php```

#### Pada file index.php tersebut variabel $ api_endpoint diinisialisasi dengan nilai variabel emvironment yang disediakan dari file docker-compose.yml sebagai $ _ENV ["API_ENDPOINT"] jika tidak kembali ke nilai default http: // localhost: 5000 / api / . Request dibuat menggunakan fungsi file_get_contents yang menggunakan variabel $ api_endpoint dan URL yang disediakan user dari $ _GET ["url"]. Beberapa analisis dan transformasi dilakukan pada respons yang diterima kemudian digunakan dalam markup untuk mengisi halaman. Selain itu terdapat file html dan css untuk mengatur tampilan layout image.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/32.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/33.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/34.jpg)

```docker-compose up -d --build```

#### Pada docker-compose.yml tersebut berisi dua servis, yaitu api dan web. Servis api akan menggunakan image linkextractor-api:step4-python yang belum dibuild, tetapi akan dibuild menggunakan Dockerfile yang berada di direktory ./api. Servis api tersebut akan berjalan di port 5000. Pada servis kedua yaitu servis web akan menggunakan image php:7-apache yang diambil langsung dari DockerHub. Maka servis web tersebut tidak lagi memerlukan Dockerfile. Servis akan ditampilkan pada HTTP port default (port 80). Pada docker-compose akan disediakan variabel environment bernama API_ENDPOINT dengan value http: // api: 5000 / api / untuk memberi tahu skrip PHP ke mana skrip tersebut harus terhubung ke akses API. api: 5000 digunakan karena pada docker-compose akan memiliki entri nama host dinamis di jaringan privat untuk layanan API yang cocok dengan nama layanannya. Terakhir, docker-compose akan mengikat mount folder ./www untuk membuat file index.php tersedia di dalam container servis web di / var / www / html, yang merupakan root web default untuk server web Apache.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/36.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/37.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/38.jpg)

```docker container ls```

#### sudah terdapat 2 container sekaligus, yaitu  linkextractor_web_1 dan linkextractor_api_1 maka proses sebelumnya telah berhasil dilakukan.
#### curl -i http://localhost:5000/api/http://example.com/

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/39.jpg)

#### perintah ```curl -i http://localhost:5000/api/http://example.com/``` akan membuat host menjadi terhubung dengan API.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/40.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/72.jpg)

```sed -i 's/Link Extractor/Super Link Extractor/g' www/index.php```

#### perintah tersebut akan mengubah www/index.php untuk memindah semua proses yang dilakukan pada Link Extractor dengan Super Link Extractor. Setelah direload ulang halamannya, maka title, header, dan footer akan ada perubahan. Ini terjadi karena folder ./www diikat terpasang di dalam container, sehingga setiap perubahan yang dilakukan di luar akan mencerminkan di dalam container atau sebaliknya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/41.jpg)

#### ```git reset --hard``` akan melakukan reset kembali ke semula

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/42.jpg)

```docker-compose down```

#### Perintah tersebut akan menghentikan container, tetapi juga menghapus container yang terhenti serta jaringan apa pun yang dibuat. Pada tammpilan akan menghentikan linkextractor_api_1 dan linkextractor_web_1 serta menghapus linkextractor_api_1, linkextractor_web_1, dan network linkextractor_default

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/43.jpg)

### Step 5: Redis Service for Caching

```git checkout step5```

#### Pada proses tersebut melakukan checkout file step5 yang berada di dalam repo linkextractor. Perintah checkout tersebut saat dilakukan maka semua file akan dikembalikan seperti keadaan pada nomer commit yang dilakukan pada step5.

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/44.jpg)

```cat www/Dockerfile```

#### Dockerfile tersebut ditempatkan pada folder ./www untuk web apps PHP untuk membangun image contained sendiri dan menghindari pemasangan file langsung. Dockerfile tersebut menggunakan image php:7-apache sebagai basic dan menyalin semua file dari folder ./www ke folder / var / www / html / folder image. Proses ini hampir sama dengan proses yang sebelumnya, perbedaannya ementara di sini kita membuat bagian kode dari image sendiri. Dockerfile tersebut juga telah menambahkan environment variabel API_ENDPOINT dengan nilai default, yang akan digunakan untuk pemberitahuan informasi penting yang perlu ada agar layanan berfungsi dengan baik (dan harus disesuaikan pada waktu berjalan dengan nilai yang sesuai).

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/45.jpg)

```cat api/main.py```

#### Pada file main.py yang merupakan komponen api tersebut melakukan import modul os, json, redis, flask (disini dari flask melakukan import Fflask dan request) lalu juga melakukan import linkextractor. Main.py ini digunakan untuk membuat layanan API, maka perlu diberi cara untuk menghubungkan ke instance Redis karena akan menggunakan redis untuk melakukan caching. Informasi ini dapat tersedia pada saat dijalankan menggunakan environment variabel REDIS_URL. Entri ENV yang sesuai juga ditambahkan di Dockerfile dari layanan API dengan nilai default. Contoh client redis dibuat menggunakan redis host name dan port Redis default 6379.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/46.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/47.jpg)

```cat docker-compose.yml```

#### Pada docker-compose.yml tersebut berisi servis servis web akan menggunakan image buatan sendiri yaitu linkextractor-web:step5-php. Maka servis web tersebut  memerlukan Dockerfile. Servis akan ditampilkan pada HTTP port default (port 80). Pada docker-compose akan disediakan variabel environment bernama API_ENDPOINT dengan value http: // api: 5000 / api / untuk memberi tahu skrip PHP ke mana skrip tersebut harus terhubung ke akses API. api: 5000 digunakan karena pada docker-compose akan memiliki entri nama host dinamis di jaringan privat untuk layanan API yang cocok dengan nama layanannya. docker-compose akan mengikat mount folder ./www untuk membuat file index.php tersedia di dalam container servis web di / var / www / html, yang merupakan root web default untuk server web Apache. Konfigurasi layanan api sebagian besar tetap sama seperti sebelumnya, kecuali tag image yang diperbarui dan variabel environment yang ditambahkan REDIS_URL yang menunjuk ke layanan Redis. Pada docker-compose.yml  ini tidak lagi dipasang folder ./www menggunakan konfigurasi volume Lalu layanan baru bernama redis ditambahkan yang akan menggunakan image resmi dari DockerHub dan sehingga tidak memerlukan konfigurasi khusus. Layanan ini dapat diakses oleh API Python menggunakan nama layanannya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/48.jpg)

#### ```docker-compose up -d --build``` akan membuild layanan yang telah dibuat

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/49.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/50.jpg)

#### ```docker-compose exec redis redis-cli monitor``` akan menjalankan redis yang digunakan untuk menghubungkan ke instance Redis karena akan menggunakan redis untuk melakukan caching

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/51.jpg)

#### ```sed -i 's/Link Extractor/Super Link Extractor/g' www/index.php``` pada proses tersebut tidak dilakukan pemasangam folder / www di dalam container

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/59.jpg)

```git reset --hard```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/60.jpg)

```docker-compose down```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/61.jpg)

### Step 6: Swap Python API Service with Ruby

```git checkout step6```

#### Pada proses tersebut melakukan checkout file step6 yang berada di dalam repo linkextractor. Perintah checkout tersebut saat dilakukan maka semua file akan dikembalikan seperti keadaan pada nomer commit yang dilakukan pada step6.

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/62.jpg)

```cat api/linkextractor.rb```

#### Pada file linkextractor.rb tersebut  yang merupakan file ruby digunakan sebagai sevice api denga menggunakan bahasa ruby, skrip dalam file tersebut  melakukan import modul "sinatra",require "open-uri","uri","nokogiri","json","redis".  file linkextractor.rb ini digunakan untuk membuat layanan API, maka perlu diberi cara untuk menghubungkan ke instance Redis karena akan menggunakan redis untuk melakukan caching. Informasi ini dapat tersedia pada saat dijalankan menggunakan environment variabel REDIS_URL. Entri ENV yang sesuai juga ditambahkan di Dockerfile dari layanan API dengan nilai default. Terdapat fungsi extract_links yang akan menangani proses ektraksi link dari suat halaman web.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/63.jpg)

```cat api/Dockerfile```

#### Dockerfile tersebut menggunakan ruby 2.6 dengan label Sawood Alam. Dockerfile tersebut menggunakan environment variabel LANG C.UTF-8 dan environment variabel REDIS_URL="redis://localhost:6379" yang menggunakan port 6379 dan menggunakan workdir /app direktory lalu meakukan copy Gemfile ke direktory tersebut yang kemudian akan menjalankan perintah instalasi dengan menggunakan bundle install yang akan melakukan install modul Gemfile dan untuk direktory proses tersebut dilokasikan pada /app. Selanjutnya Dockerfile akan menjalankan copy file linkextractor.rb ke direktory tersebut dan menjalankan chmod a+x linkextractor.rb.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/64.jpg)

```cat docker-compose.yml```

#### Pada docker-compose.yml versi 3 tersebut berisi servis web akan menggunakan image buatan sendiri yaitu linkextractor-web:step6-php. Maka servis web tersebut  memerlukan Dockerfile. Servis akan ditampilkan pada HTTP port default (port 80). Pada docker-compose akan disediakan variabel environment bernama API_ENDPOINT dengan value http: // api: 4567/ api / untuk memberi tahu skrip PHP ke mana skrip tersebut harus terhubung ke akses API. api: 5000 digunakan karena pada docker-compose akan memiliki entri nama host dinamis di jaringan privat untuk layanan API yang cocok dengan nama layanannya. docker-compose akan mengikat mount folder ./www untuk membuat file index.php tersedia di dalam container servis web di / var / www / html, yang merupakan root web default untuk server web Apache. Konfigurasi layanan api sebagian besar tetap sama seperti sebelumnya, kecuali tag image yang diperbarui dan variabel environment yang ditambahkan REDIS_URL yang menunjuk ke layanan Redis. Pada docker-compose.yml  ini tidak lagi dipasang folder ./www menggunakan konfigurasi volume Lalu layanan baru bernama redis ditambahkan yang akan menggunakan image resmi dari DockerHub dan sehingga tidak memerlukan konfigurasi khusus.  Untuk api service nya menggunakan image dengan nama linkextractor-api:step6-ruby dan port mapping nya diganti dari port 5000 ke  4567.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/65.jpg)

```docker-compose up -d --build```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/66.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/67.jpg)

```curl -i http://localhost:4567/api/http://example.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/68.jpg)

```docker-compose down```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/69.jpg)

```cat logs/extraction.log```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/70.jpg)