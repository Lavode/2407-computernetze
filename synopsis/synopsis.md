# Rechnernetze und Kommunikationssysteme

## Kommunikationssytem:

- Erlaubt austausch von Daten zwischen entfernten
  Anwendungen / Benutzern.
- Ziele:
  - Gemeinsame Resourcennutzung
  - Redundanz
  - Beschleunigung
- Tradeoffs: Datenverlust / Datendurchsatz / Verzögerung

## Eigenschaften

- Form: P2P, Broadcast, Multicast
- Richtung: Simplex, Halbduplex, Vollduplex
- Ausdehungen:
  - 1m: PAN
  - 10m-1km: LAN
  - 10km: MAN (metropolitan)
  - 100km-1000km: WAN
  - 10000km: GAN (global)
- Bandbreite: Anzahl übertragener Bits in Zeiteinheit (!= Frequenzbandbereich)
- Durchsatz: Gemessene Leistung (Einbezug Verzögerung)
- Verzögerung, Zuverlässigkeit, Realisierungsaufwand, 

## Schichtenmodell

- N-Instanz erbringt N-Dienst, stellt ihn N+1-Instanzen zur Verfügung.

## Dateneinheiten

TODO: Img

## Dienstprimitive

- Anforderung / Request: Aktivierung Dienstleistung durch Nutzer
- Anzeige / Indication: Anzeige (auf Remote) dass Dienstleistung angefordert
- Antwort / Response: Quittierung der Anzeige durch Benutzer
- Bestätigung / Confirmation: Quittierung der Anforderung durch Anbeiter

## Dienste

- Bestätigt (mit Response/Confirm), unbestätigt (ohne) (Response???)
- Verbindungslos / Verbindungsorientiert

## Schichtenmodell / Internet Protokoll

TODO: Img


# Sicherheit

- Vertraulichkeit: Nur Berechtigte dürfen lesen
- Authentizität: Identität sichergestellt
- Integrität: Nur durch berechtigte modifiziert
- Operationelle Sicherheit: Funktionen in Org nicht beeinträchtigt

## Angriffsmethoden

- Passiv: Abhören, Analyse
- Aktiv: Masquerading (Identität vortäuschen)
- Replay
- Modifikation
- DoS

## Symmetrische Verschlüsselung

- zB AES
- Angriffe: Kryptoanalyse, Brute-Force

## Asymmetrisch

- Problem: Identität nicht implizit (durch Kenntniss d Schlüssels)
  sichergestellt.
- Rechenintensiv

TODO: img

## Integrität

- Digitale: Signatur + Zertifikat zwecks Verifikation öffentlicher Schlüssel:
  - Sender *entschlüsselt* Nachricht mit privatem Schlüssel
  - Empfänger *verschlüsselt* Signatur mit öffentlichem Schlüssel -> Erhält
    Nachricht
  - Stellt sicher dass Nachricht von Sender, da nur er Kenntniss des privaten
    Schlüssels.
- Message digest: Alternative, da Signatur der ganzen Nachricht evtl zu komplex
  - Signatur eines Fingerabdrucks (Message Digest, zb hash) der Nachricht

## Diffie Hellman Key Exchange

TODO: img

# Übertragungsmedien

- Leitungsgebundene vs nicht-leitungsgebundene Medine
- Probleme: Rauschen, Dämpfung, Zeitliche Verzerrung

## Rauschen
- Temp. Abhängig, durch Menschen verursacht (elektrostatisch)

- Signal to Noise: SNR = 10 * log(10, S/N)
  - Erhöhung SNR durch stärkeres Signal
  - dBm: Dämpfung/Verstärkung (G) in Vergleich zu Refernzgrösse 1 mW: G = 10 * log(10, P[mW] / 1[mW])

- Nyquist Theorem: Max D-Rate für Kanal mit Bandbreite B: D = 2 * B * log(2, M)
  - M: Diskrete Signalstufen (zB binäres Signal => 2)
  - Bandbreite d Kanal (Hz)

- Shannon'sche Kapazitätssatz:
  - Max Bitrate C = B * log(2, 1 + S/N)
  - zB SNR = 30 dB; B = 3000 Hz; => S/N = 1000 => C = 30000 bit/s

## Dämpfung

TODO: img

## Leitungsgebundene Medien

### Kuferdrahtpaare:

- UTP: Unshielded twisted pair (Mehr Verdrillung ~ Mehr besser)
- STP: Abschirmung, teuer, aber weniger Einfluss auf / von Umwelt

### Koaxialkabel:

- Frequenz bis 500 MHz bis 10km, kurze Distanzen bis 750Mhz
- Fehlerw'keit 10^-7

### LWL

TODO: img brechung

- Multimode: Verschmierung d Signals (aber höhere Kapzität)
- Monomode: Wenige Wellenlängen, nur 'gerade' Ausbreitung, lange Distanzen mgl, teurer

TODO: img LWL

## Nicht-Leitungsgebunden

- Optisch: Infrarot
- Funk

### Infrarot

- ~ 15m
- Absorption Wände
- Line-of sight (geringe Leistung), diffus (hohe Leistung)

### Optische Freiraumübertragung (Laser)

- Bis 1 Gbit/s
- Wenige 100m

### Funk

- Hohe Frequenz folgt kurze Reichweite
- lambda = c / f; Wellenlänge lambda, Frequenc f, Lichtgeschwindigkeit c = 299 * 10^6 m/s

TODO: img funk

### Satelliten

- Uplink & Downlink häufig verschidenene Frequenz
- Geostationär vs LEO/MEO

# Bitübertragung

- Mechanischen, elektrischen, ... Eigenschaften um physikalische Vrb zwischen
  DEE und DÜE aufzubauen, aufrechtzuerhalten, und abzubauen.

TODO: img physikalische Schicht

## Diskretisierung

TODO: img diskretisierung

- Zeitkontinuerlich -> Diskret: Abstatung
- Wertkontinuerlich -> Diskret: Quantisierung
- Ziel: Rekonstruierbarkeit bei Empfänger
- Abtasttheorem: Für fehlerfreie Rekonstruktion muss f_A > 2 * f_S
  - f_A: Abtastfrequenz
  - f_S: Höchste Grezfrequenz in Quellsignal
- Quantisierungsfehler ist kleiner als a/2 (a Breite des Quantisierungsintervalls)

### PCM

- f_A = 8 kHz (gem. Theorem wäre 6.8 kHz ausreichend)
- 256 Quantisierungsintervall -> 8 Bit
- => Bitrate = 64 kbit/s

#### Quantisierung

- Gleichförm: Gleiche intervalle, Probleme:
  - Fehler sind bei kleinen Signalwerten mehr bemerkbar
  - Feine Unterschiede bei tiefen Signalen relevanter
- Logarithmisch:
  - Behebt Probleme oben

## Signale zwecks Datenübertragung

- Basisband: Direkte Übertragung des rechteckigen Quellsignals
- Breitband: Modulation
- Baudrate: [1/s], Anzahl Zustandswechsel d Signal
- Bitrate: Anzahl übertragene Bitstellen [bit/s]
- Falls jeder Schritt 1 Bit: Bitrate = Baudrate
  - Sonst: zB 2B1Q => 2 Baud, 4 Bit/s

TODO: img Leitungscode

### Breitbandmodulation

TODO: img Modulation

## Multiplexing

- Zusammenfassen von versch Kanälen auf einem Übertragungsweg
- Raum / Zeit / Frequenz / Code
- Erlaubt, ungenutzte Frequenzbereiche anderer Netze für Datenübertragung zu
  verwenden, zB Daten via Koax, Powerline, ADSL, ...
  - Bsp ADSL: POTS nutzt 0-20 kHz, Upstream 25-200, Downstream 200-1000

TODO: img multiplex

## Bitsynchronisation

- Asynchron: Anfange/Ende von Sender markiet (zB Präambel)
- Synchron: Permanente Synchronisation d Frequenzen via zB Taktsignal oder Code
  mit Taktrückgewinnung
- Ethernet: 
  - Präambel bestimmt Sendetakt
  -  Start-Frame-Delimiter zeigt Beginn der Daten
  -  Codierung erlaubt Taktrückgewinnung

# Medienzugriff

## Zugangskontrolle

- Fest: ISDN-B: SDH/SONET Nachrichten
- Variabel
  - Dezentral: Ethernet, WLAN DCF
  - Zentral: WLAN PCF

## Ethernet

TODO: img ethernet

- 10 Base 5: Koax, max 500m
- 10 Base 2: Dünnes Koax, max 200m
- 10 Base T: UTP, max 100m
- 10 Base F: LWL

### CSMA/CD

TODO: img CSMA

### History

- Fast Ethernet
  - 1995
  - 100 Base T/TX/T4/FX
  - CSMA/CD
- Gigabit Ethernet
  - 1999
  - 1000 Base X
  - 25-100m (KOAX), 55m (Multimode LWL), 5km (Monomode LWL)
  - CSMA/CD
  - 8B10B
  - 512 Bytes min. frame size
- 10-Gigabit Ethernet
  - 2002
  - Auto-negation d Geschwindigkeit
  - Monomode LWL bis 40km oder
  - Multimode LWL (weniger) oder
  - 4 Paare UTP6
  - Meist 64B66B
- 100-Gigabit Ethernet
  - 2010
  - Lanes: Aufteilung Daten in 66-Bit Worte, Verteilen (round-robin) auf
    mehrere 4, 10, ... Spuren
  - Kupfer, Multimode, Monomode
- 200/400 Gigabit Ethernet
  - 2017
  - Mehrere Fasern / Wellenlängen pro Faser
  - Multimode (100m), Monomode (10km)
  - Fehlerbehebung durch Kodierung

## WLAN 802.11

TODO: img wlan

### CSMA/CA

TODO: img CSMA/CA

### Probleme Drahtlos

- Hidden Node: Empfänger ausserhalb Fk Bereich
  - RTS/CTS (Ready to send / clear to send)

TODO: img hidden node

### Sicherheit

- ESSID: In Cleartext in zB Mgmt Frames
- MAC Addresse: Spoofing, Konfigurationsaufwand
- WEP: Shared secret (aber unsicher)
- IEEE 802.11i: Periodische Schlüsseländerung
- IEEE 802.1X: Radius

# Sicherung

- HDLC: Austausch von Bf und Mld zwischen Leit- und Folgestationen
  - Aufforderungsbetrieb: Folgestation sendet nur nach Aufruf (Polling)
  - Spontanbetrieb: Folgestation kann jederzeit Mldg an Leitstation senden
  - Gleichberechtigter Spont Betr: Hypridstationen dürfen jederzeit Mld und Bf
    übermitteln

## Rahmenerkennung

### Bit stuffing

- Ausser bei Flags fügt Sneder nach jedem fünften 1 eine 0 ein
- Empfänger löscht diese

### Character (Byte) stuffing

- \DLE: Zeigt Steuerzeichen an
- \STX: Xstart of Text, \ETX: End of text
- Literal \DLE: \DLE\DLE
  - Bsp: PPP

### Prüfsummen

- Bsp ATM: HEC Erkennung

TODO: img atm hec

### Zählen

- Bsp SONET

### Coderegelverletzung

- Bsp 4B5B: Nutzt 16 von 32 Codewörtern
  - Ungültige zeigen Beginn/Ende eines Rahmens

## Fehlerkontrolle

- Erkennung:
  - Verlust / Duplizierung Dateneinheit
  - Abweichung Empfangsreihenfolge
  - Bit-Swaps

- Korrektur:
  - Negative Quittung -> Falsch empfangen oder Timeout, erneutes Senden
  - Vorwärtsfehlerbehebung: Falls Code erlaubt
  - Hamming Codes: h(C): Min Abstand d Code C. h(C) = d + 1 -> Bis zu d Fehler
    erkennbar, h(C) = 2e + 1 -> Bis zu e fehler korrigierbar.

### Prinzip

- Ergänzen der Codes um redundante Informationen, so dass gültige Wörter mehr
  als 1 Zeichen unterschied

### Fehlererkennend

- Paritätsbit
  - Längs/Querparität (Gerade/Ungerade Anzahl 0/1)
- Prüfsummen (Internet-Prüfsumme)
  - Weniger robust als CRC
  - Basiert auf Einerkomplement
  - Einfach zu implementieren

#### CRC

TODO: img CRC 

- Einzelbitfehler: G(x) = x^i + x^j: Erkennt alle 1-Bit Fehler
- Zweibitfehler: G(x) so dass nicht durch x teilbar, und kein Teiler von x^k +
  1, dann alle Zweitbitfehler erkannt.
  - Bsp: x^15 + x^14 + 1 nicht Teiler von x^k + 1 für k kleiner 32'768
- Ungerade Anzahl: G(x) mit Faktor x+1 erkennt alle Fehler mit ungerader Anzahl
  an Fehlern
  - CRC-12: x^12 + x^11 + x^3 + x^2 + x + 1
- Burst-Fehler: Gen Pol mit r Bits erkennt alle Burst-Fehler deren Länge
  kleiner-gleich r

## Übertragungswiederholung

### Stop-and-wait

- Jedes Paket quittiert, synchron
- Bleibt Quittung aus (Timeout) oder Negativquittung (Fehler): Wiederholung

### Go-Back-N

- Jedes Paket hat Sendenummer
- Bei Empfang Paket N: Quittierung Paket N-1
- Falls Nr von empfangenem Paket zu hoh: Ein Paket verloren -> Reject, retransmit, ack

TODO: img go-back-n

### Selektive Wiederholung

TODO: img selektiv

## Fehlerkorrigierende Codes

- Hamming: Weitere Redundanzinformationen
  - zB Code X, Erkennung & korrektur von Einfachfehlern, oder Erkennung von Zweifachfehlern

TODO: img hamming

## Flusskontrolle

- X-On/ X-Off: Unterbruch/Wiederaufnahme Transfer
- Stop-and-Go
- Fensterbasiert (HLDC)
  - Mit jeder Quittung: Angabe eines Windows (ab quittiertem Element) wieviele
    Pakete bereit zu empfangen
- Ratenbasiert
  - x Pakete / s

TODO: img hdlc_fenster
