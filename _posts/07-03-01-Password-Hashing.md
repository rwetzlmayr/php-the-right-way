---
isChild: true
title: Passwort-Hashing
---

## Passwort-Hashing {#password_hashing_title}

Früher oder später baut jeder eine PHP-Anwendung, die angemeldete Benutzer benötigt. Benutzernamen und Passwörter werden in einer Datenbank gespeichert und später verwendet, um den Benutzer bei der Anmeldung zu authentifizieren.

Es ist wichtig, Passwörter vor dem Speichern korrekt zu [_hashen_][3]. Passwort-Hashing ist eine nicht umkehrbare Einbahnfunktion, die auf das Passwort des Benutzers angewandt wird. Sie erzeugt einen String mit fester Länge, der nicht mit vertretbarem Aufwand entschlüsselt werden kann. Das bedeutet, dass du einen Hashwert mit einem zweiten vergleichen kannst, um festzustellen, ob beide den selben Quellstring repräsentieren. Du kannst den ursprünglichen String aber nicht mehr wiederherstellen. Wenn Passwörter nicht gehasht werden und die Datenbank in falsche Hände gerät, sind alle Benutzerkonten kompromittiert. Einige Benutzer werden das selbe Passwort auch bei anderen Diensten verwenden. Darum ist es wichtig, Sicherheit ernst zu nehmen.

**Passwörter mit `password_hash` hashen**

Mit PHP 5.5 wird die Funktion `password_hash` eingeführt. Zur Zeit verwendet sie BCrypt, den stärksten aktuell von PHP unterstützten Algorithmus. Zukünftig wird sie aktualisiert werden, um bei Bedarf weitere Algorithmen zu unterstützen. Die Bibliothek `password_compat` wurde geschaffen, um mit PHP >= 5.3.7 vorwärtskompatibel zu sein.

Unten hashen wir einen String und prüfen anschließend gegen einen neuen String. Wie die beiden Strings unterschiedlich sind ('secret-password' gegen 'bad-password'), wird diese Anmeldung scheitern.

{% highlight php %}
<?php
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    //Correct Password
} else {
    //Wrong password
}
{% endhighlight %}  


* [Mehr über `password_hash`] [1]
* [`password_compat` für PHP  >= 5.3.7 && < 5.5] [2]
* [Mehr über Hashing in Bezug auf Kryptographie] [3]
* [PHP `password_hash` RFC] [4]

[1]: http://us2.php.net/manual/en/function.password-hash.php
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
