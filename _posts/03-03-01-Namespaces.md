---
title: Namespaces
isChild: true
---

## Namespaces {#namespaces_title}

Wie oben erwähnt besteht die PHP-Gemeinschaft aus vielen Entwicklern, die eine Menge Code produzieren. Das bedeutet, dass der PHP-Code aus einer Bibliothek die selben Klassennamen verwenden kann wie der Code einer anderen Bibliothek. Wenn beide Bibliotheken im selben Namensraum verwendet werden, entstehen Kollisionen und verursachen Probleme.

_Namespaces_ lösen dieses Problem. Laut der Beschreibung im PHP-Handbuch können Namespaces mit den Verzeichnissen vom Dateisystemen verglichen werden, die Namensräume für Dateien bilden; zwei Dateien mit dem selben Namen können in unterschiedlichen Verzeichnissen existieren. Ebenso können zwei PHP-Klassen mit dem selben Namen in getrennten PHP-Namespaces koexistieren. So einfach ist  das.

Für dich ist wichtig, deinen Code in Namensräumen zu ordnen, damit er von anderen Entwicklern ohne Sorge um mögliche Kollisionen mit anderen Bibliotheken verwendet werden kann.

Ein empfohlene Methode zum Einsatz von Namespaces ist in [PSR-0][psr0] mit dem Ziel einer standardisierten Datei-, Klassen- und Namespace-Konvention für Plug-and-Play-Code umrissen.

* [Mehr über Namespaces][namespaces]
* [Mehr über PSR-0][psr0]

[namespaces]: http://php.net/manual/de/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
