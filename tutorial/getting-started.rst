开始
====

配置你的项目和开发环境
----------------------

新建一个文件夹，创建一个叫做 ``README.rst`` 的文件，包含如下内容。

.. code-block:: rst
   :caption: README.rst

   Lumache
   =======

   **Lumache** (/lu'make/) is a Python library for cooks and food
   lovers that creates recipes mixing random ingredients.

现在是时候创建一个Python的虚拟环境并安装必要的工具了。打开一个命令行终端，
``cd`` 到及刚刚创建的文件夹，然后运行以下命令：

.. code-block:: console

   $ python -m venv .venv
   $ source .venv/bin/activate
   (.venv) $ python -m pip install sphinx

.. note::

   上面的安装方法在 :ref:`install-pypi`
   中有更详细的描述。在剩余的教程当中，将会假设运行在一个Python的虚拟环境当中。

如果你正确执行了上述的指导，你现在就可以在命令行使用Sphinx的命令行工具了。运行以下的指令来做一个简单的验证：

.. code-block:: console

   (.venv) $ sphinx-build --version
   sphinx-build 4.0.2

如果你得到了一个类似的输出，那么证明上面的操作你都做对了！

创建文档的布局
--------------

然后，在命令行当中运行以下命令：

.. code-block:: console

   (.venv) $ sphinx-quickstart docs

这将会在你项目的 ``docs``
文件夹下创建的文档的基本结构和布局，同时询问你一系列的配置问题。为了继续我们的教程，像下面这样回答问题：

- ``> Separate source and build directories (y/n) [n]``: Write"``y``"
  (without quotes) and press :kbd:`Enter`.
- ``> Projec name``: Write "``Lumache``" (without quotes) and press
  :kbd:`Enter`.
- ``> Author name(s)``: Write "``Graziella``" (without quotes) and
  press :kbd:`Enter`.
- ``> Project release []``: Write "``0.1``" (without quotes) and press
  :kbd:`Enter`.
- ``> Project language [en]``: Leave it empty (the default, English)
  and press :kbd:`Enter`.

在这之后，你能看到一个新的 ``docs`` 文件夹，它的目录是这样的。

.. code-block:: text

   docs
   ├── build
   ├── make.bat
   ├── Makefile
   └── source
       ├── conf.py
       ├── index.rst
       ├── _static
       └── _templates

每个文件夹的作用是：

``build/``
  目前它是一个空的文件夹，之后它会用来存放渲染出来的文档。

``make.bat`` 和 ``Makefile``
  用来简化一些Sphinx常用操作的脚本

``source/conf.py``
  一个保存着本Sphinx项目的配置文件的Python脚本。它包含着你在
  ``sphin-quickstart`` 中输入的项目名称，和一些其他额外的配置关键字。

``source/index.rst`` 
  本项目的 :term:`root document`
  ，作为一个欢迎页面并且包含着目录树的根节点（或者称为 *toctree* ）。

多亏了上面的引导步骤，你已经具有了将文档渲染成HTML所需要的所有文件。运行下面的命令来渲染看看：

.. code-block:: console

   (.venv) $ sphinx-build -b html docs/source docs/build/html

最后，在浏览器当中打开 ``docs/build/html/index.html``
。你会看到像下面这样的页面。

.. figure:: /tutorial/_image/lumache-first-light.png
   :width: 80%
   :align: center
   :alt: Freshly created documentation of Lumache

   Freshly created documentation of Lumache

做好了！你已经使用Sphinx创建了你的第一个HTML文档，现在你可以开始
:doc:`customizinf it </tutorial/first-steps>` 了。

