---
name: Authentication
---

# Authentication

Gogs supports authentication by various external sources.  Currently supported are: LDAP, SMTP, PAM, and GitHub.  Sources can be configured in **Admin Panel - Authentication Sources**, or (starting from `0.11.45.0412`) using configuration files in `custom/conf/auth.d`.  

## Using configuration files

Since version `0.11.45.0412`, files with the suffix `.conf` under `custom/conf/auth.d` will be recognized as authentication sources.  An example for each of the supported sources can be found [here](https://github.com/gogs/gogs/tree/main/conf/auth.d).

Authentication sources defined via configuration files appear in the **Admin Panel - Authentication Sources** just like sources created via the web interface.

![](/docs/images/auth_sources.png)

Configuration files are read once when Gogs starts.  To edit them while Gogs is running, use the web interface.

## Configuration

### LDAP

There are two variants for LDAP authentication: with or without a separate Bind DN.  In both cases authentication is performed by attempting to bind to the LDAP with the User DN and password.  The difference is that with the Bind DN, a query is first performed (by the Bind DN) to find the User DN.

The Bind DN mechanism has these advantages:

- It may be more secure than blindy attempting to bind with a possibly non-existent User DN
- It supports login with e.g. email address or phone number.  The preliminary search could look up the User DN using their `mail` or `mobile` attribute (but see the FreeIPA section further down: features in Gogs may have obsoleted the need for this)
- A Bind DN is required when the LDAP does not allow the User DN to query its own attributes or group memberships

The downside to the Bind DN mechanism is that, unless the LDAP allows anonymous queries, it requires a bind DN to be defined in the LDAP, and Gogs needs to store its credentials.  Gogs currently does not encrypt these.

In the ideal situation, the LDAP allows anonymous queries (at least in the "user container") and the Bind DN mechanism can be used without a Bind DN and password.  The options available to you depend on how the LDAP in your organisation has been configured.

**Shared configuration fields** between _Bind DN_ and _Simple Auth_ authentication

- Authentication Name **(required)**
  - A friendly name to assign to the new authentication source

- Security Protocol **(required)**
  - Unencrypted (0), LDAPS (1), StartTLS (2)

- Host **(required)**
  - The address where the LDAP server can be reached.
  - Example: `ldap.mydomain.com`

- Port **(required)**
  - The port to use when connecting to the server.
  - Usually `389` for the LDAP and StartTLS protocols, `636` for LDAPS protocol.

- User Filter **(required)**
  - An LDAP filter declaring which users should be allowed to log in.  Used as the
    initial search query in the Bind DN authenticator.  Applied "on top of" the
    authenticated user context in Simple Authentication. The `%s` matching parameter
    will be substituted with the login name given on the sign-in form.
    - Example: `(&(objectClass=posixAccount)(uid=%s))`
  - Can be used to filter on group membership if the User DN object has `memberOf`
    attributes:
    - `(&(objectClass=posixAccount)(uid=%s)(memberOf=cn=gogs_users,cn=groups,...)`
  - In the Bind DN authenticator can be used to retrieve the user account using any
    of a number of user attributes:
    - Example: `(&(objectClass=Person)(|(uid=%s)(mail=%s)(mobile=%s)))`

- Admin Filter (optional)
  - An LDAP filter which is applied to the User DN context to determine whether the
    user should have Gogs administrator privileges.
  - Example: `(objectClass=adminAccount)` or `(memberOf=cn=admins,cn=groups,...)`

- Username attribute (optional)
  - The attribute of the user's LDAP record containing the user name. The given
    attribute value will be used for a new Gogs account user name after the first
    successful sign-in. Leave empty to use the login name given on the sign-in form.
  - This is useful when the supplied login name is matched against multiple
    attributes, but only a single specific attribute should be used for the Gogs
    account name (see "User Filter").
  - Example: `uid`

- First name attribute (optional)
  - The attribute of the user's LDAP record containing the user's first name.
    This will be used to populate their account information.
  - Example: `givenName`

- Surname attribute (optional)
  - The attribute of the user's LDAP record containing the user's last name.
    This will be used to populate their account information.
  - Example: `sn`

- Email attribute **(required)**
  - The attribute of the user's LDAP record containing the user's email
    address. This will be used to populate their account information.
  - Example: `mail`

**LDAP using Simple Auth** adds the following field:

- User DN **(required)**
  - The template to use as the user's DN. The `%s` matching parameter will be
    substituted with the login name given on the sign-in form.
  - Example: `cn=%s,ou=Users,dc=mydomain,dc=com`
  - Example: `uid=%s,ou=Users,dc=mydomain,dc=com`

**LDAP via BindDN** adds the following fields:

- Bind DN (optional)
  - The DN to bind to the LDAP server with when searching for the user. This
    may be left blank to perform an anonymous search.
  - Example: `cn=Search,dc=mydomain,dc=com`

- Bind Password (optional)
  - The password for the Bind DN specified above, if any. *Note: The password
    is stored in plaintext on the server. As such, ensure that your Bind DN
    has as few privileges as possible.*

- User Search Base **(required)**
  - The LDAP base below which the user account will be searched.
  - Example: `ou=Users,dc=mydomain,dc=com`

- Fetch attributes in Bind DN context (optional)
  - By default user attributes are retrieved while bound as the User DN; tick this
    box to retrieve them while bound as the Bind DN

**Verify group membership in LDAP** uses the following fields:

- Group Search Base DN (optional)
  - The LDAP base below which groups will be searched
  - Example: `ou=group,dc=mydomain,dc=com`

- Group Filter (optional)
  - An LDAP filter declaring the groups that entitle the user to have access
  - Example: `(|(cn=gogs_users)(cn=admins))`

- Group Attribute Containing List of users (optional)
  - Which multi-valued attribute has the group's members
  - Example: `memberUid` or `member`

- User Attribute Listed in Group (optional)
  - Which user attribute is listed in the membership attributes on the group
  - Example: `uid` or `dn`

### PAM

To configure this you just need to set the **PAM Service Name** to a file name in `/etc/pam.d/`.
If you want it to work with normal Linux passwords, the user running Gogs must have read access to `/etc/shadow`.

### SMTP

This option allows Gogs to log in to your SMTP host as a Gogs user. To configure this, simply set the fields below:

- Authentication Name **(required)**
  - A name to assign to the new method of authentication.

- SMTP Authentication Type **(required)**
  - Type of authentication for use on your SMTP host: `PLAIN` or `LOGIN`.

- Host **(required)**
  - The address where the SMTP host can be reached.
  - Example: `smtp.mydomain.com`

- Port **(required)**
  - The port to use when connecting to the server.
  - Example: `587`

- Allowed Domains
  - Restrict what domains can log in if you're using a public SMTP host or an SMTP host with multiple domains.
  - Example: `gogs.io,mydomain.com,mydomain2.com`

- Enable TLS Encryption
  - Enable TLS encryption on authentication.

- Skip TLS Verify
  - Disable TLS verify on authentication.
  
- This authentication is activated
  - Enable or disable this auth method.

### FreeIPA

It is possible to use either Bind DN or Simple Auth with FreeIPA.  Below are
the relevant parts of sample configurations.  These assume that your domain is
`domain.com`, and that users must be a member of group `gogs_users` to get access.

**Using Simple Auth**

Setting up access using Simple Auth is trivial:

    user_dn            = uid=%s,cn=users,cn=accounts,dc=domain,dc=com
    filter             = (&(objectClass=posixAccount)(memberOf=cn=gogs_users,cn=groups,cn=accounts,dc=domain,dc=com))
    attribute_username = uid
    attribute_name     = givenName
    attribute_surname  = sn
    attribute_mail     = mail
    admin_filter       = (memberOf=cn=admins,cn=groups,cn=accounts,dc=domain,dc=com)
    group_enabled      = false

**Using Bind DN**

If you want to allow login by email address, you run into the issue that IPA by
default does not grant anonymous search access to the `mail` attribute.  This can
be changed easily in IPA:

    ipa permission-mod --includedattrs=mail 'System: Read User Standard Attributes'

Alternatively, you could ask your LDAP administrators (who will not be keen on exposing
email addresses to unauthenticated LDAP clients) for a bind user account.

**However** all this is probably not necessary any more, as Gogs translates email
logins to the corresponding user ID\* before it makes the authentication call to the
backend LDAP.

All that is required is that the user's _first login_ is with their user ID,
After that they can use user ID and email address.

---

**Footnotes**

\*) To be precise: it maps their login name onto their "Authentication Login Name",
    which administrators can edit on the User's "Edit Account" page.

