GO命名规则

1）任何需要对外暴露的量必须大写字母开头（例如非主函数），不需要对外暴露的量应该小写字母开头

2）变量名由字母数字下划线构成

3）变量名区分大小写

4）变量名只能以字母或下划线开头

var 变量名 变量类型

5）包名称字母全部小写，并且不使用数字和下划线

package 包名称

6）文件名称用下划线分割单词，字母全部小写

文件名.go

7）接口名称用纯字母构成每个单词第一个字母大写并结尾加上er

例子

type 接口名称 interface{

Read(p []byte)(n int,err error)

}

8）结构名称用纯字母构成每个单词第一个字母大写

type 结构名称 struct{

变量名 变量类型

}

9）数组声明

var 数组名称 [数组长度]数组元素类型

10）切片声明

var 切片名称 []切片元素类型

var 切片名称 []切片元素类型 =make（[]切片元素类型，切片初始长度）

切片名称：=make（[]切片元素类型，切片初始长度）

切片名称：=make([]切片元素类型，切片初始长度，切片容量)

11）map声明

var 名称 map[键数据类型]值数据类型

名称=make（map[键数据类型]值数据类型）

12）函数声明

func 函数名称（参数列表）[返回值名称 返回值数据类型]{//参数列表包括参数名称和参数数据类型

函数体

return 返回值名称

}

13)接口声明

type interfacename interface{

methodname[returntype]

}

14）批量声明

var(

变量名 变量类型

)

GO关键字

break,default,func,interface,select,case,defer,go,map,struct,chan,else,goto,package,switch,const,fallthrough,if,range,type,continue,for,import,return,var

GO预定义字

append,bool,byte,cap,close,complex,complex64,complex128,uint8,uint16,uint32,uint64,copy,false,float32,float64,imag,int,int8,int16,int32,int64,iota,len,make,new,nil,panic,print,println,real,recover,string,true,uint,uintptr