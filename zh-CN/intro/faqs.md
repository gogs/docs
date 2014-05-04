---
name: 常见问题
sort: 3
---

# 常见问题

### 部署应用

#### 如果使用 Nginx 的反向代理？

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

### 管理权限

#### 如果成为管理员？

1. 当用户注册时 `ID = 1` 则会自动成为管理员，无需邮箱验证。
2. 默认管理员登录 `Admin -> Users` 面板并设置其它人员为管理员。
3. 通过安装页面注册的用户会自动成为管理员。