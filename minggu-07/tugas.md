#### Carilah image yang menarik untuk anda di DockerHub
``` docker container run -idt alpine uptime```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T1.jpg)

##### proses image
``` docker ps -a```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T2.jpg)
##### menjalankan image alpine
``` docker container run -idt alpine uptime```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T3.jpg)

``` docker rename stoic_chatterjee workfromhome```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T4.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T5.jpg)
``` docker logs 9fd186ea25e3```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T6.jpg)

``` docker pull nginx```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T7.jpg)

``` docker run -d -p 8080:80 --name mynginx nginx```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T8.jpg)

``` localhost:8080```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T9.jpg)

``` docker exec -it mynginx /bin/bash```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T10.jpg)

```  docker ps -l```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T11.jpg)

``` docker run -d --name ghost -p 3001:2368 ghost:alpine```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-07/T12.jpg)