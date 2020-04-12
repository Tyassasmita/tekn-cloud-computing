#### Step 1: Setup
1. Membuat direktori projek
##### membuat direktori dengan perintah ``` $ mkdir composetest```. Lalu masuk direktori dengan perintah ``` $ cd composetest```.
	
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/l1.jpg)

2. Membuat file ```app.py```
##### Membuat file app.py dengan isi projek seperti pada gambar dibawah ini.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/l2.jpg)

3. Membuat file ```requirements.txt```
##### Membuat file requirement.txt dengan isi projek seperti pada gambar dibawah ini.
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/l3.jpg)

#### Step 2: Create a Dockerfile
##### Membuat file DockerFile
###### Menggunakan perintah ```vim dockerfile```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/21.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/22.jpg)
#### Step 3: Define services in a Compose file
##### Membuat File docker-compose.yml
###### Menggunakan perintah ``` vim docker-compose.yml```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/31.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/32.jpg)
#### Step 4: Build and run your app with Compose
1. Start up your application by running ```docker-compose up```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/41.jpg)
##### pada file dockerfile isikan seperti gambar dibawah ini.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/411.jpg)
##### Penjelasan 
##### Step 1/9, dari image python:3.7-alpine , akan melakukan pull dari library python

##### Step 2/9, akan Menghapus container  perantara e96193fb6702

##### Step 3/9, akan menjalankan enfironment flask framework pada app.py

##### Step 4/9, pada environment flask menjalankan host 0.0.0.0

##### Step 5/9, akan menjalankan apk dengan melakukan instalasi beberapa komponen dari alpine

##### Step 6/9, akan mencopy apa yang dibutuhkan pada proses build container pada requirements.txt, yaitu flask dan redis

##### Step 7/9, akan melakukan instalasi yang dibutuhkan pada proses build container pada requirements.txt, yaitu flask dan redis dengan menggunakan pip, dengan melakukan download flask framework dan redis dan beberapa package pendukungnya. Setelah didwonload, maka dilakukan build MarkupSafe dan dilakukan proses install

##### Step 8/9, melakukan copy

##### Step 9/9, menjalankan build image alpine yang menggunakan flask framework
##### Setelah itu dijalankan pada url ip machine dan port 5000: http://192.168.99.100:5000
2. Enter http://localhost:5000/ in a browser

``` Hello World! I have been seen 1 times.```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/42.jpg)

3. Refresh the page.

``` Hello World! I have been seen 2 times.```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/43.jpg)

4. Type ```docker image ls```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/44.jpg)
#### Step 5: Edit the Compose file to add a bind mount
###### Edit file ``` docker-compose.yml``` seperti gambar dibawah ini.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/5.jpg)
#### Step 6: Re-build and run the app with Compose
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/6.jpg)
#### Step 7: Update the application
1. Ubah pesan pada file app.py
``` Hello from Docker!```
2. Refresh the app in your browser

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/72.jpg)
#### Step 8: Experiment with some other commands
``` docker-compose up -d```
``` docker-compose ps ```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/8.jpg)

``` docker-compose run web env```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/81.jpg)

``` docker-compose stop```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/82.jpg)

``` docker-compose down --volumes```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/83.jpg)

### Where to go next
[LINK](https://docs.docker.com/compose/wordpress/)
1. Membuat direktori projek ```my_wordpress```
2. Membuat file ```docker-compose.yml```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/84.jpg)

#### Build the project
##### run ```docker-compose up -d```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/85.jpg)

#### Bring up WordPress in a web browser
``` http://localhost:8000```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/86.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/87.jpg)
#### Shutdown
``` docker-compose down```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/88.jpg)