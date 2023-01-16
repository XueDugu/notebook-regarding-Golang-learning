init函数(晚于变量初始化先于main函数，自动执行，无输入和返回，不能被其他函数调用)

例子

package main

import "fmt"

var a int = initVar()

func main() {

  fmt.Println("main...")

  fmt.Printf("a: %v\n", a)

}

func init() {

  fmt.Println("init...")

}

func initVar() int {

  fmt.Println("iii...")

  return 10

}

/*

输出

iii...

init...

main...

a: 10

*/