Go 语言进阶与依赖管理

Go可以充分发挥多核优势，高效运行。

协程：用户态，轻量级线程，栈MB级别。

线程：内核态，线程跑多个协程，栈KB级别。

Go提倡通过通信共享内存而不是通过共享内存而实现通信由于可能会影响程序性能。

Channel

make(元素类型，缓冲大小)//可以不包含缓冲大小

无缓冲通道就是同步通道

共享内存不加锁可能会出现并发安全问题

可以利用WaitGroup实现协程的同步

WaitGroup方法

Add(delta int)//计数器加delta

Done()//计数器减1，可以在写成结束时调用

Wait()//阻塞直至计数器为0，可以在程序return前调用

sdk：软件开发工具包

广泛应用的依赖管理是Go Module

环境变量$GOPATH：bin(项目编译的二进制文件)、pkg(项目编译的中间产物，加速编译)、src(项目源码)(项目代码的直接依赖)(go get下载最新版本的包会放在这里)

GOPATH问题：无法实现package的多版本控制

Go Vender项目依赖优先从Go Vender中获取，如果没有才从GOPATH获取

Go Vender问题：同一项目不能依赖不同版本、无法控制依赖的版本

Go Module通过go.mod文件管理依赖包版本

依赖管理三要素：go.mod、Proxy、go get/mod

go.mod组成：依赖管理基本单元、原生库（表示版本号）、单元依赖（每个依赖由路径和版本号构成）

version：语义化版本（${MAJOR}.${MINOR}.${PATCH}）和伪版本（vX.0.0-yyyymmddhhmmss-abcdefgh1234）

非直接依赖会用//indirect标识出来

主版本是2以上要加上/vN

没有go.mod文件会加上+incompatible

GOPROXY="url,direct"//direct表示源站

go get 路径 ？

当？为@none时删除依赖

当？为@vx.y.z时特定语义版本

当？为@bascobqwociai时特定伪版本

当？为@master时分支最新commit

go mod init

初始化，创建go.mod文件

go mod download

下载模块到本地缓存

go mod tidy

增加需要的依赖，删除不需要的依赖