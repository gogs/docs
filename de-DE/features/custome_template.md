---
name: Eigenes Template
---

# Eigenes Template

Du kannst deinen eigenen Head- oder Footerinhalt zu Gogs hinzufügen, ohne den Quellcode des Hauptrepos anzufassen. Dies ist hilfreich, wenn du analytics code oder eigene statische Quellen hinzufügen möchtest.

Lese mehr über "[inject custom head and footer](https://discuss.gogs.io/t/how-to-inject-custom-head-and-footer/943)".

## Eigene CSS Datei laden

Hier ist ein Beispiel, wie du deine eigene CSS Datei zu deiner Gogs Instanz hinzufügen kannst. Namen und Ordner sind nur zur Demonstration. Du kannst deine Dateien überall speichern, solange sie von Netzwerkanfragen gelesen werden können.

1. Erstelle eine Datei namens `custom.css` im `public/css` Verzeichnis.
2. Erstelle deine CSS Regeln in der Datei.
3. Editiere `custom/templates/inject/head.tmpl` und füge die Zeile `<link rel="stylesheet" href="/css/custom.css">` hinzu.
4. Starte Gogs neu
5. Weiteres Bearbeiten der eigenen CSS Datei erfordert keinen Neustart von Gogs
