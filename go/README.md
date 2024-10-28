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

Go程序由包组成，包之间数据/函数的交互以及调用使用 _导出名_ 。导出名是约定的写法：若方法/函数/变量的首字母大写，则是可以在其他包访问的；若小写则是包内部的。

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

另外，函数也可以返回多个值：

Function can also return values:
```go
func swap(x, y string) (string, string) {
    return y, x
}
```

或者带名字的返回值：

Or named-result:
```go
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```

### Variables

变量使用`var`语句声明，变量类型在变量名后。变量可以在包/函数层级声明。

Variables are declared using the `var` statement with the variable type after the variable name. Variables can be declared at package/function level.

```go
package main

import "fmt"

var c, python, java bool

func main() {
	var i int
	fmt.Println(i, c, python, java)
}
```
输出为：`0 false false false`  

The output is: `0 false false false`

变量也可以设置初始值，如果设置了初始值可以不用声明类型，会自动推断类型。未设置初始值，默认为0值，（0，false，“”）

Variables can also be initialized with values, and if an initial value is set, the type can be omitted as it will be inferred.

```go
func main() {
	var c, python, java = true, false, "no!"
	fmt.Println(i, j, c, python, java)
}
```

函数内也可以使用短变量声明，函数外每个语句都必须以关键字开始。
_Short variable declarations_ can also be used inside a function. Outside a function, every statement must start with a keyword.

```go
func main() {
	var c, python, java = true, false, "no!"
    k := 1
	fmt.Println(k, c, python, java)
}
```

### Basic Types

go的基本类型有什么`bool string int unit float complex`之类的。`int`是有符号的整型，`uint`是无符号的，只能储存正数或者0。

Basic types contains `bool string int unit float complex`. `int` can store integers with sign, `uint` with no sign.


类型转换可以使用`T(v)`把`v`转换为`类型T`的值。

Type conversions: `T(v)` convert value `v` to type `T`.
