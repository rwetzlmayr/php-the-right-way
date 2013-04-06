---
title: Schnittstelle für die Kommandozeile
isChild: true
---

## Schnittstelle für die Kommandozeile {#command_line_interface_title}

PHP wurde primär für die Erstellung von Web-Anwendungen geschaffen, aber es ist auch beim verfassen von Kommandozeilenprogrammen (CLI; command line interface) nützlich. PHP-Programme für die Kommandozeile können dir helfen, allgemeine Aufgaben wie Softwaretests, Ausrollung und Administratives zu automatisieren.

CLI-PHP-Programme sind mächtig, weil sie den Code deiner Anwendung direkt ohne Web-Oberfläche benutzen können. Achte nur darauf, dass deine CLI-Scripts nicht im öffentlichen Webverzeichnis liegen!

Versuche, PHP von der Kommandozeile aus aufzurufen:

{% highlight bash %}
> php -i
{% endhighlight %}

Die Option `-i` gibt die PHP-Konfiguration ähnlich wie die Funktion [`phpinfo`][phpinfo] aus.

Die Option `-a` startet eine interaktive Shell ähnlich wie IRB in Ruby oder Pythons interaktive Shell. Es gibt einige andere nützliche [Optionen für die Kommandozeile][cli-options].

Schreiben wir doch ein CLI-Programm für "Hello, $name". Erstelle eine Datei `hello.php` und gib diesen Code in die Datei ein:

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP erstellt zwei spezielle Variable auf Basis der Argument, mit denen dein Script gestartet wird. [`$argc`][argc] ist eine Integer-Variable und enthält die *Anzahl* der Argumente; [`$argv`][argv] ist ein eine Array-Variable, die den *Wert* jedes Arguments enthält. Das erste Argument ist immer der Name deines PHP-Scripts, in unserem Fall also `hello.php`.

Der Ausdruck `exit()` wird mit einer Zahl ungleich Null aufgerufen, um die Shell davon zu informieren, dass der Befehl gescheitert ist. Gebräuchliche Exitcodes findet man [hier][exit-codes].

Starte unser Script von der Kommandozeile:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Mehr über den Einsatz von PHP auf der Kommandozeile][php-cli]
 * [Mehr über die Einrichtung von Windows für den Einsatz von PHP auf der Kommandozeile][php-cli-windows]

[phpinfo]: http://php.net/manual/de/function.phpinfo.php
[cli-options]: http://www.php.net/manual/de/features.commandline.options.php
[argc]: http://php.net/manual/de/reserved.variables.argc.php
[argv]: http://php.net/manual/de/reserved.variables.argv.php
[php-cli]: http://php.net/manual/de/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/de/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
