## Create a Cluster
``` minikube version```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/1.jpg)

```minikube start```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/2.jpg)

``` kubectl version```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/3.jpg)

```kubectl cluster-info```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/4.jpg)

```kubectl get nodes```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/5.jpg)

## Create a Deployment

```kubectl version```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/3.jpg)

```kubectl get nodes```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/5.jpg)

### Deploy App
```kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/6.jpg)

```kubectl get deployments```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/7.jpg)

### View App

#### We will open a second terminal window to run the proxy.
```echo -e "\n\n\n\e[92mStarting Proxy. After starting it will not output a response. Please click the first Terminal Tab\n"; ```

```kubectl proxy```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/8.jpg)

```curl http://localhost:8001/version```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-13/9.jpg)

```export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')```

```echo Name of the Pod: $POD_NAME```

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