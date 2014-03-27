---
isChild: true
title: Bytecode-Cache
---

## Bytecode-Cache {#bytecode_cache_title}

Wenn eine PHP-Datei ausgeführt wird, wird sie im Hintergrund zuerst in Bytecode (auch Opcode genannt) kompiliert und dieser Bytecode anschließend ausgeführt.
Solange die PHP-Datei nicht verändert wurde, bleibt dieser Bytecode gleich. Das heißt, dass der Kompilierungsschritt eine Verschwendung von CPU-Ressourcen ist.

Hier kommt der Bytecode-Cache ins Spiel. Er verhindert die redundante Kompilierung durch das Speichern von Bytecode im Hauptspeicher und ermöglicht die Wiederverwendung bei nachfolgenden Aufrufen. Der Bytecode-Cache ist innerhalb weniger Minuten einzurichten und wird deine Anwendung signifikant beschleunigen. Es gibt wirklich keinen Grund, ihn nicht einzusetzen.

Beliebte Bytecode-Caches sind:

* [APC](http://php.net/manual/de/book.apc.php)
* [XCache](http://xcache.lighttpd.net/)
* [Zend Optimizer+](http://www.zend.com/de/products/server/) (Teil der Pakets "Zend Server")
* [WinCache](http://www.iis.net/download/wincacheforphp) (Erweiterung für MS Windows Server)
