Go性能优化

性能优化

基准测试工具benchmark

评估性能的代码

go test -bench=.-benchmem

性能评估工具的使用

go mod init pprof

go build 

./pprof -cpuprofile cpu.prof -memprofile mem.prof

go tool pprof cpu.prof

性能优化建议：

slice预分配内存尽可能在使用make()初始化切片时提供容量信息，切片操作不复制切片指向的元素，创建新的切片会复用原切片底层数组，可使用copy替代re-slice。

map预分配内存不断向map中添加元素会触发map的扩容，提前分配空间可以减少内存拷贝和Rehash消耗。

字符串使用strings.WriteString()底层为[]byte数组，不需要重新分配内存，拼接字符串比加号和其他方法快得多。

空结构体不占据空间可作为占位符使用，可以用map代替实现Set，不适用map的值能节省空间。

atomic包效率比锁高，sync.Mutex应用来保护一段逻辑而非变量，非数值操作用atomic.Value能承载一个interface{}。

普通应用代码不要一味追求性能。