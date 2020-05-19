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

```kubectl get pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/11.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/12.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/13.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/14.jpg)

### Step 2 Show the app in the terminal

```echo -e "\n\n\n\e[92mStarting Proxy. After starting it will not output a response. Please click the first Terminal Tab\n"; kubectl proxy```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/15.jpg)

```export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')```

```echo Name of the Pod: $POD_NAME```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/16.jpg)

```curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/proxy/```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/17.jpg)

### Step 3 View the container logs

```kubectl logs $POD_NAME```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/18.jpg)

### Step 4 Executing command on the container

```kubectl exec $POD_NAME env```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/19.jpg)

```kubectl exec -ti $POD_NAME bash```

```cat server.js```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/20.jpg)

```curl localhost:8080```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/21.jpg)

## Exposimg App

### Step 1 Create a new service

```kubectl get services```

```kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080```

```kubectl get services```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/22.jpg)

```kubectl describe services/kubernetes-bootcamp```

```export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')```

```echo NODE_PORT=$NODE_PORT```

```curl $(minikube ip):$NODE_PORT```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/23.jpg)

### Step 2: Using labels

```kubectl describe deployment```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/24.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/25.jpg)

```kubectl get pods -l run=kubernetes-bootcamp```

```kubectl get services -l run=kubernetes-bootcamp```

```export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')```

```echo Name of the Pod: $POD_NAME```

```kubectl label pod $POD_NAME app=v1```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/26.jpg)

```kubectl describe pods $POD_NAME```

```kubectl get pods -l app=v1```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/27.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/28.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/29.jpg)

### Step 3 Deleting a service

```kubectl delete service -l run=kubernetes-bootcamp```

``` kubectl get services```

```curl $(minikube ip):$NODE_PORT```

```kubectl exec -ti $POD_NAME curl localhost:8080```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/30.jpg)

## Scaling App

### Step 1: Scaling a deployment

```kubectl get deployments```

```kubectl get rs```

```kubectl scale deployments/kubernetes-bootcamp --replicas=4```

```kubectl get deployments```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/31.jpg)

```kubectl get pods -o wide```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/32.jpg)

```kubectl describe deployments/kubernetes-bootcamp```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/33.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/34.jpg)

### Step 2: Load Balancing

```kubectl describe services/kubernetes-bootcamp```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/35.jpg)

```export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')```

```echo NODE_PORT=$NODE_PORT```

```curl $(minikube ip):$NODE_PORT```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/36.jpg)

### Step 3: Scale Down

```kubectl scale deployments/kubernetes-bootcamp --replicas=2```

```kubectl get deployments```

```kubectl get pods -o wide```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/37.jpg)

## Update App

### Step 1: Update the version of the app

```kubectl get deployments```

```kubectl get pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/38.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)

```kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2```

```kubectl get pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/40.jpg)

### Step 2: Verify an update

```kubectl describe services/kubernetes-bootcamp```

````export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')```

```$ echo NODE_PORT=$NODE_PORT```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/41.jpg)

```curl $(minikube ip):$NODE_PORT```

```kubectl rollout status deployments/kubernetes-bootcamp```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/42.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)

###  Step 3: Rollback an update

```kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=gcr.io/google-samples/kubernetes-bootcamp:v10```

```kubectl get deployments```

```kubectl get pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/43.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)

```kubectl rollout undo deployments/kubernetes-bootcamp```

```kubectl get pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/44.jpg)

```kubectl describe pods```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/39.jpg)