---
name: Authentifzierung
---

# Authentifizierung

## LDAP

Sowohl LDAP via BindDN und simple auth LDAP benutzen die folgenden Felder:

* Authentifizierungsname **(benötigt)**
    * Ein Name, der der Authentifizierungsquelle zugewiesen wird

* Host **(benötigt)**
    * Die Adresse, unter dem der LDAP-Server erreicht werden kann.
    * Beispiel: mydomain.com

* Port **(benötig)**
    * Der Port, über den die Verbindung zum Server aufgebaut wird
    * Beispiel: 636

* TLS-Verschlüsselung aktivieren (optional)
    * Entscheidet, ob der Server mittels TLS mit dem Server kommuniziert

* Admin Filter (optional)
    * Ein LDAP-Filter, der Benutzer identifiziert, denen Admin-Rechte
      gewährt werden. Wenn ein Account diesem Filter entspricht, werden
      diesem User Admin-Rechte gewährt.
    * Beispiel: (objectClass=adminAccount)

* Vorname Attribut (optional)
    * Das Attribut des LDAP-Eintrags, in dem der Vorname gespeichert wird.
      Dieser Wert wird dem User-Account hinzugefügt werden.
    * Beispiel: givenName

* Nachname Attribut (optional)
    * Das Attribut des LDAP-Eintrags, in dem der Nachname gespeichert wird.
      Dieser Wert wird dem User-Account hinzugefügt werden.
    * Beispiel: sn

* E-Mail Attribut **(benötigt)**
    * Das Attribut des LDAP-Eintrags, in dem die e-Mail-Adresse des Benutzers gespeichert
      wird. Dieser Eintrag wird in den User-Account übernommen.
    * Beispiel: mail

**LDAP via BindDN** fügt noch die folgenden Felder hinzu:

* DN binden (optional)
    * Der DN, unter dem in LDAP nach Benutzern gesucht wird. Dieses Attribut kann leer
      gelassen werden, um eine anonyme Suche zuzulassen.
    * Beispiel: cn=Search,dc=mydomain,dc=com

* Passwort binden (optional)
    * Das Passwort für den DN, der oben gesetzt wurde, wenn er gesetzt wurde. _Hinweis: Das
      Passwort wird im Klartext auf dem Server gespeichert. Nimm also als `DN binden` einen
      Benutzer, der möglichst wenig Rechte hat._

* Benutzer-Such-Basis **(benötigt)**
    * Die LDAP-Basis, unter der nach Benutzern gesucht wird.
    * Beispiel: ou=Users,dc=mydomain,dc=com

* Benutzernamen-Filter **(benötigt)**
    * Ein LDAP-Filter, der nach dem User sucht, der sich authentifizieren will.
      Der '%s'-Parameter wird dabei mit dem Benutzernamen ersetzt.
    * Beispiel: (&(objectClass=posixAccount)(uid=%s))

**LDAP mit simple auth** fügt die folgenden Felder hinzu:

* User DN **(benötigt)**
    * Ein Template, das als User-DN benutzt werden soll. Der `%s` Parameter wird
      dabei durch den Usernamen des Benutzers ersetzt
    * Beispiel: cn=%s,ou=Users,dc=mydomain,dc=com
    * Beispiel: uid=%s,ou=Users,dc=mydomain,dc=com

* User Filter **(benötigt)**
    * EIn LDAP-Filter, der festlegt, welche User sich einloggen können dürfen
      sollen. Der `%s` Parameter wird dabei wieder mit dem Usernamen des
      Benutzers ersetzt.
    * Beispiel: (&(objectClass=posixAccount)(cn=%s))
    * Besipiel: (&(objectClass=posixAccount)(uid=%s))
