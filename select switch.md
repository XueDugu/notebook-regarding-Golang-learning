select switch

用于处理异步IO操作

select会监听case中的通道读写写操作，如果能正常读写才会触发相应动作

多个case都能运行会随机执行一个

例子

package main

import "fmt"

var chanInt = make(chan int, 0)

var chanStr = make(chan string)

func main() {

  go func() {

​    chanInt <- 100

​    chanStr <- "hello"

​    defer close(chanInt)

​    defer close(chanStr)

  }()

  for {

​    select {

​    case r := <-chanInt:

​      fmt.Printf("%v\n", r)

​    case r := <-chanStr:

​      fmt.Printf("r: %v\n", r)

​    default:

​      fmt.Println("default...")

​    }

​    break

  }

}