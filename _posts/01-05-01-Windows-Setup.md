---
title: Installation unter Windows
isChild: true
---

## Installation unter Windows {#windows_setup_title}

PHP für Windows wird über mehrere Wege angeboten. Du kannst [die Binaries herunterladen][php-downloads], und bis vor Kurzem konntest du PHP auch über eine '.msi'-Datei installieren. Diese Installationsdatei wird seit PHP 5.3.0 nicht mehr unterstützt.

Zum Erlernen und für die lokale Entwicklung kannst du den in PHP 5.4 eingebauten Webserver verwenden und dich nicht weiter um die Konfiguration kümmern. Wenn du lieber ein "Komplettpaket" mit einem vollständigen Webserver und MySQL einsetzen möchtest, verhelfen dir Werkzeuge wie der [Web Platform Installer][wpi], [Zend Server CE][zsce], [XAMPP][xampp] und [WAMP][wamp] schnell zu einer Entwicklungsumgebung unter Windows. Bitte beachte, dass diese Werkzeuge kleine Unterschiede zur Produktivumgebung haben und du darauf achten solltest, wenn du unter Windows entwickelst und auf Linux ausrollst.

Wenn deine Produktionssite unter Windows läuft, liefert IIS7 die stabilste und leistungsfähigste Grundlage. Du kannst [phpmanager][phpmanager] (ein GUI-Plugin für IIS7) für die einfache Konfiguration und Verwaltung von PHP einsetzen. IIS7 enthält FastCGI, daher musst du nur PHP als FastCGI-Handler konfigurieren. Es gibt einen [spezialisierten Bereich auf iis.net][php-iis] mit  Unterstützung und weiteren Informationen.

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/de/products/server-ce/
[xampp]: http://www.apachefriends.org/de/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
