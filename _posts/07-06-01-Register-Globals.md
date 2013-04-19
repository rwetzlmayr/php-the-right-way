---
isChild: true
---

## Register Globals {#register_globals_title}

**ACHTUNG:** Seit PHP 5.4.0 wurde die Einstellung `register_globals` entfernt. Sie kann nicht mehr eingesetzt werden. Dieser Abschnitt ist nur als Warnung für jene gedacht, die eine alte Anwendung aktualisieren wollen.

Die Konfigurationseinstellung `register_globals` macht einige Typen von Variablen (inklusive denen aus `$_POST`, `$_GET` und `$_REQUEST`) im globalen Sichtbarkeitsbereich benutzbar. Das kann schnell zu Sicherheitsproblemen führen, da die Anwendung die Herkunft der Daten nicht mehr effektiv verfolgen kann.

Zum Beispiel: `$_GET['foo']` würde über `$foo` erreichbar und könnte so Variablen überschreiben, die nicht deklariert wurden. Wenn du PHP < 5.4.0 einsetzt, __stelle sicher__, dass `register_globals` __off__ ist.

* [Register_globals im PHP-Handbuch](http://www.php.net/manual/de/security.globals.php)