---
title: Datenbanken
---

# Datenbanken {#databases_title}

Oft wird dein PHP-Code eine Datenbank verwenden, um Informationen dauerhaft zu speichern. Es gibt einige Möglichkeiten, um dich mit deiner Datenbank zu verbinden und mit ihr zu interagieren. Die empfohlene Auswahl _bis PHP 5.1.0__ waren die nativen Treiber wie [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql] etc.

Native Treiber sind gut geeignet, wenn du nur ein Datenbanksystem in deiner Anwendung einsetzt. Wenn du aber zum Beispiel MySQL und ein wenig von MSSQL verwenden oder dich mit einer Oracle-Datenbank verbinden möchtest, kannst du nicht dieselben Treiber verwenden. Du musst ein völlig neues API für jedes Datenbanksystem erlernen - und das kann albern werden.

Zusätzlich ist zu sagen, dass die MySQL-Erweiterung für PHP nicht mehr aktiv weiterentwickelt wird und der offizielle Status seit PHP 5.4.0 "langfristige Abkündigung" lautet. Das bedeutet, dass sie im Zug der nächsten Releases entfernt werden wird. Sie könnte also mit PHP 5.6 (oder welche Version auch immer nach 5.5 kommen wird) verschwinden. Setzt du `mysql_connect()` und `mysql_query()` in deiner Anwendung ein, wirst du den Code dann umschreiben müssen. Die beste Wahl ist ist es, in deinen Anwendungen während eines geplanten Entwicklungszyklus mysql durch mysqli oder PDO zu ersetzen und so einer späteren erzwungenen Umstellung auszuweichen. _Vermeide die mysql-Erweiterung bei einem neuen Projekt: Verwende die [mysqli-Erweiterung][mysqli] oder PDO._

* [PHP: Choosing an API for MySQL](http://php.net/manual/de/mysqlinfo.api.choosing.php)

## PDO

PDO ist eine Bibliothek zur Datenbankabstraktion - seit Version 5.1.0 in PHP integriert - die eine gemeinsame Schnittstelle zu vielen verschiedenen Datenbanksystemen bietet. PDO übersetzt keine SQL-Abfragen und emuliert keine fehlenden Eigenschaften; es dient rein der Verbindung zu mehreren Datenbanksystemen mit einem einheitlichen API.

Wichtiger noch: PDO erlaubt dir, externe Eingaben wie zum Beispiel IDs sicher in deine SQL-Abfragen einzubauen, ohne dich über SQL-Injection-Angriffe zu sorgen. Das geschieht über PDO-Statements und gebundene Parameter.

Nehme wir an, dass ein PHP-Script eine numerische ID als Query-Parameter annimmt. Diese ID soll verwendet werden, um einen Benutzerdatensatz aus der Datenbank zu lesen. Hier ist der `falsche` Weg, das zu erledigen:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

Das ist schrecklicher Code. Du fügst einen ungefilterten Query-Parameter in eine SQL-Abfrage ein. Du wirst innerhalb von Sekunden gehackt. Stell dir vor, dass ein  Hacker einen erfinderischen `id`-Parameter über eine URL wie `http://domain.com/?id=1%3BDELETE+FROM+users` übergibt. Das setzt die Variable `$_GET['id']` auf `1;DELETE FROM users` und löscht so alle deine User! Du solltest stattdessen die ID-Eingabe über PDO-gebundene Parameter reinigen.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- Automatically sanitized by PDO
$stmt->execute();
{% endhighlight %}

Das ist korrekter Code. Er verwendet einen gebundenen Parameter in einem PDO-Ausdruck. Das bereinigt die externe Eingabe, bevor sie an die Datenbank weitergegeben wird, und verhindert so potentielle SQL-Injection-Angriffe.

* [Mehr über PDO][1]

Du solltest dir auch darüber klar sein, dass Datenbankverbindungen Ressourcen verbrauchen und es kann schon vorkommen, dass diese Ressourcen erschöpft werden, wenn Verbindungen nicht explizit geschlossen wurden. Das trifft aber vor allem auf andere Sprachen zu. Mit PDO kannst du eine Verbindung implizit schließen, indem du das Objekt freigibst. Dazu lösche alle verbleibenden Referenzen, indem du sie auf `NULL`setzt. Wenn du das nicht ausdrücklich machst, schließt PHP die Verbindung automatisch am Ende des Scripts, sofern du nicht persistente Verbindungen benutzt.

* [Mehr über PDO-Verbindungen][5]

## Abstraktionsschichten

Viele Frameworks enthalten ihre eigenen Abstraktionsschichten, die teilweise auf PDO aufbauen. Diese emulieren oft fehlende Eigenschaften eines Datenbanksystems, indem sie Abfragen in PHP-Methoden kleiden und so die Datenbank tatsächlich abstrahieren. Damit entsteht natürlich ein wenig Overhead, der aber beim Bau einer zwischen MySQL, PostgreSQL und SQLite portablen Anwendung seine Berechtigung hat.
 
Einige Abstraktionsschichten wurden gemäß den Namespace-Standards nach PSR-0 entwickelt und können daher in jede Anwendung eingebaut werden:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/de/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[5]: http://php.net/manual/de/pdo.connections.php
[6]: https://github.com/auraphp/Aura.Sql

[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
