[TOC]

安装Sphinx
^^^^^^^^^^

-  安装

::

    pip install Sphinx

-  创建项目code测试

::

    建一个测试项目code， 下面有两个Python文件test1.p y和test2.py


    [root@Docker ~]#  ls
    code venv
    [root@Docker ~]#  ls code/
    test1.py test2.py

-  test1.py代码

::

    # -*-coding:utf-8-*-

    class Test1():
        '''
        我是测试类，负责测试
        '''
        def hello(self):
            '''
            负责打印Hello， 人人可以学Python
            :return: 
            '''
            print("人人可以学Python")
        def renren(self):
            '''
            测试Sphinx自动生成文档
           
            :return: 
            '''
            print("自动生成文档")
    class Test2():

        def test_2(self):
            '''
            我也不知道写什么好，反正我们这里是用来写文档的
            :return: 
            '''
            print("文档自动生成测试2")
        def renren_2(self):
            '''
            所以我们开发的时候就应该在这里写好文档，然后用Sphinx自动生成

            :return: 
            '''
            print("自动生成文档2")

-  test2.py代码

::

    # -*-coding:utf-8-*-

    def init_test():
        '''
        用于初始化项目测试，不需要任何参数
        :return: 
        '''
        print("初始化项目")


    def start():
        '''
        启动项目入口，
        :return: 
        '''
        test(3)

    def test(v):
        '''
        项目运行主要函数，需要传入一个参数\n
        v:<int>
        :return: 
        '''

        print(v)

使用Python-Sphinx doc
^^^^^^^^^^^^^^^^^^^^^

-  选择配置

::

    [root@Docker ~]# sphinx-quickstart 
    Welcome to the Sphinx 1.5.5 quickstart utility.

    Please enter values for the following settings (just press Enter to
    accept a default value, if one is given in brackets).

    Enter the root path for documentation.
    > Root path for the documentation [.]: .

    > Separate source and build directories (y/n) [n]: y

    > Project name: Code Pro
    > Author name(s): Allen Woo

    > Project version []: 1.0

    > Project language [en]: zh_cn

    > autodoc: automatically insert docstrings from modules (y/n) [n]: y
    > doctest: automatically test code snippets in doctest blocks (y/n) [n]: y
    > intersphinx: link between Sphinx documentation of different projects (y/n) [n]: y
    > coverage: checks for documentation coverage (y/n) [n]: y
    > viewcode: include links to the source code of documented Python objects (y/n) [n]: y

-  配置conf.py

::

    在source/conf.py文件中加入如下代码， 导入自己的项目路径
    import os
    import sys
    sys.path.insert(0, os.path.abspath('/root/code'))

-  生成rst文件

::

    [root@Docker ~]# sphinx-apidoc -o ./source /root/code/
    Creating file ./test1.rst.
    Creating file ./test2.rst.
    Creating file ./modules.rst.

-  最后执行make html 生成html文件

::

    [root@Docker ~]#  make html
    Running Sphinx v1.5.5
    loading translations [zh_cn]... done
    loading pickled environment... done
    building [mo]: targets for 0 po files that are out of date
    building [html]: targets for 0 source files that are out of date
    updating environment: 0 added, 0 changed, 0 removed
    looking for now-outdated files... none found
    no targets are out of date.
    build succeeded.

    Build finished. The HTML pages are in build/html.

-  浏览器访问html页面 可以部署nginx的root家目录指向到html目录下

|image0|

安装Sphinx主题
^^^^^^^^^^^^^^

-  安装

::

    pip install sphinx_rtd_theme

-  配置

\``\` 编辑source/conf.py配置文件 导入模块：

import sphinx_rtd_theme

将 html_theme = “alab

.. |image0| image:: index_files/444020f9-18bd-4ee9-b6e1-783cc744821a.jpg
