走进Go语言基础语言

课程源码：https://github.com/wangkechun/go-by-example

课程短链接：https://hi-hi.cn/go

Go语言特点：高性能、高并发、语法简单、学习曲线平缓、丰富的标准库、完善的工具链、静态链接、快速编译、垃圾回收。

使用Go语言的公司：字节跳动、谷歌、腾讯、脸书、美团、七牛云、滴滴、B站、百度、PingCAP等。

基础语法

中文可能会被当作多个字符

%v适合任意类型，%+v和%#v能进一步详细打印

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

10）错误处理

防止出现空指针等错误

11）字符串函数（strings包里的）

Contains(varable1,varable2)

判断是否前者包含后者

count(varable1,varable2)

判断前者中有多少个后者

Index(varable1,varable2)

查找后者在前者中的位置

Join([]string{},varable1)

用后者来连接前者

repeat(varable1,varable2)

重复前者后者次

12）JSON处理

可以将结构体成员变量首字母大写然后进行序列化处理

13）事件处理(time包)

time.Now()

time.Parse()

now.Unix()

14）数字解析(strconv包)

ParseFloat()

ParseInt()

Atoi()

14）进程信息(os/exec包和os包)

os.Args

os.Getenv()

