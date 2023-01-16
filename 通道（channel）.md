通道（channel）

在两个携程间进行通讯

一个通道在同一时间只有一个协程能访问通道，因此不会出现数据竞争

分类：有缓存通道和无缓存通道

定义

channelname:=make(chan chantype)//无缓存通道

channelname:=make(chan chantype,number)//有缓存通道

通道接收

channelname<-text//只能是左箭头

通道发送

name:=<-channelname//只能是左箭头

发送操作间和发送操作间是互斥的

发送操作和接收操作中对值的处理是不可分割的

发送操作和接受操作在完全完成前是会被阻塞的

例子

package main

import (

  "fmt"

  "math/rand"

  "time"

)

var values = make(chan int)

func send() {

  rand.Seed(time.Now().UnixNano())

  value := rand.Intn(10)

  fmt.Printf("values: %v\n", value)

  values <- value

}

func main() {

  defer fmt.Println("over...")

  defer close(values)

  defer fmt.Println("begin to clear...")

  start := time.Now()

  go send()

  fmt.Println("waiting...")

  value := <-values

  fmt.Printf("value: %v\n", value)

  fmt.Println("end...")

  end := time.Since(start)

  fmt.Printf("end: %v\n", end)

}

/*

waiting...
values: 9
value: 9
end...
end: 520.4µs
begin to clear...
over...

*/