---
name: 源码升级
---

# 从源码升级

升级 Gogs 的一般步骤：

```bash
# 更新源码以及依赖
$ go get -u github.com/gogs/gogs

$ cd $GOPATH/src/github.com/gogs/gogs

# 移除旧的二进制
$ rm gogs

# 或将旧的二进制进行备份
$ mv gogs gogs.$(date +%Y-%m-%d).old

# 重新构建 Gogs
$ go build
```

其它操作：

- [构建 `develop` 分支版本](/docs/installation/install_from_source#%E6%9E%84%E5%BB%BA-develop-%E5%88%86%E6%94%AF%E7%89%88%E6%9C%AC)
- [测试安装](/docs/installation/install_from_source#%E6%B5%8B%E8%AF%95%E5%AE%89%E8%A3%85)
- [使用标签构建](/docs/installation/install_from_source#%E4%BD%BF%E7%94%A8%E6%A0%87%E7%AD%BE%E6%9E%84%E5%BB%BA)
