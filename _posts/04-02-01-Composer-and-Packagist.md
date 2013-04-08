---
isChild: true
title: Composer und Packagist
---

## Composer und Packagist {#composer_and_packagist_title}

Composer ist ein **brillanter** Abhängigkeitsmanager für PHP. Führe deine Abhängigkeiten in der Datei `composer.json` auf, und nach ein paar einfachen Befehlen lädt Composer automatisch die Abhängigkeiten deines Projekts herunter und setzt den Autoloader für dich auf.

Viele PHP-Bibliotheken sind bereits mit Composer kompatibel und bereit für den Einsatz in deinem Projekt. Diese "Pakete" werden bei [Packagist][1] gelistet, dem offiziellen Verzeichnis von mit Composer kompatiblen PHP-Bibliotheken.

### Composer installieren

Du kannst Composer lokal in deinem aktuellen Arbeitsverzeichnis installieren (das wird nicht mehr empfohlen), oder global etwa in /usr/local/bin. Nehmen wir einmal an, du möchtest Composer lokal installieren. Gib diese Befehle im Wurzelverzeichnis deines Projekts ein:

    curl -s https://getcomposer.org/installer | php

Damit wird `composer.phar` (ein binäres PHP-Archiv) heruntergeladen. Du kannst es mit `php` ausführen, um die Abhängigkeiten deines Projekts zu verwalten. <strong>Bitte beachte:</strong> Lies den Code zuerst online zur Sicherheitsprüfung, bevor du ihn direkt an den Interpreter weitergibst.

### Composer manuell installieren

Die manuelle Installation von Composer ist eine Technik für Fortgeschrittene. Es gibt verschiedene Gründe, warum ein Entwickler diese Methode gegenüber der interaktive Installationsroutine bevorzugen würde. Die interaktive Installation überprüft deine PHP-Umgebung auf:

- eine ausreichende Version von PHP
- die korrekte Ausführung von `.phar`-Dateien
- ausreichende Berechtigungen in bestimmten Verzeichnissen
- die Abwesenheit problematischer Erweiterungen
- bestimmte Einstellungen in `php.ini`

Da eine manuelle Installation keine dieser Bedingungen prüft, muss du entscheiden, ob die Nachteile gerechtfertigt sind. Falls das zutrifft, kannst du Composer so manuell installieren:

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

Der Pfad `$HOME/local/bin` oder anderes ein Verzeichnis deiner Wahl sollten in deiner Umgebungsvariablen `$PATH` enthalten sein. Damit wird der Befehl `composer` verfügbar.

Jedes Vorkommen von `php composer.phar install` in der Dokumentation kannst du mit folgendem Befehl ersetzen:

    composer install

### Abhängigkeiten definieren und installieren

Composer verfolgt die Abhängigkeiten deines Projekts in einer Datei namens `composer.json`. Du kannst diese Datei händisch oder mit Composer verwalten. Der Befehl `php composer.phar require` fügt eine Projektabhängigkeit hinzu. Wenn die Datei `composer.json` noch nicht existiert, wird sie erstellt. Im folgenden Beispiel wird [Twig][2] als Abhängigkeit zu deinem Projekt hinzugefügt. Starte es im Wurzelverzeichnis deines Projekts, nachdem du `composer.phar` heruntergeladen hast:

    php composer.phar require twig/twig:~1.8

Alternative führt dich der Befehl `php composer.phar init` durch die Erstellung einer vollständigen `composer.json` für dein Projekt. In jedem Fall kannst du nach der Erzeugung der Datei `composer.json` Composer anweisen, die Abhängigkeiten deines Projekts in das Verzeichnis `vendors/` herunterzuladen und zu installieren. Das trifft auch auf heruntergeladene Projekte zu, die selbst bereits eine Datei `composer.json` bereitstellen:

    php composer.phar install

Als nächsten Schritt füge diese Zeile zur primären PHP-Datei deines Projektes hinzu; damit weist du PHP an, den Autloader von Composer für deine Projektabhängigkeiten einzusetzen.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Du kannst jetzt Projektabhängigkeiten verwenden, und sie werden automatisch heruntergeladen.

### Abhängigkeiten aktualisieren

Composer erzeugt eine Datei `composer.lock`, in der die genauen Versionen jedes Pakets zu dem Zeitpunkt gespeichert sind, an dem du das erste Mal `php composer.phar install` ausgeführt hast. Wenn du dein Projekt mit anderen Programmierern teilst und die Datei `php composer.phar install` in das verteilte Produkt aufnimmst, erhalten sie die selbe Version wie du. Starte  `php composer.phar update`, um die Abhängigkeiten zu aktualisieren.

Das ist auch sehr nützlich, falls du deine Versionsansprüche flexibel definiert hast. Beispielsweise bedeutet eine erforderliche Version von ~1.8 "irgend eine Version, die neuer ist als 1.8, aber niedriger als 2.0.x-dev". Der Composer-Befehl `php composer.phar update` wird alle Abhängigkeiten auf die neueste Version aktualisieren, welche die definierten Einschränkungen erfüllen.

### Abhängigkeiten auf Sicherheitsprobleme prüfen

Der [Security Advisories Checker][4] ist ein Webdienst und ein Befehlszeilenwerkzeug. Er untersucht die Datei `composer.lock` und berichtet, ob eine Abhängigkeit aktualisiert werden muss.

* [Mehr über Composer][3]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: http://getcomposer.org/doc/00-intro.md
[4]: https://security.sensiolabs.org/
