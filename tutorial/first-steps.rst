使用Sphinx组织你项目文档最开始的几步
====================================

创建你的HTML文档
----------------

``sphinx-quickstart`` 创建的 ``index.rsr``
已经有了一些内容，并且它被渲染成作为你HTML文档的首页。它是用reStructuredText写成的，这是一个强大的标记语言。

像下面这样修改你的文件：

.. code-block:: rst
   :caption docs/source/index.rst

   Welcom to Lumache's documentation!
   ==================================

   **Lumache** (/lu'make/) is a Python library for cooks and food
   lovers that creats recips mixing random ingredients.  It pulls data
   from the `Open Food Facts database
   <http://world.openfoodfacts.org/>`_ and offers a *simple* and
   *intutive* API.

   .. note::

      This project is under active development.

这展示了一些reStructuredText的语法，包括：

- 一个使用 ``===`` 作为下划线的 **section header** ，
- 两种行内标识（:ref:`rst-inline-markup` ): ``**strong emphasis**``
  (加粗) 和 ``*emphasis*`` (斜体)，
- 一个 **行内的外部链接** ( **inline external link** )，
- 和一个 ``note`` **警告** (更多内容可以查看
  :ref:`directives<rst-directives>`)

现在来看看加入了新内容之后被渲染成了什么样子，你可以像之前一样使用
``sphinx-build`` 命令，或者像下面这样更方面的创建：

.. code-block:: console

   (.venv) $ cd docs
   (.venv) $ make html

在使用上面的命令之后，你就可以看到 ``index.html`` 文件展示了新的内容。

以其他的方式创建你的文档
========================

Sphinx除了HTML还支持与多种文件格式，包括PDF、EPUB，:ref:`and more
<builders>` 。举个例子，在 ``docs`` 文件夹下面使用如下命令：

.. code-block:: consloe
   
   (.venv) $ make epub

在这之后，你将在 ``docs/build/epub/``
文件夹下看到电子书格式的文件。你可以使用电子书阅读器比如 `Calibre
<https://calibre-ebook.com/>`_ ，打开它，或者在浏览器当中预览
``index.xhtml`` 。

.. note::

   为了快速展示完整的可以产生的格式，以及一些额外的命令，你可以通过
   :code:`make help` 来查看帮助。

每一种产生的文件格式都有一些你可以修改的配置，:ref:`including EPUB
<epub-options>` 。例如，EPUB展示url时默认是 ``inline``
的，这意味着，URLs在链接之后立即就展示在了右边括号里。你可以通过在你的
``conf.py`` 文件下添加下面的代码来更改这一行为。

.. code-block:: python

   # EPUB options
   epub_shouw_urls = 'footnote'

有了上面的配置修改，在重新运行 ``make epub``
之后，你就会发现URLs作为一个脚注展示出来，避免了使文章杂乱。
下面去阅读 :doc:`other ways to customize Sphinx
</tutorial/more-sphinx-customization>` 来继续探索sphinx。

.. note::

   使用Sphinx产生一个PDF可以通过运行 ``make latexpdf``
   ，不过前提是你的工作环境当中已经安装了一个LaTeX的发行版，这在文档
   :class:`sphinx.builders.latex.LaTeXBuilder` 当中解释了。
   尽管这是非常可行的，但是这个安装是非常巨大的，并且LaTeX在某些情况下需要一些小心的配置，所以PDF的生成并不在本教程的范围之内。
