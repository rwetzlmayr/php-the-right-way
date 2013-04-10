---
isChild: true
title: Konfigurationsdateien
---

## Konfigurationsdateien {#configuration_files_title}

Wenn du Konfigurationsdateien erstellt, empfiehlt sich als beste Vorgehensweise eine der folgenden Methoden:

- Es ist empfehlenswert, Konfigurationsinformationen dort zu speichern, wo sie nicht direkt über das Dateisystem zugreifbar sind.
- Wenn du Konfigurationsdateien im Documentroot speichern musst, gib ihnen die Erweiterung `.php`. Damit ist sichergestellt, dass sie auch beim direktem Zugriff nicht als einfacher Text ausgegeben werden.
- Die Information in Konfigurationsdateien sollte entweder durch Verschlüsselung oder durch Gruppen-/Nutzerberechtigungen des Dateisystems geschützt werden.