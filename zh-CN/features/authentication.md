---
name: 授权认证
---

# 授权认证

## LDAP

基于 BindDN 和 simple auth 的 LDAP 授权方式共享以下字段：

* 认证名称 **（必填）**
    * A name to assign to the new method of authorization.

* 主机地址 **（必填）**
    * The address where the LDAP server can be reached.
    * Example: `mydomain.com`

* 主机端口 **（必填）**
    * The port to use when connecting to the server.
    * Example: `636`

* 启用 TLS 加密（可选）
    * Whether to use TLS when connecting to the LDAP server.

* 管理员过滤规则（可选）
    * An LDAP filter specifying if a user should be given administrator
      privileges. If a user accounts passes the filter, the user will be
      privileged as an administrator.
    * Example: `(objectClass=adminAccount)`

- 用户名属性（可选）
  - The attribute of the user's LDAP record containing the user name. Given
    attribute value will be used for new Gogs account user name after first
    successful sign-in. Leave empty to use login name given on sign-in form.
  - This is useful when supplied login name is matched against multiple
    attributes, but only single specific attribute should be used for Gogs
    account name, see "User Filter".
  - 例如：`uid`

* 名字属性（可选）
    * The attribute of the user's LDAP record containing the user's first name.
      This will be used to populate their account information.
    * Example: `givenName`

* 姓氏属性（可选）
    * The attribute of the user's LDAP record containing the user's surname This
      will be used to populate their account information.
    * Example: `sn`

* 邮箱属性 **（必填）**
    * The attribute of the user's LDAP record containing the user's email
      address. This will be used to populate their account information.
    * Example: mail

**基于 BindDN** 需要填充以下字段：

* 绑定 DN（可选）
    * The DN to bind to the LDAP server with when searching for the user. This
      may be left blank to perform an anonymous search.
    * Example: cn=Search,dc=mydomain,dc=com

* 绑定密码（可选）
    * The password for the Bind DN specified above, if any. _Note: The password
      is stored in plaintext at the server. As such, ensure that your Bind DN
      has as few privileges as possible._

* 用户搜索基准 **（必填）**
    * The LDAP base at which user accounts will be searched for.
    * Example: ou=Users,dc=mydomain,dc=com

* 用户过滤规则 **（必填）**
  - An LDAP filter declaring how to find the user record that is attempting to
    authenticate. The `%s` matching parameter will be substituted with login
    name given on sign-in form.
  - Example: `(&(objectClass=posixAccount)(uid=%s))`
  - To substitute more than once `%[1]s` should be used instead, eg. when
    matching supplied login name against multiple attributes such as user
    identifier, email or even phone number.
  - Example: `(&(objectClass=Person)(|(uid=%[1]s)(mail=%[1]s)(mobile=%[1]s)))`

**基于 simple auth** 需要填充以下字段：

- User DN **（必填）**
  - A template to use as the user's DN. The `%s` matching parameter will be substituted with login name given on sign-in form.
  - Example: `cn=%s,ou=Users,dc=mydomain,dc=com`
  - Example: `uid=%s,ou=Users,dc=mydomain,dc=com`

- 用户过滤规则 **（必填）**
  - An LDAP filter declaring when a user should be allowed to log in. The `%s`
    matching parameter will be substituted with login name given on sign-in
    form.
  - Example: `(&(objectClass=posixAccount)(cn=%s))`
  - Example: `(&(objectClass=posixAccount)(uid=%s))`
