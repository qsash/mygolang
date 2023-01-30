package main

import(
 "fmt"
  "database/sql"
	_ "github.com/go-sql-driver/mysql"
   "github.com/joho/sqltocsv"

)


// connect with db
func main()  {
  db, err := sql.Open("mysql", "login:password@tcp(127.0.0.1:8889))/db_name")
  if err != nil {
    panic(err)
  }

 defer db.Close()

 res, _ := db.Query("SELECT * FROM `users...`")
 // path to the file
err = sqltocsv.WriteFile(".../file_name.csv", res)
if err != nil {
    panic(err)
}else{
  fmt.Println("done")
}

}
