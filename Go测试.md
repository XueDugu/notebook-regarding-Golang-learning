Go测试

回归测试-集成测试-单元测试，覆盖率变大，成本降低

单元测试包括输入、输出、期望、校对

单元测试可以保证质量、提升效率

单元测试规则

测试文件以_test.go结尾

测试函数TestXxx(*testing.T)

初始化逻辑放到TestMain中

assert包可以实现Equal功能

代码覆盖率可用通过多次单测提升

一般覆盖率为50%~60%，80%+为较高覆盖率

测试分支相互独立

测试单元粒度足够小，函数单一职责

外部依赖：稳定&幂等

幂等重复输入固定输出

外部依赖用到mock机制

快速mock函数：为一个函数或方法打桩，将内存中函数地址替换成运行时函数地址，不依赖本地文件，Patch()装载，UnPatch()卸载

基准测试：随计选择执行的服务器，Benchmark开头

fastrand函数地址https://github.com/bytedance/gopkg

社区话题页面-单页面服务端小功能

功能：展示话题和回帖列表、暂时不考虑前端页面实现、仅仅是先一个本地web服务、话题和回帖数据用文件存储

需求用例：浏览消费用户

分层结构：数据层（数据Model，外部数据的增删改查）、逻辑层（业务Entity，处理核心业务逻辑输出）、视图层（视图View，处理和外部的交互逻辑）

Gin高性能go web框架https://github.com/gin-gonic/gin#installation

Go Mod 

gopkg.in/gin-gonic/gin.v1@v1.3.0

通过将数据行映射到内存Map达成检索功能