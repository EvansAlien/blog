---
title: es6语法之路
author: zhangy
categories: 个人博客
date: 2019-06-20 15:02:55
tags:
---

##  const 与 let变量
    在es6之前我们定义是用**var**关键字去定义的，但是**var**带来一些很麻烦
    ```
    function a(isCold) {
        if (isClod) {
            var b = 1
        } else {
            var c = 2
            console.log(b)
        }
    }
    a(false) // undefined 因为执行function函数之前,所有变量都会被提升, 提升到函数作用域顶部.
    function a(isCold) {
        if (isClod) {
            const b = 1
        } else {
            const c = 2
            console.log(b)
        }
    }
    a(false) // b iis not defined 因为**b**没有在 else 语句、函数作用域或全局作用域内声明
    ```
    使用let声明的变量可以重新赋值,但是不能在同一作用域内重新声明
    使用const声明的变量必须赋值初始化,但是不能在同一作用域类重新声明也无法重新赋值


## 结构赋值
    es6允许按照一定的模式，从数组和对象中提取值，对变量进行赋值
    ```
    let [a, b, c] = [1, 2, 3] // let a= 1, b = 2, c = 3;
    let [a, ...b] = [1, 2, 3, 4] // let a = 1, b = [2, 3, 4]
    let [a, ...b, c] = [1, 2, 3, 4, 5, 6] // let a = 1, b报错
    let [x, y, ...z] = ['a'] // x = 'a' y = undefined z = []
    let [foo] = []; // undefined 如果解构不成功，变量的值就等于undefined
    ```

## 字符串的新方法

1.  传统上，JavaScript 只有indexOf方法，可以用来确定一个字符串是否包含在另一个字符串中。ES6 又提供了三种新方法。
    ```
    **includes()** 返回布尔值，表示是否找到了参数字符串.
    **startsWith()** 返回布尔值，表示参数字符串是否在原字符串的头部. 
    **endsWidth()** 返回布尔值，表示参数字符串是否在原字符串的尾部.
    ```
    这三种方法都有第二个参数，表示开始的索引

2.  repeat() 
    **repeat**方法返回一个新字符串，表示将源字符串重复n次

3.  padStart()，padEnd()
    ES2017 引入了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。padStart()用于头部补全，padEnd()用于尾部补全
    padStart()和padEnd()一共接受两个参数，第一个参数是字符串补全生效的最大长度，第二个参数是用来补全的字符串。

    ```
    'x'.padStart(5, 'ab') // 'ababx'
    'x'.padStart(4, 'ab') // 'abax'

    'x'.padEnd(5, 'ab') // 'xabab'
    'x'.padEnd(4, 'ab') // 'xaba'
    ```
    如果原字符串的长度，等于或大于最大长度，则字符串补全不生效，返回原字符串。
    ```
    'xxx'.padStart(2, 'ab') // 'xxx'
    'xxx'.padEnd(2, 'ab') // 'xxx'
    ```

4.  trimStart(), trimEnd()
    ES2019 对字符串实例新增了trimStart()和trimEnd()这两个方法。它们的行为与trim()一致，trimStart()消除字符串头部的空格，trimEnd()消除尾部的空格。它们返回的都是新字符串，不会修改原始字符串。
    ```
    const s = '  abc  ';

    s.trim() // "abc"
    s.trimStart() // "abc  "
    s.trimEnd() // "  abc"
    ```