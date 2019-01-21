# PerFee Python 开发人员代码规约

## 历史版本

| 版本 | 修订日期 | 参与成员 |
| :-- | :-- | :-- |
| v1.0 | 2019年01月22日 | 李文武，付江南 |

为规范和统一代码风格，提高代码的可读性和可维性，特制定此规约。世界上没有让所有人百分百完全满意的规约，所以本文中部分规则条款可能会对你目前的代码习惯造成不适。

## 参考规范与最佳实践：
> 1. PEP 8 -- Style Guide for Python Code:  
> https://www.python.org/dev/peps/pep-0008/  
> 
> 2. Google Python Style Guide  
> 英文原文：https://github.com/google/styleguide/blob/gh-pages/pyguide.md  
> 中文译文：https://zh-google-styleguide.readthedocs.io/en/latest/google-python-styleguide/

## IDE/编辑器集成指南
> pycharm: 基于 autopep8 库  
> https://github.com/hscgavin/autopep8-on-pycharm  
> https://segmentfault.com/a/1190000005816556  
>
> vim: 基于 flake9-vim 插件  
> https://github.com/andviro/flake8-vim

## 特别说明
> 1. 从规约颁布即日起，所有代码必须通过PEP8检查器（编辑器插件）检验后方可提交
> 2. 之前已有各项目代码在合适时机进行改造以符合规范

## 函数、参数、变量（属性）、常量、类命名
### 总则
> 1. 模块文件名所有单词必须小写，且中间以下划线隔开，如 ```foo_bar.py```
> 2. 类名遵守驼峰命名规则，每个单词首字母均须大写。比如 ```FooMachine```
> 3. 函数名、参数、变量名（一般属性）所有单词必须小写，且中间以下划线隔开，如 ```foo_bar```
> 4. 常量所有单词必须大写，且中间以下划线隔开，如 ```FOO_BAR```
> 5. 类的保护性成员（属性、常量、方法）须以线下划线开头，如 ```_foo``` ```_BAR``` ```_inner_hello()```

### 对照表：

| 项目 | 公有域 | 内部域（私有、保护） |
| :-- | :-- | :-- |
| 模块名 | ```lower_with_under``` | ```_lower_with_under``` |
| 包名 | ```lower_with_under``` | |
| 普通类 | ```CapWords``` | ```_CapWords``` |
| 异常类 | ```CapWords``` | |
| 函数名 | ```lower_with_under()``` | ```_lower_with_under()``` |
| 常量 | ```FOO_BAR``` | ```_FOO_BAR``` |
| 变量 | ```lower_with_under``` | ```_lower_with_under``` |
| 类变量 | ```lower_with_under``` | ```_lower_with_under``` (protected) or ```__lower_with_under``` (private) |
| 类方法 | lower_with_under() | ```_lower_with_under()``` (protected) or ```__lower_with_under()``` (private) |
| 函数/方法的参数 | ```lower_with_under``` | |
| 局部变量 | ```lower_with_under``` | |

## 代码书写规范示例

### 代码行字符宽度相关
> 错误示范：代码未超过79个字符强行换行，造成不必要的浪费和干扰，增加阅读难度

```
def hello_foo_bar(
        god, says, that, awesome, people):
    print 'hello'

```

> 正确示范

```
def hello_foo_bar(god, says, that, awesome, people):
    print 'hello'
```

> 错误示范：单行超过超过79个字符但未换行，违反PEP8规范  
> https://www.python.org/dev/peps/pep-0008/#maximum-line-length

```
def hello_foo_bar(god, says, that, awesome, people, doing, stupid, things, always):
    print 'hello'
```

> 正确示范

```
def hello_foo_bar(god, says, that, awesome, people, doing, stupid,
                  things, always):
    print 'hello'
```


### 函数参数较多情况

> 错误示范：参数从左括号换行后，没有增加缩进量，违反PEP8规范  
> https://www.python.org/dev/peps/pep-0008/#id17

```
def hello_foo_bar(
    god, says, that, awesome, people, doing, stupid, things, always):
    print 'hello'
```

> 错误示范：右括号另起一行，造成不必要的浪费和干扰，增加了阅读难度

```
def hello_foo_bar(
    god, says, that, awesome, people, doing, stupid, things, always
):
    print 'hello'
```

> 正确示范

```
# 一般换行写法
def hello_foo_bar(god, says, that, awesome, people, doing, stupid,
                  things, always):
    print 'hello'
                      
# 左括号换行写法，适用于参数特别多的情况
def hello_foo_bar(
        god, says, that, awesome, people, doing, stupid, things, always,
        you, need known, it):
    print 'hello'
```

### 模块、类、函数名较长、参数较多情况

> 错误示范：由于函数名较长，参数换行后前导空格太多，可读性差

```
# module name "funny_module.py"
def this_is_a_very_long_function_name_of_hello_foo_bar(god, says, that,
                                                       awesome, people,
                                                       doing):
    print 'hello'


# module demo client
import funny_module


funny_module.this_is_a_very_long_function_name_of_hello_foo_bar("Jack Ma",
                                                                "said",
                                                                "i",
                                                                "have",
                                                                "a",
                                                                "dream")
```

> 正确示范

```
# module name "funny_module.py"
def this_is_a_very_long_function_name_of_hello_foo_bar(
        god, says, that, awesome, people, doing):
    print 'hello'


# module demo client
import funny_module


funny_module.this_is_a_very_long_function_name_of_hello_foo_bar(
    "Jack Ma", "said", "i", "have", "a", "dream")
```
