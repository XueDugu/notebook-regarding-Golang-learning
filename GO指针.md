GO指针

package main

import "fmt"

func main() {

  var ip *int

  fmt.Printf("ip: %v\n", ip)//输出ip: <nil>

  fmt.Printf("&ip: %v\n", &ip)//输出&ip: 0xc0000ca018

  fmt.Printf("ip: %T\n", ip)//输出ip: *int

  fmt.Printf("ip: %T\n", &ip)//输出ip: **int

  i := 100

  ip = &i

  fmt.Printf("*ip: %v\n", *ip)//输出*ip: 100

  var sp *string

  var s string = "hello"

  sp = &s

  s += "a"

  fmt.Printf("sp: %v\n", sp)//输出sp: 0xc000088220

  fmt.Printf("*sp: %v\n", *sp)//输出*sp: helloa

}