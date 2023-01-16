defer(函数返回前执行，倒序执行)

例子

package main

import "fmt"

func main() {

  i := 1

  defer fmt.Printf("i: %v\n", i)

  i++

  defer fmt.Println("step2")

  defer fmt.Println("step1")

  fmt.Println("end")

}

/*

输出end

step1

step2

i: 1*/