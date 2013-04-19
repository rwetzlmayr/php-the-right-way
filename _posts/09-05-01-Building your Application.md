---
isChild: true
title: Baue deine Anwendung
---

## Baue und verteile deine Anwendung {#build_title}

Wenn du das Datenbankschema manuell änderst oder deine Tests manuell startest, bevor du deine Dateien (manuell) aktualisierst, denke noch mal nach! Mit jeder manuellen Aufgabe, die man für die Ausrollung einer neuen Version deiner Anwendung benötigt, steigen die Chancen für potentiell fatale Fehler. Ob es um ein einfaches Update, einen umfassenden Build-Prozess oder sogar um eine kontinuierliche Integrationsstrategie geht, [Build-Automation](http://en.wikipedia.org/wiki/Build_automation) ist dein Freund.

Unter den Aufgaben, die du automatisieren kannst, sind etwa:

* Verwalten von Abhängigkeiten
* Kompilieren und Verkleinern der Assets
* Tests
* Erzeugen der Dokumentation
* Verpacken
* Ausrollen

### Werkzeuge für die Build Automation

Build-Werkzeuge kann man als Sammlung von Scripts beschreiben, die übliche Aufgaben der Softwareentwicklung bearbeiten. Das Build-Werkzeug ist nicht Teil deiner Software, sonder es wirkt "von außen".

Es gibt viele Open-Source-Werkzeuge, die dir bei der Build Automation helfen. Manche davon sind in PHP geschrieben, andre nicht. Das solte dich nicht von ihrem Einsatz abhalten, wenn sie besser für einen bestimmten Job geeignet sind. Hier sind ein paar Beispiele:

[Phing](http://www.phing.info/) ist der einfachste Weg, mit automatisierter Ausrollung in der PHP-Welt zu beginnen. Mit Phing kannst du das Verpacken, Ausrollen oder Testen von einer einfachen XML-Datei aus steuern. Phing, das auf [Apache Ant](http://ant.apache.org/) basiert, bietet eine umfangreiche Menge von Aufgaben, die üblicherweise benötigt werden, um Webanwendungen zu installieren oder zu aktualisieren, und kann mit zusätzlichen in PHP geschriebenen Aufgaben erweitert werden.

[Capistrano](https://github.com/capistrano/capistrano/wiki) ist ein System für *Programmierer mit mittleren oder fortgeschrittenen Kenntnissen*, um Befehle in einer strukturierten, wiederholbaren Art und Weise auf einer oder mehrerer Maschinen durchzuführen. Es ist für die Ausrollung von Anwendungen in Ruby on Rails vorkonfiguriert, es werden aber auch **erfolgreich PHP-Systeme** damit ausgerollt. Der erfolgreiche Einsatz von Capistrano hängt von brauchbaren Kenntnissen in Ruby und Rake ab.

Dave Gardners Blogbeitrag [PHP Deployment with Capistrano](http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/)
ist ein guter Startpunkt für PHP-Programmierer, die sich für Capistrano interessieren.

[Chef](http://www.opscode.com/chef/) ist mehr als ein Framework für das Ausrollen - ein sehr mächtiges Integrationsframework auf Ruby-Basis, das deine Anwendung nicht nur ausrollt, sondern den gesamten Server oder virtuelle Maschinen baut.

Ressourcen zu Chef für PHP-Entwickler:

* [Dreiteilige Blogserie über das Ausrollen einer LAMP-Anwendung mit Chef, Vagrant und EC2](http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/)
* [Ein Chef Cookbook, das PHP 5.3 und the PEAR-Paketverwaltungssystem installiert und konfiguriert](https://github.com/opscode-cookbooks/php)

Weiterführende Literatur:

* [Automate your project with Apache Ant](http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/)
* [Maven](http://maven.apache.org/), ein Build-Framework, das auf Ant basiert, und [wie man es mit PHP verwendet](http://www.php-maven.org/)

### Kontinuierliche Integration

> Continuous Integration is a software development practice where members of a team integrate their work frequently,
> usually each person integrates at least daily — leading to multiple integrations per day. Many teams find that this
> approach leads to significantly reduced integration problems and allows a team to develop cohesive software more
> rapidly.

*-- Martin Fowler*

Es gibt verschiedene Arten, um kontinuierliche Integration für PHP zu implementieren. In letzter Zeit hat [Travis CI](https://travis-ci.org/) einen großen Beitrag dazu geleistet, kontinuierliche Integration auch für kleine Projekte Realität werden zu lassen. Travis CI ist eine gehostete Lösung für die Open-Source-Community. Es ist in Github integriert und bietet erstklassige Unterstützung für viele Sprachen inklusive PHP.

Weiterführende Literatur:

* [Kontinuierliche Integration mit Jenkins](http://jenkins-ci.org/)
* [Kontinuierliche Integration mit Teamcity](http://www.jetbrains.com/teamcity/)