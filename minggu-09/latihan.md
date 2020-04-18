#### Clone the Lab’s GitHub Repo
``` git clone https://github.com/dockersamples/linux_tweet_app```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/c1.jpg)
### Task 1: Run some simple Docker containers
#### Run a single task in an Alpine Linux container
1. Run the following command in your Linux console.

    ##### Kegunaan perintah ``` docker container run alpine hostname``` untuk menampilkan nama host kontainer image:alpine yaitu 4a2bbb4a72fd. Untuk menjalankan container alpine dengan melakukan pull container tersebut langsung dari docker hub. Pada perintah diikuti perintah hostname yang nantinya akan menampilkan hostname container tersebut, yaitu 4a2bbb4a72fd
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L1.jpg)
2. Docker keeps a container running as long as the process it started inside the container is still running. 

    ##### Untuk mengecek aplikasi berjalan dengan baik dapat dilakukan dengan menggunakan perintah ```  docker container ls --all```. Dalam kontainer ini, proses nama host keluar segera setelah output ditulis. Untuk melakukan cek container yang sedang berjalan. Diikuti –all berarti akan mengecek semua container yang berjalan. Pada list container tersebut sudah terdapat image alpine, berarti contianer alpine tadi sudah berhasil dipull.
    
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L2.jpg)
#### Run an interactive Ubuntu container
1. Run a Docker container and access its shell.

    ``` docker container run --interactive --tty --rm ubuntu bash```
    ##### untuk menjalankan akses shell, disini terdapat 3 parameter yaitu ```interactive``` untuk sesi interaktif, ```tty``` untuk mengalokasikan pseudo-tty, dan ```rm``` untuk memberi tahu Docker untuk terus maju dan mengeluarkan kontainer setelah selesai dieksekusi. Pada proses tersebut melakukan pull container ubuntu langsung dari docker hub. Nantinya linux container tersebut berada di atas alpine linux docker host dan berjalan secara interaktif.

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L3.jpg)
2. Run the following commands in the container.
   
    ##### ```  ls /``` Untuk menampilkan isi direktori dari root yang terdapat dalam container ubuntu.

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L4.jpg)

    ##### ``` ps aux``` untuk menunjukkan proses yang berjalan dalam kontainer.

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L5.jpg)

    ##### ``` cat /etc/issue``` untuk menunjukkan distro Linux mana yang dijalankan kontainer, dalam hal ini Ubuntu 18.04.3 LTS.

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L6.jpg)

3. Let’s check the version of our host VM
    
    #### ``` cat /etc/issue``` untuk mengecek versi host VM yang digunakan. Host VM menjalankan Alpine Linux, namun ini dapat menjalankan kontainer Ubuntu. Distribusi Linux di dalam kontainer tidak perlu cocok dengan distribusi Linux yang berjalan di host Docker. Namun, kontainer Linux mengharuskan host Docker menjalankan kernel Linux. 
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L7.jpg)

#### Run a background MySQL container
1. Run a new MySQL container
    
    ```  docker container run \```

    ##### ```--detach \``` akan menjalankan kontainer di latar belakang.
    
    ##### ```--name mydb \``` akan menamainya mydb.
    
    ```-e MYSQL_ROOT_PASSWORD=my-secret-pw \```
    ##### -e merupakan variabel environment yang akan melakukan pengaturan password pada root user, yaitu my-secret-pw
    
    ```mysql:latest```
    ##### Container tersebut merupakan container MySQL yang berjalan sebagai container background. Nantinya background container tersebut sebaga cara bagaimana kita akan menjalankan aplikasi. Image yang direquest tersebut tidak terdapat di local direktory, jadi Docker akan melakukan pull dari Docker hub. Selama proses MySQL berjalan, Docker akan menjaga kontainer tetap berjalan di latar belakang.

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L8.jpg)
    
 2.List the running containers.

##### ```docker container ls``` Untuk mengecek aplikasi yang sedang berjalan.
    
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L9.jpg)
3. You can check what’s happening in your containers by using a couple of built-in Docker commands: ```docker container logs``` and ```docker container top```.
##### Docker container logs akan menjalankan perintah untuk melihat catatan aktivitas yang terjadi pada contianer yang berjalan. Antara lain: melakukan entrypoint script untuk mysql server yang berjalan pada debian10, beralih ke user mysql, inisialisasi file database, lalu terdapat beberapa warning salah satunya memberitahu bahwa direktori localhost telah dibuat dengan tanpa password. Selanjutnya terdapat aktivitas inisialisasi file database dan menjalankan server sementara, dan rerakhir terdapat warning bahwa tidak bisa memuat file iso3166.tab dan leap_seconds.list pada diektori /usr/share/zoneinfo.

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L10.jpg)
4. List the MySQL version using docker container exec.

##### ```docker exec -it mydb \``` memungkinkan untuk menjalankan perintah di dalam sebuah container. PID yang ditampilkan di sini adalah PID untuk proses pada docker host. Untuk melihat proses mysqld yang sama berjalan sebagai proses utama container (PID 1) maka dilakukan perintah docker exec -it mydb \. Meskipun MySQL sedang berjalan, MySQL tersebut terpisah di dalam container karena tidak ada port jaringan yang telah dipublikasikan ke host. Lalu lintas jaringan tidak dapat mencapai kontainer dari host kecuali port diterbitkan secara eksplisit.

    ``` mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L11.jpg)

5. You can also use docker container exec to connect to a new shell process inside an already-running container. 
    
    ##### ```  docker exec -it mydb sh``` untuk terhubung ke proses shell baru di dalam kontainer yang sudah berjalan. Menjalankan perintah tersebut akan memberi shell interaktif (sh) di dalam kontainer MySQL.

    ##### ```  mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version ``` untuk memriksa nomor versi, hanya kali ini dari dalam sesi shell baru di dalam kontainer.
 
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L12.jpg)

### Task 2: Package and run a custom app using Docker
#### Build a simple website image
1. Make sure you’re in the linux_tweet_app directory.

    ```cd linux_tweet_app```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L13.jpg)
2. Display the contents of the Dockerfile.

    ``` cat Dockerfile```
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L14.jpg)
    ##### PENJELASAN 
    ##### FROM menentukan gambar dasar untuk digunakan sebagai titik awal untuk gambar baru yang di buat. Untuk contoh ini, mulai dari ```nginx:latest```.
    ##### COPY menyalin file dari host Docker ke dalam image.COPY digunakan untuk menyalin dua file ke dalam image: index.html. dan grafik yang akan digunakan di halaman web.
    ##### EXPOSE dokumen yang port aplikasi gunakan.
    ##### CMD menentukan perintah apa yang harus dijalankan ketika sebuah kontainer dimulai dari image.
3. You will have to manually type this command as it requires your unique DockerID.

    ##### ``` export DOCKERID=<your docker id>``` untuk menampilkan id docker yang digunakan untuk build image.

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L16.jpg)
4. Echo the value of the variable back to the terminal to ensure it was stored correctly.

    ##### ```  echo $DOCKERID``` untuk memastikan nilai variabel kembali ke terminal disimpan dengan benar.
    
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L17.jpg)

5. Use the docker image build command to create a new Docker image
   
    ``` docker image build --tag $DOCKERID/linux_tweet_app:1.0 .```
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L18.jpg)
    ##### PENJELASAN
    ##### --tag memungkinkan kita memberi image nama khusus. Dalam hal ini terdiri dari DockerID, nama aplikasi, dan versi. Memiliki ID Docker yang terlampir pada nama akan memungkinkan untuk menyimpannya di Docker Hub di langkah selanjutnya.
    ##### Step 1/5, dari nginx , akan melakukan pull dari docker hub
    ##### Step 2/5, akan mencopy yang dibutuhkan pada proses build container yaitu index.html dari direktori /usr/share/nginx/html
    ##### Step 3/5, akan mencopy yang dibutuhkan pada proses build container yaitu linux.png dari direktori /usr/share/nginx/html
    ##### Step 4/5, Perintah EXPOSE digunakan untuk menghubungkan port tertentu untuk mengaktifkan network antara proses yang berjalan di dalam container dan mesin host.
    ##### Step 5/5, Perintah CMD hampir sama dengan perintah RUN, CMD digunakan untuk mengeksekusi perintah yang lebih spesifik, seperti pada saat proses pembuatan container pada image.
    ##### Dockerfile di atas merupakan script yang yang berisi dari serangkaian perintah yang akan dieksekusi secara otomatis dan berurutan untuk membuat sebuah image.

6. Use the ```docker container run``` command to start a new container from the image you created.

   ``` docker container run \```
   
   ``` --detach \```
   
   ``` --publish 80:80 \```
   
   ``` --name linux_tweet_app \```
   
   ``` $DOCKERID/linux_tweet_app:1.0```
   ##### Container tersebut akan berjalan sebagai NGINX web server, digunakan flag –publish untuk mempublikasikan port 80 yang berada pada container ke port 80 yang berada di dalam host. Proses tersebut akan memungkinkan lalu lintas masuk ke host Docker pada port 80 untuk diarahkan ke port 80 dalam container. Format flag --publish adalah host_port: container_port. Hasilnya di dalam user id docker kita akan menjalankan image dengan nama linux_tweet_app:1.0.

   ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L19.jpg)

7. Check in the Browser with ip ``` http://192.168.99.100/```
    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L20.jpg)

8. Once you’ve accessed your website, shut it down and remove it

    ```  docker container rm --force linux_tweet_app```
    ##### Proses tesebut akan melakukan shut down image fengan menggunakan parameter –force untuk menghapus container yang berjalan tanpa harus melakukan shu down container tersebut. Proses tersebut tidak akan men shut down container dan menghapus secara permanen dari docker host.
    
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
    ##### Container tersebut akan berjalan sebagai NGINX web server dengan menggunakan bind mount. Saat kita menggunakan bind mount, file dan direktory pada host machine akan dipasang di dalam container. Pada proses tersebut direktory dan file akan dipasang di dalam direktory /usr/share/nginx/html pada container., digunakan flag –publish untuk mempublikasikan port 80 yang berada pada container ke port 80 yang berada di dalam host. Proses tersebut akan memungkinkan lalu lintas masuk ke host Docker pada port 80 untuk diarahkan ke port 80 dalam container. Format flag --publish adalah host_port: container_port. Hasilnya di dalam user id docker kita akan menjalankan image dengan nama linux_tweet_app:1.0
    
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

2. Before you can push your images, you will need to log into Docker Hub.

    ``` docker login```
3. Push version 1.0 of your web app using ```docker image push```.

    ``` docker image push $DOCKERID/linux_tweet_app:1.0```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L31.jpg)
4. Now push version 2.0.
    ``` docker image push $DOCKERID/linux_tweet_app:2.0```

    ![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-09/L32.jpg)