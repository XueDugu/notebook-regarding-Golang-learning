runtime包

runtime.Gosched()

让出CPU时间片重新等待安排任务

runtime.Goexit()

退出当前协程

runtime.GOMAXPROCS

设置CPU最大核心数，如果不进行设置，默认为1