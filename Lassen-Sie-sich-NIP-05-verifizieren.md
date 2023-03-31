## Lassen Sie sich NIP-05 verifizieren

Sie haben vielleicht bei vielen verschiedenen Clients bemerkt, dass einige Benutzer Überprüfungen haben, genau wie bei Twitter.

NIP-05 legt fest, wie Nostr-Benutzer ihre Identität überprüfen können. Verschiedene Clients zeigen die Verifizierung 
auf leicht unterschiedliche Weise, aber es ist eine wichtige Möglichkeit, der Nostr-Community zu zeigen, dass Sie ein echter 
Benutzer sind.

![image](https://user-images.githubusercontent.com/1324583/229061239-90369534-bd51-41b3-967c-2b0d2418fede.png)


Der Verifizierungsprozess auf Nostr ist in einem Nostr Implementation Possibilities (NIP) namens NIP-05 dokumentiert .

NIP-05 ermöglicht es einem Nostr-Benutzer, seinen öffentlichen Schlüssel einer DNS-basierten Internetkennung zuzuordnen. 
Der Verifizierungsmechanismus ähnelt dem, mit dem Google verlangt, dass Sie Ihren Besitz einer Domain mithilfe eines DNS-Eintrags 
verifizieren.

Der Hauptvorteil der Verifizierung besteht darin, dass ein Nostr-Benutzer durch einen für Menschen lesbaren Namen identifiziert
werden kann, anstatt durch einen langen, schwer zu merkenden öffentlichen Schlüssel. Dies ermöglicht es verifizierten Nostr-Benutzern, 
ihre Identität einfach mit anderen zu teilen.

Um NIP-05 zu verwenden, fügen Nostr-Benutzer ihrem Profil eine nip05-URL hinzu (die meisten Clients unterstützen dies). 
NIP-05-URLs sehen aus wie E-Mails – bob@example.com . Lassen Sie uns die Teile aufschlüsseln:

Alles vor dem @-Symbol ("bob", in unserem Beispiel). Dies muss mit dem Wert des Namensfeldes in Ihrem Nostr-Profil übereinstimmen.
Alles nach dem @-Symbol ("example.com", in unserem Beispiel). Dies ist die Domäne, in der der Client nach 
einer /.well-known/nostr.json-Datei suchen kann, die den Namen und den öffentlichen Schlüssel des Benutzers enthält.
Wenn Clients eine nip05-Url sehen, suchen sie nach einer /.well-known/nostr.json-Datei in der angegebenen Domäne. Diese Datei 
muss den öffentlichen nostr-Schlüssel für den angegebenen Benutzer enthalten. Weitere Einzelheiten finden Sie in der NIP-05-Spezifikation.

Das klingt zwar technisch, ist aber überraschend einfach zu verifizieren. Schauen wir uns an, wie es geht.


### Lassen Sie sich durch einen kostenlosen Dienst verifizieren
Zurzeit gibt es mehrere Anbieter, die den Leuten helfen, sich kostenlos verifizieren zu lassen. Das ist eine gute Möglichkeit, wenn 
Sie noch keine Sats in Ihrer Blitzgeldbörse haben. Wenn möglich, unterstützen Sie diese Projekte durch Spenden. ⚡🤙

[Nostrcheck.me](https://nostrcheck.me/)
[Nostr.Industries](https://nostr.industries/)

### Bezahlen Sie einen Anbieter für die Verifizierung
Wenn Sie keine eigene Domain haben oder sie nicht selbst einrichten wollen, können Sie einen kostenlosen oder kostenpflichtigen 
(in der Regel nur ein paar [Sats](https://coinmarketcap.com/alexandria/glossary/satoshi-sats)) NIP-05-Dienst in Anspruch nehmen. Hier sind ein paar:

[Nostrplebs](https://nostrplebs.com/)
[Nostr Verifiziert](https://nostr.how/nostrverified.com)
[Alby](https://nostr.how/getalby.com)
[Nostr-Verzeichnis](https://nostr.directory/)
[Nostr.band](https://nip05.nostr.band/)
[Nostr.com.au](https://nostr.com.au/)
[Vida](https://vida.page/)
[Stacker News](https://stacker.news/)

Selbst gehostete Überprüfung
Wenn Sie bereits eine Domain besitzen, ist dies eine kostenlose Option. Sie müssen lediglich eine .well-known/nostr.json-Datei 
zu Ihrer Domain hinzufügen. Der Inhalt der Datei sollte wie folgt aussehen:
```
{
  "names": {
    "IHR_NOSTR_NAME": "YOUR_NOSTR_PUBLIC_KEY"
  }
}
```
Kopieren
Kopiert!
Optional können Sie auch einen Abschnitt hinzufügen, um Kunden mitzuteilen, auf welchen Relays sie Sie wahrscheinlich finden werden:
```
{
  "Namen": {
    "IHR_NOSTR_NAME": "IHR_NOSTR_ÖFFENTLICHER_SCHLÜSSEL_IM_HEX_FORMAT"
  },
  "relays": {
    "DEIN_NOSTR_ÖFFENTLICHER_SCHLÜSSEL_IM_HEX_FORMAT": [
      "wss://relay.one",
      "wss://relay.two": [ "wss://relay.two",
      ...
    ]
  }
}
```

Stellen Sie sicher, dass Sie die Hex-Version Ihres öffentlichen Schlüssels in Ihrer nostr.json-Datei verwenden. 
Dies ist die Version des Schlüssels, die nicht mit npub beginnt.

Sie können Ihren Schlüssel auf Nostr.band konvertieren

![image](https://user-images.githubusercontent.com/1324583/229072297-994fc9af-118d-4001-b4eb-5e4c82c04949.png)


