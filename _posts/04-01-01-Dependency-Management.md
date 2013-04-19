---
title: Verwaltung von Abhängigkeiten
---

# Verwaltung von Abhängigkeiten {#dependency_management_title}

Es gibt eine unüberschaubare Menge von PHP-Bibliotheken, Frameworks und Bausteine, aus denen man wählen kann. In deinem Projekt wirst du wahrscheinlich mehrere davon einsetzen. Bis vor Kurzem hatte PHP keine Methode. um dies Projektabhängigkeiten zu verwalten. Selbst wenn du diese händisch verwaltet hättest, musstest du dich um Autoloader kümmern. Das ist vorbei.

Zur Zeit gibt es zwei große Paketverwaltungssysteme für PHP - Composer und PEAR. Welches ist das richtige für dich? Beide, lautete die Antwort.

 * Verwende **Composer** für die Verwaltung von Abhängigkeiten in einem einzelnen Projekt.
 * verwende **PEAR** für die Verwaltung von Abhängigkeiten von PHP in einem Gesamtsystem.

Allgemein sind Pakete aus Composer nur in den Projekten verfügbar, die du explizit angibst, während Pakete aus PEAR in allen deinen PHP-Projekten verfügbar sind. Auf den ersten Blick mag der PEAR-Ansatz einfacher erscheinen, aber der projektspezifische Zugang zu Abhängigkeiten hat Vorteile.
