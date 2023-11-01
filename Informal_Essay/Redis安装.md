# Redis数据库安装

>   前言：最近想要学习用Python控制Redis的方法，但是Redis官网是不支持Windows直接安装的，各种大佬的Windows移植版本也比较老，虽然够用，但是也希望使用官网版本。网上的各种安装教程或多或少都存在一点问题，这里我针对我所使用的服务器版本安装Redis服务进行整理，若与我采用相同的服务器需要安装Redis服务器的小伙伴可以参考如下安装教程。
>
>   服务器：Ubuntu 22.04.2 TLS
>
>   数据库：redis-cli 6.0.16



## Redis安装

1.   开启终端，此时首先需要更新系统的软件仓库（apt仓库）

     ```bash
     sudo apt update
     sudo apt upgrade -y
     ```

2.   使用`apt`安装Redis

     ```bash
     sudo apt install redis-server -y
     ```

     待全部执行完毕，若无任何报错，及安装成功。

3.   检查Redis是否安装成功，检查Redis版本。

     ```bash
     redis-cli --version
     ```

     ![image-20231101095404040](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101095404040.png)

     `redis-cli`可直接进入redis客户端交互视图。

4.   检查Redis服务运行状态。

     ```bash
     sudo systemctl status redis-server
     ```

     以下为详细信息：

     ```shell
     taknife@security-lab:~$ sudo systemctl status redis-server
     ● redis-server.service - Advanced key-value store
          Loaded: loaded (/lib/systemd/system/redis-server.service; enabled; vendor preset: enabled)
          Active: active (running) since Wed 2023-11-01 10:14:28 CST; 2min 9s ago
            Docs: http://redis.io/documentation,
                  man:redis-server(1)
        Main PID: 927 (redis-server)
          Status: "Ready to accept connections"
           Tasks: 5 (limit: 9387)
          Memory: 5.2M
             CPU: 209ms
          CGroup: /system.slice/redis-server.service
                  └─927 "/usr/bin/redis-server 127.0.0.1:6379" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "">
     
     11月 01 10:14:28 security-lab systemd[1]: Starting Advanced key-value store...
     11月 01 10:14:28 security-lab systemd[1]: Started Advanced key-value store.
     ```

     需要注意的是，Active状态要是running，若为stop可以通过以下命令进行启动：

     ```bash
     sudo systemctl start redis-server
     ```

     同时需要关注Loaded中，是否为自启动，及状态为enable，若为disenable，则需要开启自启动。

     ```bash
     sudo systemctl enable redis-server
     ```



## Redis配置

>   安装完成 Redis 后，你可能需要对 Redis 进行一些基本的配置，以确保其正常运行并满足你的需求。由于本教程针对的是搭建Redis来进行学习的小伙伴，所以以下只会整理几个最基础的配置，还有其他的配置会在后面列出。

### Redis配置文件

>   注意：这里针对的是6.0.16版本，老版本或后续更新的新版本默认配置文件路径可能不同。

Redis默认配置文件路径为`/etc/redis/redis.conf`

在Ubuntu中修改Redis配置文件需要提权

```bash
sudo vim /etc/redis/redis.conf
```

在完成Redis配置文件修改后，需要重启Redis服务，来使配置文件生效

```bash
sudo systemctl restart redis-server
```

### 设置密码认证

>   为了增强 Redis 的安全性，你可以设置密码认证，要求客户端提供密码才能访问 Redis 服务器。你可以在 Redis 配置文件中设置密码。

*   打开配置文件，找到`requirepass`参数，将其取消注释，并配置密码。例如：配置密码`admin.123`。

    ```bash
    requirepass admin.123
    ```

    ![image-20231101103122705](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101103122705.png)

    保存并退出：`:wq`

### 配置远程登录

>   在学习时，绝大部分调试Redis都不会在服务器上进行。我们可能会通过各种数据库工具来连接Redis，但是在做完如上的配置后，发现依旧无法连接Redis。在telnet服务器的6379端口后发现此端口不通，这是由于服务器默认只监听了127.0.0.1（本地回环地址）的6379端口，因此Redis需要绑定服务器网卡地址6379端口，来使我们能够通过服务器地址远程连接Redis。

*   打开配置文件，找到`bind`参数，修改`bind`参数后内容，例如：10.101.125.15地址绑定6379端口。

    ```bash
    bind 10.101.125.15
    ```

    ![image-20231101104059092](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101104059092.png)

    如果要绑定多个地址，`bind`后可接多个需要绑定的地址。

    保存并退出，记得重启Redis服务`redis-server`

### 其他配置

>   完成这些基本的配置，Redis服务器应该能够满足需求。根据实际需求和用例，可能需要进一步调整和优化Redis配置。确保在修改配置文件后重启Redis服务器以使更改生效。如果需要更具体的配置指南，可以参考 Redis 的官方文档。

1.  **更改数据存储路径**：默认情况下，Redis 数据文件存储在 `/var/lib/redis` 目录下。如果你想更改数据存储路径，可以在 Redis 配置文件中修改 `dir` 配置项。确保目标目录具有适当的权限。
2.  **限制内存使用**：你可以在 Redis 配置文件中设置最大内存使用量，以防止 Redis 消耗过多内存。使用 `maxmemory` 配置项来设置最大内存限制，并使用 `maxmemory-policy` 配置项来指定内存达到上限时的行为。
3.  **日志设置**：根据需要调整 Redis 的日志级别和日志文件路径。你可以修改 `loglevel` 和 `logfile` 配置项来配置日志。
4.  **持久化选项**：Redis 支持不同的持久化选项，如快照和日志文件。你可以选择配置 Redis 以定期保存快照或使用 AOF（Append-Only File）持久化选项。
5.  **安全性设置**：采取适当的安全措施，如限制访问、启用 TLS/SSL 加密，以及防火墙设置来保护 Redis 服务器。
6.  **性能调优**：根据你的工作负载和硬件资源，你可以调整一些性能相关的配置项，如最大连接数、缓冲区大小等。
7.  **监控和日志记录**：配置 Redis 的监控和日志记录，以便监视服务器的性能和故障排除。
8.  **备份和灾难恢复**：设置定期备份策略，以便在数据丢失或灾难发生时能够进行恢复。



## Redis连接工具

>   绝大部分的数据库工具都可以连接Redis，以下介绍我常用的两个连接Redis工具。

### Another Redis Desktop Manager

>   更快、更好、更稳定的Redis桌面(GUI)管理客户端，兼容Windows、Mac、Linux，性能出众，轻松加载海量键值。推荐使用此工具来对数据库进行调试。

**安装地址**：<https://gitee.com/qishibo/AnotherRedisDesktopManager>

![image-20231101105038060](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101105038060.png)

支持：Windows、Linux、Mac

添加新的连接：（根据前面配置添加地址、端口默认、填写密码）

![image-20231101105426563](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101105426563.png)

连接成功！

![image-20231101105529091](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101105529091.png)

### PyCharm

>   由于最近使用Python比较频繁，因此pycharm中的数据库功能也是我常用来连接Redis的工具之一。

**安装地址**：<https://www.jetbrains.com/zh-cn/pycharm/download/?section=windows>

![image-20231101110150298](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101110150298.png)

连接Redis，<font color=red>注意：pycharm连接数据库需要下载相应的数据库插件</font>

![image-20231101105846703](https://gitee.com/taknife/images-note/raw/master/imgs/image-20231101105846703.png)