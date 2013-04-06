---
title: Stilregeln für den Code
---

# Stilregeln für den Code  {#code_style_guide_title}

Die PHP-Gemeinschaft ist groß und vielfältig und besteht aus unzähligen Bibliotheken, Frameworks und Bausteinen. Üblicherweise wählen PHP-Entwickler mehrere davon aus und kombinieren sie in einem einzelnen Projekt. Es ist wichtig, dass PHP-Code einem gemeinsamen Stil folgt, um Entwicklern die Kombination von verschiedenen Bibliotheken innerhalb ihrer Projekte zu erleichtern.

Die [Framework Interop Group][fig] hat eine Reihe von Stil-Empfehlungen unter den Namen [PSR-0][psr0], [PSR-1][psr1] und [PSR-2][psr2] vorgeschlagen. Trotz des seltsamen Namens sind diese Empfehlungen nur ein Satz von Regeln, den einige Projekte wie Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium und andere in ersten Ansätzen folgen. Du kannst sie für deine eigenen Projekte anwenden oder damit fortfahren, deinen persönlichen Stil zu pflegen.

Im Idealfall solltest du PHP-Code schreiben, der sich an einen bekannten Standard hält. Das kann eine Kombination der PSRs oder einer der Code-Standards von PEAR oder Zend sein. Das bedeutet, dass andere Entwickler sich einfach einlesen und mit deinem Code arbeiten können und Anwendungen konsistent wirken, selbst wenn sie viele Bausteine von dritter Seite benutzen.

* [Mehr über PSR-0][psr0]
* [Mehr über PSR-1][psr1]
* [Mehr über PSR-2][psr2]
* [Mehr über die PEAR Coding Standards][pear-cs]
* [Mehr über die Zend Coding Standards][zend-cs]

Du kannst deinen Code mit [PHP_CodeSniffer][phpcs] gegenüber einer dieser Empfehlungen prüfen oder Plugins für Texteditoren wie [Sublime Text 2][st-cs] einsetzen, um Rückmeldungen gleich während der Bearbeitung zu erhalten.

Mit Fabien Potenciers [PHP Coding Standards Fixer][phpcsfixer] kannst du automatisch Code modifizieren, sodass er mit diesen Standards konform ist, und sparst dir somit die händische Bearbeitung.

Englisch ist die bevorzugte Sprache für alle Symbolnamen und Code-Infrastruktur. Kommentare können in jeder Sprache geschrieben wrden, die von den derzeitigen und künftigen Beteiligten gelesen werden kann.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr3]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logger-interface.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
