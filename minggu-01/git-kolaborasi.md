# TUGAS 1
### Git untuk Kolaborasi
#### Fork
+ Akses repo yang akan di-fork (https://github.com/Tyassasmita/playground-1)
+ klik Fork
![](hhttps://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/forkplay.jpg)
+ Pilih nama account
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/forkplaylok.jpg)
+ Setelah proses, repo dari upstream author sudah berada di account GitHub kita (kontributor)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-01/forkplayd.jpg)

### clone di komputer lokal
```
C:\tekn-cloud-computing\minggu-01>git clone https://github.com/Tyassasmita/playground-1
Cloning into 'playground-1'...
remote: Enumerating objects: 7, done.
remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 7
Unpacking objects: 100% (7/7), done.
```
##### konfigurasikan repo lokal kontributor. Pada kondisi saat ini, di komputer lokal sudah terdapat repo playground-1 yang berada pada direktori dengan nama yang sama. 
###### Repo ```origin``` sudah dituliskan konfigurasinya pada saat melakukan proses clone dari repo kontributor. Konfigurasi repo upstream harus dibuat.
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
### Mengirimkan Pull Request
1. Buatlah branch fitur baru 
```
C:\tekn-cloud-computing\minggu-01\playground-1>git checkout -b new
Switched to a new branch 'new'
```
2. Commit perubahannya
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git commit -am "new"
On branch new
nothing to commit, working tree clean
```
3. Push ke branch di remote
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git push origin new
Total 0 (delta 0), reused 0 (delta 0)
remote:
remote: Create a pull request for 'new' on GitHub by visiting:
remote:      https://github.com/Tyassasmita/playground-1/pull/new/new
remote:
To https://github.com/Tyassasmita/playground-1
 * [new branch]      new -> new
```
### Membuat Perubahan di Repo Lokal
#### melakukan sinkronisasi
```
C:\tekn-cloud-computing\minggu-01\playground-1>git fetch upstream
From https://github.com/Tyassasmita/playground-1
 * [new branch]      add-contributor -> upstream/add-contributor
 * [new branch]      master          -> upstream/master
 ```
#### Lakukan perubahan-perubahan, setelah itu push ke origin (milik kontributor)
```
C:\tekn-cloud-computing\minggu-01\playground-1>git checkout -b add-contributor
Switched to a new branch 'add-contributor'
M       README.md
C:\tekn-cloud-computing\minggu-01\playground-1>git branch
* add-contributor
  master
C:\tekn-cloud-computing\minggu-01\playground-1>type README.md
# Playground
It's just an example repo so that people can use it to learn Git.
## Contributor
1. [bpdp](https://github.com/bpdp)
C:\tekn-cloud-computing\minggu-01\playground-1>git status
On branch add-contributor
nothing to commit, working tree clean
```