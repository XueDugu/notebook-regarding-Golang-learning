go module

管理包的依赖关系

初始化模块

go mod init projectname

依据go.mod处理依赖关系

go mod tidy

将包复制到vender目录

go mod vender

显示详细依赖关系

go list -m -json all

下载依赖

go mod download [path@version]

