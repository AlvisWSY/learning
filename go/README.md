# Go Learning

这是用来记录go学习过程的repo。

This directory documents the process of learning Go.

## Getting Started

首先，go的语法基础使用在线工具 [Go Tour](https://tour.go-zh.org/basics/1)学习。

First, learn the basics of Go syntax and components using the online tool [Go Tour](https://tour.go-zh.org/basics/1).

## Basic Syntax

### Package

Go程序由包构成。`main`包是特殊的包，表示这是一个可独立运行的程序，而不是库或者模块。在`main`包中必须有一个`main`函数，作为程序执行的**起点**，相当于其他语言的主函数。

Go programs are constructed from packages. The `main` package is a special package indicating that this is a standalone executable program, not a library or module. The `main` package must contain a `main` function, which serves as the entry point for program execution, similar to the main function in other languages.

### Imports (Libraries/Packages)

Go使用`import`关键字导入包，例如：`import "fmt"`。多个包可以以“分组”形式一起导入：

Go uses the `import` keyword to import packages, e.g., `import "fmt"`. Multiple packages can be imported in a grouped form:
```go
import (
    "math"
    "fmt"
)
```

### Exported Names

Go程序由包组成，包之间数据/函数的交互以及调用使用_导出名_。导出名是约定的写法：若方法/函数/变量的首字母大写，则是可以在其他包访问的；若小写则是包内部的。

Go programs consist of packages, and interaction or calls between them use _exported names_. An exported name follows a convention: if a method/function/variable starts with an uppercase letter, it is accessible from other packages. If it starts with a lowercase letter, it is internal to the package.

### Functions

Go的函数定义有点像C，但是变量类型在变量名的后面。

Function definitions in Go are somewhat similar to C but with the type specified after the variable name.
```go
func Add(x int, y int) int {
    return x + y
}
```
如果连续的几个变量类型一样，可以省略写成`(x, y int)` 

If consecutive variables share the same type, it can be abbreviated as `(x, y int)`.

