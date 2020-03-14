#### LATIHAN
##### Install Go
[Link Golang](https://golang.org/dl/)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Go.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Go1.png)
##### Install MongoDB
[Link MongoDB](https://www.mongodb.com/download-center/community)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Mo.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Mo1.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Mo2.png)
##### Install Mysql Community Edition
[Link Mysql](https://www.mysql.com/products/community/)

![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Mysql.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Mysql1.png)
![](https://github.com/Tyassasmita/tekn-cloud-computing/blob/master/minggu-06/Mysql2.png)
#### Buat 2 contoh program Go masing-masing untuk koneksi dan membaca data dari MySQL dan MongoDB.
##### Program 1

```package main```

```import (```
```  "fmt"```
 ```   "database/sql"```
 ```   _ "github.com/go-sql-driver/mysql"```
```)```

```func main() {```
```fmt.Println("Go MySQL Tutorial")```

```  // Open up our database connection.```
```// I've set up a database on my local machine using phpmyadmin.```
  ```  // The database is called testDb```
  ```  db, err := sql.Open("mysql", "root:@tcp(127.0.0.1:3306)/minggu-06")```

   ``` // if there is an error opening the connection, handle it```
  ```  if err != nil {```
 ```       panic(err.Error())```
 ``` }```

   ``` // defer the close till after the main function has finished```
  ```  // executing```
  ```  defer db.Close()```
```}```

##### Program 2