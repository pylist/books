## 跨平台编译
默认我们```go build```的可执行文件都是当前操作系统可执行的文件，如果我想在windows下编译一个linux下可执行文件，那需要怎么做呢？

只需要指定目标操作系统的平台和处理器架构即可：

```cmd
SET CGO_ENABLED=0  // 禁用CGO
SET GOOS=linux  // 目标平台是linux
SET GOARCH=amd64  // 目标处理器架构是amd64
``` 
然后再执行```go build```命令，得到的就是能够在Linux平台运行的可执行文件了。

Mac 下编译 Linux 和 Windows平台 64位 可执行程序：
```bash
CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build
CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build
```
Linux 下编译 Mac 和 Windows 平台64位可执行程序：
```bash
CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build
CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build
```
Windows下编译Mac平台64位可执行程序：
```cmd
SET CGO_ENABLED=0
SET GOOS=darwin
SET GOARCH=amd64
go build
```

## Golang 执行流程分析
> 如果是对源码编译后，再执行，Go 的执行流程如下图

![image](6B2A07FF89534BB1BE30B9719466AB2F)
> 如果我们是对源码直接 执行 go run 源码，Go 的执行流程如下图

![image](80DCC9F2ACF94B23AA9E6BDC4DFE6D93)
### 两种执行流程的方式区别
1. 如果我们先编译生成了可执行文件，那么我们可以将该可执行文件拷贝到没有 go 开发环境的机器上，仍然可以运行
2. 如果我们是直接 go run go 源代码，那么如果要在另外一个机器上这么运行，也需要 go 开发环境，否则无法执行。
3. 在编译时，编译器会将程序运行依赖的库文件包含在可执行文件中，所以，可执行文件变大了很多