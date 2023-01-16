mutex加锁实现同步、

例子

package main



import (

  "fmt"

  "sync"

)

var i int = 100

var wg sync.WaitGroup

var lock sync.Mutex

func add() {

  defer wg.Done()

  lock.Lock()

  defer lock.Unlock()

  i++

  fmt.Printf("i++: %v\n", i)

}

func sub() {

  defer wg.Done()

  lock.Lock()//加锁

  defer lock.Unlock()//解锁

  i--

  fmt.Printf("i--: %v\n", i)

}

func main() {

  count := 100

  for i := 0; i < count; i++ {

​    wg.Add(1)

​    go add()

​    wg.Add(1)

​    go sub()

  }

  wg.Wait()

  fmt.Printf("i(end): %v\n", i)

}