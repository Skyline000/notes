# Python 中的 if \_\_name\_\_ == '\_\_main\_\_' 该如何理解

### 1. 摘要 <a id="1-&#x6458;&#x8981;"></a>

通俗的理解`__name__ == '__main__'`：假如你叫小明.py，在朋友眼中，你是小明`(__name__ == '小明')`；在你自己眼中，你是你自己`(__name__ == '__main__')`。

`if __name__ == '__main__'`的意思是：当.py文件被直接运行时，`if __name__ == '__main__'`之下的代码块将被运行；当.py文件以模块形式被导入时，`if __name__ == '__main__'`之下的代码块不被运行。

### 2. 程序入口 <a id="2-&#x7A0B;&#x5E8F;&#x5165;&#x53E3;"></a>

对于很多编程语言来说，程序都必须要有一个入口，比如C，C++，以及完全面向对象的编程语言Java，C\#等。如果你接触过这些语言，对于程序入口这个概念应该很好理解，C，C++都需要有一个main函数作为程序的入口，也就是程序的运行会从main函数开始。同样，Java，C\#必须要有一个包含Main方法的主类，作为程序入口。

而Python则不同，它属于脚本语言，不像编译型语言那样先将程序编译成二进制再运行，而是动态的逐行解释运行。也就是从脚本第一行开始运行，没有统一的入口。

一个Python源码文件（.py）除了可以被直接运行外，还可以作为模块（也就是库），被其他.py文件导入。不管是直接运行还是被导入，.py文件的最顶层代码都会被运行（Python用缩进来区分代码层次），而当一个.py文件作为模块被导入时，我们可能不希望一部分代码被运行。

#### 2.1 一个.py文件被其他.py文件引用 <a id="21-&#x4E00;&#x4E2A;py&#x6587;&#x4EF6;&#x88AB;&#x5176;&#x4ED6;py&#x6587;&#x4EF6;&#x5F15;&#x7528;"></a>

假设我们有一个const.py文件，内容如下：

```text
PI = 3.14

def main():
    print("PI:", PI)

main()

# 运行结果：PI: 3.1412345678
```

现在，我们写一个用于计算圆面积的area.py文件，area.py文件需要用到const.py文件中的PI变量。从const.py中，我们把PI变量导入area.py：

```text
from const import PI

def calc_round_area(radius):
    return PI * (radius ** 2)

def main():
    print("round area: ", calc_round_area(2))

main()

'''
运行结果：
PI: 3.14
round area:  12.56
'''123456789101112131415
```

#### 2.2 修改const.py，添加`if __name__ == "__main__"` <a id="22-&#x4FEE;&#x6539;constpy&#x6DFB;&#x52A0;if-name-main"></a>

我们看到const.py中的main函数也被运行了，实际上我们不希望它被运行，因为const.py提供的main函数只是为了测试常量定义。这时`if __name__ == '__main__'`派上了用场，我们把const.py改一下，添加`if __name__ == "__main__"`：

```text
PI = 3.14

def main():
    print("PI:", PI)

if __name__ == "__main__":
    main()1234567
```

运行const.py，输出如下：

```text
PI: 3.141
```

运行area.py，输出如下：

```text
round area:  12.561
```

如上，我们可以看到`if __name__ == '__main__'`相当于Python模拟的程序入口，Python本身并没有这么规定，这只是一种编码习惯。由于模块之间相互引用，不同模块可能有这样的定义，而程序入口只有一个。到底哪个程序入口被选中，这取决于`__name__`的值。  
  


### 3. `__name__` <a id="3-name"></a>

#### 3.1 `__name__`反映一个包的结构 <a id="31-name&#x53CD;&#x6620;&#x4E00;&#x4E2A;&#x5305;&#x7684;&#x7ED3;&#x6784;"></a>

`__name__`是内置变量，可用于反映一个包的结构。假设我们有一个包a，包的结构如下：

```text
a
├── b
│   ├── c.py
│   └── __init__.py
└── __init__.py12345
```

在包a中，文件`c.py，__init__.py，__init__.py`的内容都为：

```text
print(__name__)1
```

当一个.py文件（模块）被其他.py文件（模块）导入时，我们在命令行执行

```text
python -c "import a.b.c"1
```

输出结果：

```text
a
a.b
a.b.c123
```

由此可见，`__name__`可以清晰地反映一个模块在包中的层次。

#### 3.2 `__name__`表示当前模块的名字 <a id="32-name&#x8868;&#x793A;&#x5F53;&#x524D;&#x6A21;&#x5757;&#x7684;&#x540D;&#x5B57;"></a>

`__name__`是内置变量，可用于表示当前模块的名字。我们直接运行一个.py文件（模块）

```text
python a/b/c.py1
```

输出结果：

```text
__main__1
```

由此我们可知：如果一个.py文件（模块）被直接运行时，则其没有包结构，其`__name__`值为`__main__`，即模块名为`__main__`。

所以，`if __name__ == '__main__'`的意思是：当.py文件被直接运行时，`if __name__ == '__main__'`之下的代码块将被运行；当.py文件以模块形式被导入时，`if __name__ == '__main__'`之下的代码块不被运行。

### 4. `__main__.py`文件与`python -m` <a id="4-mainpy&#x6587;&#x4EF6;&#x4E0E;python-m"></a>

Python的-m参数用于将一个模块或者包作为一个脚本运行，而`__main__.py`文件相当于是一个包的“入口程序“。

#### 4.1 运行Python程序的两种方式 <a id="41-&#x8FD0;&#x884C;python&#x7A0B;&#x5E8F;&#x7684;&#x4E24;&#x79CD;&#x65B9;&#x5F0F;"></a>

* `python xxx.py`，直接运行xxx.py文件
* `python -m xxx.py`，把xxx.py当做模块运行

假设我们有一个文件run.py，内容如下：

```text
import sys

print(sys.path)123
```

我们用直接运行的方式启动

```text
python run.py1
```

输出结果\(为了说明问题，输出结果只截取了重要部分，下同\)：

```text
['/home/huoty/aboutme/pythonstudy/main', ...]1
```

然后以模块的方式运行:

```text
python -m run.py1
```

输出内容

```text
['', ...]
/usr/bin/python: No module named run.py12
```

由于输出结果只列出了关键的部分，应该很容易看出他们之间的差异：

* 直接运行方式是把run.py文件所在的目录放到了sys.path属性中
* 以模块方式运行是把你输入命令的目录（也就是当前工作路径），放到了 sys.path 属性中。

以模块方式运行还有一个不同的地方：多出了一行`No module named run.py`的错误。实际上以模块方式运行时，Python先对run.py执行一遍 import，所以`print(sys.path)`被成功执行，然后Python才尝试运行run.py模块，但是在path变量中并没有run.py这个模块，所以报错。正确的运行方式，应该是`python -m run`。

#### 4.2 `__main__.py`的作用 <a id="42-mainpy&#x7684;&#x4F5C;&#x7528;"></a>

仍然先看例子，假设我们有如下一个包package：

```text
package
├── __init__.py
└── __main__.py123
```

其中，文件`__init__.py`的内容

```text
import sys

print("__init__")
print(sys.path)1234
```

其中，文件`__main__.py`的内容

```text
import sys

print("__main__")
print(sys.path)1234
```

接下来，我们运行这个package，使用`python -m package`运行，输出结果：

```text
__init__
['', ...]

__main__
['', ...]12345
```

使用`python package`运行，输出结果：

```text
__main__
['package', ...]12
```

总结一下

* 当加上-m参数时，Python会把当前工作目录添加到sys.path中；而不加-m时，Python则会把脚本所在目录添加到sys.path中。
* 当加上-m参数时，Python会先将模块或者包导入，然后再执行。
* `__main__.py`文件是一个包或者目录的入口程序。不管是用`python package`还是用`python -m package`运行，`__main__.py`文件总是被执行。  

### 5. 参考文章 <a id="5-&#x53C2;&#x8003;&#x6587;&#x7AE0;"></a>

[1. Python 中的 if **name** == ‘**main**’ 该如何理解](http://blog.konghy.cn/2017/04/24/python-entry-program/)

