在Sphinx中叙述文档
==================

使用多个页面来组织你的文档
--------------------------

用 ``sphinx-quickstart`` 生成的 ``index.rst`` 文件是根文件 :term:`root
document`
，它主要的作用就是作为一个欢迎页面并且包含着目录树。Sphinx允许你通过不同的文件来装配你的项目，当项目增长的时候这是非常有帮助的。

作为一个例子，创建一个文件 ``docs/source/usage.rst`` （临近
``index.rst`` ），写入如下内容：

.. code-block:: rst
   :caption: docs/source/usage.rst

   Usage
   =====

   Installation
   ------------

   To use Lumache, first install it using pip:

   .. code-block:: console

      (.venv) $ pip install lumache

这个新的文件包含着两个标题 :ref:`section <rst-section>`
，普通的段落文本和一个代码块 :rst:dir:`code-block`
，代码块里的内容会被像源码一样渲染展示，并且还有语法高亮。

文档的结构是由标题决定的，这意味着，通过在 ``===`` 说明的
“Usage”标题下使用 ``---`` 来说明“Installation”
是标题，意味着“Installation”是“Usage”的 *子部分*

在完整的过程中，还要向 ``index.rst`` 最后添加一个 ``toctree``
:ref:`derective <rst-directives>` 来包含你刚添加进去的文件，像这样：

.. code-block:: rst
   :caption: docs/source/index.rst

   Contents
   --------

   .. toctree::

      usage

这一步骤向你的文档目录当中添加了你刚才创建的文件，使你的项目看起来像这样：

.. code-block::text

   index
   └── usage

如果你用 ``make html`` 命令创建你的HTML文档，你会发现 ``toctree``
被渲染成了一个超链接的列表。

.. warning::

   在 *toctree* 之外的文档会在生成文档的时候导致一个警告， ``WARNING: document isn't
   included in any toctree`` 而且这个文档对于使用者来说是不会看到的。

添加交叉引用
------------

Sphinx一个强大特征就是可以无缝的像文档的特定部分添加交叉索引 :ref:`cross-references
<xref-syntax>`
，你可以向文档，部分，图片，代码块等等添加索引。这篇教程充满了交叉索引。

为了添加一个交叉索引，在 ``index.rst``
文件的介绍后面紧接着写下如下内容：

.. code-block:: rst
   :caption: docs/source/index.rst

   Check out the :doc:`usage` section for further information.

上面的 :rst:role:`doc` :ref:`role <rst-roles-alt>`
你是用了之后就自动的连接到了你的某个文档，在这个例子中连接到了你之前创建的
``usage.rst`` 。

或者，你也可以向文档的任何一个部分添加一个交叉引用。为了这样做，你需要使用
:rst:role:`ref` 命令，并且添加一个明确的 *标签*
来作为一个超链接的指向目标。

举个例子，为了引用“Installation”这一子部分，可以像下面这样在标题之前添加一个标签

.. code-block:: rst
   :caption: docs/source/index.rst
   :emphasize-lines: 4

   Usage
   =====

   .. _installation:

   Installation
   ------------

   ...

并且让你的 ``index.rst`` 文档看起来像是这样：

.. code-block:: rst
   :caption: docs/source/index.rst

   Check out the :doc:`usage` section for further information,
   including how to :ref:`installation <installation> the project.

注意到这里的一个小技巧： ``install``
部分将会展示为Installation。

下一篇将会介绍如何在Sphinx当中对代码写文档 :doc:`documenting code
objects in Sphinx </tutorial/describing-code>`
