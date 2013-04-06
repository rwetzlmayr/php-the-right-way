---
title: Schnittstelle für die Kommandozeile
isChild: true
anchor:  command_line_interface
---

## Schnittstelle für die Kommandozeile {#command_line_interface_title}

PHP wurde primär für die Erstellung von Web-Anwendungen geschaffen, aber es ist auch beim verfassen von Kommandozeilenprogrammen (CLI; command line interface) nützlich. PHP-Programme für die Kommandozeile können dir helfen, allgemeine Aufgaben wie Softwaretests, Ausrollung und Administratives zu automatisieren.

CLI-PHP-Programme sind mächtig, weil sie den Code deiner Anwendung direkt ohne Web-Oberfläche benutzen können. Achte nur darauf, dass deine CLI-Scripts **nicht** im öffentlichen Webverzeichnis liegen!

Versuche, PHP von der Kommandozeile aus aufzurufen:

{% highlight console %}
> php -i
{% endhighlight %}

Die Option `-i` gibt die PHP-Konfiguration ähnlich wie die Funktion [`phpinfo()`][phpinfo] aus.

Die Option `-a` startet eine interaktive Shell ähnlich wie IRB in Ruby oder Pythons interaktive Shell. Es gibt einige andere nützliche [Optionen für die Kommandozeile][cli-options].

Schreiben wir doch ein CLI-Programm für "Hello, $name". Erstelle eine Datei `hello.php` und gib diesen Code in die Datei ein:

{% highlight php %}
<?php
if ($argc !== 2) {
    echo "Usage: php hello.php <name>.\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP erstellt zwei spezielle Variable auf Basis der Argument, mit denen dein Script gestartet wird. [`$argc`][argc] ist eine Integer-Variable
und enthält die *Anzahl* der Argumente; [`$argv`][argv] ist ein eine Array-Variable, die den *Wert* jedes Arguments enthält. Das erste
Argument ist immer der Name deines PHP-Scripts, in unserem Fall also `hello.php`.

Der Ausdruck `exit()` wird mit einer Zahl ungleich Null aufgerufen, um die Shell davon zu informieren, dass der Befehl gescheitert ist. Gebräuchliche Exitcodes findet man [hier][exit-codes].

Starte unser Script von der Kommandozeile:

{% highlight console %}
> php hello.php
Usage: php hello.php <name>
> php hello.php world
Hello, world
{% endhighlight %}

 * [Mehr über den Einsatz von PHP auf der Kommandozeile][php-cli]

[phpinfo]: https://secure.php.net/function.phpinfo
[cli-options]: https://secure.php.net/features.commandline.options
[argc]: https://secure.php.net/reserved.variables.argc
[argv]: https://secure.php.net/reserved.variables.argv
[exit-codes]: https://www.gsp.com/cgi-bin/man.cgi?section=3&amp;topic=sysexits
[php-cli]: https://secure.php.net/features.commandline.options
