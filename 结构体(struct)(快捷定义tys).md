结构体

定义

type structname struct{

membername membertype;//同类型成员可在一起声明用逗号相隔

}

匿名结构体定义

例子

package main

import "fmt"

func main() {

  var ypj struct {

​    id  int

​    name string

  }

  ypj.id = 22307130296

  ypj.name = "Ben Smith"

  fmt.Printf("ypj: %v\n", ypj)//ypj: {22307130296 Ben Smith}

}