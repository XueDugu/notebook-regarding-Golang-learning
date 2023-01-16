GO自增常量

iota初始为0，每声明一个常量iota++，遇到const变回0

使用下划线或赋其他值可以跳过某些值

例

const(

a1=iota//a1为0

b=666

_

a2=iota//a2为3

)