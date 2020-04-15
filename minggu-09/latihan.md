#### Clone the Lab’s GitHub Repo
``` git clone https://github.com/dockersamples/linux_tweet_app```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/c1.jpg)
### Task 1: Run some simple Docker containers
#### Run a single task in an Alpine Linux container
1. Run the following command in your Linux console.
``` docker container run alpine hostname```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L1.jpg)
2. Docker keeps a container running as long as the process it started inside the container is still running. 
```  docker container ls --all```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L2.jpg)
#### Run an interactive Ubuntu container
1. Run a Docker container and access its shell.
``` docker container run --interactive --tty --rm ubuntu bash```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L3.jpg)
2. Run the following commands in the container.

```  ls /```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L4.jpg)

``` ps aux```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L5.jpg)

``` cat /etc/issue```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L6.jpg)
3. Let’s check the version of our host VM
``` cat /etc/issue```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L7.jpg)

#### Run a background MySQL container
1. Run a new MySQL container
```  docker container run \```
 ```--detach \```
 ```--name mydb \```
 ```-e MYSQL_ROOT_PASSWORD=my-secret-pw \```
 ```mysql:latest```

 ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L8.jpg)
 2.List the running containers.
 ```docker container ls```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L9.jpg)
3. You can check what’s happening in your containers by using a couple of built-in Docker commands: ```docker container logs``` and ```docker container top```.
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L10.jpg)
4. List the MySQL version using docker container exec.
```  docker exec -it mydb \```
``` mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L11.jpg)
5. You can also use docker container exec to connect to a new shell process inside an already-running container. 
```  docker exec -it mydb sh```
```  mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L12.jpg)

### Task 2: Package and run a custom app using Docker
#### Build a simple website image
1. Make sure you’re in the linux_tweet_app directory.

```cd linux_tweet_app```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L13.jpg)
2. Display the contents of the Dockerfile.

``` cat Dockerfile```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L14.jpg)
3. Echo the value of the variable back to the terminal to ensure it was stored correctly.

```  echo $DOCKERID```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L15.jpg)
