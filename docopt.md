docopt 是一款很好用的命令行参数解释器
docopt 本质上是在 Python 中引入了一种针对命令行参数的形式语言，在代码的最开头使用"""文档注释的形式写出符合要求的文档，就会自动生成对应的parse，体验非常赞。
样例：
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
   ticket -g 北京 上海 2017-1-20
"""
from docopt import docopt

def cli():
	"""command-line interface"""
	arguments=docopt(__doc__)
	print(arguments)
if __name__ == '__main__':
	cli()
	