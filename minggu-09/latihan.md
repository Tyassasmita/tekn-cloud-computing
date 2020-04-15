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

    ```  mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version ```
 
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L12.jpg)

### Task 2: Package and run a custom app using Docker
#### Build a simple website image
1. Make sure you’re in the linux_tweet_app directory.

    ```cd linux_tweet_app```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L13.jpg)
2. Display the contents of the Dockerfile.

    ``` cat Dockerfile```
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L14.jpg)
3. You will have to manually type this command as it requires your unique DockerID.

    ``` export DOCKERID=<your docker id>```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L16.jpg)
4. Echo the value of the variable back to the terminal to ensure it was stored correctly.

    ```  echo $DOCKERID```
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L17.jpg)

5. Use the docker image build command to create a new Docker image
   
    ``` docker image build --tag $DOCKERID/linux_tweet_app:1.0 .```
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L18.jpg)
6. Use the ```docker container run``` command to start a new container from the image you created.

   ``` docker container run \```
   
   ``` --detach \```
   
   ``` --publish 80:80 \```
   
   ``` --name linux_tweet_app \```
   
   ``` $DOCKERID/linux_tweet_app:1.0```
   
   ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L19.jpg)

7. Check in the Browser with ip ``` http://192.168.99.100/```
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L20.jpg)

8. Once you’ve accessed your website, shut it down and remove it

    ```  docker container rm --force linux_tweet_app```
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L21.jpg)

### Task 3: Modify a running website
#### Start our web app with a bind mount
1. Let’s start the web app and mount the current directory into the container.
    
    ```docker container run \```

    ``` --detach \```
    
    ``` --publish 80:80 \```
    
    ``` --name linux_tweet_app \```
    
    ``` --mount type=bind,source="$(pwd)",target=/usr/share/nginx/html \  ```
    
    ``` $DOCKERID/linux_tweet_app:1.0```
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L22.jpg)

#### Modify the running website
1. Copy a new ```index.html``` into the container.

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L23.jpg)
2. Go to the running website and refresh the page.
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L24.jpg)

##### To show this, stop the current container and re-run the 1.0 image without a bind mount.
1. Stop and remove the currently running container.

    ``` docker rm --force linux_tweet_app```
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L25.jpg)
2. Rerun the current version without a bind mount.

    ```docker container run \```

    ``` --detach \```

    ``` --publish 80:80 \```

    ``` --name linux_tweet_app \```

    ``` $DOCKERID/linux_tweet_app:1.0```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L26.jpg)
3. Notice the website is back to the original version
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L20.jpg)
4. Stop and remove the current container

    ``` docker rm --force linux_tweet_app```
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L25.jpg)

#### Update the image
1.Build a new image and tag it as 2.0
    ```  docker image build --tag $DOCKERID/linux_tweet_app:2.0 .```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L27.jpg)
2. Let’s look at the images on the system.

    ```docker image ls```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L28.jpg)

#### Test the new version
1. Run a new container from the new version of the image

    ``` docker container run \```
   
    ``` --detach \```
   
    ``` --publish 80:80 \```
   
    ``` --name linux_tweet_app \```
   
    ```$DOCKERID/linux_tweet_app:2.0```
   
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L29.jpg)
2. Check the new version of the website 
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L24.jpg)

#### Push your images to Docker Hub
1. List the images on your Docker host.

    ``` docker image ls -f reference="$DOCKERID/*"```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L30.jpg)
2.Before you can push your images, you will need to log into Docker Hub.
    ``` docker login```
3. Push version 1.0 of your web app using ```docker image push```.

    ``` docker image push $DOCKERID/linux_tweet_app:1.0```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L31.jpg)
3. Now push version 2.0.
    ``` docker image push $DOCKERID/linux_tweet_app:2.0```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L32.jpg)