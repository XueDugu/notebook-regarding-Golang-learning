Go性能优化分析工具

性能调优原则：要依据数据而不是猜测，要定位最大瓶颈而不是细枝末节、不要过早优化、不要过度优化。

pprof是用于可视化和分析性能分析数据的工具。

运行测试时可以打开localhost:6060/debug/pprof/

排查时重点关注allocs,block,heap,mutex,profile。

