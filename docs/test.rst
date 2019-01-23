这就是一个标题
===================
这也是一个章节标题
----------------
- 这里是列表的第一个列表项
 
- 这是第二个列表项
 
- 这是第三个列表项
 
  - 这是缩进的第一个列表项
    注意，这里的缩进要和当前列表项的缩进同步。
 
- 第一级的第四个列表项
 
- 列表项之间要用个空格来分割。

1. 第一项
    巴拉巴拉好多内容在这里。。。
 
#. 第二项
 
    a. 第二项的第一小项
 
    #. 第二项的第二小项
 
#. 第三项

术语1
    术语1的定义
 
术语 2
    术语2的定义,这是第一段
 
    术语2的定义，第二段
 
术语 3 : 分类器
    术语3的定义
 
 
术语 4 : 分类器1 : 分类器2
    术语4的定义

+------------------------+------------+----------+----------+
| Header row, column 1   | Header 2   | Header 3 | Header 4 |
| (header rows optional) |            |          |          |
+========================+============+==========+==========+
| body row 1, column 1   | column 2   | column 3 | column 4 |
+------------------------+------------+----------+----------+
| body row 2             | Cells may span columns.          |
+------------------------+------------+---------------------+
| body row 3             | Cells may  | - Table cells       |
+------------------------+ span rows. | - contain           |
| body row 4             |            | - body elements.    |
+------------------------+------------+---------------------+


基本形式
========
 
`下面这种是最简单的表格形式，当然你也可以去掉表头展示。`
 
=====  =====  =======
  A      B    A and B
=====  =====  =======
False  False  False
True   False  False
False  True   False
True   True   True
=====  =====  =======
 
表内嵌入
========
 
`下面这种简单表内有列表`
 
=====  =====
col 1  col 2
=====  =====
1      Second column of row 1.
2      Second column of row 2.
       Second line of paragraph.
3      - Second column of row 3.
 
       - Second item in bullet
         list (row 3, column 2).
\      Row 4; column 1 will be empty.
=====  =====
 
表头合并
========
 
`表头进行分类合并`
 
=====  =====  ======
   Inputs     Output
------------  ------
  A      B    A or B
=====  =====  ======
False  False  False A
True   False  True
False  True   True
True   True   True
=====  =====  ======


下面是我们的测试代码：
 
::
 
    for i in [1,2,3,4,5]:
        print i
    # 代码块测试
 
很简单的代码块测试。


.. Strong Emphasis
 
This is **Strong Text**. HTML tag is strong.粗体
 
.. Italic, Emphasis
 
This is *Emphasis* Text.这个HTML使用em， 斜体
 
.. Interpreted Text
 
This is `Interpreted Text`. 注意，这个HTML一般用<cite>表示
 
.. Inline Literals
 
This is ``Inline Literals``. HTML tag is <tt>. 等宽字体.


我这里是一个 链接_.
 
.. _链接: http://blog.useasp.net



这里同样是一个 `链接<http://blog.useasp.net>`_，不需要特别设置。