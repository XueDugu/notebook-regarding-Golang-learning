接口（interface）(定义快捷方法tyi)

接口可以把所有具有共性的方法定义在一起

定义的都是空方法

定义的方法要具有通用性

一个类型可以实现多个接口

多个类型可以实现同一个接口

定义

type interfacename interface{

methodname[returntype]

}

接口实现方法

func(name structname)methodname()[returntype]{

}

例子

package main

import "fmt"

type USB interface {

  read()

  write()

}

type Computer struct {

  name string

}

type Mobile struct {

  name  string

  laptop Computer

}

func (c Computer) read() {

  fmt.Printf("%s ", c.name)

  fmt.Println("computer read...")

}

func (c Computer) write() {

  fmt.Printf("%s ", c.name)

  fmt.Println("computer write...")

}

func (c Mobile) read() {

  fmt.Printf("%s's %s ", c.laptop, c.name)

  fmt.Println("phone read...")

}

func (c Mobile) write() {

  fmt.Printf("%s's %s ", c.laptop, c.name)

  fmt.Println("computer write...")

}

func main() {

  c := Computer{

​    name: "HUAWEI",

  }

  c.read()//HUAWEI computer read...

  c.write()//HUAWEI computer write...

  d := Mobile{

​    name: "APPLE",

  }

  d.laptop.name = "USA"

  d.read()//{USA}'s APPLE phone read...

  d.write()//{USA}'s APPLE computer write...

}