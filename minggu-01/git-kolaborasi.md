# TUGAS 1
### Git untuk Kolaborasi
#### Fork
+ Akses repo yang akan di-fork (https://github.com/Tyassasmita/playground-1)
+ klik Fork
![](hhttps://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/forkplay.jpg)
+ Pilih nama account
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/lokasifork.png)
+ Setelah proses, repo dari upstream author sudah berada di account GitHub kita (kontributor)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/forkkita.png)

### clone di komputer lokal
    ```C:\tekn-cloud-computing\minggu-01>git clone https://github.com/Tyassasmita/playground-1
    Cloning into 'playground-1'...
    remote: Enumerating objects: 7, done.
    remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 7
    Unpacking objects: 100% (7/7), done.
    ```
#### konfigurasikan repo lokal kontributor. Pada kondisi saat ini, di komputer lokal sudah terdapat repo 175610028-sqa yang berada pada direktori dengan nama yang sama. 
##### Repo ```origin``` sudah dituliskan konfigurasinya pada saat melakukan proses clone dari repo kontributor. Konfigurasi repo upstream harus dibuat.
```
C:\tekn-cloud-computing\minggu-01\playground-1>git remote -v
origin  https://github.com/Tyassasmita/playground-1 (fetch)
origin  https://github.com/Tyassasmita/playground-1 (push)
```
##### Tambahkan remote upstream:
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git remote add upstream https://github.com/Tyassasmita/playground-1.git
```
#### Hasil 
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git remote -v
origin  https://github.com/Tyassasmita/playground-1 (fetch)
origin  https://github.com/Tyassasmita/playground-1 (push)
upstream        https://github.com/Tyassasmita/playground-1.git (fetch)
upstream        https://github.com/Tyassasmita/playground-1.git (push)
 
```
### Membuat Perubahan di Repo Lokal

