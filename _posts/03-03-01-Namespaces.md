---
title: Namespaces
isChild: true
anchor:  namespaces
---

## Namespaces {#namespaces_title}

Wie oben erwähnt besteht die PHP-Gemeinschaft aus vielen Entwicklern, die eine Menge Code produzieren. Das bedeutet, dass der PHP-Code aus einer Bibliothek die selben Klassennamen verwenden kann wie der Code einer anderen Bibliothek. Wenn beide Bibliotheken im selben Namensraum verwendet werden, entstehen Kollisionen und verursachen Probleme.

_Namespaces_ lösen dieses Problem. Laut der Beschreibung im PHP-Handbuch können Namespaces mit den Verzeichnissen vom Dateisystemen verglichen werden, die Namensräume für Dateien bilden; zwei Dateien mit dem selben Namen können in unterschiedlichen Verzeichnissen existieren. Ebenso können zwei PHP-Klassen mit dem selben Namen in getrennten PHP-Namespaces koexistieren. So einfach ist  das.

Für dich ist wichtig, deinen Code in Namensräumen zu ordnen, damit er von anderen Entwicklern ohne Sorge um mögliche Kollisionen mit anderen Bibliotheken verwendet werden kann.

Ein empfohlene Methode zum Einsatz von Namespaces ist in [PSR-4][psr4] mit dem Ziel einer standardisierten Datei-, Klassen- und Namespace-Konvention für Plug-and-Play-Code umrissen.

In October 2014 the PHP-FIG deprecated the previous autoloading standard: [PSR-0][psr0]. Both PSR-0 and PSR-4 are still perfectly usable.  The latter requires PHP 5.3, so many PHP 5.2-only projects implement PSR-0.

If you're going to use an autoloader standard for a new application or package, look into PSR-4.

* [Read about Namespaces][namespaces]
* [Read about PSR-0][psr0]
* [Read about PSR-4][psr4]


[namespaces]: https://secure.php.net/language.namespaces
[psr0]: https://www.php-fig.org/psr/psr-0/
[psr4]: https://www.php-fig.org/psr/psr-4/
