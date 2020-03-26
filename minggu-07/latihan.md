1. Install Docker

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L1.jpg)
##### Klik Next
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L2.jpg)
##### Klik Next
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L3.jpg)
##### Klik Next
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L4.jpg)
##### Klik Next
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L5.jpg)
##### Klik Install
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L6.jpg)
##### Klik Finish
#### Di Desktop klik ikon Terminal QuickStart Docker.
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L8.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/L7.jpg)
2. Kerjakan no 4 pada Materi dan Penjelasan di atas.

[link Docker get started](https://docs.docker.com/get-started/)
#### Part 1 Orientasi dan pengaturan
##### Test Docker version
``` docker --version```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/G1.jpg)
##### Test Docker installation
###### Uji instalasi dengan menjalankan gambar Docker hello-world
``` docker run hello-world```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/G2.jpg)
###### Menjalankan ``` docker image ls```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/G3.jpg)

``` docker container ls --all ```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/G4.jpg)
#### Part 2 Build and run your image
##### Git
``` git clone https://github.com/dockersamples/node-bulletin-board```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P21.jpg)

``` cd node-bulletin-board/bulletin-board-app``` 

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P22.jpg)
#### Build and test your image
``` docker image build -t bulletinboard:1.0 .```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P23.jpg)
#### Run your image as a container
``` docker run --publish 8000:8080 --detach --name bb bulletinboard:1.0```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P24.jpg)
#### Visit your application in a browser at localhost:8000
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P26.jpg)
#### Part 3 Share images on Docker Hub
##### Create a Docker Hub repository and push your image
1. Klik ikon Docker di bilah menu Anda, dan navigasikan ke Repositories > Create. Anda akan dibawa ke halaman Docker Hub untuk membuat repositori baru.
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P31.jpg)
2. Isi nama repositori dengan bulletinboard. 
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P32.jpg)
3. Sekarang Anda siap untuk membagikan gambar Anda di Docker Hub.
``` docker tag bulletinboard:1.0 tyassasmita/bulletinboard:1.0```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/P33.jpg)
4. Terakhir, push gambar Anda ke Docker Hub:
``` docker push tyassasmita/bulletinboard:1.0 ```