Docopt
=====
docopt 是一款很好用的命令行参数解释器</br>
docopt 本质上是在 Python 中引入了一种针对命令行参数的形式语言，在代码的最开头使用"""文档注释的形式写出符合要求的文档，就会自动生成对应的parse，体验非常赞。</br>
样例：
```python
#coding:utf-8
"""命令行火车票查看器

Usage:
    ticket [-gkzdt] <from> <to> <date> 

Options:
    -h,-help: 显示帮助菜单
    -g: 高铁
    -k: 普快
    -z: 直达
    -d: 动车
    -t: 特快
  
Example:
   ticket -g 北京 上海 2017-1-20</br>
"""
from docopt import docopt

def cli():
	"""command-line interface"""
	arguments=docopt(__doc__)
	print(arguments)
	
if __name__ == '__main__':
	cli()
```
下面根据样例来介绍一下docopt的用法:
## Usage  
```
所有出现在`Usage`:（区分大小写）和一个空行之间的文本都会被识别为一个命令组合，Usage后的第一个词将会被识别为这个程序的名字，所有命令组合的每一个部分（空格分隔）都会成为字典中的一个key.
```
### Argument
形如 `<argument>` 或者 `ARGUMENT` 的文本将会被识别为参数。 在转化后的字典中的取值为 `True` 或者 `False` 。如上面的例子中:  
```
ticket [-gkzdt] <from> <to> <date>  
from to date 都被识别为参数了 
```
### Option  
形如 `[optional elements]` 的文本是可选项。 elements包括上述的三种类型：参数，选项以及命令。在上面的例子里：  
```
ticket [-gkzdt] <from> <to> <date>
[-gkzdt]就是可选项
```
### Required elements
形如 `(required elements)` 的文本是必填项。
### Another Optional
形如 `element|another` 的文本是选择项.  
```
eg: 
Usage: my_program go (--up | --down | --left | --right)
```
