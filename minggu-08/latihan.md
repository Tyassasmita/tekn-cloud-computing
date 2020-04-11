#### Step 1: Setup
1. Membuat direktori projek
	``` $ mkdir composetest```
	``` $ cd composetest```
	
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/l1.jpg)

2. Membuat file ```app.py```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/l2.jpg)

3. Membuat file ```requirements.txt```

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
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/411.jpg)
2. Enter http://localhost:5000/ in a browser

``` Hello World! I have been seen 1 times.```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/42.jpg)

3. Refresh the page.

``` Hello World! I have been seen 2 times.```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/43.jpg)

4. Type ```docker image ls```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-08/44.jpg)
#### Step 5: Edit the Compose file to add a bind mount
###### Edit file ``` docker-compose.yml```

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