### LATIHAN
##### Perbarui dan Tingkatkan Sistem
##### Untuk memulai, masuk ke sistem Ubuntu 18.04 Anda menggunakan protokol SSH dan perbarui & perbarui repositori sistem.
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/Screenshot_0.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/Screenshot_1.png)
##### Install DevStack
##### Service yang akan diinstall dan dijalankan oleh Devstack memerlukan user account, untuk itu kita akan membuat user yang memiliki akses ke sudo, Selanjutnya untuk instalasi Devstack kita perlu melakukan cloning GIT repo.
``` sudo su -l stack ```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/Screenshot_3.png)
```sudo useradd -s /bin/bash -d /opt/stack -m stack ```
```echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack```
```sudo su - stack```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/1.jpg)
###### git clone https://opendev.org/openstack/devstack
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/2.jpg)
######  cd devstack
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/3.jpg)
##### Selanjutnya buat Devstack answer file, pada direktori devstack buat file bernama local.conf. Pada file tersebut kita akan diisi dengan password service-service dan admin Devstack.
``` sudo nano local.conf ```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/Screenshot_6.png)
##### Start the Install
###### ./stack.sh
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/4.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/5.jpg)