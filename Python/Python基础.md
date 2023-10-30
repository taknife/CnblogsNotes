# Python基础



## 1. Python起源

>   以下均由ChatGPT提供

Python是由荷兰程序员Guido van Rossum于1989年开始开发的一种高级编程语言。

1.  **起源（Late 1980s）**：Guido van Rossum在1989年开始着手开发Python，最初的目标是创建一种简单易读的语言，同时允许程序员编写更具表达力的代码。Python的名称灵感来自于英国的喜剧团队Monty Python。
2.  **第一个公开版本（February 20, 1991）**：Guido van Rossum发布了Python的第一个公开版本，即Python 0.9.0。这个版本具有一些基本的语言特性，包括模块、异常处理、函数和一些标准库模块。
3.  **Python 1.0（January 26, 1994）**：Python 1.0发布，它引入了一些重要的特性，如 lambda、map、reduce、filter等。
4.  **Python 2.0（October 16, 2000）**：Python 2.0引入了列表推导式、垃圾回收等重要特性。这个版本在很长一段时间内是主要版本。
5.  **Python 3.0（December 3, 2008）**：Python 3.0，也称为Python 3000或简称Python 3，引入了一些不兼容的语言变更，以解决Python 2.x版本中的一些设计缺陷和语言不一致性。这个版本的发布被视为Python语言的一次重大升级。
6.  **持续发展**：自从Python 3发布以来，Python持续发展，每个版本都引入了新特性、改进和性能优化。Python社区非常活跃，有数以千计的第三方库和框架可供使用。

Python以其简洁、易读的语法、强大的标准库以及跨平台特性而闻名。它被广泛用于Web开发、科学计算、数据分析、人工智能、自动化脚本编写等各种领域。 Python的成功和流行得益于其开源性质和活跃的社区支持。 Python现在被视为一种多用途的编程语言，适用于各种不同的编程任务。



## 2. Python的优缺点

>   以下均由ChatGPT提供

Python是一种广泛使用的编程语言，具有许多优点和一些限制。以下是Python的主要优点和缺点：

**Python的优点：**

1.  **简单和易读的语法**：Python的语法非常直观和易于理解，使新手能够更轻松地入门编程。
2.  **丰富的标准库**：Python附带了大量的标准库，用于处理各种任务，从文件操作到网络编程，再到数据分析和科学计算。
3.  **跨平台性**：Python是一种跨平台语言，可以在多种操作系统上运行，包括Windows、Linux和macOS。
4.  **强大的社区支持**：Python拥有庞大且活跃的社区，提供了大量的文档、教程和第三方库，有助于解决各种问题。
5.  **广泛的应用领域**：Python适用于多个领域，包括Web开发、数据分析、机器学习、人工智能、自动化、游戏开发等。
6.  **开源和免费**：Python是开源的，可以免费使用和分发，这降低了成本。
7.  **易于扩展**：Python可以与其他编程语言（如C、C++、Java）集成，允许使用性能敏感的代码。
8.  **动态类型系统**：Python的动态类型系统允许更快的开发迭代和灵活性。
9.  **大数据和数据科学**：Python在大数据处理和数据科学领域非常受欢迎，有许多库和框架，如NumPy、Pandas、Matplotlib、SciPy和TensorFlow。

**Python的缺点：**

1.  **性能**：Python通常比编译语言（如C++）慢，尤其在计算密集型任务中，性能可能成为问题。
2.  **全局解释器锁（GIL）**：在CPython（Python的标准实现）中，有一个全局解释器锁，它防止多线程Python程序在多核处理器上充分利用多核。这对于多线程应用可能是限制因素。
3.  **内存消耗**：Python应用程序通常使用较多的内存，这可能在资源受限的环境中成为问题。
4.  **移动开发**：相对于一些专门的移动开发语言，Python的移动开发支持相对有限。
5.  **不适合实时性要求高的应用**：由于GIL和性能限制，Python不太适合实时性要求高的应用，如高频交易。
6.  **Python 2.x兼容性**：由于Python 2.x 和 Python 3.x 之间的不兼容性，许多项目需要迁移到Python 3，这可能导致一些麻烦。

总的来说，Python是一种多功能、易学、高度可扩展的编程语言，特别适用于快速开发原型、数据分析、科学计算和Web开发。然而，它可能不适合所有类型的应用程序，特别是在性能和实时性要求高的领域。选择使用Python还是其他编程语言通常取决于具体的项目需求。



## 3. Python的安装

**安装Python解释器**

*   **Windows**

    1.   安装Python解释器，直接进入官网https://www.python.org/，在Downloads下可根据自身系统安装所需的版本。
    2.   在下载页面上，你可以选择下载最新的Python版本（通常是3.x版本），并根据你的操作系统位数（32位或64位）选择相应的安装程序。通常来说，选择Windows Installer安装程序（.exe文件）。
    3.   下载安装程序并运行它。
    4.   在安装向导中，确保选择“Add Python X.X to PATH”选项，这将使Python可执行文件自动添加到系统PATH中，方便在命令行中运行Python。
    5.   完成安装。

*   **Linux**

    >   **Debian/Ubuntu**

    在大多数Debian/Ubuntu Linux发行版中，Python通常已经预安装。如果需要安装特定版本的Python，可以使用以下命令：

    ```shell
    sudo apt-get update
    sudo apt-get install python3
    ```

    >   **Red Hat/CentOS**

    在Red Hat/CentOS Linux中，你可以使用以下命令来安装Python 3：

    ```shell
    sudo yum install python3
    ```

    这将安装Python 3.x，你可以将 `python3` 替换为具体的版本号。

*   **Mac**

    1.  访问Python的官方网站：https://www.python.org/downloads/mac-osx/。
    2.  在下载页面上，你可以选择下载最新的Python版本（通常是3.x版本），并选择macOS安装程序。
    3.  下载安装程序并运行它。
    4.  在安装向导中，确保选择“Install launcher for all users”选项，以确保Python可执行文件可以从终端访问。
    5.  完成安装。

**安装ipython交互环境**

>   ipython是一个增强的交互式Python解释器，它提供了比标准Python REPL（Read-Eval-Print Loop）更多的功能和特性。ipython的目标是使交互式编程更加强大、便捷和有趣。
>
>   简单来说：ipython比普通python交互环境更加强大，可以补全代码。

使用`pip`安装`ipython`

打开终端或命令提示符，并运行以下命令：

```shell
pip install ipython
```

在某些系统中，你可能需要使用 `pip3` 而不是 `pip`，具体取决于你的 Python 版本。

注意：由于pip采用的是国外源，因此可能会存在下载超时问题。此处可以在此条命令后加一个`-i`选项，后面加上国内pip源地址即可，修改后如下：

```shell
pip install ipython -i https://pypi.tuna.tsinghua.edu.cn/simple
```

其他国内源：

```shell
清华: https://pypi.tuna.tsinghua.edu.cn/simple/
中国科技大学: https://pypi.mirrors.ustc.edu.cn/simple/
华中理工大学: http://pypi.hustunique.com/
山东理工大学: http://pypi.sdutlinux.org/
豆瓣: http://pypi.douban.com/simple/
```

安装好后进入终端或者命令提示符执行：`ipython`，如下：

![image-20231031004312176](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231031004312176.png)

**安装集成开发环境IDE**

>   Python的集成开发环境有很多，入Pycharm、VSCode、IDLE等，此次以Pycharm为例。

1.  **下载PyCharm**：访问PyCharm的官方网站https://www.jetbrains.com/pycharm/download/并下载你想要的版本（Community版或Professional版）。Community版是免费的，而Professional版需要付费许可证。
2.  **运行安装程序**：双击下载的安装程序（通常是一个.exe文件）来运行安装向导。
3.  **选择安装类型**：在安装向导中，你可以选择安装类型。如果你是新用户，选择默认选项即可。如果你是升级用户，可以选择"Import settings from a previous version"以导入以前版本的设置。
4.  **选择安装位置**：在接下来的屏幕上，选择要安装PyCharm的位置。默认位置通常是在`C:\Program Files\JetBrains\PyCharm`。
5.  **选择启动器选项**：安装过程中，你可以选择是否创建桌面快捷方式和启动器图标。根据你的偏好进行选择。
6.  **选择关联文件类型**：你可以选择将Python文件与PyCharm关联，以便在双击Python文件时自动使用PyCharm打开。
7.  **安装过程**：点击"Install"按钮开始安装。安装程序将复制文件并配置PyCharm。
8.  **完成安装**：安装完成后，点击"Finish"按钮退出安装向导。
9.  **启动PyCharm**：现在，你可以在开始菜单或桌面上找到PyCharm的快捷方式，并启动它。
10.  **激活PyCharm**：如果你安装的是Professional版，你需要提供有效的许可证来激活它。如果你是新用户，可以选择试用版本，然后在试用期结束前激活。

安装完成后，可以配置PyCharm，包括选择主题、插件和版本控制集成等。然后就可以开始使用PyCharm来编写、调试和管理Python代码了。