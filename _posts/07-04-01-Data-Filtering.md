---
isChild: true
title: Daten filtern
---

## Daten filtern {#data_filtering_title}

Vertraue niemals (niemals!) Eingaben in deinen PHP-Code von außen. Bereinige und validiere externe Eingaben, bevor du sie in deinem Code verwendest. Die Funktionen `filter_var` und `filter_input` können Text bereinigen und Textformate wie zum Beispiel E-Mail-Adressen validieren.

Eine Eingabe von außen kann alles mögliche  sein: Formulareingaben über `$_GET` und `$_POST`, einige Werte im Superglobal `$_SERVER` und der Inhalt des HTTP-Requests über `fopen('php://input', 'r')`. Denke daran: Fremdeingaben sind nicht beschränkt auf Formulardaten, die ein Benutzer absendet. Hochgeladene und heruntergeladene Dateien, Sessionwerte, Daten aus Cookies und Daten von dritter Seite wie Webservices sind auch Fremdeingaben.

Während Fremdeingaben gespeichert, kombiniert und später verwendet werden können, bleiben sie noch immer Fremdeingaben. Frage dich jedes  Mal, ob die Daten korrekt gefiltert sind, wenn du sie in deinem Code verarbeitest, ausgibst, verbindest oder einbaust.

Daten können - abhängig von der Verwendung - unterschiedlich _gefiltert_ werden. Werden ungefilterte Fremdeingaben in die HTML-Seite eingeschleust, kann HTML und JavaScript auf deiner Site ausgeführt werden. Das nennt man Cross-Site Scripting (XSS), eine sehr gefährliche Angriffsmethode. Eine Methode, um XSS zu vermeiden, ist, alle vom Benutzer erzeugten Daten vor der Ausgebe zu bereinigen. Dazu kannst du entweder alle HTML-Tags mit der Funktion `strip_tags` entfernen oder Zeichen mit spezieller Bedeutung mit Hilfe der Funktionen `htmlentities` oder `htmlspecialchars` in die entsprechenden HTML-Entitäten umwandeln.

Ein weiteres Beispiel ist die unerwünschte Weitergabe von Optionen an die Ausführung über die Befehlszeile. Das kann extrem gefährlich sein und ist ganz allgemein eine schlechte Idee. Du kannst die eingebaute Funktion `escapeshellarg` verwenden, um die Argumente des ausgeführten Befehls zu bereinigen.

Ein letztes Beispiel ist die Verwendung von Fremdeingaben zur Bestimmung einer Datei, die vom Dateisystem geladen wird. Das kann ausgenutzt werden, um an Stelle eines Dateinamens einen Dateipfad zu erreichen. Du musst "/", "../", [Null-Bytes][6] und andere Zeichen aus dem Dateipfad entfernen, damit nicht versteckte, private und heikle Dateien geladen werden.

* [Mehr über Datenfilterung][1]
* [Mehr über `filter_var`][4]
* [Mehr über `filter_input`][5]
* [Mehr über die Behandlung von Null-Bytes][6]

### Bereinigung

Mit der Bereinigung entfernt oder entschärft man illegale oder unsichere Zeichen aus Fremdeingaben.

Zum Beispiel solltest du Fremdeingaben bereinigen, bevor du die Eingabe in HTML einbaust oder sie in einer SQL-Abfrage verwendest. Wenn du gebundene Parameter mit [PDO](#databases) verwendest, wird PDO die Eingaben für dich bereinigen.

Manchmal ist es nötig, einige sichere HTML-Tags in der Eingabe zu erlauben. Das ist sehr schwierig und wird oft vermieden. Als Ausweichlösung werden Markdown, Textile oder BBCode verwendet, obwohl Whitelisting-Bibliotheken wie [HTML Purifier][html-purifier] aus diesem Grund existieren.


[Siehe Filter zur Bereinigung][2]

### Validierung

Validierung stellt sicher, dass Fremdeingaben den Erwartungen entsprechen. Zum Beispiel kannst du eine E-Mail-Adresse, eine Telefonnummer oder eine Altersangabe validieren, wenn du eine Registrierungsanmeldung verarbeitest.

[Siehe Filter zur Validierung][3]

[1]: http://www.php.net/manual/de/book.filter.php
[2]: http://www.php.net/manual/de/filter.filters.sanitize.php
[3]: http://www.php.net/manual/de/filter.filters.validate.php
[4]: http://php.net/manual/de/function.filter-var.php
[5]: http://www.php.net/manual/de/function.filter-input.php
[6]: http://php.net/manual/de/security.filesystem.nullbytes.php
[html-purifier]: http://htmlpurifier.org/
