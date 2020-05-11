
## Section 2: Configure Swarm Mode

```docker run -dt ubuntu sleep infinity```
#### akan menjalankan container ubuntu dalam mode daemon. sleep infinity akan menjaga container tetap hidup dalam mode daemon tanpa batas waktu.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/1.jpg)

```docker ps```
#### Pada hasil perintah tersebut sudah ada container ubuntu dengan keterangan command sleep infinity

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/2.jpg)

### Step 2.1 - Create a Manager node

#### Run docker swarm init on node1.

```docker swarm init --advertise-addr $(hostname -i)```
#### akan melakukan inisialisasi docker swarm. Penggunaan --advertise-addr digunakan jika alamat node lain mencapai node manager pertama bukanlah alamat yang sama dengan yang dibaca oleh node manajer Misalnya, dalam pengaturan cloud yang mencakup wilayah yang berbeda, host memiliki alamat internal untuk akses di dalam wilayah dan alamat eksternal yang digunakan untuk akses dari luar wilayah itu. Dalam hal ini, kita harus menentukan alamat eksternal dengan --advertise-addr sehingga node dapat menyebarkan informasi itu ke node lain yang kemudian terhubung ke sana.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/3.jpg)

#### Perintah ```docker info``` akan menampilkan informasi seluruh sistem mengenai instalasi pada Docker. Informasi yang ditampilkan termasuk versi kernel, jumlah container dan image. Jumlah image yang ditampilkan adalah jumlah unique image. Uuntuk image yang sama ditandai dengan nama yang berbeda hanya dihitung satu kali. Docker info tersebut memuat informasi driver penyimpanan yang digunakan, informasi tambahan  seperti pool name, file data, file metadata, penyimpanan data yang digunakan, total memori, memori metadata yang digunakan, dan total memori metadata.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/4.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/5.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/6.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/7.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/8.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/9.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/10.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/11.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/12.jpg)

### Step 2.2 - Join Worker nodes to the Swarm

#### Perintah ``` docker swarm join --token SWMTKN-1-5t91j5u3prqbydwtq641swgfk8q02spg2v84b23bvocuipua5m-b8ajw7det44uvje95dbapfuc7 192.168.0.8:2377``` akan menjalankan swarm pada node 1,2,dan3. Perintah docker swarm join tersebut berfungsi untuk mendaftarkan server/host pada docker swarm master.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/13.jpg)

#### Perintah ```docker node ls``` akan menampilkan node / host / server apa saja yang telah terdaftar, pada tampilan sudah terdapat 3 node yang telah terdaftar, yaitu node1, node2 dan node3 yang dimana kedua node tersebut saling berhubungan, node 1 menyebarkan informasi ke node 2 dan 3yang kemudian terhubung ke sana.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/14.jpg)

## Section 3: Deploy applications across multiple hosts
### Step 3.1 - Deploy the application components as Docker services
#### You will perform this procedure from node1.

#### Perintah ``` docker service create --name sleep-app ubuntu sleep infinity``` akan melakukan deploy service dengan nama sleep-app yang akan berjalan di container ubuntu. sleep infinity akan menjaga service tetap hidup dalam mode daemon tanpa batas waktu.


![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/15.jpg)

``` docker service ls```
#### Pada hasil perintah tersebut sudah ada service dengan nama  sleep-app yang berjalan di container ubuntu keterangan command sleep infinity

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/16.jpg)

## Section 4: Scale the application

#### Perintah ```docker service update --replicas 7 sleep-app``` akan melakukan skala angka container dalam service sleep-app ke angka 7. Replika adalah istilah yang digunakan untuk menggambarkan container identik yang menyediakan layanan yang sama.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/17.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/18.jpg)

#### Perintah ```docker service ps sleep-app``` akan menampilkan proses running setiap replika yang berjalan secara real time. Bisa real time karena menggunakan sleep infinity yang sudah dilakukan pada step sebelumnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/19.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/20.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/21.jpg)

#### Perintah ```docker service update --replicas 4 sleep-app``` akan melakukan skala angka container dalam service sleep-app dari 7 skala dikurangi menjadi 4 skala. Replika adalah istilah yang digunakan untuk menggambarkan container identik yang menyediakan layanan yang sama.


![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/22.jpg)

#### Perintah ```docker service ps sleep-app``` akan menampilkan proses running setiap replika yang berjalan secara real time. Bisa real time karena menggunakan sleep infinity yang sudah dilakukan pada step sebelumnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/23.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/24.jpg)

## Section 5: Drain a node and reschedule the containers

```docker node ls```
#### docker node ls akan menampilkan bahwa node 1 merupakan node utama yang menjalankan container.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/25.jpg)

#### Let’s see the containers that you have running on node2.

#### Perintah ```docker ps``` terdapat satu sleep-app yang sedang berjalan, dimana sleep-app tersebut merupakan milik node 1

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/26.jpg)

####  back to node1

```docker node ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/27.jpg)

#### Perintah ```docker node update --availability drain 690hkbdiu8fp5kt2v75pwo4xr ``` akan mengganti manager  docker pada node 2 dari active menjadi drain

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/28.jpg)

```docker node ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/29.jpg)

#### Switch back to node2 and see what is running there by running ```docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/30.jpg)

```docker service ps sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/31.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/32.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/33.jpg)

## Cleaning Up

```docker service rm sleep-app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/34.jpg)

```docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/35.jpg)

#### Lets run docker swarm leave --force on node1, node2 and node3.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-12/36.jpg)