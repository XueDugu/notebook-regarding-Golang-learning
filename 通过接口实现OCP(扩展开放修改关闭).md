通过接口实现OCP(扩展开放修改关闭)

面向对象可复用设计的第一步基石

例子

package main

import "fmt"

type Pet interface {

  eat()

  sleep()

}

type Dog struct {

  name string

  age  int

}

type Cat struct {

  name string

  age  int

}

func (dog Dog) eat() {

  fmt.Println("dog eating...")

}

func (cat Cat) eat() {

  fmt.Println("cat eating...")

}

func (dog Dog) sleep() {

  fmt.Println("dog sleeping...")

}

func (cat Cat) sleep() {

  fmt.Println("cat sleeping...")

}

type Person struct {

  name string

}

func (per Person) care(pet Pet) {

  pet.eat()

  pet.sleep()

  fmt.Printf("the %T's owner is %v\n", pet, per.name)

}

func main() {

  dog := Dog{

​    name: "CC",

​    age:  10,

  }

  cat := Cat{

​    name: "DD",

​    age:  20,

  }

  per := Person{

​    name: "Ben Smith",

  }

  per.care(dog)

/*

dog eating...
dog sleeping...
the main.Dog's owner is Ben Smith

*/

  per.care(cat)

/*

cat eating...
cat sleeping...
the main.Cat's owner is Ben Smith

*/

}

