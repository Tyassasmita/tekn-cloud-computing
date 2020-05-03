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

```docker image ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/12.jpg)

```docker container run -it --rm linkextractor:step1 http://example.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/13.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/71.jpg)

```docker container run -it --rm linkextractor:step1 https://training.play-with-docker.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/14.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/15.jpg)

### Step 2: Link Extractor Module with Full URI and Anchor Text

```git checkout step2```

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/16.jpg)

```cat linkextractor.py```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/17.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/18.jpg)

```docker image build -t linkextractor:step2 .```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/19.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/20.jpg)

```docker image ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/21.jpg)

```docker container run -it --rm linkextractor:step2 https://training.play-with-docker.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/22.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/23.jpg)

```docker container run -it --rm linkextractor:step1 https://training.play-with-docker.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/24.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/25.jpg)

### Step 3: Link Extractor API Service

```git checkout step3```

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/26.jpg)

```cat Dockerfile```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/27.jpg)

```cat main.py```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/28.jpg)

```docker image build -t linkextractor:step3 .```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/52.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/53.jpg)

```docker container run -d -p 5000:5000 --name=linkextractor linkextractor:step3```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/54.jpg)

```docker container ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/55.jpg)

```curl -i http://localhost:5000/api/http://example.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/56.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/72.jpg)

```docker container logs linkextractor```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/57.jpg)

```docker container rm -f linkextractor```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/58.jpg)

### Step 4: Link Extractor API and Web Front End Services

```git checkout step4```

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/30.jpg)

```cat docker-compose.yml```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/31.jpg)

```cat www/index.php```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/32.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/33.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/34.jpg)

```docker-compose up -d --build```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/36.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/37.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/38.jpg)

```docker container ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/39.jpg)

```curl -i http://localhost:5000/api/http://example.com/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/40.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/72.jpg)

```sed -i 's/Link Extractor/Super Link Extractor/g' www/index.php```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/41.jpg)

```git reset --hard```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/42.jpg)

```docker-compose down```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/43.jpg)

### Step 5: Redis Service for Caching

```git checkout step5```

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/44.jpg)

```cat www/Dockerfile```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/45.jpg)

```cat api/main.py```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/46.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/47.jpg)

```cat docker-compose.yml```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/48.jpg)

```docker-compose up -d --build```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/49.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/50.jpg)

```docker-compose exec redis redis-cli monitor```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/51.jpg)

```sed -i 's/Link Extractor/Super Link Extractor/g' www/index.php```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/59.jpg)

```git reset --hard```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/60.jpg)

```docker-compose down```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/61.jpg)

### Step 6: Swap Python API Service with Ruby

```git checkout step6```

```tree```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/62.jpg)

```cat api/linkextractor.rb```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/63.jpg)

```cat api/Dockerfile```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-11/64.jpg)

```cat docker-compose.yml```

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