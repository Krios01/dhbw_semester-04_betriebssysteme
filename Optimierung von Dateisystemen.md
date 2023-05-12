- Wie kann ein Dateisystem optimiert werden?
	- Cache
	- Blöcke werden zwecks schnellem Zugriff im Speicher gehalten
		- Speicherzugriff ca. 10 ns
		- Festplattenzugriff ca. 100 MiB/s und 5-10 ms Suchzeit
	- Verwaltung analog Paging möglich
	- Achtung: Änderung zeitnah auf Festplatte speichern
		- Unix - aller 30 Sekunden
		- Windows - bei Änderungen
		- Unterschied aufgrund Historie
			- Entwicklung von Unix aus Hard-Disk-World
			- Entwicklung von Windows aus Floppy-Disk-World
- Welche Problematik besteht bei Dateisystemen?
	- Bsp: Löschen einer Datei (Unix)
		1. Datei aus Verzeichnistabelle löschen
		2. Freigabe der I-Node in die Liste der freien I-Node
		3. Freigabe aller Blöcke in die Liste der freien Blöcke
	- Inkonsistenzen, wenn Systemabsturz bevor Abschluss aller Aufgaben
- Wie beheben Journaling File Systems (JFS) die Problematik von Dateisystemen?
	- Ablaufplan:
		1. Änderungen werden in Datei geloggt und auf Festplatte geschrieben
		2. Ausführung der Aktionen
		3. bei Erfolg: Log-Datei gelöscht
	- im Falle eines Systemabsturzes
		- Operationen befinden sich noch in Log-Datei
		- wiederholte Ausführung der Operationen
	- Design der Operationen:
		- mehrfache Ausführung hintereinander möglich
		- Ergebnis immer gleich (idempotente Operationen)
- Wie kann eine Konsistenzprüfung aussehen?
	- Unix: fsck, Windows: scandisk
	- Zwei Überprüfungsmöglichkeiten: Blöcke und Dateien
- Welche Fälle können bei Konsistenzprüfungen auftreten?
	- Fall 1: ![[Pasted image 20230511104243.png]]
		- alles in Ordnung
	- Fall 2: ![[Pasted image 20230511104312.png]]
		- setze Freiblockeintrag auf 1
	- Fall 3: ![[Pasted image 20230511104342.png]]
		- setze Freiblockeintrag auf 1
	- Fall 4: ![[Pasted image 20230511104415.png]]
		- Kopie von Block 3
		- Eintrag in einer Datei setzen
		- Korrektur des Eintrages auf 1
- Wie funktioniert *Dateienbasierte Konsistenzprüfung*?
	- Erstellung einer Tabelle - nach I-Node-Nummer indiziert
	- Tabelle enthält Infos über Anzahl der Vorkommen in Verzeichnissen
	- Vergleich der Tabelleneinträge mit I-Node internem Zähler
	- bei Abweichung: Angleichung des internen Zählers

