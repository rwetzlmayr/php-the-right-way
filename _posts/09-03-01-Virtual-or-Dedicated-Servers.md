---
isChild: true
title: Virtuelle oder dedizierte Server
---

## Virtuelle oder dedizierte Server {#virtual_or_dedicated_servers_title}

Wenn du mit der Systemadministration vertraut bist oder ein Interesse hast, das zu lernen, erhältst du bei virtuellen oder dedizierten Servern die volle Kontrolle über die Produktivumgebung deiner Anwendung.

### nginx und PHP-FPM

Über den eingebauten FastCGI Process Manager (FPM) passt PHP sehr gut zu [nginx](http://nginx.org), einem schlanken leistungsstarken Webserver. Nginx benötigt weniger Speicher als Apache und kann mehr gleichzeitige Zugriffe besser bearbeiten. Das ist speziell bei virtuellen Servern mit wenig Speicher wichtig.

* [Mehr über nginx](http://nginx.org)
* [Mehr über PHP-FPM](http://php.net/manual/en/install.fpm.php)
* [Mehr über die sichere Installation von nginx und PHP-FPM](https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/)

### Apache und PHP

PHP und Apache haben eine lange gemeinsame Geschichte. Apache ist flexibel konfigurierbar und besitzt viele [Module](http://httpd.apache.org/docs/2.4/mod/) zur Funktionserweiterung. Apache ist eine beliebte Wahl für billiges Shared Hosting und eine einfache Basis für PHP-Frameworks und Open-Source-Anwendungen wie [Textpattern CMS](http://textpattern.com/). Unglücklicherweise benötigt Apache mehr Ressourcen als nginx und kann nicht so viele Besucher gleichzeitig bedienen.

Apache hat einige Möglichkeiten, um PHP zu starten. Die geläufigste und einfachste ist das [Prefork MPM](http://httpd.apache.org/docs/2.4/mod/prefork.html) mit mod_php5. Zwar ist es nicht die effizienteste, aber die einfachste Methode der Installation und des Betriebs. Es ist wahrscheinlich die beste Wahl wenn du nicht zu tief in die Serveradministration einsteigen möchtest. Beachte, dass mod_php das Prefork MPM erfordert.

Alternativ kannst du für mehr Leistung und Stabilität dasselbe FPM-System wie nginx einsetzen und das [Worker MPM](http://httpd.apache.org/docs/2.4/mod/worker.html) oder das [Event MPM](http://httpd.apache.org/docs/2.4/mod/event.html) mit mod_fastcgi oder mod_fcgid verwenden. Diese Konfiguration wird signifikant effizienter mit dem Speicher umgehen und schneller sein, aber mehr Arbeit bei der Installation machen.
* [Mehr über Apache](http://httpd.apache.org/)
* [Mehr über Multi-Processing-Module](http://httpd.apache.org/docs/2.4/mod/mpm_common.html)
* [Mehr über mod_fastcgi](http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html)
* [Mehr über mod_fcgid](http://httpd.apache.org/mod_fcgid/)
