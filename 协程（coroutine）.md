协程（coroutine）

通俗来说就是遇到go关键词开启协程来运行go后的函数主线程继续执行主函数

协程原理

协程是运行在线程之上，当一个协程执行完成之后，可以选择主动让出，让另一个协程运行在当前的线程之上。**协程并没有增加线程的数量，只是在线程的基础上通过分时复用的方式运行多个协程，而且协程的切换在用户态完成，切换的代价比线程从用户态到内核态的代价小很多**。

创建协程

go taskfunctionname()

例子（一）

package main

import (

  "fmt"

  "time"

)

func show(msg string) {

  start := time.Now()

  for i := 1; i < 5; i++ {

​    cost := time.Since(start)

​    fmt.Printf("%s(%d): %v\n", msg, i, cost)

​    time.Sleep(time.Millisecond * 100)

  }

}

func main() {

  go show("java")

  go show("C")

  show("golang")

  fmt.Println("end...")

}

/*

java(1): 0s
C(1): 0s
golang(1): 0s
golang(2): 110.5987ms
C(2): 110.5987ms
java(2): 110.5987ms
java(3): 217.2008ms
golang(3): 217.2008ms
C(3): 217.2008ms
C(4): 322.6789ms
golang(4): 322.6789ms
java(4): 322.6789ms
end...

*/

例子（二）

package main



import (

  "fmt"

  "io"

  "log"

  "net/http"

  "time"

)



func responseSize(url string) {

  fmt.Println("Step1:", url)

  response, err := http.Get(url)

  if err != nil {

​    log.Fatal(err)

  }

  fmt.Println("Step2:", url)

  defer response.Body.Close()

  fmt.Println("Step3:", url)

  body, err := io.ReadAll(response.Body)

  if err != nil {

​    log.Fatal(err)

  }

  fmt.Println("Step4:", len(body))

  fmt.Println(url, " is  over")

}

func main() {

  go responseSize("https://baidu.com")

  go responseSize("https://jd.com")

  go responseSize("https://elearning.fudan.edu.cn/")

  time.Sleep(10 * time.Second)

}

/*

Step1: https://elearning.fudan.edu.cn/
Step1: https://baidu.com
Step1: https://jd.com
Step2: https://jd.com
Step3: https://jd.com
Step4: 156768
https://jd.com  is  over
Step2: https://baidu.com
Step3: https://baidu.com
Step4: 365260
https://baidu.com  is  over
Step2: https://elearning.fudan.edu.cn/
Step3: https://elearning.fudan.edu.cn/
Step4: 42676
https://elearning.fudan.edu.cn/  is  over

*/