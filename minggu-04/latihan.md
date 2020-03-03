### LATIHAN
##### Install DevStack
##### Service yang akan diinstall dan dijalankan oleh Devstack memerlukan user account, untuk itu kita akan membuat user yang memiliki akses ke sudo, Selanjutnya untuk instalasi Devstack kita perlu melakukan cloning GIT repo.
```sudo useradd -s /bin/bash -d /opt/stack -m stack ```

```echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack```

```sudo su - stack```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/1.jpg)
###### git clone https://opendev.org/openstack/devstack
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/2.jpg)
######  cd devstack
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/3.jpg)
##### Start the Install
###### ./stack.sh
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/4.jpg)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-04/5.jpg)