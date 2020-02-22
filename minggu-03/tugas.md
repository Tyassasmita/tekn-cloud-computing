### TUGAS
##### Membuat App di Heroku
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-03/t1.jpg)
##### Login Heroku melalui CMD
```
C:\tekn-cloud-tugas>heroku login
heroku: Press any key to open up the browser to login or q to exit:
Opening browser to https://cli-auth.heroku.com/auth/cli/browser/1116ccbf-23af-4742-ac4b-d8e6df45e1ea
Logging in... done
Logged in as tyassasmita12@gmail.com
```
```
C:\tekn-cloud-tugas>git init
Initialized empty Git repository in C:/tekn-cloud-tugas/.git/
```
```
C:\tekn-cloud-tugas>heroku git:remote -a mybiodata
set git remote heroku to https://git.heroku.com/mybiodata.git
```
```
C:\tekn-cloud-tugas>git add index.php
```
```
C:\tekn-cloud-tugas>git commit -m "updt"
[master (root-commit) a6c4dd3] updt
 1 file changed, 5 insertions(+)
 create mode 100644 index.php
 ```
 ```
 C:\tekn-cloud-tugas>git push heroku master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 345 bytes | 172.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote: Compressing source files... done.
remote: Building source:
remote:
remote: -----> PHP app detected
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/mybiodata.git
 * [new branch]      master -> master
 ```
 