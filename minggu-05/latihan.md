### LATIHAN
##### Install OpenJDK 8
``` sudo apt update ```

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_1.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_2.png)
###### java -version
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_3.png)
##### Install Apache OFBiz
###### Sekarang Java sudah diinstal dan dikonfigurasi, jalankan perintah di bawah ini untuk mengunduh versi terbaru Apache OFBiz
``` cd /tmp ```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_4.png)
``` wget http://apache.claz.org/ofbiz/apache-ofbiz-16.11.05.zip ```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_5.png)
###### Setelah mengunduh, jalankan perintah di bawah ini untuk mengekstrak dan pindah ke folder bin lokal
``` unzip apache-ofbiz-16.11.05.zip ```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_6.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_7.png)
``` sudo mv apache-ofbiz-16.11.05 /usr/local/apache-ofbiz```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_9.png)
###### Selanjutnya, ubah menjadi direktori OFBiz dan jalankan perintah di bawah ini untuk memuat data default-nya 
``` cd /usr/local/apache-ofbiz```
![]@(https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_10.png)
``` ./gradlew cleanAll loadDefault```
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_11.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_12.png)
###### Ketika semua paket diunduh dan diinstal, Anda akan melihat pesan penyelesaian seperti di bawah ini:
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_13.png)
###### Jika Anda hanya menguji, maka jalankan perintah di bawah ini:
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-05/Screenshot_14.png)