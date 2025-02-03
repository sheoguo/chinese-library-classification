# Chinese-library-classification
 <span style="color:blue;"><i> 一个好用的中文图书分类数据获取工具！！！Please read this in English. </i></span>
 
## 介绍
------------
这是一个获取中文图书分类数据的python包！《中国图书馆分类法》是我国建国后编制出版的一部具有代表性的大型综合性分类法，简称《中图法》。它是我国图书馆，信息文献机构使用最广泛的分类法体系，目前已经编制到第五版。我在硕士期间做过许多涉及到中图分类数据的项目，发现目前的结构化中图分类数据比较难获得，用来做一些任务比较不方便。于是想写这样一个python包，可以直接检索中图分类数据，也能获取其各级分类数据，优化一下类似工作流程。
## 数据源
------------
中图分类官网给出的[电子版链接](http://clc.nlc.cn/ztfdzbjj.jsp)也比较难用，由于想要获取的是结构化的中图分类数据，所以只能从目前的一些中图分类号检索网站进行数据爬取。本python包用到的中图分类数据由两个网站爬取并最终综合得来: [网站1](http://clc.nlc.cn/ztfdzbjj.jsp) [网站2](https://ztflh.xhma.com/)。爬取代码看项目[CLC-data-crawl](https://github.com/sheoguo/CLC-data-crawl)。
## 安装
------------

install via pip (from PyPI):

    pip install chinese-library-classification

## 功能

------------

由分类号获取其相关信息(其中两个link是两个数据爬取网站对应的此分类号页面)

```python
>>> from chinese_library_classification import Chineselibraryclassification
>>> CLC = Chineselibraryclassification()
>>> print(CLC.num2info('A2'))

{"name":"列宁著作","level":2,"link1":"https://ztflh.xhma.com/html/17.html","link2":"https://www.clcindex.com/category/A2/","up_level":"A","next_level":['A21','A22','A23','A25','A26','A28']}


#由分类号获取其所在的上层所有类目

>>> print(CLC.num2upper('P455'))

[['P45','天气预报'],['P4','大气科学（气象学）'],['P','天文学、地球科学']]

#由分类号获取其所在的下一级所有分类
>>> print(CLC.num2next('U655'))

[('U655.1','施工技术管理'),('U655.2','施工组织与设计'),('U655.3','施工设备'),('U655.4','施工技术'),('U655.5','各种工程')]




