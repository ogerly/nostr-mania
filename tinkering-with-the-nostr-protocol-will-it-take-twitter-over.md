## Am NOSTR-Protokoll basteln. Wird es Twitter übernehmen?
Quelle: https://medium.com/@p2w34/tinkering-with-the-nostr-protocol-will-it-take-twitter-over-74c4bf0fea66 


Die Landschaft der sozialen Medien entwickelt sich ständig weiter und es ist nur eine Frage der Zeit, bis wir Nachfolger 
der derzeitigen Marktführer in diesem Bereich sehen. Nichts hält ewig. Ständig tauchen neue Ideen auf und sorgen für viel 
Aufsehen. Sie erregen oft die Aufmerksamkeit von Branchengurus wie Jack Dorsey , einem der Mitbegründer von Twitter. 
Er hat seinen Glauben an Dezentralisierung und Zensurwiderstand als entscheidende Komponenten der neuen Protokolle, die 
entwickelt werden, lautstark zum Ausdruck gebracht. NOSTR, was für: „Notes and Other Stuff Transmitted by Relays“ steht, 
gehört zu den Projekten, die er (auch finanziell) unterstützt.

Die Einfachheit des NOSTR-Protokolls macht es so überzeugend. Das Ziel dieses Artikels ist es, dies zu demonstrieren, indem er 
mit dem Lesen und Schreiben einfacher Posts experimentiert.

Wir werden uns im weiteren Verlauf mit einfachen JavaScript-Schnipseln helfen, aber es sind keine Programmierkenntnisse 
erforderlich. Alle bereitgestellten Beispiele können mithilfe kostenloser Online-Tools nachvollzogen werden. Bitte bedenken 
Sie, dass dies immer noch ein sich entwickelnder Bereich ist und es einige Ecken und Kanten geben kann, aber mit 
Fortschritt kommt Innovation. Ich hoffe, Sie finden diesen Artikel lehrreich.

Haben Sie keine Angst zu experimentieren. Wenn irgendetwas in diesem Beitrag nicht funktioniert, versuchen Sie, eine 
Alternative zu finden.

Wenn Sie zum ersten Mal von NOSTR hören, sollten Sie einige Grundlagen lesen, bevor Sie sich mit dem Rest des Artikels befassen. 
Um das bereits Geschriebene nicht zu wiederholen, möchten Sie sich vielleicht mit Folgendem vertraut machen:

https://github.com/nostr-protocol/nips für die formale Beschreibung, NIP-01 sollte für den ersten Lesevorgang ausreichen.
https://github.com/nostr-protocol/nostr für eine menschenfreundlichere Erklärung.
https://github.com/aljazceru/awesome-nostr , um eine Liste bestehender Clients/Server anzuzeigen (pardon, Relays im NOSTR-Jargon). 
Ich habe einen anständigen Webbrowser-Client verwendet: Coracle . Einen Versuch wert ist ein iOS- Damus- Client, der sich zum 
Zeitpunkt der Erstellung dieses Beitrags im Testflug befindet.
Beiträge lesen
Als Ausgangspunkt versuchen wir, einen beliebigen Beitrag zu lesen. "REQ"Aus NIPS-01 sehen wir, dass wir ein Ereignis an ein 
Relais senden müssen . Die Kommunikation erfolgt über WebSockets. Machen Sie sich keine Sorgen, wenn Sie mit WebSockets nicht 
vertraut sind. Sehen Sie es als Alternative zu HTTPS. Der Unterschied besteht darin, dass WebSockets eine bidirektionale 
Kommunikation in Echtzeit zwischen einem Client und einem Server ermöglichen. Der einfachste Weg, mit ihnen zu experimentieren, 
ist die Verwendung eines beliebigen Online-Tools wie Websocketking . Wenn Sie mit dem Postman- Tool oder einem Websocat- 
Dienstprogramm vertraut sind , sind diese ebenfalls eine gute Wahl.

Um eine HTTPS-Seite von einem Server abzurufen, benötigen Sie Adressen wie https://.... Ebenso benötigen Sie eine 
WebSocket-'Adresse' in Form von wss://.... Der schnellste Weg besteht darin, es aus einer vorkonfigurierten Liste 
von Relais zu entnehmen, die jeder Client haben sollte. Unter Verwendung des oben genannten Clients und seiner 
Relays-Liste Coracle-Relays können wir versuchen, uns mit dem folgenden WebSocket zu verbinden: wss://bitcoiner.social.

[zurück](https://github.com/ogerly/nostr-mania)
