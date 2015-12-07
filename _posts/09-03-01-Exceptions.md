---
isChild: true
title: Exceptions
---

## Exceptions {#exceptions_title}

Exceptions sind ein Standardbestandteil moderner populärer Programmiersprachen, werden aber oft von PHP-Programmierern übersehen. Sprachen wie Ruby legen viel Gewicht auf Exceptions, so dass viele Fehler wie etwa ein erfolgloser HTTP-Request, eine falsche Datenbankabfrage oder eine fehlende Grafikdatei die Anzeige von Exceptions am Bildschirm auslösen und so auf Fehler hinweisen.

PHP selbst ist relativ nachlässig, so dass ein `file_get_contents()` üblicherweise nur zu einem `FALSE` und einer Warnung führt. Viele ältere Frameworks wie CodeIgniter geben auch nur `FALSE` zurück, schreiben eine Nachricht in ihr Fehlerlog und erlauben dir den Aufruf einer Methode wie `$this->upload->get_error()`, um die Ursache des Fehlers zu finden. Das Problem dabei ist, dass du nach dem Fehler fragen und in der Dokumentation nach der Fehlermethode für diese Klasse suchen musst, statt es äußerst offensichtlich zu machen.

Ein weiteres Problem besteht, wenn Klassen automatisch Fehler auslösen und den Prozess beenden. Wenn du so vorgehst, hinderst du andere Entwickler daran, Fehler dynamisch zu behandeln. Exceptions sollten ausgelöst werden, um Entwickler auf Fehler hinzuweisen und ihnen Gelegenheit zu geben, darauf zu reagieren. Ein Beispiel:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
{% endhighlight %}

### SPL Exceptions

Die generische Klasse `Exception` enthält sehr wenig Kontext für das Debugging durch den Entwickler. Zur Erleichterung kann man über eine Unterklassen der generischen Klasse `Exception` einen spezialisierten `Exception`-Typ schaffen:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

So kannst du mehrere `catch`-Blöcke einrichten und unterschiedliche Exceptions auch unterschiedlich behandeln. Das kann zu einer <em>Vielzahl</em> von benutzerdefinierten Exceptions führen, von denen einige durch den Einsatz von SPl Exceptions aus der  [SPL-Erweiterung][splext] vermeidbar sind.

Zum Beispiel könnte die magische Methode `__call()` beim Aufruf einer ungültigen Methode `throw new BadFunctionCallException;` aufrufen, statt die Standard-Exception oder eine benutzerdefinierte Exception auszulösen.

* [Mehr über Exceptions][exceptions]
* [Mehr über SPL Exceptions][splexe]
* [Verschachtelte Exceptions in PHP][nesting-exceptions-in-php]
* [Beste Methoden für Exceptions in PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/de/class.exception.php
[splexe]: http://php.net/manual/en/spl.exceptions.php
[splext]: #standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
