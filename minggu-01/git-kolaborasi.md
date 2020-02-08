# TUGAS 1
### Git untuk Kolaborasi
#### Fork
+ Akses repo yang akan di-fork (https://github.com/novendrasatria/175610028-sqa)
+ klik Fork
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/fork.png)
+ Pilih nama account
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/lokasifork.png)
+ Setelah proses, repo dari upstream author sudah berada di account GitHub kita (kontributor)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/forkkita.png)

### clone di komputer lokal
    ```C:\tekn-cloud-computing\minggu-01>git clone https://github.com/Tyassasmita/175610028-sqa
    Cloning into '175610028-sqa'...
    remote: Enumerating objects: 3, done.
    remote: Counting objects: 100% (3/3), done.
    remote: Compressing objects: 100% (2/2), done.
    remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
    Unpacking objects: 100% (3/3), done.
    ```
#### konfigurasikan repo lokal kontributor. Pada kondisi saat ini, di komputer lokal sudah terdapat repo 175610028-sqa yang berada pada direktori dengan nama yang sama. 
##### Repo ```origin``` sudah dituliskan konfigurasinya pada saat melakukan proses clone dari repo kontributor. Konfigurasi repo upstream harus dibuat.
```
C:\tekn-cloud-computing\minggu-01\175610028-sqa>git remote -v
origin  https://github.com/Tyassasmita/175610028-sqa (fetch)
origin  https://github.com/Tyassasmita/175610028-sqa (push)
```
##### Tambahkan remote upstream:
``` 
C:\tekn-cloud-computing\minggu-01\175610028-sqa>git remote add upstream https://github.com/Tyassasmita/175610028-sqa.git
```
#### Hasil 
``` 
C:\tekn-cloud-computing\minggu-01\175610028-sqa>git remote -v
origin  https://github.com/Tyassasmita/175610028-sqa (fetch)
origin  https://github.com/Tyassasmita/175610028-sqa (push)
upstream        https://github.com/Tyassasmita/175610028-sqa.git (fetch)
upstream        https://github.com/Tyassasmita/175610028-sqa.git (push)    
```
### Membuat Perubahan di Repo Lokal

