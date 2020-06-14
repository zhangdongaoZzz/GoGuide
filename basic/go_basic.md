

## 1.Golang基础

### 1.1 Golang语言有哪些特点？

1.  并发实现和控制简单。语言级别支持协程(goroutine)并发协程又称微线程，比线程更轻量、开销更小，性能更高（实际上协程就是一个线程同步执行多个任务），关键字（go）用于启动协程。**高并发是Golang语言最大的亮点 。**

2.  Golang内存自动回收。C/C++程序员需要自己管理内存的分配，增加了程序崩溃的可能性。

3.  编译。Go是一门静态语言，但是相对于C/C++，Golang在大型项目上的编译速度要快得多。编译过程可以参考这篇文章：[初探 Go 的编译命令执行过程](https://halfrost.com/go_command/)

4. 由于Golang诞生的比较晚（2009年），所以Golang天生具备了完善的网络编程接口，在Web服务开发上，Golang原生的接口就能高效完成基本任务。对框架的依赖远小于Java，python等等。

5. 编程规范。Go语言的编程规范强制集成在语言中，比如明确规定花括号摆放位置，强制要求一行一句，不允许导入没有使用的包，不允许定义没有使用的变量。通常开发中，我们使用gomat工具来强制格式化代码。

6. 异常处理。Golang不支持try...catch这样的异常处理方式，而是被调用函数直接返回异常值,例如：

   ~~~go
   buf := make([]byte, 100)
   n, err := r.Read(buf)   //此处直接返回err
   if err!= nil{
       log.Fatal("read error:",err)//打印日志看err详情
   }
   ~~~

7. 其他：Go语言没有VM，没有类概念，不支持继承，没有构造方法，没有注解，没有泛型，秉承less is more的极简思想。面试官再也不会让你判断这段代码输出的到底是汪汪汪还是喵喵喵了。

 ### 1.2 Golang语法

#### 1.2.1 名称

* 关键字:只能用在语法允许的地方，不能作为变量名。

<table>
    <tr>
      <td>break</td>
      <td>default</td>
      <td>func</td>
      <td>interface</td>
      <td>select</td>
   </tr>
   <tr>
      <td>case </td>
      <td>defer</td>
      <td>go</td>
      <td>map</td>
      <td>struct</td>
   </tr>
   <tr>
      <td>chan</td>
      <td>else</td>
      <td>goto</td>
      <td>package</td>
      <td>switch</td>
   </tr>
   <tr>
      <td>const</td>
      <td>fallthrough</td>
      <td>if</td>
      <td>range</td>
      <td>type</td>
   </tr>
   <tr>
      <td>continue</td>
      <td>for</td>
      <td>import</td>
      <td>return</td>
      <td>var</td>
   </tr>
</table>

* 常量：true/false/nil/iota

* 类型：

  |         整数类型          |             浮点型              |             其他数字类型              |
  | :-----------------------: | :-----------------------------: | :-----------------------------------: |
  |  uint8<br/>无符号8位整型  | float32<br/>IEEE-754 32位浮点型 |          byte<br />类似uint8          |
  | uint16<br/>无符号8位整型  | float64<br/>IEEE-754 64位浮点型 |          rune<br />类似int32          |
  | uint32<br/>无符号32位整型 |  complex64<br/>32位实数和虚数   |          uint<br />32或64位           |
  | uint64<br/>无符号64位整型 |  complex128<br/>64位实数和虚数  |        int<br />与uint一样大小        |
  |  int8<br/>有符号8位整型   |                                 | uintptr<br />无符号整型，用于存放指针 |
  | int16<br/>有符号16位整型  |                                 |        string<br />字符串bool         |
  | int32<br/>有符号32位整型  |                                 |          bool<br />布尔类型           |
  | int64<br/>有符号64位整型  |                                 |                                       |

  

#### 1.2.2 声明

