---
layout: post
title: rang循环取元素地址时无法取得正确的指针地址
category: it
tags: [golang]
no-post-nav: true
---

创建指针数组的时候， range 循环容易采的坑。

错误代码
```错误代码
const max = 3

func main() {
    number := [max]int{5, 6, 7}
    var ptrs [max]*int //指针数组
    //将number数组的值的地址赋给ptrs
    for i, x := range &number {
        ptrs[i] = &x
    }
    for i, x := range ptrs {
        fmt.Printf("指针数组：索引:%d 值:%d 值的内存地址:%d\n", i, *x, x)
    }
}
```

```输出结果
指针数组：索引:0 值:7 值的内存地址:824634204304
指针数组：索引:1 值:7 值的内存地址:824634204304
指针数组：索引:2 值:7 值的内存地址:824634204304
```

>原因：
从结果中我们发现内存地址都一样，而且值也一样。怎么回事？
这个问题是range循环的实现逻辑引起的。跟for循环不一样的地方在于range循环中的x变量是临时变量。
range循环只是将值拷贝到x变量中。因此内存地址都是一样的。

正确代码1
```正确代码1
const max = 3

func main() {
    number := [max]int{5, 6, 7}
    var ptrs [max]*int //指针数组
    //将number数组的值的地址赋给ptrs
    for i := 0; i < max; i++ {
        ptrs[i] = &number[i]
    }
    for i, x := range ptrs {
        fmt.Printf("指针数组：索引:%d 值:%d 值的内存地址:%d\n", i,*x, x)
    }
}
```

```输出结果
指针数组：索引:0 值:5 值的内存地址:824634212672
指针数组：索引:1 值:6 值的内存地址:824634212680
指针数组：索引:2 值:7 值的内存地址:824634212688
```

正确代码2
```正确代码2
cconst max = 3

func main() {
    number := [max]int{5, 6, 7}
    var ptrs [max]*int //指针数组
    //将number数组的值的地址赋给ptrs
    for i, _ := range number {
        ptrs[i] = &number[i]
    }
    for i, x := range ptrs {
        fmt.Printf("指针数组：索引:%d 值:%d 值的内存地址:%d\n", i, *x, x)
    }
}
```