- Welche Software-Anforderungen gibt es für die Ein- und Ausgabe?
	- Geräteunabhängigkeit
	- Einheitliches Benennungsschema
	- Einheitliche Fehlerbehandlung
	- Darstellung als blockierende Aufrufe
		- im Hintergrund meist unterbrechender Aufruf
		- Programm soll schlafen bis Daten da sind und nicht auf Interrupt warten (nicht Busy-Wait)
	- Puffermöglichkeit (Zwischenspeicherung)
	- Unterschiedliche Geräte
		- Shareable devices (z.B. Festplatte)
		- Dedicated devices (z.B. CD-Brenner)
- Welche Ansätze gibt es zur Durchführung von EIn-/Ausgabe?
	1. Programmierte Ein-/Ausgabe
	2. Interrupt-gesteuerte Ein-/Ausgabe
	3. DMA-basierte Ein-/Ausgabe
- Wie funktioniert die Programmierte Ein-/Ausgabe?
	- Sende Auftrag an Controller; Warte auf das Ergebnis 
	- Prinzip: busy wait bzw. polling 
	- Nachteil: Prozessor komplett belegt 
	- aber Nutzung in eingebetteten Systemen
- Wie funktioniert die Interrupt-gesteuerte Ein-/Ausgabe?
	- Beauftragung des Controllers 
	- ggf. Blockierung des auftraggebenden Prozesses 
	- bei Ende des Auftrags: Controller sendet Interrupt 
		- Gerät jetzt wieder bereit 
	- Interrupt-Behandlung 
	- ggf. Aktivierung des auftraggebenden Prozesses 
	- Anwendungsmöglichkeit: bei langsamen E/A-Geräten
- Wie funktioniert die DMA-basierte EIn-/Ausgabe?
	- Datenübertragung über DMA-Controller 
		- Parameter an DMA-Controller: Geräte-Adresse, Startadresse, Länge der Daten und Transferrichtung 
		- Auftragsbeendigung: Interrupt vom DMA-Controller 
	- Programmierte Ein-/Ausgabe … aber über DMA-Controller 
	- Vorteile: 
		- Entlastung der CPU 
		- weniger Interrupts 
	- Achtung: DMA-Controller oft langsamer als CPU
- Wie ist Ein-/Ausgabesoftware strukturiert?
	- Hintergrund: Nutzer will etwas von einem Gerät
	- Einteilung in Schichten
	- Hintergrund:
		- Abstraktionsschicht anbieten
		- vom Speziellen zum Allgemeinen
	- Schichten:
		1. Benutzer-Level E/A-Software
		2. Geräte-unabhängige E/A-Software
		3. Geräte-Treiber
		4. Interrupt-Handler
		5. Hardware
- Was sind die Ziele des *Interrupt-Handlers*?
	- Interrupts verbergen
	- Semaphoren-angelehnter Umgang (down and up)
- Was sind die Aufgaben der *Geräte-Treiber*?
	- Verarbeitung abstrakter Lese- und Schreib-Anfragen
	- Initialisierung der Hardware (Vorbereitung)
- Was ist die Aufgabe der *Geräte-unabhängige E/A-Software*?
	- Bereitstellung der Abstraktionsschicht für Benutzer-Level E/A-Software
- Was sind die Aufgaben der *Benutzer-Level E/A-Software*?
	- Funktionen aus Bibliotheken
		- Schnittstelle zu den Systemaufrufen
		- Formatierung der Ein- und Ausgabe
	- Spooling -> Alternative im Umgang mit Dedicated Devices
		- z.B. Drucker oder Datei-Transfer übers Netzwerk
		- extra Prozess: Daemon
		- spezieller Ordern: Spooling-Ordner