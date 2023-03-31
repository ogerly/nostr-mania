## Nostr Unterschiede zu Blockchain und anderen Lösungen

Nostr Unterschiede zu Blockchain und anderen Lösungen
Geschrieben von Alex Freed  in Nostr , Dev , Users

was ist nostr
Dieses Video ist ein Muss, um die unterschiedliche Philosophie hinter Nostr vs. Blockchain und anderen bestehenden Lösungen 
zu verstehen. Kevin Rooke interviewt William Casarin, einen Bitcoin-Entwickler, der am Lightning Protocol arbeitet und 
derzeit an Damus arbeitet, einem Projekt, das mit dem Nostr-Protokoll erstellt wurde (wir haben Damus hier behandelt ), 
also ist er eine großartige Quelle, um die Unterschiede zu erklären und die Themen darin zu kennen aus. Dieses Video hat 
uns so gut gefallen, dass dieser gesamte Blogbeitrag eine detaillierte Zusammenfassung des Gesprächs ist. Hoffe es gefällt 
euch so wie uns!

https://youtu.be/QXd0vLTw6NA

### Was ist ein NOSTR auf hohem Niveau und warum ist es das?
Nostr war also ein Versuch, geschrieben von diesem Typen namens Jeff, der auch an der Eleniral-Spezifikation beteiligt 
war. Viele Bitcoiner sind einfach wegen Fiat im Weltraum. Aber es ist kein Bitcoin-Projekt, es ist kein Lightning-Projekt, 
es ist ein eigenständiges Protokoll. Es wurde als Fiat-Versuch konzipiert, die einfachste mögliche zensurresistente 
Twitter-Alternative, ein globales soziales Netzwerk, zu schaffen.

Es gab in der Vergangenheit Versuche dazu, wie Macedon, das das Aktivitätsprotokoll verwendet. Aber das hatte ein sehr 
großes Problem, bei dem, wenn Sie einem Server beitreten, dieser Server zu Ihrer Community wird. Wenn Sie etwas Falsches 
sagen, kann der Serveradministrator Sie sperren, und Sie müssen alle Ihre Follower in eine neue Instanz verschieben. Es 
war weniger zensurresistent als Twitter.

Also dachte FiatJeff: „Lass es uns einfacher machen.“ Anstatt sich darauf zu verlassen, dass Ihre Identität an einen Server 
gebunden ist, ist Ihre Identität nur ein privater Schlüssel. Sie veröffentlichen einfach Nachrichten, die mit Ihrem 
Schlüssel signiert sind, an 5 oder 6 oder 10 oder 100 Relais. Diese Relais sind dumm und akzeptieren nur Nachrichten 
jeglicher Art, die von verschiedenen Personen signiert sind. Auf diese Weise laufen Sie nicht Gefahr, von einem einzelnen 
Server gesperrt zu werden, denn wenn Sie von einem gesperrt werden, befinden sich Ihre Nachrichten auf 6 anderen Relais und 
Sie können weitermachen. Es ist wirklich einfach, Ihre Nachrichten zu übertragen, indem Sie sie einfach von einem Relais zum 
anderen kopieren. Es ist eine wirklich einfache Idee, eine zensurresistente dezentrale Datenbank aufzubauen, die für viele 
verschiedene Dinge verwendet werden kann, wie z. B. Schachengines.

Die wichtigste Eigenschaft ist, dass es sich nicht um eine Blockchain handelt. Diese Besessenheit, alles auf eine Blockchain 
zu setzen, ist lächerlich; Wir haben wirklich effiziente Datenbanken wie Postgres und SQLite. Warum muss alles ein 
unveränderliches Hauptbuch sein? Es ist einfach albern. Glücklicherweise hat Nostr dieses Leiden nicht.


### Nostr ist eine offene Datenbank, 
unterscheidet sich jedoch von Datenbanken, die Sie im Internet finden würden. Normalerweise sind Datenbanken, die Sie im Internet 
finden, sehr gesperrt, und Sie können die Daten nicht einfach herunterladen und verlassen. Mit Nostr können Sie die Daten 
herunterladen, und der Server kann Sie nicht daran hindern, zu gehen. Sie laufen auch nicht Gefahr, dass der Server ausfällt, 
da sich die Daten auf mehreren Relays befinden.

Nostr definiert eine sehr einfache Möglichkeit, die Datenbank abzufragen. Sie können sagen: „Hey, geben Sie mir alle Beiträge 
aus dem Pub-Schlüssel dieses Benutzers“, und es wird in Echtzeit zu Ihnen gestreamt. Es verfügt über eine WebSocket-Komponente, 
mit der Sie beispielsweise Chatrooms erstellen können. Sie können sagen: „Hey, abonnieren Sie den Chatroom“, und dann erhalten 
Sie alle Nachrichten in diesem Chatroom in Echtzeit. Es handelt sich also um eine Echtzeitdatenbank mit einer gut definierten 
Schnittstelle zum Abfragen und Einfügen von Daten in die Datenbank.

Die Daten werden auf den Relais gespeichert, und der Client (wie Damus) spricht mit den Relais und weiß, wie er mit der 
Datenbank interagieren muss. Sie müssen keinen Knoten ausführen. Dies ist ein weiteres wichtiges Prinzip von Nostr: Um an 
Bord zu kommen, müssen Sie nichts ausführen. Sie sagen einfach: „Ich werde alle meine Nachrichten an diese 10 Relais senden“, 
und ständig tauchen neue Relais auf.

Es gibt einen Anreiz für jemanden, ein öffentliches Relay zu betreiben, weil es eine ziemlich große Datenbank wäre. Heutzutage 
sind dies jedoch nur kleine JSON-Blobs in Bezug auf den Datenumfang, sodass es nicht schwierig ist, diese Daten auf einem 
Server zu speichern. Sie können beispielsweise ein Relais auf einem Raspberry Pi betreiben. Sie brauchen nicht viele Ressourcen. 
Der Hauptanreiz für den Betrieb eines Relays ist die Befriedigung, zum Netzwerk beizutragen und eine zensurresistente 
Kommunikation zu unterstützen.


### Hauptunterschiede zwischen Nostr und anderen Lösungen
Um ein Konto zu erstellen, müssen Sie nicht einmal Ihre E-Mail-Adresse oder Telefonnummer eingeben. Sie können einen beliebigen 
Benutzernamen festlegen und erhalten dann einen Schlüssel. Dann sind Sie im System. So einfach sollte es sein.

Wenn Sie Nachrichten an all diese Relais senden, können Sie effektiv garantieren, dass Sie nicht vom gesamten System ausgeschlossen 
werden. Ihre Freunde müssen jedoch denselben Satz von Relais verwenden, sonst erhalten Sie ihre Nachrichten nicht. Es ist kein 
Peer-to-Peer-Netzwerk, in dem alle Nachrichten an alle Knoten gesendet werden, aber das macht es tatsächlich flexibler.

Wenn Sie beispielsweise ein Relay für Ihr eigenes Unternehmen betreiben, könnte es durch eine Firewall geschützt und nur innerhalb 
Ihrer Organisation zugänglich sein. Dann könnte jeder in Ihrem Unternehmen Nachrichten an dieses Relay senden, und nur Ihr Client 
kann diese Nachrichten sehen, weil Sie damit authentifiziert oder mit einem VPN verbunden sind, das nur dieses Relay sehen kann. 
Sie könnten auch ein privates Nostr-Relay auf Ihrem WireGuard VPN zu Hause betreiben und Echtzeit-Benachrichtigungen über 
Zahlungen und andere Ereignisse erhalten.

Nun, zuerst einmal möchte ich, dass das gelingt, weil ich finde, dass es eine wirklich coole Idee ist. Das ist für mich kein 
ausreichender Grund, aber es gibt einige Relays, die etwas gegen Spam tun können. Wenn der Spam zum Beispiel zu schlimm wird, 
können Relais sagen: „Hey, wenn Sie eine Nachricht an mein Relais senden möchten, müssen Sie diese Blitzrechnung vielleicht 
einmal im Monat bezahlen.“ FiatJeff hat tatsächlich ein Beispiel dafür, das als „teures Dash-Relais“ bezeichnet wird. Es wird 
Ihnen eine Blitzrechnung geben, und dann haben Sie die Erlaubnis, diese Weiterleitung zu senden.

Wenn Sie Spam-bewusst sind, möchten Sie vielleicht nur eine Verbindung zu bezahlten Relays herstellen. Spam ist ein Problem im 
Netzwerk, und es werden eine Reihe verschiedener Ansätze in Betracht gezogen, wie z. B. Proof-of-Work und bezahlte Relay-Optionen. 
Ich habe ein paar Ideen, wie man ein „Orangen-Scheck“-System haben kann, bei dem man einen Orangen-Scheck kauft und dann Leute 
blockiert, die Orangen-Schecks kaufen und im Laufe der Zeit spammen.

Eine andere Möglichkeit, Geld zu verdienen, besteht darin, Damus (das Domus-Relais) zu bezahlen und einen orangefarbenen Scheck zu 
erhalten, was nur eine Nostr-Nachricht ist. Kunden können diese orangefarbenen Schecks herunterladen und sie als Spam-Schutz verwenden. 
Es gibt viele verschiedene Ansätze zur Bekämpfung von Spam und Monetarisierung in Nostr.


### Was ist mit dem Lightning-Netzwerk?
William Casarin, den wir bereits am Anfang des Posts erwähnt haben und der Damus baut, ein Projekt, das das Nostr-Protokoll 
verwendet, das es Benutzern ermöglicht, Nachrichten zu senden und Aktionen wie das „Gefällt mir“ von Posts durchzuführen, 
erwägt die Verwendung des Protokolls, um Benutzern das Senden zu ermöglichen Blitztipps im Netz. Bleiben Sie dran, da sich 
das Thema noch entwickelt und das Protokoll flexibel und offen für jeden ist, neue Funktionen vorzuschlagen und hinzuzufügen.


