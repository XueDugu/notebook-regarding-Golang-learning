利用WAITGROUP实现同步

由于主协程结束后函数运行也会结束，可以用WAITGROUP让主线程等待到所有携程运行完后再继续运行

两个协程相互等待

例子

package main

import (

  "fmt"

  "sync"

)

var wg sync.WaitGroup

func helo(i int) {

  defer wg.Done()

  fmt.Println(i, ":Hello Goroutine")

  return

}

func main() {

  for i := 0; i < 10; i++ {

​    wg.Add(1)//如果不等待将只输出end...

​    go helo(i)

  }

  wg.Wait()

  fmt.Println("end...")

}

/*

9 :Hello Goroutine
0 :Hello Goroutine
2 :Hello Goroutine
6 :Hello Goroutine
4 :Hello Goroutine
5 :Hello Goroutine
7 :Hello Goroutine
8 :Hello Goroutine
1 :Hello Goroutine
3 :Hello Goroutine
end...

*/