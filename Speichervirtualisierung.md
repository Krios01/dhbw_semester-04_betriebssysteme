- Was ist das Konzept des virtuellen Speichers aus Prozesssicht?
	- Adressraumaufteilung eines Programms in Seiten 
	- Seiten sind aneinander angrenzende Bereiche von Adressen 
	- Seiten werden physikalischen Speicher zugeordnet 
		- hier nicht unbedingt angrenzende Bereiche 
	- und nicht alle Seiten zwingend im physikalischen Speicher 
		- demnach Handlungsbedarf bei Zugriff auf Seite ohne Entsprechung im Hauptspeicher
- Was ist "Paging"?
	- Prozesse sehen virtuellen Speicher / virtuelle Adressen 
	- Hauptspeicher kennt physikalische Adressen 
	- Ziel: Speicherzugriff verlangt Abbildung von virtueller nach physikalischer Adresse 
		- Hardwareunterstützung: MMU (Memory Management Unit)
- Wie funktioniert die Aufteilung der Adressräume in Blöcke fester Größe?
	- Seite (page): Block mit virtuellem Adressraum 
	- Seitenrahmen (pageframe): Block mit physikalischem Adressraum 
	- Seitengröße und Seitenrahmengröße gleich 
	- typische Größe: 512B bis 64 KiB (auf jeden Fall 2er Potenz)
- Was ist für die Erstellung und Verwaltung von Seitentabellen zuständig?
	- Betriebssystem erstellt und verwaltet Seitentabelle
	- Übersetzung von Seite nach Seitenrahmen, falls existent
- Wie funktioniert das Übersetzungsprinzip bzgl. der Datenströme?
	1. virtuele Adresse an MMU
	2. wenn Abbildung möglich -> Zugriff auf physikalische Adresse
	3. wenn Seite mit der Adresse nicht im RAM
		- Seitenrahmenanforderung von der Festplatte
	4. neuer Seitenrahmen kommt auf RAM und anderer wird ausgelagert
- Wie funktioniert der allgemeine Ablauf (ohne page fault)?
	1. Prozess greift auf (virtuelle) Adresse zu
	2. MMU bestimmt Seite der virtuellen Adresse
	3. durch Seitentabelle: Bestimmung des Seitenrahmens
		- kein Fehler (page fault), wenn Zuordnung existent
	4. MMU: Umwandlung in physikalische Adresse
	5. MMU-Zugriff auf physikalische Adresse zum Lesen oder Schreiben
- Wie funktioniert der allgemeine Ablauf (mit page fault)?
	1. Prozess greift auf (virtuelle) Adresse zu 
	2. MU bestimmt Seite der virtuellen Adresse 
	3. durch Seitentabelle: Bestimmung des Seitenrahmens 
		- Fehler (page fault), da Zuordnung jetzt nicht existent 
		- Nachladen erforderlich 
	4. Betriebssystem: Verschiebung eines Seitenrahmens aus dem RAM auf Festplatte 
	5. Betriebssystem: Verschiebung des gewünschten Seitenrahmens in den RAM 
	6. Betriebssystem: Änderung der Seitentabelle 
	7. Nochmaliges Ausführen des Befehls
- Wie arbeitet die MMU?
	1. virtuelle Adresse "eingelesen"
	2. Präfix wird genommen und in Seitentabelle korrespondierende Zeile gesucht
	3. Seitenrahmen Präfix aus Zeile wird genommen und mit Offset der Adresse kombiniert
	4. physikalische Adresse "ausgegeben"
- Was ist das Modified-Bit (Dirty Bit)?
	- wurde die Seite geändert?
- Was ist das Referenced-Bit?
	- wurde in letzter Zeit auf Seite zugegriffen?
	- Bit wird regelmäßig wieder auf 0 gesetzt
