## Prozessor
- Was ist zeitliches Multiplexing beim Prozessor?
	- Laufende Programme anhalten
	- Status speichern zur späteren Wiederherstellung
	- Neues Programm starten
- Welche Optimierung gibt es bei Prozessoren?
	- Vorbereitung von Berechnungen bevor vorangegangene Berechnungen abgeschlossen sind
- Warum gibt es interne Register zum Speichern von Befehlen oder Daten?
	- Holen eines Befehls oder von Daten dauert gewöhnlich länger als die Ausführung
	- Verkürzen der Zeit durch interne Register
- Welche zusätzlichen Register gibt es?
	- Befehlszähler (program counter)
		- enthält Speicheradressen des nächsten Befehls
	- Kellerregister (stack pointer)
		- zeigt auf Ende des aktuellen Stacks
		- Ablegung von "frames" (Rahmen) für jede angesprungene, aber nicht beendete Prozedur
		- enthält Eingabeparameter, lokale Variablen, ...
	- Programmstatuswort (PSW)
- Welche Statusbits enthält des Programmstatuswort (PSW)?
	- CPU-Priorität
	- Ausführungsmodus (Benutzermodus: user mode, Kernmodus: kernel mode)
	- und andere Kontrollbits
- Warum ist der Ausführungsmodus wichtig für die Sicherheit?
	- Anwenderprogramme nur im Benutzermodus (eingeschränkter Zugriff)
	- Betriebssystem darf Kernmodus-Befehle (alle Befehle des Befehlssatzes) ausführen
	- Kernmodus u.a. Ein- und Ausgaben
- Wie kann Anwendungsprogramm auf die Festplatte zugreifen?
	- durch Systemaufruf (kontrollierter Moduswechsel)
	- alias: Dienst des Betriebssystems wird genutzt
		- Spezieller Befehl (system call, TRAP)
		- Wichtige Infos im Stack abgespeichert
		- Umschalten des Systemmodus
		- Durchführung des Aufrufs
		- Rückkehrbefehl schaltet wieder in Benutzermodus
- Was bedeuten Unterbrechungen für das Betriebssystem?
	- Handlungsbedarf für das Betriebssystem
	- Interrupts (von Hardware erzeugt)
	- Exceptions (Programmierfehler)
## Speicher
- Wie sieht die Speicherhierarchie aus?
	1. Register
	2. Cache (L1, L2, L3)
	3. Arbeitsspeicher (RAM)
	4. Magnetplatte / Festplatte
	5. Magnetbänder
- Was ist transienter Speicher?
	- "flüchtiger" Speicher
- Was ist persistenter Speicher?
	- "dauerhafter" Speicher
## E/A-Geräte
- Woraus besteht ein zweiteiliges E/A-Gerät?
	1. Gerät selbst
	2. Controller - ein oder mehrere Mikrochips zur Steuerung des Gerätes auf der Hardwareebene eingebettete Computer
	- Betriebssystem sieht Schnittstelle zum Controller
- Was ist Betriebssystem-seitig für die Verwendung von E/A-Geräten nötig?
	- Gerätetreiber (device driver)
	- Integration ins Betriebssystem
	- Grund: Zugriff nur im Kernmodus - ergo Treiber Teil des Betriebssystems
- Welche Ein- und Ausgabe - Spielvarianten gibt es?
	1. Anfrage und Warten (busy waiting)
	2. Anfrage mit Aufforderung zum Interrupt
	3. über DMA-Controller (Direct Memory Access)
## Bussysteme
- Wofür sind Bussysteme zuständig?
	- Kommunikation zwischen Hardware
- Worüber läuft die Kommunikation?
	- Bus (Verbindung mehrerer Geräte über gleichen Satz von Leitungen)
	- Direktverbindung, bzw. Point-to-Point-Verbindung
- Wie läuft der Datenaustausch ab?
	- seriell
	- parallel