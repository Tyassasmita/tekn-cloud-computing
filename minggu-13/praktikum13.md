## Create a Cluster
#### Perintah ``` minikube version``` untuk melakukan cek apakah minikube sudah terinstall

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/1.jpg)

#### Perintah ```minikube start``` akan memulai cluster, dengan menjalankan minikube start. Jika sudah done, maka kluster kubernets sekarang sudah berhasil dijalankan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/2.jpg)

#### Perintah ``` kubectl version```untuk melakukan cek apakah kubetcl sudah terdapat dalam command.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/3.jpg)

```kubectl cluster-info```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/4.jpg)

#### Perintah ```kubectl get nodes``` untuk melihat node di cluster menggunakan kubectl get nodes, Perintah tersebut menunjukkan semua node yang dapat digunakan untuk meng-host aplikasi kita. Sekarang kita hanya memiliki satu node, dan kita dapat melihat bahwa statusnya siap (siap menerima aplikasi untuk ditempatkan).

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/5.jpg)

## Create a Deployment

```kubectl version```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/3.jpg)

```kubectl get nodes```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/5.jpg)

### Deploy App
#### Perintah ```kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1``` akan melakukan deploy aplikasi pertama kali dengan kubectl create command deployment.  Bootcamp adalah nama aplikasi yang akan dideploy, gcr.io/google-samples/kubernetes-bootcamp:v1 adalah lokasi/url repositori untuk image yang dihosting di luar hub Docker.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/6.jpg)

#### Perintah ```kubectl get deployments``` untuk melihat daftar deployment image. ada 1 deployment yang menjalankan satu instance aplikasi. Mesin virtual dijalankan di dalam container Dockor di node tersebut.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/7.jpg)

### View App

#### We will open a second terminal window to run the proxy.
#### Perintah ```echo -e "\n\n\n\e[92mStarting Proxy. After starting it will not output a response. Please click the first Terminal Tab\n"; ``` Karena Pods sedang berjalan di private network yang sedang terisolasi, maka pada proses tersebut perlu mem-proxy akses ke sana agar kita bisa men-debug dan berinteraksi dengannya. Untuk melakukannya, akan digunakan perintah proxy kubectl untuk menjalankan proxy di terminal kedua.

#### Perintah ```kubectl proxy```. Pada hasil keluaran sudah terdapat proxy kubectl yang akan digunakan untuk menjalankan proxy di terminal kedua

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/8.jpg)

#### Perintah ```curl http://localhost:8001/version``` akan melakukan eksplore API menggunakan curl saat proxy server sedang berjalan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/9.jpg)

#### Perintah ```export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')```. Proses tersebut akan melakukan proses untuk mendapatkan nama Pod dan meminta pod itu langsung melalui proxy.  dan kemudian menyimpannya dalam variabel POD_NAME

#### Perintah ```echo Name of the Pod: $POD_NAME```Sudah terdapat nama POD nya, yaitu  kubernetes-bootcamp-69fbc6f4cf-qgk9f.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/10.jpg)

## Viewing Pods and Nodes
### Step 1 Check application configuration

#### Perintah ```kubectl get pods``` akan melakukan cek pod yang sedang berjalan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/11.jpg)

#### Perintah ```kubectl describe pods``` akan menampilkan deskripsi dari pod yang sedang berjalan berupa nama namespace, priority, node (minikube yang berjalan pada IP 172.17.0.34), waktu mulai. Label, Anotasi, Status aktivitasnya, IP yang digunakan yaitu 172.18.0.4, ID container dan ID Image serta post untuk memanggilnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/12.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/13.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/14.jpg)

### Step 2 Show the app in the terminal

#### Perintah ```echo -e "\n\n\n\e[92mStarting Proxy. After starting it will not output a response. Please click the first Terminal Tab\n"; kubectl proxy``` akan melakukan pemanggilan kembali pods yang sedang berjalan di private network yang terisolasi, maka pada proses tersebut perlu mem-proxy akses ke sana agar kita bisa men-debug dan berinteraksi dengannya. Untuk melakukannya, akan digunakan perintah proxy kubectl untuk menjalankan proxy di terminal kedua

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/15.jpg)

#### Perintah ```export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')``` merupakan proses untuk melakukan export query yang akan ditempatkan pada proxy yang kemudian pada proses echo Name of the Pod: $POD_NAME akan memanggil nama pod tersebut kembali untuk melakukan cek nama pod tersebut.

```echo Name of the Pod: $POD_NAME```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/16.jpg)

#### Perintah ```curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/proxy/``` akan menjalankan container kubernetes pada port 8001vdiikuti dengan nama pod dan proxy bawaan

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/17.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/45.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/46.jpg)

### Step 3 View the container logs

#### Perintah ```kubectl logs $POD_NAME``` akan menampilkan log container.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/18.jpg)

### Step 4 Executing command on the container

#### Perintah```kubectl exec $POD_NAME env``` akan menjalankan command pada container sekaligus saat Pod sedang berjalan dengan menggunakan perintah exec

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/19.jpg)

```kubectl exec -ti $POD_NAME bash```

```cat server.js```
#### Perintah tersebut akan membuka console pada container saat menjalankan app NodeJS.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/20.jpg)

#### Perintah ```curl localhost:8080``` akan menjalankan container kubernetes pada port 8080

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/21.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/47.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/48.jpg)

## Exposing App

### Step 1 Create a new service

#### Perintah ```kubectl get services``` Akan menampilkan servis dengan nama kubernetes yang dimana servis tersebut merupakan servis default minikube saat minikube memulai klusternya.

#### Perintah ```kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080``` akan menampilkan default deploy dengan nama container kubernetes-bootcamp, dengan tipe NodePort yang akan berjalan pada port 8080

```kubectl get services```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/22.jpg)

#### Perintah ```kubectl describe services/kubernetes-bootcamp``` akan mencari tahu port berapa yang dibuka oleh NodePort

#### Perintah ```export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')```. Dengan menjalankan proses export, kita sekarang dapat menggunakan kubectl untuk mengukur jumlah replika. Melakukan penskalaan deploy akan meminta Kubernetes untuk meluncurkan Pod tambahan. Pod ini kemudian akan secara otomatis dimuat seimbang menggunakan Layanan yang terbuka

#### Perintah ```echo NODE_PORT=$NODE_PORT``` akan menampilkan port yang digunakan, yaitu 30237

#### Dengan perintah ```curl $(minikube ip):$NODE_PORT```, sekarang kita dapat menguji bahwa aplikasi terbuka di luar cluster menggunakan curl.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/23.jpg)

### Step 2: Using labels

#### Perintah ```kubectl describe deployment```untuk mencari tahu apa yang dibuat Kubernetes, kita bisa mendeskripsikan proses deployment. Deskripsi termasuk berapa banyak replika yang tersedia dan menampilkan masalah dan kesalahan yang mungkin terjadi. Pada langkah berikutnya kita akan mengekspos layanan yang sedang berjalan berupa nama namespace, priority, node (minikube yang berjalan pada IP 172.17.0.34), waktu mulai. Label, Anotasi, Status aktivitasnya, IP yang digunakan, ID container dan ID Image serta post untuk memanggilnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/24.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/25.jpg)

#### Perintah ```kubectl get pods -l run=kubernetes-bootcamp``` akan menggunakan kubectl get pods yang diikuti dengan I parameter, yang nantinya akan menjalankan image kubernetes-bootcamp.

#### Perintah ```kubectl get services -l run=kubernetes-bootcamp``` akan menjalankan servis yang diikuti dengan I parameter, yang nantinya akan menjalankan image kubernetes-bootcamp.

```export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')```

```echo Name of the Pod: $POD_NAME```
#### Proses tersebut akan melakukan export query yang akan ditempatkan pada proxy yang kemudian pada proses echo Name of the Pod: $POD_NAME akan memanggil nama pod tersebut kembali untuk melakukan cek nama pod tersebut.

#### Perintah ```kubectl label pod $POD_NAME app=v1``` akan menempatkan label baru yang diikuti berdasarkan tipe objek, nama objek, dan label baru.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/26.jpg)

#### Perintah ```kubectl describe pods $POD_NAME``` akan mencari tahu apa yang dibuat Kubernetes pada pod kubernetes-bootcamp, kita bisa mendeskripsikan proses deployment. Deskripsi termasuk berapa banyak replika yang tersedia dan menampilkan masalah dan kesalahan yang mungkin terjadi. 

#### Perintah ```kubectl get pods -l app=v1``` akan menggunakan kubectl get pods yang diikuti dengan I parameter, yang nantinya akan menjalankan app pada node part 1.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/27.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/28.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/29.jpg)

### Step 3 Deleting a service

#### Perintah ```kubectl delete service -l run=kubernetes-bootcamp``` akan menghapus service kubernetes-bootcamp yang telah dibuild pada step yang sudah dilakukan tadi.

#### Perintah ``` kubectl get services```akan melakukan cek untuk memastikan bahwa kubernetes-bootcamp telah terhapus.

#### Perintah ```curl $(minikube ip):$NODE_PORT``` untuk melakukan cek untuk memastikan bahwa route yang digunakan pada kubernetes-bootcamp telah tidak digunakan lagi.

#### Perintah ```kubectl exec -ti $POD_NAME curl localhost:8080``` untuk membuktikan bahwa aplikasi tidak dapat dijangkau lagi dari luar cluster. Kita lihat di sini bahwa aplikasi sudah tidak ada. Ini karena Deployment mengelola aplikasi. Untuk mematikan aplikasi, kita  harus menghapus Deploymentnya juga.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/30.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/49.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/50.jpg)

## Scaling App

### Step 1: Scaling a deployment

#### Perintah ```kubectl get deployments``` akan melakukan cek apakah masih ada servis yang dudeploy atau tidak. Ternyata masih terdapat servis kunernetes-bootcamp

```kubectl get rs```

#### Perintah tersebut akan melakukan pengecekan terhadap replika set deployment. Terdapat beberapa keterangan seperti : 
#### DESIRED yang berarti menampilkan jumlah replika aplikasi yang diinginkan, yang akan ditetapkan saat membuat deployment. Hal tersebut adalah kondisi yang diinginkan untuk proses deployment.
#### CURRENT yang berarti menampilkan berapa banyak replika yang sedang berjalan.

```kubectl scale deployments/kubernetes-bootcamp --replicas=4```

#### Pada proses tersebut akan melakukan penskalaan deployment kubernetes-bootcamp menjadi sebanyak 4 replika.

```kubectl get deployments```

#### Setelah dilakukan perintah tersebut kembali, maka pada servis yang di deploy menjadi 4 dan keempat servis tersebut merupakan hasl dari proses yang sebelumnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/31.jpg)

#### Perintah ```kubectl get pods -o wide``` akan menampilkan pods yang berjumlah 4 dari hasil penskalaan keempat replika tadi. Terdapat IP yang berbeda-beda, yaitu 172.18.0.7 untuk replika 1, 172.18.0.9 untuk replika 2, 172.18.0.2 untuk replika 3, 172.18.0.8 untuk replika 4.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/32.jpg)

```kubectl describe deployments/kubernetes-bootcamp```

#### Proses tersebut dijalankan untuk mencari tahu detail servis  kubernetes-bootcamp, kita bisa mendeskripsikan proses deployment. Deskripsi termasuk berapa banyak replika yang tersedia dan menampilkan masalah dan kesalahan yang mungkin terjadi. Pada langkah berikutnya kita akan mengekspos layanan yang sedang berjalan berupa nama namespace, priority, node), waktu mulai. Label, Anotasi, Status aktivitasnya, IP yang digunakan, ID container dan ID Image serta post untuk memanggilnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/33.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/34.jpg)

### Step 2: Load Balancing

```kubectl describe services/kubernetes-bootcamp```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/35.jpg)

```export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')```

#### Proses tersebut akan menjalankan proses export, dimana sekarang dapat menggunakan kubectl untuk mengukur jumlah replika (sebanyak 4 replika). Melakukan penskalaan deploy akan meminta Kubernetes untuk meluncurkan Pod tambahan. Pod ini kemudian akan secara otomatis dimuat seimbang menggunakan Layanan yang terbuka.

```echo NODE_PORT=$NODE_PORT```

#### Proses tersebut akan menampilkan port yang digunakan oleh node, yaitu 32395.

#### Perintahn```curl $(minikube ip):$NODE_PORT``` akan melakukan cek untuk memastikan bahwa route yang digunakan pada kubernetes-bootcamp telah tidak digunakan lagi.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/36.jpg)

### Step 3: Scale Down

```kubectl scale deployments/kubernetes-bootcamp --replicas=2```

#### Akan melakuam penskalaan servis kubernetes-bootcamp pada replika nomor 2. Proses ini nantinya akan menjalankan servis kubernetes-bootcamp yang terdapat pada replika nomor 2.

#### Perintah ```kubectl get deployments```, servis yang di deploy menjadi servis nomor 2  setelah dilakukan penskalaan pada replika 2.

#### Perintah ```kubectl get pods -o wide``` akan menampilkan pods yang berjumlah 4 dari hasil penskalaan keempat replika tadi. Terdapat IP yang berbeda-beda, yaitu 172.18.0.7 untuk replika 1, 172.18.0.9 untuk replika 2, 172.18.0.2 untuk replika 3, 172.18.0.8 untuk replika 4.  Yang berjalan adalah replika 2 dan 3, sedangkan replika 1 dan 4 di terminate, karena akibat dari dilakukannya penskalaan pada replika 2.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/37.jpg)

## Update App

### Step 1: Update the version of the app

#### Perintah ```kubectl get deployments``` akan melakukan cek deployments, dimana masih terdapat 4 replika yang dideploy.

#### Perintah ```kubectl get pods``` akan menampilkan keempat identitas replika yan statusnya masih running semua. Ini menandakan bahwa keempat replika tersebut masih aktif.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/38.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)

#### Perintah ```kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2```. Proses tersebut akan melakukan update image pada aplikasi menjadi versi ke 2 dengan menggunakan image yang bersumber dari jocatalin/kubernetes-bootcamp:v2.
 
```kubectl get pods```

#### Setelah dilakukan perintah tersebut kembali, ternyata masih menampilkan keempat identitas replika yan statusnya masih running semua.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/40.jpg)

### Step 2: Verify an update

#### Perintah ```kubectl describe services/kubernetes-bootcamp```. Proses tersebut menampilkan detail yang hampir sama pada step sebelumnya. Hanya saja pada proses kali ini menampilkan keseluruhan pods yang antara lain:
#### kubernetes-bootcamp-7d6f8694b6-6p6zt   1/1     Running   0          82s
#### kubernetes-bootcamp-7d6f8694b6-b4j2b   1/1     Running   0          76s
#### kubernetes-bootcamp-7d6f8694b6-nv4bw   1/1     Running   0          76s
#### kubernetes-bootcamp-7d6f8694b6-vqkqq   1/1     Running   0          83s
#### dan selanjutnya juga menampilkan keempat Endpoints 172.18.0.10:8080,172.18.0.11:8080,172.18.0.12:8080, 172.18.0.13:8080

````export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')```

```$ echo NODE_PORT=$NODE_PORT```

#### Proses tersebut akan melakukan export query yang akan ditempatkan pada proxy yang kemudian pada proses echo Name of the Pod: $POD_NAME akan memanggil nama pod tersebut kembali untuk melakukan cek nama pod tersebut. Selanjutnya akan menggunakan kubectl get pods yang diikuti dengan I parameter, yang nantinya akan menjalankan image kubernetes-bootcamp

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/41.jpg)

#### Perintah ```curl $(minikube ip):$NODE_PORT``` akan melakukan cek untuk memastikan berapa IP dan Port yang digunakan.

#### Perintah ```kubectl rollout status deployments/kubernetes-bootcamp```,proses tersebut digunakan untuk konfirmasi update penggantian Pod yang dilakukan


![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/42.jpg)

#### Perintah ```kubectl describe pods```, Setelah dilakukan lagi proses tersebut, proses tersebut menampilkan 2 detail deskripsi ods yang berjalan secara bersamaan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)

###  Step 3: Rollback an update

```kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=gcr.io/google-samples/kubernetes-bootcamp:v10```

#### Pada hasil perintah tersebut sudah ada google-samples/kubernetes-bootcamp:v10Akan melakukan skala angka container dalam service sleep-app . Replika adalah istilah yang digunakan untuk menggambarkan container identik yang menyediakan layanan yang sama.

```kubectl get deployments```
#### Setelah dilakukan perintah tersebut kembali, maka pada servis yang di deploy menjadi 4 dan yang berjalan hanya 3 dari keempat servis tersebut

```kubectl get pods```

#### Setelah dilakukan perintah tersebut kembali, ternyata dihasilkan servis sebanyak 5  servis dan yang berjalan sebanyak 3 servis. Servis tersebut merupakan replika dari kubernetes-bootcamp.    

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/43.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)

```kubectl rollout undo deployments/kubernetes-bootcamp```

#### Karena image v10 tidak ada di dalam epositori, maka harus dilakukan roll back agar kita bisa mmenjalankan pada versi yang ditentukan. Perintah rollout mengembalikan deployment ke kondisi yang diketahui sebelumnya (image v2). Pembaruan diversi dimana kita  dapat kembali ke status Penerapan yang sebelumnya telah diketahui.

```kubectl get pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/44.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/51.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/52.jpg)