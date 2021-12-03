更多Sphinx自定义配置
====================

除了sphinx的本体，你还有两种方式来自定义你的文档配置：插件和主题

开启一个插件
============

除了这些配置值，你还可以使用文档 :doc:`extensions
</usage/extensions/index>`
来自定义你的sphinx。sphinx本身提供了一些插件， :ref:`builtin ones
<builtin-extensions>` 你可以在社区中更多的插件 :ref:`mainrained by the
community <third-party-extensions>` 。

例如，为了打开 :mod:`sphinx.ext.duration` 插件，在你的 ``conf.py``
文件中找到 ``extensions`` 列表，并想下面这样向其中添加元素：

.. code-block:: python
   :caption: docs/soure/cong.py

   # Add any sphinx extension module names here, as strings. They can
   # be extensions coming with Sphinx(named 'sphinx.exe.*') or your
   # custom ones.
   extensions = [
        'sphinx.ext.duration', 
    ]

在这之后，你每次生成你的文档的时候，你都会在命令行的最后看到一个简短的报告，像下面这样：

.. code-block:: console

   (.venv) $ make html
   ...
   The HTML page are in build/html.

   ======================= slowest reading durations ============
   0.042 temp/source/index

使用一个第三方的HTML主题
------------------------

主题，在另一方面，是自定义你文档的外观的方式。Sphinx有一些
:ref:`builtin themes <builtin-thems>` ,并且也有第三方的主题
`third-party ones <https://sphinx-themes.org/>`_.

例如，为了使用 `Furo <https://pradyunsg.me/fuso/>`_
这个第三方的主题，首先你需要使用 ``pip``
在你的python虚拟环境中安装它，像这样：

.. code-block:: console

   (.venv) $ pip install furo

然后，在你的 ``conf.py`` 文件当中找到 ``html_theme``
这个变量并且像下面这样替换它的值：

.. code-block:: python
   :caption: docs/source/confy

   # The theme to use for HTML and HTML Help pages. See the
   # documention for a list builtin themes.
   html_theme = 'furo'

有了这个变换，你将会看到你的HTML文档有了一个新的外观。

.. figure:: /tutorial/_image/lumache-furo.png
   :width: 80%
   :align: center
   :alt: HTML documentation of Lumache with the Furo theme

   HTML documatation of Lumache with the Furo theme

现在是时候来读文档 :doc:`expand the narrative documentation and split
it into several documents </tutorial/narrative-documentation>` 。


