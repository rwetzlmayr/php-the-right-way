---
isChild: true
title: Datum und Zeit
---

## Datum und Zeit {#date_and_time_title}

PHP beinhaltet eine Klasse namens DateTime, die beim Lesen, Schreiben, Vergleichen und Berechnen von Datum und Zeit hilft. Es gibt neben DateTime viele weitere Funktionen mit Bezug zu Datum und Zeit in PHP, aber die Klasse bietet eine schöne objektorientierte Schnittstelle für die häufigsten Anwendungsfälle. Sie kann auch Zeitzonen verarbeiten, das ist allerdings nicht Inhalt dieser kurzen Einführung.

Konvertiere einen unformatierten Datums- und Zeitstring mit der Factory-Methode `createFromFormat()` oder verwende `new \DateTime` für die aktuelle Zeit und das aktuelle Datum, um mit DateTime zu beginnen. Verwende die Methode `format()`, um ein DateTime-Objeckt wieder in einen String zur Ausgabe zu konvertieren.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('m/d/Y') . "\n";
{% endhighlight %}

Die Klasse DateInterval ermöglicht Berechnungen mit DateTime. DateTime besitzt Methoden wie `add()` and `sub()`, die ein DateTime-Intervall als Argument akzeptieren. Schreibe keinen Code, der annimmt, dass jeder Tag die selbe Zahl von Sekunden dauert. Sowohl Sommerzeit-/Winterzeitwechsel als auch Zeitzonenwechsel verletzen diese Annahme. Verende stattdessen DateInterval. Verwenden die Methode `diff()`, um Datumsunterschiede zu berechnen. Das Ergebnis ist ein DateInterval, das sehr einfach anzuzeigen ist.

{% highlight php %}
<?php
// create a copy of $start and add one month and 6 days
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Difference: 1 month, 6 days (total: 37 days)
{% endhighlight %}

Du kannst herkömmliche Vergleichsoperatoren auf DateTime-Objekte anwenden:

{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}

Ein letztes Beispiel zeigt die Klasse DatePeriod. Sie wird verwendet, um über wiederkehrende Ereignisse zu iterieren. Sie akzeptiert zwei DateTome-Objekt für Beginn und Ende und ein Intervall und gibt alle Ereignisse dazwischen zurück.
{% highlight php %}
<?php
// output all thursdays between $start and $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('m/d/Y') . ' ';
}
{% endhighlight %}

* [Mehr über DateTime][datetime]
* [Mehr über Datumsformatierung][dateformat] (gültige Formatstrings für Datumswerte)

[datetime]: http://www.php.net/manual/de/book.datetime.php
[dateformat]: http://www.php.net/manual/de/function.date.php
