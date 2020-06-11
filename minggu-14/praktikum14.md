### Start the cluster

```ls```

```kubeadm init --apiserver-advertise-address $(hostname -i)```

#### Proses melakukan inisiasi alamat cluster. Alamat IP cluster yang terdapat da;am hostname merupakan alamat IP cluster yang akan diadvertise oleh Server API. Jika tidak disetel, antarmuka jaringan default akan digunakan, seperti pada hasil proses ini, alamat IP yang digunakan adalah alamat default, yaitu 127.17.0.73.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/1.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/2.jpg)

``` kubeadm join 172.17.0.73:6443 --token abpr7a.6crccv8u6h55taan \--discovery-token-ca-cert-hash sha256:3c2d18b83207ffba89206eec9a5bc8e21d238b2ba0d07884f05297b1a7256906```

#### proses tersebut dilakukan agar user dapat melakukan join oada kubeadm. Setiapu user melakukan join menggunakan token dan hash yang didapatkan dari proses kubeadm init yang dilakukan sebelumnya. Proses yang dilalui antara lain Melewati pemeriksaan pre flight, mencoba menyambung ke Server API yang telah disetting, meminta info dari cluster https://172.26.0.2:6443, meminta info dari "https://172.26.0.2:6443" lagi untuk memvalidasi TLS terhadap kunci public yang disisipkan, menandai info kluster dan kontennya valid dan sertifikat TLS memvalidasi terhadap root yang disisipkan, akan menggunakan API Server "172.26.0.2:6443", lalu yang terakhir terdapat keterangan berhasil membangun koneksi dengan API Server "172.26.0.2:6443"

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/3.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/4.jpg)

```sudo cp /etc/kubernetes/admin.conf $HOME/```

```sudo chown $(id -u):$(id -g) $HOME/admin.conf```

```export KUBECONFIG=$HOME/admin.conf```

```cat /opt/weave-kube```

#### Pada prosess tersebut,client melakukan konfigurasi. Untuk melakukan konfigurasi, maka kubeadm harus melakukan inisiasi cluseter. Perintah tersebut mencopy konfigurasi ke direktori home pengguna dan menetapkan variabel environment untuk digunakan dengan CLI.

#### Perintah ``` kubectl apply -f /opt/weave-kube```, proses tersebut akan melakukan pengunduhan weave cube

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/5.jpg)

#### Perintah ``` kubectl get nodes ```pada hasil proses tersebut, menandakan sudah terdapat 2 node pada cluster yang telah dibuat

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/6.jpg)

#### Perintah ``` kubectl apply -n kube-system -f \    "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 |tr -d '\n')" ``` merupakan proses melakukan inisialisasi jaringan cluster yang akan digunakan. Container jaringan yang digunakan adalah weave. Weave sendiri digunakan untuk mengatasi masalah kluster Kubernetes saat user menyiapkan dan mengkonfigurasinya. Cara kerjanya weave  akan deploy Sock Shop, aplikasi layanan microser, ke dalamnya, dan dengan Weave Scope dan weave  akan menjelajahi layanan microser saat dijalankan di Kubernetes.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/7.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_29.jpg)

#### Perintah ```kubectl create deployment http --image=katacoda/docker-http-server:latest``` merupakan proses menggunakan Kubectl untuk menggunakan pod. Perintah tersebut akan membuat Pod berdasarkan pada Docker Image katacoda / docker-http-server.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_30.jpg)

#### Perintah ```kubectl get pods``` merupakan proses yang dilakukan untuk melihat pembuatan Pod, sudah terdapat pods yang akan digunakan untuk cluster.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_31.jpg)

#### Perintah ```docker ps | grep docker-http-server```pada proses tersebut terlihat bahwa container yang dideploy sudah berjalan pada node.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_32.jpg)

#### Perintah ```kubectl apply -f dashboard.yaml``` merupakan proses untuk melakukan deploy dashboard yaml pada cluster. Dashboard Kubernetes dapat digunakan untuk mendeploy aplikasi yang tercontainer ke Kubernetes cluster. Kita dapat memecahkan masalah aplikasi yang tercontainer dan sumber daya cluster dapat diatur. Kita dapat menggunakan dashboard Kubernetes untuk mendapatkan gambaran umum yang jelas tentang aplikasi yang berjalan di cluster.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_33.jpg)

#### Perintah ```kubectl get pods -n kube-system```merupakan proses yang dijalankan untuk mencari tahu detail servis  kube-system, kita bisa mendeskripsikan proses deployment. Deskripsi termasuk berapa banyak replika yang tersedia dan menampilkan masalah dan kesalahan yang mungkin terjadi. Pada langkah berikutnya kita akan mengekspos layanan yang sedang berjalan berupa nama namespace, priority, node), waktu mulai.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_34.jpg)

#### Perintah ```cat <<EOF | kubectl create -f -``` merupakan proses yang akan menampilkan status deployment yang dilakukan. Dashboardnya sendoro dideploy di dalam kube-system namespace. Pada proses tersebut diperlukan ServiceAccount untuk masuk. ClusterRoleBinding digunakan untuk menetapkan ServiceAccount baru (admin-pengguna) peran cluster-admin pada cluster. Ini berarti mereka dapat mengontrol semua aspek Kubernetes. Dengan ClusterRoleBinding dan RBAC, tingkat izin yang berbeda dapat ditentukan berdasarkan persyaratan keamanan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_35.jpg)

#### Perintah ```kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')``` merupakan proses yang akan menampilkan token untuk login. Ketika dashboard digunakan, itu menggunakan eksternalIP untuk mengikat layanan ke port 8443. Ini membuat dashboard tersedia untuk di luar cluster dan dapat dilihat di hasil dibawah.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_36.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_37.jpg)

### Getting the application source code

``` git clone https://github.com/dockersamples/dockercoins```

#### Pada perintah tersebut melakukan clone Link dockercoins dari github. Link dockercoins sendiri merupakan aplikasi yang akan melakukan scraping link dari suatu halaman web.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/8.jpg)

### Running the application

``` cd ~/dockercoins ```

#### cd ~/dockercoins masuk ke direktory dockercoins

``` docker-compose up```

#### Setelah proses tersebut dijalankan, hasilnya menunjukkan bahwa Docker Compose secara otomatis membuat jaringan bernama dockercoins_default, lalu selanjutnya  Docker Compose melakukan pull image php: 7-apache dari DockerHub, lalu selanjutnya melakukan build image redis menggunakan Dockerfile, dan akhirnya, Docker Compose menjalankan container Dockercoin yang merupakan container untuk minning seperti trading, bitcoins.
#### Pada tampilan tersebut merupakan hasil dari Dockercoins. Dockercoins  sendiri terbuat dari 5 layanan:
#### rng = layanan web yang menghasilkan byte acak
#### hasher = hash komputasi layanan web dari data POSTed
#### worker = proses latar belakang memanggil rng dan hasher
#### webui = antarmuka web untuk melihat progress
#### redis = penyimpanan data (melakukan penghitungan yang diperbarui oleh worker)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/9.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/14.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/15.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/16.jpg)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/10.jpg)

## First contact with kubectl
### kubectl get

```kubectl get no```

```kubectl get node```

```kubectl get nodes```

#### Perintah tersebut digunakan untuk melihat daftar node yang terdapat pada cluster yang kita buat.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/11.jpg)

### Obtaining machine-readable output

#### Perintah ```kubectl get nodes -o wide``` digunakan untuk melihat daftar node yang terdapat pada cluster yang kita buat.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/12.jpg)

#### Perintah ```kubectl get no -o yaml``` digunakn untuk melihat informasi yaml yang terdapat pada cluster yang kita buat. Untuk informasi yang dimuat antara lain apiVersion, Items, kind, metadata, annotations/anotasi yag menggunakan cri-socket meaty, creationTimestamp, labels, dan masih banyak lagi.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/13.jpg)

### (Ab)using kubectl and jq

#### Perintah ```kubectl get nodes -o json |```

#### ```      jq ".items[] | {name:.metadata.name} + .status.capacity"``` merupakan proses untuk menampilkan kapasitas semua node yangdibungkussebagai aliran objek JSON.  Node yang ditampilkan adalah master dan node1. Informasi yang ditampilkan antara lainL name, cpu, ephemeral-sorage, hugepages-1Gi, hugepages-2Mi, memory, pods.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/17.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/18.jpg)
### What’s available?

#### Perintah ```kubectl describe nodes master```untuk melakukan deskripsi coomand dengan verbose output. Untuk mencari tahu apa yang dibuat Kubernetes, kita bisa mendeskripsikan proses deployment. Deskripsi termasuk berapa banyak replika yang tersedia dan menampilkan masalah dan kesalahan yang mungkin terjadi. Pada langkah berikutnya kita akan mengekspos layanan yang sedang berjalan berupa nama namespace, priority, node (minikube yang berjalan pada IP 172.17.0.34), waktu mulai. Label, Anotasi, Status aktivitasnya, IP yang digunakan, ID container dan ID Image serta post untuk memanggilnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_42.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_43.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_44.jpg)

### Services

#### Proses tersebut dijalankan untuk mencari tahu detail servis  master, kita bisa mendeskripsikan proses deployment. Deskripsi termasuk berapa banyak replika yang tersedia dan menampilkan masalah dan kesalahan yang mungkin terjadi. Pada langkah berikutnya kita akan mengekspos layanan yang sedang berjalan berupa nama namespace, priority, node), waktu mulai. Label, Anotasi, Status aktivitasnya, IP yang digunakan, ID container dan ID Image.

#### Perintah ```kubectl get services``` dan ```kubectl get svc``` digunakan untuk menampilkan servis dengan nama kubernetes yang dimana servis tersebut merupakan servis default minikube saat minikube memulai klusternya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/19.jpg)

### ClusterIP services

```curl -k https://10.96.0.1```
#### Sekarang kita dapat menguji bahwa aplikasi terbuka di luar cluster menggunakan curl. -k digunakan untuk melewati verifikasi sertifikat. Selain itu curl digunakan untuk mengganti 10.96.0.1 dengan CLUSTER-IP.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/20.jpg)

### Listing running containers

### Perintah ```kubectl get pods``` pods belum ada, karena belum diberikan pada cluster tersebut

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_45.jpg)

### Namespaces
#### Namespaces adalah cara untuk membagi sumber daya cluster antara beberapa pengguna (melalui kuota sumber daya). Dalam versi Kubernetes yang akan datang, objek di namespace yang sama akan memiliki kebijakan kontrol akses yang sama secara default. Tidak perlu menggunakan banyak ruang nama hanya untuk memisahkan sumber daya yang sedikit berbeda, seperti versi berbeda dari perangkat lunak yang sama dan menggunakan label untuk membedakan sumber daya dalam namespace yang sama.

```kubectl get namespaces```

```kubectl get namespace```

```kubectl get ns```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/21.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/22.jpg)

### Accessing namespaces

#### Perintah ```kubectl -n kube-system get pods``` akan memberikan informasi mengenai list pods yang sedang berjalan, -n akan memberikan keterangan nama pods beserta dengan statusnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/23.jpg)

### Starting a simple pod with kubectl run

#### Perintah ```kubectl run pingpong --image alpine ping 8.8.8.8``` akan melakukan ping ke 8.8.8.8, yaitu Google DNS. Ping tersebut dilakukan dari image alpine. Hasilnya deployment yang sebelumnya akan terdeprecated dan akan dihapus, yan selanjutnya akan diganti dengan deployment yang baru.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/24.jpg)

### Behind the scenes of kubectl run

#### Perintah ```kubectl get all``` akan menampilkan informasi deployment. Proses ini akan menghasilkan informasi seperti
#### deploy / pingpong akan menampilkan deployment yang baru saja kita buat
#### rs / pingpong-xxxx akan menampilkan set replika yang dibuat oleh deployment
#### po / pingpong-yyyy akan menampilkan pod yang dibuat oleh set replika

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/25.jpg)

### Viewing container output

#### Perintah ```kubectl logs deploy/pingpong```akan melakukan cek status log darip deployment pingpong

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/26.jpg)

### Streaming logs in real time

#### Perintah ```kubectl logs deploy/pingpong --tail 1 --follow``` akan melakukan pemanggilan kembali pods yang sedang berjalan di private network yang pingpong, maka pada proses tersebut perlu mem-proxy akses ke sana agar kita bisa men-debug dan berinteraksi dengannya. Untuk melakukannya, akan digunakan perintah proxy kubectl untuk menjalankan proxy di terminal kedua

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_46.jpg)

### Scaling our application

#### Perintah ```kubectl scale deploy/pingpong --replicas 8``` akan melakukan scaling dari depoloyment pingpong dengan 8 replika. 

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/27.jpg)

### Resilience

#### Perintah ```kubectl get pods -w```, Setelah dilakukan perintah tersebut kembali, maka pada servis yang di deploy menjadi 8 dan keempat servis tersebut merupakan hasil dari proses yang sebelumnya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/28.jpg)

### Viewing logs of multiple pods

#### Perintah ```kubectl logs -l run=pingpong --tail 1``` akan menampilkan deskripsi dari pingpong --tail 1yang sedang berjalan berupa nama namespace, priority, node (minikube yang berjalan pada IP 8.8.8.8), seq, ttl, time.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/29.jpg)

### Clean-up

#### Perintah ```kubectl delete deploy/pingpong``` akan menghapus container pingpong dari deployan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/30.jpg)

### Running containers with open ports

#### Perintah ```kubectl run elastic --image=elasticsearch:2 --replicas=4``` proses tersebut akan menjalankan  container elasticsearch. Elasticsearch dapat memakan memori yang besar dan berat karena mengurutkan dan mengumpulken data, jadi ketika dijalankan pada Kubernetes, maka yang diperlukan hanya komputer memiliki cukup memori untuk menjalankan Kubernetes, alat manajemen data, dan Elasticsearch itu sendiri.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/31.jpg)

### Exposing our deployment

#### Perintah ```kubectl expose deploy/elastic --port 9200``` proses tersebut akan membuat objek service yang mengekspos deployment dari elasticsearch pada port 9200

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/32.jpg)

### Testing our service

#### Perintah ```IP=$(kubectl get svc elastic -o go-template --template '{{ .spec.clusterIP }}')``` Proses tersebut dilakukan untuk mendapatkan alamat IP yang akan dialokasikan untuk proses deploy elasticsearch.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_55.jpg)

#### Perintah ``` curl http://$IP:9200/``` Akan mengirimkan rekuest ke port 9200. Hasilnya didapatkan IP 10.107.164.154 dengan nama Monica Rappaccini, dengan cluster name elasticsearch, terdapat cluster uuid. Dan nomor versi serta leterangan dari build version tersebut.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_56.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_57.jpg)

### Clean up

#### Perintah ```kubectl delete deploy/elastic``` Akan menghapus container elastic dari deployan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_58.jpg)

### Setup 

#### Perintah ```export USERNAME=tyassasmita``` untuk melakukan export username akun dockerhub. Ini akan digunakan untuk penyimpanan hasil deploy ke dockerhub.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/33.jpg)

### Building and pushing our images

#### Perintah ```cd ~/dockercoins/stacks``` untuk masuk ke subdirektory stacks pada direktory dockercoins yang di clone. Didalam stacks tersebut nantinya akan menjalankan file dockercoins.yml

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/34.jpg)

```docker-compose -f dockercoins.yml build```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/35.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/36.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/37.jpg)
#### Proses tersebut akan melakukan build  image dockercoins dengan menjalankan file dockercoins.yml
#### Step 1/5, dari image python:alpine , akan melakukan pull dari library python
#### Step 2/5, akan melakukan instalasi yang dibutuhkan pada proses build container pada requirements.txt, yaitu flask dan redis dengan menggunakan pip, dengan melakukan download flask framework dan redis dan beberapa package pendukungnya. Setelah didwonload, maka dilakukan build MarkupSafe dan dilakukan proses install
#### Step 3/5, akan menjalankan enfironment flask framework pada app.py
#### Step 4/5, pada environment flask menjalankan host 0.0.0.0
#### Step 5/5, akan mencopy apa yang dibutuhkan pada proses build container pada requirements.txt, yaitu flask dan redis

```docker-compose -f dockercoins.yml push```
#### Hasil dari build diatas kemudian akan dipush ke akun Dockerhub yang telah diexport tadi. Hal ini dilakukan supaya hasilnya dapat terdaftar pada Dockerhub.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/38.jpg)

### Deploying all the things

#### Perintah ```kubectl run redis --image=redis``` merupakan proses  untuk menjalankan image redis dari Dockerhub(disini dari flask melakukan import flask dan request) lalu juga melakukan import linkextractor. Proses ini akan  membuat layanan untuk menghubungkan ke instance Redis karena akan menggunakan redis untuk melakukan caching. Informasi ini dapat tersedia pada saat dijalankan menggunakan environment variabel REDIS_URL. Entri ENV yang sesuai juga ditambahkan di Dockerfile dari layanan API dengan nilai default. Contoh client redis dibuat menggunakan redis host name dan port Redis default 6379.

```for SERVICE in hasher rng webui worker; do```

```  kubectl run $SERVICE --image=$USERNAME/$SERVICE -l app=$SERVICE```

```done```
#### Pada proses tersebut akan memberikan komponen pada deploy redis dengan memberi worker, dan menjalankan perintah programming untuk menjalankan image berdasarkan username dockerhub yang telah diekspor.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/39.jpg)

### Is this working?

#### Perintah ```kubectl logs deploy/rng``` akan melakukan cek logs app rng, dimana rng tersebut berjalan pada alamat 0.0.0.0:80

#### Perintah ```kubectl logs deploy/worker``` akan melakukan cek logs node worker.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/40.jpg)

## Exposing services
### Exposing services internally

#### Perintah ```kubectl expose deployment redis --port 6379```, Deployment dari redis tersebut agar host Docker dapat mengakses port container pada network 6379 ini harus di expose portnya atau di open lewat firewall.

#### Perintah ```kubectl expose deployment rng --port 80```, Deployment dari rng tersebut agar host Docker dapat mengakses port container pada network 80 ini harus di expose portnya atau di open lewat firewall. 

#### Perintah ```kubectl expose deployment hasher --port 80```, Deployment dari hasher tersebut agar host Docker dapat mengakses port container pada network 80 ini harus di expose portnya atau di open lewat firewall.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/41.jpg)

### Is this working yet?

#### ```kubectl logs deploy/worker --follow``` tunggu revocer hingga 10 menit
#### Pada proses tersebut ketika dijalankan akan terjadi error dan worker secara otomatis melakukan looping tak terbatas, lalu selanjutnya worker akan melakukan recovery hingga waktu 10 menit.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/42.jpg)

### Exposing services for external access

#### Perintah ```kubectl create service nodeport webui --tcp=80 --node-port=30001```, proses tersebut dilakukan ketika kita akan mengakses web UI yang kita deploy. Pada proses tersebut akan mengekspose nodeport dengan port 30001. Nah port tersebutlah yang akan digunakan untuk sebagai service dari web Ui tersebut.

#### Perintah ``kubectl get svc``` digunakan untuk menampilkan servis dengan nama kubernetes yang dimana servis tersebut merupakan servis default minikube saat minikube memulai klusternya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/43.jpg)

### Scaling a deployment

#### Perintah ```kubectl get pods``` akan melakukan cek pod yang sedang berjalan, pada hasilnya terdapat beberapa pods dari deployment termasuk yang sebelumnya dijalankan, yaitu webui.

#### Perintah ```kubectl get deployments``` akan melakukan cek apakah masih ada servis yang dideploy atau tidak. Deployment yang akan digunakan pada proses kali ini adalah deployment worker.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/44.jpg)

#### Perintah ```kubectl scale deploy/worker --replicas=10``` akan melakukan scaling dari depoloyment worker dengan 10 replika. Setelah dilakukan perintah tersebut kembali, maka pada servis yang di deploy menjadi 10 replika dan semua servis tersebut merupakan hasil dari proses kubectl scale.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/45.jpg)

### Creating a daemon set

```kubectl apply -f foo.yaml```
#### proses tersebut error dan tidak dapat dilakukan, karena pada Kubernetes 1.9, CLI tidak dapat membuat set daemon. Lebih tepatnya ia tidak memiliki sub perintah untuk membuat set daemon

```kubectl get deploy/rng -o yaml --export >rng.yml```
#### Proses tersebut akan melakukan dump rng resource pada YAML. Proses ini nantinya sebagai permulaan dari proses pembuatan YAML file untuk daemon set. –export akan mengapus informasi  cluster-specific yang antara lain: namespace, statis dam waktu pembuatam, resource version dan uid

```kubectl apply -f rng.yml```
#### proses tersebut akan membuat resource baru rng.yml. pada keterangan menunjukan bahwa kubetcl apply harus digunakan pada resource yang dibuat oleh antara kubetcl create –save-config atau kubetcl apply

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/46.jpg)

### Use the --force, Luke

```kubectl apply -f rng.yml --validate=false```
#### proses tersebut akan membuat resource baru rng.yml dengan menambahkan –force yang berarti dengan menambahkan –force tersebut, maka perintah akan memberi tahu Kubernetes untuk mengabaikan kesalahan dan tetap menjalankan proses.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/48.jpg)

### Checking what we’ve done

#### Perintah ```kubectl get all``` akan menampilkan semua resource deployment. Pada hasil terlihat bahwa deploy/rng dan ds/rng telah berhasi diberikan dan menandakan bahwa kita tetap punya deployment rng yang lama dan juga punya deployment rng yang baru. Jika kita melihat podnya, kita memiliki: satu pod untuk deploymentdan satu pod per node untuk keperluan daemonset.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/49.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/50.jpg)

### Deep dive into selectors

```kubectl describe deploy rng```
#### proses tersebut akan menampilkan detail informasi mengenai rng deployment. Detail informasi termasuk berapa banyak replika yang tersedia dan menampilkan masalah dan kesalahan yang mungkin terjadi. Pada langkah berikutnya kita akan mengekspos layanan yang sedang berjalan berupa nama namespace, priority, node, waktu mulai. Label, Anotasi, Status aktivitasnya, IP yang digunakan, ID container dan ID Image serta post untuk memanggilnya, bahkan keterangan nama akun dockerhub yang mendeploy rng tersebut pun dimunculkan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/51.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/52.jpg)

```kubectl describe rs rng-yyyy```
#### proses tersebut akan menampilkan detail informasi mengenai replika dari rng. Namun karena tidak terdapat replika, maka proses ini tidak dapat berjalan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/53.jpg)

### Adding our label

```kubectl edit daemonset rng```
#### Pada proses ini akan dilakukan update pada daemonset rng menggunakan perintah kubetcl edit. Perintah editnya pun sama seperti text editor pada umumnya, yaitu dengan menekan shift+i untuk insert/edit, escape untuk keluar dari mode edit. Akan diberikan komponen tambahan berupa isactive: "yes". isactive: "yes" akan menandakan bahwa rng tersebut aktif dan akan siap dijalankan.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_80.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_81.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_82.jpg)

### Checking what we’ve done

#### Perintah ```kubectl logs -l run=rng```, akan melakukan cek logs app rng yang sedang berjalan, untuk mengkonfirmasi bahwa hanya kedua rng yang aktif

#### Perintah ```kubectl get pods``` akan melakukan cek pod yang sedang berjalan, pada hasilnya terdapat beberapa pods dari deployment termasuk yang sebelumnya dijalankan dan rng lama maupun yang baru.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_83.jpg)

### Building a new version of the worker service


```export TAG=v0.2```
#### proses tersebut akan melakukan ekspor tag baru, yaitu v0.2 pada worker untuk melakukan update versi baru pada worker.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_84.jpg)

```docker-compose -f dockercoins.yml build```
#### Proses tersebut akan melakukan build  image dockercoins dengan menjalankan file dockercoins.yml

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_85.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_86.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_87.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_88.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_89.jpg)

#### Step 1/5, dari image python:alpine , akan melakukan pull dari library python
#### Step 2/5, akan melakukan instalasi yang dibutuhkan pada proses build container dengan menggunakan pip, dengan melakukan download flask framework dan redis dan beberapa package pendukungnya. Setelah didwonload, maka dilakukan build MarkupSafe dan dilakukan proses install
#### Step 3/5, akan melakukan instalasi yang dibutuhkan pada proses build container dengan menggunakan pip, dengan melakukan download request dan kemudian menginstallnya
#### Step 4/5, akan melakukan copy file worker.py
#### Step 5/5, akan menjalankan file worker.py
#### 8 step, menggunakan ruby
#### Step 1/8, dari image ruby:alpine , akan melakukan pull dari library ruby
#### Step 2/8, akan menjalanken update app dengan update build-base curl
#### Step 3/8, akan melakukan instalasi yang dibutuhkan pada proses build container yaitu dependency sinatra melalui command gem
#### Step 4/8, akan melakukan instalasi yang dibutuhkan pada proses build container yaitu dependency sinatra melalui command thin
#### Step 5/8, menambahkan hasher
#### Step 6/8, akan menjalankan file hasher.rb 
#### Step 7/8, akan melakukan ekspose pada port 80, supaya container berjalan pada port 80
#### Step 8/8, memberikan keterangan bahwa build telah berhasil dilakukan
#### 7 step, menggunakan js
#### Step 1/7, akan mengambil image dari node:4-slim
#### Step 2/7, akan melakukan instalasi yang dibutuhkan pada proses build container yaitu framework express dengan instalasi menggunakan perintah npm
#### Step 3/7, akan melakukan instalasi yang dibutuhkan pada proses build container yaitu framework redis dengan instalasi menggunakan perimtah npm
#### Step 4/7, akan melakukan copy pada direktory files
#### Step 5/7, akan melakukan copy file webui.js
#### Step 6/7, akan menjalankan file webui.rb 
#### Step 7/7, akan melakukan ekspose pada port 80, supaya container berjalan pada port 80

```docker-compose -f dockercoins.yml push```
#### Hasil dari build diatas kemudian akan dipush ke akun Dockerhub yang telah diexport tadi. Hal ini dilakukan supaya hasilnya dapat terdaftar pada Dockerhub.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_90.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_91.jpg)

### Rolling out the new worker service

```kubectl get pods -w```
#### akan melakukan cek pod yang sedang berjalan pada worker, pada hasilnya terdapat beberapa pods dari deployment termasuk yang sebelumnya dijalankan dan rng lama maupun yang baru.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_92.jpg)

#### Perintah ```kubectl get replicasets -w``` digunakan untuk menghilangkan deploy replikasi sehingga mejadi 5 servis utama dan akan melakukan cek replicasets yang sedang berjalan pada worker, pada hasilnya terdapat beberapa replicasets dari deployment yaitu hasher, redis, rng,webui, dan worker dengan masing-masing kode nya.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_93.jpg)

#### Perintah ```kubectl get deployments -w```untuk mendapatkan semua deployment yang telah dibuat dan akan melakukan cek deployments yang sedang berjalan pada worker, pada hasilnya terdapat beberapa deployments dari deployment yaitu hasher, redis, rng,webui, dan worker.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_94.jpg)

```kubectl set image deploy worker worker=$USERNAME/worker:$TAG```
#### Proses tersebut digunakan untuk memperbarui worker username yang telah dideploy. proses tersebut akan melakukan update worker dengan melakukan set image worker yang menggunakan username dockerhub diikuti tag dari worker itu sendiri

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_96.jpg)

### Rolling out an error

```export TAG=v0.3```
#### proses tersebut akan melakukan ekspor tag baru, yaitu v0.3 pada worker untuk melakukan update versi baru pada worker.

```kubectl set image deploy worker worker=$REGISTRY/worker:$TAG```
#### Proses tersebut digunakan untuk memperbarui worker image register yang telah dideploy.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_97.jpg)

#### Perintah ```kubectl rollout status deploy worker``` digunakan untuk mengecek apakah Deployment telah selesai.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-14/Screenshot_98.jpg)

