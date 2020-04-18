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
            (env) project/ $ python manage.py runserver 8000
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

        +

        +

    + 操作

        +

        +

+ ### 任务六：

    + 知识点

        +

        +

    + 操作

        +

        +

+ ### 任务七：

    + 知识点

        +

        +

    + 操作

        +

        +