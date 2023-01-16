GO初始化

1）命名处初始化

var 变量名 变量类型 = 赋值

2）命名后初始化

var 变量名 变量类型

变量名=赋值

3）类型推导初始化

var 变量名=赋值//根据赋值来确定变量类型

4）批量初始化

var 变量名，变量名，变量名=赋值，赋值，赋值////根据赋值来确定变量类型

5）短变量声明（只能在函数内部使用）

变量名：=赋值

6）map初始化

var 名称=map[键数据类型]值数据类型{键：值}//赋值时用逗号间隔//map中的键值对一一对应，但键值对之间是无序的

7）结构体初始化

name:=structname{

correspondmembervalue,

}

name:=structname{
membername:correspondmembervalue,

}

8）数组初始化

var groupname [size]type=[size]type{value}

9）切片初始化

var slicename []type=[]type{value}