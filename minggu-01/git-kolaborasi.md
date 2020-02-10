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
C:\tekn-cloud-computing\minggu-01>git clone https://github.com/bpdp/playground-1
fatal: destination path 'playground-1' already exists and is not an empty directory.

C:\tekn-cloud-computing\minggu-01>git clone https://github.com/bpdp/playground-1
Cloning into 'playground-1'...
remote: Enumerating objects: 7, done.
remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 7
Unpacking objects: 100% (7/7), done.

```
##### konfigurasikan repo lokal kontributor. Pada kondisi saat ini, di komputer lokal sudah terdapat repo playground-1 yang berada pada direktori dengan nama yang sama. 
##### Repo ```origin``` sudah dituliskan konfigurasinya pada saat melakukan proses clone dari repo kontributor. Konfigurasi repo upstream harus dibuat.
```
C:\tekn-cloud-computing\minggu-01\playground-1>git remote -v
origin  https://github.com/bpdp/playground-1 (fetch)
origin  https://github.com/bpdp/playground-1 (push)
```
##### Tambahkan remote upstream:
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git remote add upstream https://github.com/Tyassasmita/playground-1.git
```
#### Hasil 
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git remote -v
origin  https://github.com/bpdp/playground-1 (fetch)
origin  https://github.com/bpdp/playground-1 (push)
upstream        https://github.com/Tyassasmita/playground-1.git (fetch)
upstream        https://github.com/Tyassasmita/playground-1.git (push)
 
```
### Mengirimkan Pull Request
1. Buatlah branch fitur baru 
```
C:\tekn-cloud-computing\minggu-01\playground-1>git checkout -b new-branch
Switched to a new branch 'new-branch'
```
2. Commit perubahannya
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git commit -am "new-branch"
On branch new-branch
nothing to commit, working tree clean
```
3. Upstream author me-review dan kemudian menyetujui (merge) ke master atau menolak PR.(Jika disetujui dan di-merge ke repo master dari upstream author, sinkronkan repo di komputer lokal dan repo GitHub kontributor.)
``` 
C:\tekn-cloud-computing\minggu-01\playground-1>git push origin new-branch
remote: Permission to bpdp/playground-1.git denied to Tyassasmita.
fatal: unable to access 'https://github.com/bpdp/playground-1/': The requested URL returned error: 403
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