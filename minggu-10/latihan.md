# LATIHAN 
## Section #1 - Networking Basics
### Step 1: The Docker Network Command

```docker network```
#### Perintah Docker network merupakan perintah yang memungkinkan kita untuk melakukan segala hal yang berhubungan dengan manajemen administrasi jaringan, seperti membuat jaringan, menghubungkan, melihat informasi jaringan hingga mendetail sekali dan menerapkannya di kontainer yang akan kita jalankan. Pada hasil  perintah tersebut terdapat Commands: Connect yang digunakan untuk melakukan koneksi container ke jaringan yang akan dibangun, Create yang digunakan untuk membuat jaringan, Disconnect yang digunakan untuk memutus koneksi container dengan jaringan yang akan dibangun, Inspect yang digunakan untuk menampilkan detail informasi pada jaringan, ls yang digunakan untuk menampilkan daftar jaringan yang dibangun, prune yang digunakan untuk menghapus semua jaringan yang tidak lagi digunakan, dan rm yang digunakan untuk menghapus jaringan.


![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/1.jpg)

### Step 2: List networks
#### ```docker network ls``` digunakan untuk melihat daftar jaringan kontainer yang telah dibuat. Setiap jaringan mendapatkan ID dan NAME yang unik. Setiap jaringan juga dikaitkan dengan satu driver.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/2.jpg)

### Step 3: Inspect a network
```docker network inspect bridge```
#### Perintah Docker network inspect merupakan perintah yang digunakan untuk menampilkan detail informasi pada jaringan bridge.  Bridge sendiri merupakan jenis network (default) yg digunakan Docker, apabila jika akan membuat container network defaultnya secara otomatis menggunakan Bridge sebagai networknya, network jenis ini memungkinkan Docker container saling terhubung pada lingkungan network private, agar host Docker dapat mengakses port container pada network ini harus di expose portnya atau di open lewat firewall. Terdapat beberapa informasi seperti nama, id, waktu dibuat, scope, driver, support atau tidaknya terhadap Ipv6, IPAM yang digunakan untuk konfigurasi tempat IP address (IP Address Management), support atau tidaknya penyimpanan internal, support atau tidaknya  attachable, support atau tidaknya  ingress, configFrom,jaringan, dan beberapa part pendukung lainnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/3.jpg)

### Step 4: List network driver plugins
#### ```docker info``` digunakan untuk menunjukkan banyak informasi menarik tentang instalasi Docker.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/4.jpg)

## Section #2 - Bridge Networking
### Step 1: The Basics
```docker network ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/2.jpg)

``` apk update```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/5.jpg)

``` apk add bridge```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/6.jpg)

``` brctl show```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/7.jpg)

``` ip a```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/8.jpg)

### Step 2: Connect a container
``` docker run -dt ubuntu sleep infinity```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/9.jpg)

``` docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/10.jpg)

``` brctl show```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/11.jpg)

``` docker network inspect bridge```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/12.jpg)

### Step 3: Test network connectivity
``` ping -c5 172.17.0.2```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/13.jpg)

``` docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/14.jpg)

``` docker exec -it fcdbadcccbf6 /bin/bash```

``` apt-get update && apt-get install -y iputils-ping```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/28.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/29.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/30.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/31.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/32.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/33.jpg)

``` ping -c5 www.github.com```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/15.jpg)

### Step 4: Configure NAT for external connectivity
``` docker run --name web1 -d -p 8080:80 nginx```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/16.jpg)

``` docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/17.jpg)

``` curl 127.0.0.1:8080```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/18.jpg)

## Section #3 - Overlay Networking
### Step 1: The Basics
``` docker swarm init --advertise-addr $(hostname -i)```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/19.jpg)

``` docker swarm join --token SWMTKN-1-1t59fxncbeths7ykym6vomvqeg7jlxqb4wi1b08dd96c1g8jbx-280hzwqz7kr41ncm50ad8ytxn 192.168.0.48:2377```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/46.jpg)

``` docker node ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/21.jpg)

### Step 2: Create an overlay network
``` docker network create -d overlay overnet```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/22.jpg)

```docker network ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/23.jpg)

#### Run the same docker network ls command from the second terminal. 

``` docker network ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/24.jpg)   

``` docker network inspect overnet```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/25.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/26.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/27.jpg)

### Step 3: Create a service

``` docker service create --name myservice \```

```--network overnet \```

```--replicas 2 \```

```ubuntu sleep infinity```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/34.jpg)

```docker service ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/35.jpg)

``` docker service ps myservice ```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/36.jpg)

#### Now that the second node is running a task on the “overnet” network it will be able to see the “overnet” network. Lets run docker network ls from the second terminal to verify this.

``` docker network ls```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/47.jpg)

#### We can also run docker network inspect overnet on the second terminal to get more detailed information about the “overnet” network and obtain the IP address of the task running on the second terminal.

``` docker network inspect overnet```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/48.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/49.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/50.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/51.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/52.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/53.jpg)

### Step 4: Test the network

``` docker network inspect overnet```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/37.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/38.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/39.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/40.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/41.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/42.jpg)

``` docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/43.jpg)

``` docker exec -it fcdbadcccbf6 /bin/bash```

``` apt-get update && apt-get install -y iputils-ping```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/28.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/29.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/30.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/31.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/32.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/33.jpg)

``` ping -c5 10.0.0.3```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/44.jpg)

### Step 5: Test service discovery

``` cat /etc/resolv.conf```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/45.jpg)

``` ping -c5 myservice```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/54.jpeg)

``` docker service inspect myservice```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/55.jpeg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/56.jpeg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/57.jpeg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/58.jpeg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/59.jpeg)

## Cleaning Up

``` docker service rm myservice```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/60.jpeg)

``` docker ps```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/61.jpeg)

```docker swarm leave --force```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-10/62.jpeg)