Was sind Zaps?

Die einfachste Art, über Zaps nachzudenken, ist, dass es sich einfach um Tipps handelt. Tipps, die mit Lichtgeschwindigkeit 
und praktisch ohne Transaktionsgebühren über das Lightning-Netzwerk übertragen werden.

Seit Beginn des Nostr-Protokolls war es üblich, Lightning-Rechnungen in Notizen zu sehen. Seit der Implementierung von 
NIP-57 sind Zaps die Hauptmethode, mit der Werte in Nostr-Noten übertragen werden. Schauen wir uns genauer an, was NIP-57 
implementiert hat und wie Zaps funktionieren.

NIP-57
NIP-57 ist das Dokument, das beschreibt, wie Zaps implementiert werden sollten. Es erstellt zwei neue Arten von Notizen, 
Art 9735 (A Zap) und Art 9734 (A Zap-Anfrage). Zusammen ermöglichen diese beiden Arten es Nostr-Kunden, Zap-Rechnungen 
von LNURL-Servern anzufordern und zu bezahlen. Die NIP-57-Spezifikation beschreibt auch, wie Lightning-Wallets, die 
Zap-Zahlungen erhalten, Notizen erstellen sollten, die an Relais gesendet werden.

Unterhaltsame Tatsache, die für Zaps gewählte Notizart ist die gleiche wie der Netzwerkport (9735), den Lightning verwendet.


![zap-flow translated](https://user-images.githubusercontent.com/1324583/229059161-85e9cf57-f0e9-4079-adbe-3aa5ac968403.jpg)

Wir werden uns hier nicht in die Tiefen der Technik begeben, aber für die Neugierigen unter Ihnen, lassen Sie uns einen Blick 
auf die grundlegende Mechanik werfen, wie Zaps funktionieren.

Wenn Sie auf das kleine ⚡-Symbol in Ihrem Client (Damus, Iris, Amethyst usw.) klicken oder tippen, pingt der Client als Erstes 
den LNURL-Server an, der vor der Lightning-Brieftasche der Person sitzt, die Sie zu zappen versuchen. Die erste Anfrage lautet 
etwa so: "Hallo, ich würde Alice gerne ein paar Sats geben."

Der LNURL-Server antwortet, und wenn Alices Brieftasche Zaps unterstützt, teilt er dies dem Client mit und sendet/bestätigt 
den öffentlichen Schlüssel von Alice.
An diesem Punkt macht sich der Client die Mühe, eine Zap-Anforderung (eine Art 9734-Note) mit Daten über das Profil oder die 
Note, die er zappen möchte, den Betrag, die Relais, an die die Note gesendet werden soll, und einige andere Dinge zusammenzustellen. 
Dies ist praktisch eine Anfrage an den LNURL-Server für eine Rechnung.
Der LNURL-Server antwortet mit der angeforderten Rechnung.

An diesem Punkt übergibt der Client die Rechnung an die Lightning-Wallet des Benutzers, um sie zu bezahlen. Wenn Sie eine 
Geldbörse wie Alby im Browser verwenden (und ein Budget festgelegt haben), kann dieser Vorgang sehr schnell ablaufen.
Sobald der Benutzer die Rechnung direkt an die Brieftasche der Person, die er zappt, bezahlt hat, erstellt die Brieftasche des 
Empfängers eine Art 9735-Note und sendet diese an die zuvor in der Zap-Anfrage angegebenen Relais.
Die Relays, die diese Notiz erhalten, können dann die angeschlossenen Kunden über den Zap informieren und den Nutzern den Zap in 
ihrem UI anzeigen.
All dies geschieht in wenigen Sekunden und kostet nur einen winzigen Bruchteil eines Pfennigs.


### Wie kann ich Zaps senden und empfangen?
Um andere Leute in Nostr zu zappen, brauchst du nur zwei Dinge:

Eine Zap-kompatible Lightning-Wallet (wie Alby oder Wallet of Satoshi)
Einen Client, der Zaps implementiert hat (wie Damus, Amethyst, Iris, oder Snort)
Die einzige andere Sache, die Sie tun müssen, ist sicherzustellen, dass Sie Ihre Lightning-Adresse in Ihrem Nostr-Profil 
eingestellt haben. Dies ist die Adresse, an die Sie Zaps erhalten werden.

Denken Sie daran, dass es möglich ist, Zaps von einer anderen Brieftasche/Adresse zu bezahlen als der, die Sie in Ihrem Profil für 
den Empfang von Zaps eingestellt haben.

Stellen Sie sich zum Beispiel Folgendes vor:

Sie haben in Ihrem Nostr-Profil eine Blitzadresse für Stacker News eingerichtet, über die Sie alle Zaps erhalten.
In Ihrem Webbrowser verwenden Sie Iris als Client und zahlen für Zaps mit Ihrer Alby-Geldbörse über die Chrome-Erweiterung
Auf dem Handy verwenden Sie Damus als Client und zahlen für Zaps mit der Wallet of Statoshi App.

