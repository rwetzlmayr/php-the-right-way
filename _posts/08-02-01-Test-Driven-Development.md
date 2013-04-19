---
isChild: true
title: Testgetriebene Entwicklung
---

## Testgetriebene Entwicklung {#test_driven_development_title}

Aus [Wikipedia](http://en.wikipedia.org/wiki/Test-driven_development):

> Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: first the developer writes a failing automated test case that defines a desired improvement or new function, then produces code to pass that test and finally refactors the new code to acceptable standards. Kent Beck, who is credited with having developed or 'rediscovered' the technique, stated in 2003 that TDD encourages simple designs and inspires confidence

Du kannst diene Anwendung auf verschiedene Arten testen.

### Unit-Tests

Unit-Tests sind ein Entwicklungsansatz, der sicherstellt, dass Funktionen, Klassen und Methoden wie erwartet arbeiten von Beginn der Entwicklung über den ganzen Entwicklungszyklus. Durch die Überprüfung von Werten, die als Ein- und Ausgabe von Funktionen und Methoden fungieren, kannst du die Korrektheit der inneren Logik sicherstellen. Über Dependency Injection, "Attrappen"-Klassen und Funktionsstummel kannst du die Testabdeckung erhöhen und verifizieren, dass Abhängigkeiten korrekt verwendet werden.

Beim Bau einer Klasse oder Funktion solltest du einen Unit-Test für jedes Verhalten schaffen. Zumindest solltest du sicherstellen, dass bei ungültigen Eingabewerten Fehler passieren und die Funktion bei gültigen Argumenten funktioniert. Damit ist sichergestellt, dass alte Funktionalität erhalten bleibt, wenn du diese Klasse später änderst. Die einzige Alternative wäre var_dump() in einer test.php, und so baut man keine Anwendung - ob klein oder groß.

Die andere Anwendung für Unit-Tests ist als Beitrag in einem Open Source Projekt. Wenn du einen Unit-Test schreiben kannst, der zeigt, dass eine Funktionalität fehlerhaft ist und das dann mit durchlaufendem Testergebnis korrigierst, werden Patches wahrscheinlicher akzeptiert. Wenn du ein Projekt betreibst, das Pull Requests akzeptiert, solltest du das als Erfordernis empfehlen.

[PHPUnit](http://phpunit.de) ist das De-Facto Testframework zum Erstellen von Unit-Tests für PHP, aber es gibt einige Alternativen:

* [SimpleTest](http://simpletest.org)
* [Enhance PHP](http://www.enhance-php.com/)
* [PUnit](http://punit.smf.me.uk/)
* [atoum](https://github.com/atoum/atoum)

### Integrationstests

Aus [Wikipedia](http://en.wikipedia.org/wiki/Integration_testing):

> Integration testing (sometimes called Integration and Testing, abbreviated "I&T") is the phase in software testing in which individual software modules are combined and tested as a group. It occurs after unit testing and before validation testing. Integration testing takes as its input modules that have been unit tested, groups them in larger aggregates, applies tests defined in an integration test plan to those aggregates, and delivers as its output the integrated system ready for system testing.

Viele der gleichen Werkzeuge für Unit-Tests können auch für Integrationstests verwendet werden, da dieselben Prinzipien verwendet werden.

### Funktionaler Test

Funktionale Test oder Akzeptanztest bestehen aus Werkzeugen, mit denen automatisierte Tests erstellt werden können, die deine Anwendung tatsächlich benutzen, anstatt nur das korrekte Verhalten einzelner Codeeinheiten und deren Verständigung untereinander zu verifizieren. Diese Werkzeuge arbeiten typischerweise mit Echtdaten und simulieren tatsächliche Anwender der Applikation.

#### Funktionale Testwerkzeuge

* [Selenium](http://seleniumhq.com)
* [Mink](http://mink.behat.org)
* [Codeception](http://codeception.com) ist ein vollständiges Testframework, das Werkzeuge für Akzeptanztests inkludiert
