## ⭐ 任务清单

> 完成每一步后请截图，并命名为 1.png（或 jpg），任务几图片命名就为几

+ ### 任务一：创建虚拟环境，并命名为 `env`

    + 知识点

        + 每一个虚拟环境都相当于一个新的操作系统。你可以在这个新的环境里安装软件，保存资料。

        + 而 Python 中的虚拟环境为用户提供一个崭新的第三方库和解释器。

    + 操作

        + 下载第三方库 `virtualenv`

            ```bash
            # 终端下执行
            $ pip install virtualenv
            ```

        + 在项目文件夹下创建虚拟环境（创建好后是个文件夹）

            ```bash
            # 终端下执行
            # 默认项目文件夹为 `project`
            project/ $ virtualenv env

            # 创建好后 `project` 文件夹下会多出 `env` 文件夹
            ```

+ ### 任务二：开启虚拟环境，并在虚拟环境下安装 `django 3.0`，最后退出虚拟环境

    + 知识点

        + `virtualenv` 中，创建好虚拟环境 `env` 后（Windows 10 下），进入到 `./env/Scripts/` 文件夹，里面包含 Python 解释器—`python.exe`、pip 安装器—`pip.exe`、虚拟环境启动器—`activate.bat` 及退出—`deactivate.bat`。

        + 每次在终端要先启动 `activate.bat` 才能把全局环境更换为虚拟环境。

        + `django` 是 Python Web 开发的一套框架，开发者可以使用 `django` 来快速开发网站。

    + 操作

        + 在项目文件夹下开启虚拟环境

            ```bash
            # 终端下执行
            # 默认项目文件夹为 `project`
            project/ $ .\\env\\Scripts\\activate
            (env) project/ $

            # 成功开启后，终端命令提示符前会有虚拟环境文件夹名提醒
            ```

        + 在虚拟环境下安装 `django`

            ```bash
            # 终端下执行
            (env) project/ $ pip install django
            ```

        + 退出虚拟环境

            ```bash
            # 终端下执行
            (env) project/ $ .\\env\\Scripts\\deactivate
            project/ $
            ```

+ ### 任务三：在项目文件夹下创建 `django` 项目，命名为 `mysite` 并启动

    + 知识点

        + 创建 django 项目命令：`django-admin startproject mysite`

        + 启动 django 项目命令：`python manage.py runserver 127.0.0.1:8000`

        + 其中，`127.0.0.1` 为本机 ip 地址，可用 `localhost` 替换，若不填写，则此为默认值。

        + 其中，`8000` 为端口号，可以任意换为其他未占用的端口，若不填写，则此为默认值。

    + 操作

        + 在项目文件夹下开启虚拟环境

            ```bash
            # 终端下执行
            # 默认项目文件夹为 `project`
            project/ $ .\\env\\Scripts\\activate
            (env) project/ $

            # 成功开启后，终端命令提示符前会有虚拟环境文件夹名提醒
            ```

        + 在项目文件夹下创建 `django` 项目

            ```bash
            # 终端下执行
            (env) project/ $ django-admin startproject mysite
            ```

        + 启动 `django` 项目

            ```bash
            # 终端下执行
            # 进入刚创建好的项目文件夹
            (env) project/ $ cd mysite
            # 启动项目，用默认 8000 端口开启
            (env) project/mysite/ $ python manage.py runserver 8000
            ```

+ ### 任务四：修改 `django` 项目中配置文件 `settings.py`，添加 templates 和 static 文件夹路径，修改语言和时区

    + 知识点

        + 修改基本配置，以便后续开发使用。

    + 操作

        + 修改 `settings.py` 文件以添加 template 目录

            ```python
            ...
                # 第 57 行
                'DIRS': [os.path.join(BASE_DIR, 'templates'),],
                # 第 58 行
                'APP_DIRS': False,
            ...
            ```

        + 修改 `settings.py` 文件以添加静态文件 static 目录

            ```python
            # 第 121 行后添加
            STATICFILES_DIRS = (
                os.path.join(BASE_DIR, 'static'),
            )
            ```

        + 修改 `settings.py` 文件以修改语言

            ```python
            # 第 107 行修改
            LANGUAGE_CODE = 'zh-hans'
            ```

        + 修改 `settings.py` 文件以修改时区

            ```python
            TIME_ZONE = 'Asia/Shanghai'
            ```

+ ### 任务五：创建名为 `blog` 的 app 应用，并在总路由下分配路由 `/blog/`，以及在 `blog` 应用下创建两个子路由 `/blog/demo1/` 和 `/blog/demo2/`

    + 知识点

        + 在 `django` 项目中创建 app 应用：`python manage.py startapp app_name`

        + 主路由在 `mysite.urls` 中配置，子路由在创建的 `app.urls` 中配置

    + 操作

        + 创建 `app` 应用，命名为 `blog`

            ```bash
            # 终端下执行
            (env) project/mysite $ python manage.py startapp blog
            ```

        + 在 `settings.py` 文件中配置 `blog` 应用

            ```python
            # 第 33 行中添加 blog
            INSTALLED_APPS = [
                'django.contrib.admin',
                'django.contrib.auth',
                'django.contrib.contenttypes',
                'django.contrib.sessions',
                'django.contrib.messages',
                'django.contrib.staticfiles',
                'blog',
            ]
            ```

        + 在 `mysite/` 项目文件夹下，修改 `urls.py` 文件，创建 `/blog/` 路由

            ```python
            from django.contrib import admin
            from django.urls import path, include

            urlpatterns = [
                path('admin/', admin.site.urls),
                path('blog/', include('blog.urls', namespace='blog'))
            ]
            ```

        + 在 `blog/` 应用文件夹下，新建 `urls.py` 文件，创建 `/blog/demo1/` 和 `/blog/demo2/` 路由

            ```python
            from django.urls import path
            from . import views

            app_name = 'blog'

            urlpatterns = [
                path('demo1/', views.demo1),
                path('demo2/', views.demo2),
            ]
            ```

            > 注意，此时运行程序会报错，因为还没有写对应路由下的视图函数。

+ ### 任务六：编写 `/blog/demo1/` 和 `/blog/demo2/` 的视图函数，对应为 `blog` 应用下 `views.py` 文件中 `demo1` 函数 和 `demo2` 函数

    + 知识点

        + 所谓视图函数，就是通过编写函数的形式调用视图层文件（在 django 中为 templates 模板文件），通常都是展示给用户的图形界面。

        + 路由中指定对应的视图函数，视图函数负责调用 `html` 文件。

    + 操作

        + 修改在 `blog/views.py` 文件

            ```python
            from django.shortcuts import render

            # Create your views here.

            def demo1(request):
                return render(request, 'blog/demo1.html')

            def demo2(request):
                return render(request, 'blog/demo2.html')
            ```

        + 创建 `templates` 目录，并创建 `blog` 文件夹，在里面新建 `demo1.html` 和 `demo2.html`

            ```bash
            # 整体结构如下
            ├── mysite
            │   ├── blog
            │   │   ├── __init__.py
            │   │   ├── admin.py
            │   │   ├── apps.py
            │   │   ├── models.py
            │   │   ├── tests.py
            │   │   ├── urls.py
            │   │   ├── views.py
            │   ├── mysite
            │   │   ├── __init__.py
            │   │   ├── settings.py
            │   │   ├── urls.py
            │   │   ├── wsgi.py
            │   ├── templates
            │   │   ├── blog
            │   │   │   ├── demo1.html
            │   │   │   ├── demo2.html
            │   ├── db.sqlite3
            │   ├── manage.py
            ```

        + 现在，在 `demo1.html` 和 `demo2.html` 中添加内容，可以在对应的 `127.0.0.1:8000/blog/demo1` 和 `127.0.0.1:8000/blog/demo2` 进行显示

+ ### 任务七：在 `demo1.html` 中创建 html5 最基本结构，包括 `html5` 声明，html 标签、head 标签、title 标签、body 标签

    + 知识点

        + html5 声明只需要在 html 文档第一行编写：`<!DOCTYPE html>`

        + html 最基本的结构如下：

            ```html
            <html>

            <head>
                <meta charset="utf-8">
                <title>标题</title>
            </head>

            <body>
                Welcome
            </body>

            </html>
            ```

            > 其中，\<html\>\</html\> 标签 表示文档的开头与街尾；\<head\>\</head\> 标签 表示文档的头部信息，一般是给浏览器看的；\<body\>\</body\> 标签 表示文档的主体信息，一般是给用户看的

    + 操作

        + 打开 `demo1.html` 文件进行编辑

            ```html
            <!DOCTYPE html>
            <html>

            <head>
                <meta charset="utf-8">
                <title>标题</title>
            </head>

            <body>
                Welcome
            </body>

            </html>
            ```

+ ### 任务八：在 `demo1.html` 中创建基本标签，\<h1\>、\<p\>、\<a\> 标签，并启动 `django` 项目进行预览

    + 知识点

        + \<h1\>—\<h6\> 标签 表示标题从最大的一号到六号，使用方法为：`<h1>我是 h1 标签</h1>`

        + \<p\> 标签 表示段落，使用方法为：`<p>我是一个段落</p>`

        + \<a\> 标签 表示超链接，可以链接到其他网页资源文件，使用方法为：`<a href="www.baidu.com">点击我跳转到百度页面</a>`

    + 操作

        + 打开 `demo1.html` 文件进行编辑

            ```html
            <!DOCTYPE html>
            <html>

            <head>
                <meta charset="utf-8">
                <title>标题</title>
            </head>

            <body>
                <h1>我是 h1 标签</h1>
                <p>我是一个段落</p>
                <a href="www.baidu.com">点击我跳转到百度页面</a>
            </body>

            </html>
            ```

+ ### 任务九：使用 css 元素选择器修改 `demo1.html` 页面样式，要求如下：设定 `html` 元素的 `background-color` 为 `#F0F0F0`；设定 `header` 元素的 `padding` 为 `40px`，`background-color` 为白色；添加 `footer` 元素的 `font-size` 为 `0.6em`，字体颜色为灰色(`grey`)。其中，元素内的内容自定

    + 知识点

        + 最常见和易理解的 CSS 选择器是元素选择器，又称为类型选择器。也就是将 HTML 文档中的元素，直接作为选择器使用。

        + 例如对于如下页面：

            ```html
            <body>
                <h1>标题1</h1>
                <h2>标题2</h2>
                <p>普通段落中<a href="#">删除的引用。</a></p>
            </body>
            ```

        + 使用元素选择器添加元素样式：

            ```html
            <style type="text/css">
                html {color:black;}
                h1 {color:darkcyan;}
                h2 {color:lightSeaGreen;}
                p {color:grey;}
                a {text-decoration:line-through;}
            </style>
            ```

            > 其中，style 标签加在 head 标签之中

        + 显示效果如下：

            <img src="https://www.educoder.net/api/attachments/185116">

        + 当我们指定一个元素，并设置样式属性之后，文档中该元素便会应用样式。例如，我们设置 p 元素的颜色为灰色(grey)，在没有其他样式覆盖的情况下，文档中所有的 p 元素都将为灰色。

        + 如果想要多种元素应用同一样式，可以直接使用组合元素选择器。将多个要应用样式的元素用逗号隔开，例如：

            ```html
            <body>
                <h1>组合选择器</h1>
                <p>组合选择器，可以将样式同时运用于多个元素。</p>
            </body>
            ```

        + 使用元素选择器添加元素样式：

            ```html
            <style type="text/css">
                /* 组合元素选择器 */
                /*将`h1`、`p`元素的颜色同时设置为灰色*/
                h1,p {color:grey;}
            </style>
            ```

            > 注意：多个元素之间的逗号是必不可少的，如果缺失了逗号将表示其他含义。

        + 显示效果如下：

            <img src="https://www.educoder.net/api/attachments/192511">

    + 操作

        + 根据要求编写 `demo1.html`

            ```html
            <!DOCTYPE html>
            <html lang="zh">
            <head>
                <meta charset="UTF-8">
                <title>元素选择器</title>
                <style type="text/css">
                    /* 元素选择器 */
                    html {
                        background-color: #F0F0F0;
                    }

                    header {
                        padding: 40px;
                        background-color: white;
                    }

                    footer {
                        margin-top: 20px;
                        font-size: 0.6em;
                        color: grey;
                    }
                </style>
            </head>

            <body>

                <header>
                    <li><a href="#chosen">精选</a></li>
                    <li><a href="#news">时事</a></li>
                    <li><a href="#finance">财政</a></li>
                    <li><a href="#think">思想</a></li>
                    <li><a href="#life">生活</a></li>
                </header>

                <footer>Copyright (c) News Copyright Holder All Rights Reserved.</footer>

            </body>
            </html>
            ```

+ ### 任务十：使用 `类选择器` 和 `id 选择器` 将下列样例保存到 `demo1.html` 中

    ```html
    <!DOCTYPE html>
    <html lang="zh">
    <head>
        <meta charset="UTF-8">
        <title>选择器</title>
        <style type="text/css">
            /* 元素选择器 */
            html {
                background-color: #F0F0F0;
            }
            header {
                padding: 40px;
                background-color: white;
            }
            footer {
                margin-top: 20px;
                font-size: 0.6em;
                color: grey;
            }

            /* 类选择器 */
            .main {
                margin: 10px;
            }
            .newsSection {
                margin-top: 20px;
                padding: 20px;
                background-color: white;
            }

            /* id 选择器 */
            #chosen {
                color: red;
            }
            #news {
                color: blue;
            }
            #finance {
                color: olive;
            }
            #think {
                color: green;
            }
            #life {
                color: orange;
            }

            /*选择menu元素下的li子元素*/
            #menu li {
                float: left;
                width: 70px;
                font-size: 1.2em;
                font-weight: lighter;
            }
            /*选择menu元素下的li子元素和li下得a子元素*/
            #menu li, li a {
                list-style: none;
                text-decoration: none;
            }
        </style>
    </head>

    <body>
        <div class="main">
            <header id="menu">
                <li><a href="#chosen">精选</a></li>
                <li><a href="#news">时事</a></li>
                <li><a href="#finance">财政</a></li>
                <li><a href="#think">思想</a></li>
                <li><a href="#life">生活</a></li>
            </header>

            <div class="newsSection">
                <section>
                    <h2 id="chosen">精选</h2>
                    <li>精选新闻1</li>
                    <li>精选新闻2</li>
                    <li>精选新闻3</li>
                </section>
                <section>
                    <h2 id="news">时事</h2>
                    <li>时事新闻1</li>
                    <li>时事新闻2</li>
                    <li>时事新闻3</li>
                </section>
                <section>
                    <h2 id="finance">财政</h2>
                    <li>财政新闻1</li>
                    <li>财政新闻2</li>
                    <li>财政新闻3</li>
                </section>
                <section>
                    <h2 id="think">思想</h2>
                    <li>思想新闻1</li>
                    <li>思想新闻2</li>
                    <li>思想新闻3</li>
                </section>
                <section>
                    <h2 id="life">生活</h2>
                    <li>生活新闻1</li>
                    <li>生活新闻2</li>
                    <li>生活新闻3</li>
                </section>
            </div>
            <footer>Copyright (c) News Copyright Holder All Rights Reserved.</footer>
        </div>
    </body>

    </html>
    ```

    + 知识点

        + 类选择器与id选择器类似，那么它们的区别是什么呢？什么情况下应该使用哪一种选择器呢？它们最大的区别在于，在一个 HTML 文档中，可以为任意多个元素指定类，但 id 选择器只能使用一次，一个 id 只能运用于一个元素。

        + 一般情况下，都推荐使用类选择器。而在一些特定情况下，我们才会建议使用 id 选择器。例如，通过 id 选择器在页面中定义锚，在编写 JavaScript 为指定的页面元素应用特殊行为时。

        + 使用类选择器时，指定一个元素属于某类，使用的是关键字 class，例如:

            ```html
            <body>
                <h1 class="important">温馨提示</h1>
                <p>少一串脚印，多一份绿意。</p>
            </body>
            ```

        + 而在使用 id 选择器时，使用的是关键字 id。对于上面类选择器的例子，用 id 选择器书写：

            ```html
            <body>
                <h1 id="important">温馨提示</h1>
                <p>少一串脚印，多一份绿意。</p>
            </body>
            ```

+ ### 任务十一：在项目文件夹下新建 `static` 目录，并在下面创建 `blog` 文件夹，整体结构如下，创建好后在 `image` 目录下放入一定的图片资源

    ```bash
    # 整体结构如下
    ├── mysite
    │   ├── blog
    │   │   ├── __init__.py
    │   │   ├── ...
    │   ├── mysite
    │   │   ├── __init__.py
    │   │   ├── ...
    │   ├── static
    │   │   ├── blog
    │   │   │   ├── css
    │   │   │   │   ├── style.css
    │   │   │   ├── image
    │   │   │   │   ├── 1.png
    │   ├── templates
    │   │   ├── blog
    │   │   │   ├── demo1.html
    │   │   │   ├── demo2.html
    │   ├── db.sqlite3
    │   ├── manage.py
    ```    
    
+ ### 任务十二：在 `demo2.html` 文件中通过 `img` 标签引入 `1.png`，通过 `link` 标签引入 `style.css`

    + 知识点

        + 这里涉及到 `django` templates 模板语法。
        
        + 其中，`static` 下的资源均为静态文件，可以通过 html 的语法进行引入，而在 `django` 中，指定静态资源的路径需要用到模板语法

        + 也可以通过 `127.0.0.1:8000/static/xx` 访问静态资源

    + 操作

        + 编辑 `demo2.html` 文件

            ```html
            {% load staticfiles %}
            <!DOCTYPE html>
            <html>

            <head>
                <meta charset="utf-8">
                <title>demo2</title>
                <link rel="stylesheet" href="{% static 'style.css' %}">
            </head>

            <body>
                <img src="{% static '1.png' %}" />
            </body>

            </html>
            ```