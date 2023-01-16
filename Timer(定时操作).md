Timer(定时操作)

通过管道实现

例子

package main



import (

  "fmt"

  "time"

)



func main() {

  timer1 := time.NewTimer(time.Second * 2)

  t1 := time.Now()

  fmt.Printf("t1: %v\n", t1)

  t2 := <-timer1.C

  fmt.Printf("t2: %v\n", t2)

  timer2 := time.NewTimer(time.Second * 2)

  <-timer2.C

  fmt.Println("2s后")

  time.Sleep(time.Second * 2)

  fmt.Println("再2s后")

  <-time.After(time.Second * 2)

  fmt.Println("再再2s后")

  timer3 := time.NewTimer(time.Second)

  go func() {

​    <-timer3.C

​    fmt.Println("Timer 3 expired")

  }()

  stop := timer3.Stop()

  if stop {

​    fmt.Println("timer 3 stopped")

  }

  fmt.Println("before")

  timer4 := time.NewTimer(time.Second * 5)

  timer4.Reset(time.Second * 1)

  <-timer4.C

  t5 := time.Since(t1)

  fmt.Printf("t5: %v\n", t5)

  fmt.Println("after")

}

/*
t1: 2022-11-10 20:01:34.5113736 +0800 CST m=+0.001051301
t2: 2022-11-10 20:01:36.5230342 +0800 CST m=+2.012700201
2s后
再2s后
再再2s后
timer 3 stopped
before
t5: 9.0351556s
after

*/