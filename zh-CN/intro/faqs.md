---
name: 常见问题
---

# 常见问题

### 部署应用

#### 如果我已经有其它应用使用端口 3000 了怎么办？

您可以在您第一次启动 Gogs 的时候通过以下方式修改默认的监听端口：

    ./gogs web -port 3001

该方法同样会在您填写安装页面时生效，因此请选择一个您希望以后一直给 Gogs 使用的端口号。

#### 如何使用 NGINX 的反向代理？

在 `nginx.conf` 文件中，将下面的 `server` 部分增加至 `http` 分区内并重载配置：

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

##### 配置子路径

如果您想要通过域名的子路径来访问 Gogs 实例，可以将 NGINX 的配置修改为以下形式（特别注意后缀 `/`）:

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location /gogs/ {
        proxy_pass http://localhost:3000/;
    }
}
```

然后在配置文件中设置 `[server] ROOT_URL = http://git.crystalnetwork.us/gogs/`。

##### 为什么上传大文件时总是发生错误？

想要了解如何让 NGINX 支持大文件上传的讨论，可以查看 [此贴](http://stackoverflow.com/a/15021750) 。一般 NGINX 会返回 `413` 错误，在配置文件中加入以下内容可以解决该问题：

```
client_max_body_size 50m;
```

##### 如果我用的是 Apache 2 怎么配置子路径？

可以尝试使用下面的配置模板：

```
<VirtualHost *:443>
        ...
        <Proxy *>
                 Order allow,deny
                 Allow from all
        </Proxy>

        ProxyPass /git http://127.0.0.1:3000
        ProxyPassReverse /git http://127.0.0.1:3000
</VirtualHost>
```

##### 有没有用 lighttpd 配置子路径的例子？

```
server.modules  += ( "mod_proxy" )
$HTTP["host"] == "git.example.com" {
    proxy.server = ( "" => ( ( "host" => "127.0.0.1", "port" => "3000" ) ) )
}
```

```
# requires lighttpd 1.4.46 or later
server.modules  += ( "mod_proxy" )
$HTTP["url"] =~ "^/gogs/" {
    proxy.server = ( "" => ( ( "host" => "localhost", "port" => "3000" ) ) )
    proxy.header = ( "map-urlpath" => ( "/gogs/" => "/" ) )
}
```

#### 如何使用 HTTPS？

在 `custom/conf/app.ini` 文件中修改下列配置选项（以下仅为示例）：

```
[server]
PROTOCOL = https
ROOT_URL = https://try.gogs.io/
CERT_FILE = custom/https/cert.pem
KEY_FILE = custom/https/key.pem
```

如果您想要使用自签名的 HTTPS，则可以使用下列命令来生成所需文件（需要使用构建标签 `cert` 或直接从官方下载二进制）：

	$ ./gogs cert -ca=true -duration=8760h0m0s -host=myhost.example.com

#### 如何使用离线模式？

如果您需要将 Gogs 运行于内网环境下，只需将 `custom/conf/app.ini` 文件中的配置选项 `server -> OFFLINE_MODE` 修改为 `true` 即可。

#### 如何使用自定义 robots.txt？

在 `custom` 目录下创建 `robots.txt` 文件即可。

#### 如何以守护进程形式运行？

Gogs 拥有一些由第三方提供的脚本来支持以守护进程形式运行：

- [init.d/centos](https://github.com/gogs/gogs/blob/master/scripts/init/centos/gogs)
- [init.d/debian](https://github.com/gogs/gogs/blob/master/scripts/init/debian/gogs)
- 下小节中的 Systemd 服务

#### Systemd 服务

在 GitHub 上的 Gogs 仓库有一个 [systemd 服务模版文件](https://github.com/gogs/gogs/blob/master/scripts/systemd/gogs.service)，您需要做出一定的修改才能够使用它：

1. 更新 `User`、`Group`、`WorkingDirectory`、`ExecStart` 和 `Environment` 为相对应的值。其中 `WorkingDirectory` 为您的 Gogs 实际安装路径根目录。
3. [可选] 如果您 Gogs 安装示例使用 `MySQL/MariaDB`、`PostgreSQL`、`Redis` 或 `memcached`，请去掉相应 `After` 属性的注释。

当您完成修改后，请将文件保存至 `/etc/systemd/system/gogs.service`，然后通过 `sudo systemctl enable gogs` 命令激活，最后执行 `sudo systemctl start gogs`。

您可以通过 `sudo systemctl status gogs -l` 或 `sudo journalctl -b -u gogs`  命令检查 Gogs 的运行状态。

### 管理权限

#### 如何成为管理员？

1. 当用户注册时 `ID = 1` 则会自动成为管理员，无需邮箱验证。
2. 默认管理员登录 `Admin -> Users` 面板并设置其它人员为管理员。
3. 通过安装页面注册的用户会自动成为管理员。

### 仓库管理

#### 如何给予用户 Git 钩子权限？

由于这是一个 **可能损坏您系统的高级权限**，您必须在用户管理面板（`/admin/users/:userid`）为您完全信任的用户单独开启。

### 其它

#### 如何获取 Gogs 当前版本？

纯文本形式的 Gogs 版本存储在文件 `templates/.VERSION` 中。
