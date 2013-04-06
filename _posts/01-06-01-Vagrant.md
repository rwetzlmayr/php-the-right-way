---
title: Vagrant
isChild: true
---

## Vagrant {#vagrant_title}

Der Betrieb einer Anwendung in zwischen Entwicklung und Produktion unterschiedlichen Umgebungen kann zu seltsamen Bugs führen. Ein Team von Entwicklern auf dem selben Versionsstand aller Bibliotheken zu halten kann ebenfalls umständlich werden.

Du solltest den Einsatz einer virtuellen Maschine erwägen, wenn du unter Windows entwickelst und auf Linux oder ein anderes Nicht-Windows-Betriebssystem ausrollst oder in einem Team entwickelst. Das klingt kompliziert, aber mit Hilfe von [Vagrant][vagrant] kannst du eine einfache virtuell Maschine in wenigen Schritten einrichten. Diese Basismaschinen kannst du anschließend manuell aufsetzen oder Software wie [Puppet][puppet] or [Chef][chef] zur "Provisionierung" einsetzen. Eine Basismaschine zu provisionieren ist eine gute Methode, um sicherzustellen, dass mehrere Maschinen identisch konfiguriert sind und reduziert den Bedarf von komplizierten Checklisten für das Setup. Du kannst eine Basismaschine auch ohne manuelle Schritte zerstören und mit einer neuen Installation wieder frisch aufbauen.

Vagrant erstellt geteilte Verzeichnisse, um den Code zwischen dem Host und den virtuellen Maschinen zu verteilen. Damit kannst du den Code auf der Hostmaschine bearbeiten und in den virtuellen Maschinen ablaufen lassen.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
