## ⭐ 任务清单

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

+ ### 任务三：

    + 知识点

        +

        +

    + 操作

        +

        +

+ ### 任务四：

    + 知识点

        +

        +

    + 操作

        +

        +

+ ### 任务五：

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