---
name: Authentication
---

# Authentication

## LDAP

Both the LDAP via BindDN and the simple auth LDAP share the following fields:

- Authorization Name **(required)**
  - A name to assign to the new method of authorization.

- Host **(required)**
  - The address where the LDAP server can be reached.
  - Example: `mydomain.com`

- Port **(required)**
  - The port to use when connecting to the server.
  - Example: `636`

- Enable TLS Encryption (optional)
  - Whether to use TLS when connecting to the LDAP server.

- Admin Filter (optional)
  - An LDAP filter specifying if a user should be given administrator
    privileges. If a user accounts passes the filter, the user will be
    privileged as an administrator.
  - Example: `(objectClass=adminAccount)`

- Username attribute (optional)
  - The attribute of the user's LDAP record containing the user name. Given
    attribute value will be used for new Gogs account user name after first
    successful sign-in. Leave empty to use login name given on sign-in form.
  - This is useful when supplied login name is matched against multiple
    attributes, but only single specific attribute should be used for Gogs
    account name, see "User Filter".
  - Example: `uid`

- First name attribute (optional)
  - The attribute of the user's LDAP record containing the user's first name.
    This will be used to populate their account information.
  - Example: `givenName`

- Surname attribute (optional)
  - The attribute of the user's LDAP record containing the user's surname.
    This will be used to populate their account information.
  - Example: `sn`

- E-mail attribute **(required)**
  - The attribute of the user's LDAP record containing the user's email
    address. This will be used to populate their account information.
  - Example: `mail`

**LDAP via BindDN** adds the following fields:

- Bind DN (optional)
  - The DN to bind to the LDAP server with when searching for the user. This
    may be left blank to perform an anonymous search.
  - Example: `cn=Search,dc=mydomain,dc=com`

- Bind Password (optional)
  - The password for the Bind DN specified above, if any. _Note: The password
    is stored in plaintext at the server. As such, ensure that your Bind DN
    has as few privileges as possible._

- User Search Base **(required)**
  - The LDAP base at which user accounts will be searched for.
  - Example: `ou=Users,dc=mydomain,dc=com`

- User Filter **(required)**
  - An LDAP filter declaring how to find the user record that is attempting to
    authenticate. The `%s` matching parameter will be substituted with login
    name given on sign-in form.
  - Example: `(&(objectClass=posixAccount)(uid=%s))`
  - To substitute more than once `%[1]s` should be used instead, eg. when
    matching supplied login name against multiple attributes such as user
    identifier, email or even phone number.
  - Example: `(&(objectClass=Person)(|(uid=%[1]s)(mail=%[1]s)(mobile=%[1]s)))`

**LDAP using simple auth** adds the following fields:

- User DN **(required)**
  - A template to use as the user's DN. The `%s` matching parameter will be substituted with login name given on sign-in form.
  - Example: `cn=%s,ou=Users,dc=mydomain,dc=com`
  - Example: `uid=%s,ou=Users,dc=mydomain,dc=com`

- User Filter **(required)**
  - An LDAP filter declaring when a user should be allowed to log in. The `%s`
    matching parameter will be substituted with login name given on sign-in
    form.
  - Example: `(&(objectClass=posixAccount)(cn=%s))`
  - Example: `(&(objectClass=posixAccount)(uid=%s))`

**Verify group membership in LDAP** uses the following fields:

* Group Search Base (optional)
    * The LDAP DN used for groups.
    * Example: `ou=group,dc=mydomain,dc=com`

* Group Name Filter (optional)
    * An LDAP filter declaring how to find valid groups in the above DN.
    * Example: `(|(cn=gogs_users)(cn=admins))`

* User Attribute in Group (optional)
    * Which user LDAP attribute is listed in the group.
    * Example: `uid`

* Group Attribute for User (optional)
    * Which group LDAP attribute contains an array above user attribute names.
    * Example: `memberUid`

## PAM

To configure this you just need to set the 'PAM Service Name' to a filename in `/etc/pam.d/`.
If you want it to work with normal Linux passwords, the user running Gogs must have read access to `/etc/shadow`.

## SMTP

This option allows Gogs to log in to your SMTP host as a Gogs user. To configure this, simply set the fields below:

- Authentication Name **(required)**
  - A name to assign to the new method of authorization.

- SMTP Authentication Type **(required)**
  - Type of authentication for use on your SMTP host, PLAIN or LOGIN.

- Host **(required)**
  - The address where the SMTP host can be reached.
  - Example: `smtp.mydomain.com`

- Port **(required)**
  - The port to use when connecting to the server.
  - Example: `587`
- Allowed Domains
  - Restrict what domains can log in if you're using public SMTP host or SMTP host with multiple domains.
  - Example: `gogs.io,mydomain.com,mydomain2.com`

- Enable TLS Encryption
  - Enable TLS encryption on authentication.

- Skip TLS Verify
  - Disable TLS verify on authentication.
  
- This authentication is activate
  - Enable or disable this auth.

## Freeipa

- In order to login to the Gogs using FreeIPA credentials, you need to create a bind account for Gogs to use:

-  On the FreeIPA server, create a `gogs.ldif` file, replacing dc=example,dc=com with your DN, and providing an appropriately secure password:
```
  dn: uid=gogs,cn=sysaccounts,cn=etc,dc=example,dc=com
  changetype: add
  objectclass: account
  objectclass: simplesecurityobject
  uid: gogs
  userPassword: secure password
  passwordExpirationTime: 20380119031407Z
  nsIdleTimeout: 0
```

- Import the LDIF (change localhost to an IPA server if needed), you’ll be prompted for your Directory Manager password:
```
  ldapmodify -h localhost -p 389 -x -D \
  "cn=Directory Manager" -W -f gogs.ldif
```
-  Add an IPA group for gogs_users :
```
  ipa group-add --desc="Gogs Users" gogs_users
```
-  Note! if you get error about ipa credentials please run kinit admin and give your admin accound password.

-  Now login to the gogs as an Admin, click on “Authentication” under Admin Panel. Then click New LDAP Source and fill in the details, changing all where appropriate to your own domain as photo below:

![Freeipa-Gogs](https://raw.githubusercontent.com/Karen09/docs/master/images/Freeipa-Gogs.png)

