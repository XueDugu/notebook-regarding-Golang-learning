Ticker（可以周期执行）

例子

package main

import (

  "fmt"

  "time"

)

func main() {

  ticker := time.NewTicker(time.Second)

  counter := 1

  for _ = range ticker.C {

​    fmt.Println("ticker...")

​    counter++

​    if counter > 5 {

​      ticker.Stop()

​      break

​    }

  }

  fmt.Println("end...")

}