---
isChild: true
title: Fehlermeldungen
---

## Fehlermeldungen  {#error_reporting_title}

Das Aufzeichnen von Fehlern kann helfen, Problembereiche in deiner Anwendung zu finden, es kann aber auch Informationen über die Struktur deiner Anwendung gegenüber der breiten Allgemeinheit enthüllen. Um deine Anwendung effektiv vor Problemen zu schützen, die durch die Ausgabe diese Meldungen entstehen könnten, musst du deinen Produktivserver anders konfigurieren als deinen Entwicklungsserver.

### Entwicklung

Um jeden möglichen Fehler während der Entwicklung anzuzeigen, konfiguriere folgende Einstellung in deiner `php.ini`:

    display_errors = On
    display_startup_errors = On
    error_reporting = -1
    log_errors = On

> Mit dem Wert `-1` wird jeder mögliche Fehler auch in zukünftigen Versionen von PHP angezeigt. Die Konstante `E_ALL` verhält sich seit PHP 5.4 auch so. - [php.net](http://php.net/manual/function.error-reporting.php)

Der Errorlevel `E_STRICT` wurde mit PHP 5.3.0 eingeführt und ist nicht Teil von `E_ALL`, wurde aber Teil von `E_ALL` in 5.4.0. Was bedeutet das? In Bezug auf Fehlermeldungen musst du in Verion 5.3 entweder `-1` oder `E_ALL | E_STRICT` verwenden.

**Jeden Fehler melden ja nach PHP-Version**

* &lt; 5.3 `-1` oder `E_ALL`
* &nbsp; 5.3 `-1` oder `E_ALL | E_STRICT`
* &gt; 5.3 `-1` oder `E_ALL`

### Produktion

Um keinen Fehler im Produktivsystem anzuzeigen, konfiguriere folgende Einstellung in deiner `php.ini`:

    display_errors = Off
    display_startup_errors = Off
    error_reporting = E_ALL
    log_errors = On

Mit diesen Einstellungen im Produktivsystem werden Fehler immer noch in den Error Logs des Webservers eingetragen, aber dem Benutzer nicht angezeigt. Weitere Informationen zu diesen Einstellungen findest du im PHP-Handbuch:

* [error_reporting](http://php.net/manual/errorfunc.configuration.php#ini.error-reporting)
* [display_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-errors)
* [display_startup_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-startup-errors)
* [log_errors](http://php.net/manual/errorfunc.configuration.php#ini.log-errors)
