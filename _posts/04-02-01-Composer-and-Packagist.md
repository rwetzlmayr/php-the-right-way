---
title: Composer und Packagist
isChild: true
anchor:  composer_and_packagist
---

## Composer und Packagist {#composer_and_packagist_title}

Composer is the recommended dependency manager for PHP. List your project's dependencies in a `composer.json` file and,
with a few simple commands, Composer will automatically download your project's dependencies and setup autoloading for
you. Composer is analogous to NPM in the node.js world, or Bundler in the Ruby world.

Viele PHP-Bibliotheken sind bereits mit Composer kompatibel und bereit für den Einsatz in deinem Projekt. Diese "Pakete" werden bei [Packagist] gelistet, dem offiziellen Verzeichnis von mit Composer kompatiblen PHP-Bibliotheken.

### Composer installieren

The safest way to download composer is by [following the official instructions](https://getcomposer.org/download/).
This will verify the installer is not corrupt or tampered with.
The installer installs a `composer.phar` binary in your _current working directory_.

We recommend installing Composer *globally* (e.g. a single copy in `/usr/local/bin`). To do so, run this command next:

{% highlight console %}
mv composer.phar /usr/local/bin/composer
{% endhighlight %}

**Note:** If the above fails due to permissions, prefix with `sudo`.

To run a locally installed Composer you'd use `php composer.phar`, globally it's simply `composer`.

#### Installing on Windows

For Windows users the easiest way to get up and running is to use the [ComposerSetup] installer, which
performs a global install and sets up your `$PATH` so that you can just call `composer` from any
directory in your command line.

### Abhängigkeiten definieren und installieren

Composer verfolgt die Abhängigkeiten deines Projekts in einer Datei namens `composer.json`. Du kannst
diese Datei händisch oder mit Composer verwalten. Der Befehl `composer require` fügt eine
Projektabhängigkeit hinzu. Wenn die Datei `composer.json` noch nicht existiert, wird sie erstellt.
Im folgenden Beispiel wird [Twig] als Abhängigkeit zu deinem Projekt hinzugefügt.

{% highlight console %}
composer require twig/twig:^2.0
{% endhighlight %}

Alternative führt dich der Befehl `composer init` durch die Erstellung einer vollständigen `composer.json`
für dein Projekt. In jedem Fall kannst du nach der Erzeugung der Datei `composer.json` Composer anweisen,
die Abhängigkeiten deines Projekts in das Verzeichnis `vendors/` herunterzuladen und zu installieren. Das
trifft auch auf heruntergeladene Projekte zu, die selbst bereits eine Datei `composer.json` bereitstellen:

{% highlight console %}
composer install
{% endhighlight %}

Als nächsten Schritt füge diese Zeile zur primären PHP-Datei deines Projektes hinzu; damit weist du PHP an, den Autloader von Composer für deine Projektabhängigkeiten einzusetzen.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Du kannst jetzt Projektabhängigkeiten verwenden, und sie werden automatisch heruntergeladen.

### Abhängigkeiten aktualisieren

Composer erzeugt eine Datei `composer.lock`, in der die genauen Versionen jedes Pakets zu dem Zeitpunkt
gespeichert sind, an dem du das erste Mal `composer install` ausgeführt hast. Wenn du dein Projekt mit
anderen Programmierern teilst und die Datei `composer install` in das verteilte Produkt aufnimmst,
erhalten sie die selbe Version wie du. Starte  `composer update`, um die Abhängigkeiten zu aktualisieren.
Don't use `composer update` when deploying, only `composer install`, otherwise you may end up with different
package versions on production.

Das ist auch sehr nützlich, falls du deine Versionsansprüche flexibel definiert hast. Beispielsweise bedeutet
eine erforderliche Version von ~1.8 "irgend eine Version, die neuer ist als 1.8, aber niedriger als 2.0.x-dev".
Der Composer-Befehl `composer update` wird alle Abhängigkeiten auf die neueste Version aktualisieren, welche
die definierten Einschränkungen erfüllen.

### Update Notifications

To receive notifications about new version releases you can sign up for [libraries.io], a web service
that can monitor dependencies and send you alerts on updates.

### Abhängigkeiten auf Sicherheitsprobleme prüfen

Der [Security Advisories Checker] ist ein Webdienst und ein Befehlszeilenwerkzeug. Er untersucht die Datei
`composer.lock` und berichtet, ob eine Abhängigkeit aktualisiert werden muss.

### Handling global dependencies with Composer

Composer can also handle global dependencies and their binaries. Usage is straight-forward, all you need
to do is prefix your command with `global`. If for example you wanted to install PHPUnit and have it
available globally, you'd run the following command:

{% highlight console %}
composer global require phpunit/phpunit
{% endhighlight %}

This will create a `~/.composer` folder where your global dependencies reside. To have the installed
packages' binaries available everywhere, you'd then add the `~/.composer/vendor/bin` folder to your
`$PATH` variable.

* [Mehr über Composer]

[Packagist]: https://packagist.org/
[Twig]: https://twig.symfony.com/
[libraries.io]: https://libraries.io/
[Security Advisories Checker]: https://security.symfony.com/
[Learn about Composer]: https://getcomposer.org/doc/00-intro.md
[ComposerSetup]: https://getcomposer.org/Composer-Setup.exe
