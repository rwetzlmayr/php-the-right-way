---
isChild: true
title: Objektcache
---

## Objektcache {#object_caching_title}

Manchmal ist es vorteilhaft, einzelne Objekte in deinem Code zu cachen wie etwa Daten, die nur mit hohem Aufwand zu erhalten sind, oder Datenbankzugriffe, deren Ergebnis sich wahrscheinlich nicht ändert. Du kannst Objektcache-Software verwenden, um diese Teile von Daten im Speicher zu halten und extrem schnell später darauf zuzugreifen. Wenn du diese Elemente in einem Datenspeicher sicherst, nachdem du sie abgerufen hast, und anschließend für nachfolgende Anfragen direkt aus dem Cache holst, kannst du wesentliche Verbesserungen bezüglich Geschwindigkeit erreichen und die Last der Datenbankserver vermindern.

Viele beliebte Lösungen für Bytecode-Caches erlauben dir auch, eigene Daten zu cachen, was noch ein zusätzlicher Grund ist, diese zu deinem Vorteil zu nutzen. APC, XCache und WinCache bieten APIs, um Daten aus deinem PHP-Code in ihren Cachespeicher zu sichern.

Die meist verbreiteten Systeme für speicherbasierende Objektcaches sind APC und memcached. APC ist eine exzellente Wahl für Objektcaches; es beinhaltet ein einfaches API, das an den Server gebunden ist, auf dem es installiert ist. Memcached andererseits wird als getrennter Dienst installiert und kann über das Netzwerk angesprochen werden; das bedeutet, dass du Objekte in einem schnellen Datenspeicher ablegen und von vielen verschiedenen Systemen abrufen kannst.

Beachte: Wenn PHP als (Fast-)CGI-Anwendung deines Webserver läuft, besitzt jeder PHP-Prozess seinen eigenen Cache. Das heißt, dass die APC-Daten nicht zwischen den Arbeitsprozessen geteilt werden. In diesen Fällen könnte man den Einsatz von memcached überlegen, da dieser nicht an PHP-Prozesse gebunden ist.

In einer Netzwerk-Konfiguration wird APC im Regelfall schneller sein als memcached, während memcached weiter und schneller skaliert. Wen du nicht planst, deine Anwendung auf mehrere Server zu verteilen oder die zusätzlichen Eigenschaften von memcached nicht benötigst, ist APC wahrscheinlich die beste Wahl als Objektcache.

 Beispiellogik für APC:

{% highlight php %}
<?php
// check if there is data saved as 'expensive_data' in cache
$data = apc_fetch('expensive_data');
if ($data === false) {
    // data is not in cache; save result of expensive call for later use
    apc_add('expensive_data', $data = get_expensive_data());
}

print_r($data);
{% endhighlight %}

Mehr über populäre Objektcaching-Systeme:

* [APC-Funktionen](http://php.net/manual/de/ref.apc.php)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache APIs](http://xcache.lighttpd.net/wiki/XcacheApi)
* [WinCache Functions](http://www.php.net/manual/de/ref.wincache.php)
