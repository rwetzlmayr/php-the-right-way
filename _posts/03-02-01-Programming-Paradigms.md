---
title: Programmierparadigmen
isChild: true
---

## Programmierparadigmen {#programming_paradigms_title}

PHP ist eine flexible, dynamische Sprache, die unterschiedliche Programmiertechniken unterstützt. Sie hat sich über die Jahre dramatisch entwickelt, speziell mit der Ergänzung um ein solides objektorientiertes Modells in PHP 5.0 (2004), anonyme Funktionen und Namespaces in PHP 5.3 (2009) und Traits in PHP 5.4 (2012).

### Objektorientierte Programmierung

PHP besitzt eine weitgehend vollständige Menge von objektorientierten Eigenschaften inklusive der Unterstützung von Klassen, Vererbung, Konstruktoren, Cloning, Exceptions und mehr.

* [Mehr über objektorientiertes PHP][oop]
* [Mehr über Traits][traits]

### Funktionale Programmierung

PHP unterstützt Funktionen erster Klasse. Das heißt, dass Funktionen an Variablen zugewiesen werden können. Sowohl benutzerdefinierte als auch eingebaute Funktionen können über eine Variable referenziert und dynamisch aufgerufen werden. Funktionen können als Argumente an andere Funktionen übergeben werden.

Rekursion, eine Eigenschaft, die den Aufruf einer Funktion durch sich selbst erlaubt, wird von der Sprache unterstützt, aber der Großteil des PHP-Codes hat den Schwerpunkt auf Iteration.

Neue anonyme Funktionen mit der Unterstützung von Closures sind seit PHP 5.3 (2009) vorhanden.

Mit PHP 5.4 kam die Fähigkeit, Closures an den Gültigkeitsbereich eines Objekts zu binden und die verbesserte Unterstützung für Callables, die seither gleichberechtigt mit anonymen Funktionen in fast allen Fällen einsetzbar sind.

* Erfahre mehr über [funktionales Programmieren in PHP](./pages/Functional-Programming.html)
* [Mehr zu anonymen Funktionen][anonymous-functions]
* [Mehr züber die Klasse `Closure`][closure-class]
* [Weitere Details im Closures RFC][closures-rfc]
* [Mehr zu Callables][callables]
* [Mehr über den dynamischen Aufruf von Funktionen über `call_user_func_array`][call-user-func-array]

### Meta-Programmierung

PHP unterstützt verschiedene Formen der Meta-Programmiereung über Mechanismen wie das Reflection API und magische Methoden. Die magischen Methoden wie etwa `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()` etc. erlauben Entwicklern, sich in das Verhalten von Klassen einzuhängen. Ruby-Entwickler behaupten oft, dass in PHP `method_missing` fehlt, aber diese ist als `__call()` and `__callStatic()` vorhanden.

* [Mehr über magische Methoden][magic-methods]
* [Mehr über Reflection][reflection]

[namespaces]: http://php.net/manual/de/language.namespaces.php
[overloading]: http://php.net/manual/de/language.oop5.overloading.php
[oop]: http://www.php.net/manual/de/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/de/functions.anonymous.php
[closure-class]: http://php.net/manual/de/class.closure.php
[callables]: http://php.net/manual/de/language.types.callable.php
[magic-methods]: http://php.net/manual/de/language.oop5.magic.php
[reflection]: http://www.php.net/manual/de/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/de/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
