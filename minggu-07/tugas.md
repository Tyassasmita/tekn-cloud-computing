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