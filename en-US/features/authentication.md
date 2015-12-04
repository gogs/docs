---
name: Authentication
---

# Authentication

## LDAP

Both the LDAP via BindDN and the simple auth LDAP share the following fields:

* Authorization Name **(required)**
    * A name to assign to the new method of authorization.

* Host **(required)**
    * The address where the LDAP server can be reached.
    * Example: mydomain.com

* Port **(required)**
    * The port to use when connecting to the server.
    * Example: 636

* Enable TLS Encryption (optional)
    * Whether to use TLS when connecting to the LDAP server.

* Admin Filter (optional)
    * An LDAP filter specifying if a user should be given administrator
      privileges. If a user accounts passes the filter, the user will be
      privileged as an administrator.
    * Example: (objectClass=adminAccount)

- Username attribute (optional)
  - The attribute of the user's LDAP record containing the user name. Leave empty to use sign-in form value for user name.

* First name attribute (optional)
    * The attribute of the user's LDAP record containing the user's first name.
      This will be used to populate their account information.
    * Example: givenName

* Surname attribute (optional)
    * The attribute of the user's LDAP record containing the user's surname This
      will be used to populate their account information.
    * Example: sn

* E-mail attribute **(required)**
    * The attribute of the user's LDAP record containing the user's email
      address. This will be used to populate their account information.
    * Example: mail

**LDAP via BindDN** adds the following fields:

* Bind DN (optional)
    * The DN to bind to the LDAP server with when searching for the user. This
      may be left blank to perform an anonymous search.
    * Example: cn=Search,dc=mydomain,dc=com

* Bind Password (optional)
    * The password for the Bind DN specified above, if any. _Note: The password
      is stored in plaintext at the server. As such, ensure that your Bind DN
      has as few privileges as possible._

* User Search Base **(required)**
    * The LDAP base at which user accounts will be searched for.
    * Example: ou=Users,dc=mydomain,dc=com

* User Filter **(required)**
    * An LDAP filter declaring how to find the user record that is attempting to
      authenticate. The '%s' matching parameter will be substituted with the
      user's username.
    * Example: (&(objectClass=posixAccount)(uid=%s))

**LDAP using simple auth** adds the following fields:

* User DN **(required)**
    * A template to use as the user's DN. The `%s` matching parameter will be
      substituted with the user's username.
    * Example: cn=%s,ou=Users,dc=mydomain,dc=com
    * Example: uid=%s,ou=Users,dc=mydomain,dc=com

* User Filter **(required)**
    * An LDAP filter declaring when a user should be allowed to log in. The `%s`
      matching parameter will be substituted with the user's username.
    * Example: (&(objectClass=posixAccount)(cn=%s))
    * Example: (&(objectClass=posixAccount)(uid=%s))
