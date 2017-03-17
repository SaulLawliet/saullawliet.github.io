---
layout: post
title: Bash 条件判断中括号的用法
categories: bash
comments: true
share: false
image:
  feature:

modified:
date: 2017-03-17T11:26:48+08:00
---

{% include _toc.html %}

在这里总结一下条件语句中的各种括号。<br>
**注：以下的测试代码只展示下划线部分**<br>
`if ___;then echo "true"; else echo "false";fi`


# ( ) 或 无括号
一段命令是否执行成功

~~~ bash
cat exist-file > /dev/null  # true
cat not-exist-file          # false
~~~

# (( ))
数学表达式

~~~ bash
0  # false
1  # true   ps: 非0的数字都是true
a  # false  ps: 字母都是false
1a # false  ps: 数字+字母会报错
a1 # false  ps: 字母开头混合数字都是false

# 支持各种整数数学运算
1+1  == 2  # true
2*2  == 4  # true
2**3 == 8  # true
4/2  == 2  # true
4%2  == 0  # true
~~~

# [ ]

> 建议用 `[[ ]]` 代替 `[ ]`

**括号前后一定要有空格**<br>
对于逻辑运算符，只支持 `==` 和 `!=`， 并且只能用于字符串比较<br>
其他比较请用 `-xx`(`-z, -f, -eq ...`) 的形式<br>
另，逻辑非(`!`)，逻辑与(`-o`)，逻辑或(`-a`)

~~~ bash
a == a  # true
a != a  # false

$a == b    # 如果 $a 未赋值，则报错。所以有下面这种写法
a$a == ab  # 在 $a 和 b 前(或后)加入相同的字符，则可避免 $a 未赋值的报错

-z ''   # true
1 -eq 1 # true

-z '' -a 1 -eq 2    # false
-z '' -o 1 -eq 2    # true
-z '' -a ! 1 -eq 2  # true  ! 1 -eq 2 等同于 1 -ne 2 ，为了用 ! 而用;)
~~~

# [[ ]]
**括号前后一定要有空格**<br>
可以理解为`[ ]`的升级版，并且向下兼容<br>
对于逻辑运算符，支持 `==` `!=` `>` `<` `&&` `||`，不支持 `>=` `<=`<br>

~~~ bash
$a == b  # 如果 $a 未赋值，不会报错

1 == 1 && 2 > 3  # false
1 == 1 || 2 > 3  # true
~~~
