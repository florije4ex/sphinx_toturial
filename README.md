# Usage

```text
丰富的输出格式：HTML（包括Windows HTML Help）, LaTex（用于可打印PDF）, epub, Texinfo, manual pages, plain text
完备的交叉引用：语义化的标签, 并自动链接函式、类、引文、术语以及类似片段信息
明晰的层级结构：轻松定义文档树, 并自动化链接同级/父级/下级文章
美观的自动索引：自动生成索引以及特定语言模块的索引
精确的语法高亮: 基于 Pygments 自动语法高亮
开方的扩展: 支持代码片段的自动测试, 从Python模块的文档字符串包含（API文档）, 参考 more
用户贡献的扩展: 用户提供的 大约50个扩展,大多可以通过PyPI安装
强大简洁的书写语言: 使用 新结构化文本(reStructuredText) 作为标记语言.
```

```shell
sphinx-build --version
sphinx-quickstart docs

sphinx-build -b html docs/source/ docs/build/html

cd docs && make html
```
## 更换主题
```shell
pip install sphinx_rtd_theme
conf.py

import sphinx_rtd_theme

# html_theme = 'sphinxdoc'
html_theme = 'sphinx_rtd_theme'

#html_theme_path = []
html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]
```

## reStructuredText
```text
reStructuredText 是 Docutils (Documentation Utilities) 标记语法和解析器组件 ( Markup Syntax and Parser Component of Docutils ).
reStructuredText是一个易读, 易写, 所见即所得的明文标记语法和解析系统, 对于 “in-line” 程序文档 (如 Python docstrings) 非常有用, 用于快速创建简单的网页和本地文档. 

专注于文本内容而不是排版样式
兼容所有文本编辑器与字处理软件
渲染导出格式丰富, 如HTML、PDF, 借助一些工具还可以导出Latex、epub等文件
可以使用Git等版本控制系统管理文章版本
可读、直观、易学
```

### 章节
```text
章节头部 ( 参考 ) 由下线(也可有上线)和包含标点的标题 组合创建, 其中下线要至少等于标准文本的长度, 如:
======
Title
======

Subtitle1
---------

SubSubtitle
+++++++++++

Subtitle2
-----------

通常没有专门的符号表示标题的等级, 但是对于Python 文档, 可以使用如下约定:

# 下划线及上划线表示 部分
* 下划线及上划线表示 章节
= 下划线表示 小章节
- 下划线表示 子章节
^ 下划线表示 子章节的子章节
" 下划线表示 段落
```

### 段落
```text
段落由空白行分割, 且应左对齐, 与Markdown相同; 
这是第一段

这是第二段
这个还是第二段
```

### 行内标注
```text
reST文本	解析渲染结果	注解
*emphasis*	emphasis	通常渲染成斜体, 与Markdown相同
**emphasis**	emphasis	通常渲染成粗体, 与Markdown相同
`interpreted text`	interpreted text	强调解释.
``inline literal``	inline literal	常用于行内代码, 与Markdown相同
A :sub:`xxx`	A xxx	下标(subscript)
A :sup:`xxx`	A xxx	上标(superscript)
:guilabel:`Action`	Action	GUI labels
:kbd:`Ctrl+Shift`	Ctrl+Shift	Key-bindings
:menuselection:`A-->B-->C`	A‣B‣C	菜单选择
```

### 列表
```text
无序列表使用 ``-`` , ``*`` , ``+`` 来标记:

- 无序列表第一项
- 无序列表第二项

有序列表使用 ``num.`` 来标记:

1. 有序列表第一项
2. 有序列表第二项

自动编号列表必须使用 ``#.`` 来标记:

#. 自动编号的列表第一项
#. 自动编号的列表第二项

这是一个定义列表:

term
    术语定义必须缩进

    可以包含多个段落

next term
    术语描述

下面是一个嵌套列表, 每一级别向右缩进一次, 同级别缩进应相同:

1. 有序列表第一项
    * 无序列表第一项
    * 无序列表第二项
#. 有序列表第二项
    + 无序列表第一项
    + 无序列表第二项
```

### 源代码
```text
标记符号 :: 紧接一空白行, 然后紧跟代码, 整个代码文本块必须缩进 (同所有的段落一样, 使用空白行和周围文本完成分隔), 如:

::

    some codes
    some codes
    some codes

这里是正常段落!

.. code-block:: python

   def some_function():
       interesting = False
       print 'This line is highlighted.'
       print 'This one is not...'
       print '...but this one is.'
```

### 表格
```text
.. table:: Grid Table Demo
   :name: table-gridtable

   +------------------------+----------+----------+----------+
   | Header row, column 1   | Header 2 | Header 3 | Header 4 |
   | (header rows optional) |          |          |          |
   +========================+==========+==========+==========+
   | body row 1, column 1   | column 2 | column 3 | column 4 |
   +------------------------+----------+----------+----------+
   | body row 2             | ...      | ...      |          |
   +------------------------+----------+----------+----------+
```

### 插入图片
```text
即通过 .. image:: imagepath 实现插入图像:

.. image:: picture.jpeg
   :height: 100px
   :width: 200 px
   :scale: 50 %
   :alt: 对于不能显示图片的时候, 显示这些文字
   :align: right
```

### 提示警告类
```text
.. tip:: This is a tip

.. note:: This is a note

.. hint:: This is a hint

.. danger:: This is a danger

.. error:: This is an error

.. warning:: This is a warning

.. caution:: This is a caution

.. attention:: This is an attention

.. important:: This is an important

.. seealso:: This is seealso
```

### 引用文档
```text
自定义引用文字

:doc:`引用本地的其它rst文档,rst后缀要省略，如about_us <../about_us>`

使用标题文字
:doc:`../about_us`
```


### QA
支持markdown
```text
pip install recommonmark
pip install sphinx_rtd_theme

source_suffix = ['.rst', '.md', '.MD']
html_theme = 'sphinx_rtd_theme'

source_parsers = {
    '.md': CommonMarkParser,
    '.MD': CommonMarkParser,
}

```

托管到https://readthedocs.org/
```text
ReadTheDocs 可是直接用于托管 sphinx 生成的网页文档。 将之前的文档用 Git 管理，并推送到 Github，然后在 ReadTheDocs 中 Import a Project 即可。
```

## python api to doc
