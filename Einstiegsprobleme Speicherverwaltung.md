- Wie kann man mehrere Prozesse laufen lassen, wenn nur RAM und keine Speicherabstraktion?
	1. Swapping
	2. Zugriffsverbot (Schlüssel-Schloss-Prinzip)
	3. Statische Relokation
- Was ist Swapping?
	- ein Prozess immer nur im Speicher 
	- lege gesamten Inhalt des Speichers in Festplattedatei ab 
	- nächstes Programm holen und ausführen
- Was ist Zugriffsverbot (Schlüssel-Schloss-Prinzip)?
	- mit spezieller Zusatzhardware 
	- Speichereinteilung in 2-KiB Blöcke 
	- jeder Block 4-Bit Schutzschlüssel in CPU-Register gespeichert 
	- erlaubter Zugriff, wenn Programmstatuswort (PSW) = Schutzschlüssel
- Was ist statische Relokation?
	- Lösung des IBM 360 
	- Annahme: Laden eines Programms an Stelle M 
	- Modifikation: jeder Programmadresse mit M addiert
- Wie kann man mehrere Prozesse mit Speicherabstraktion laufen lassen?
	- Konzept des Adressraums
- Was ist das Konzept des Adressraums?
	- ist Menge von Adressen, die ein Prozess zur Adressierung des Speichers nutzen kann 
	- jeder Prozess mit eigenem Adressraum (ausgenommen beim Teilen eines Adressraums versch. Prozesse) 
	- Adressraumbeispiele: 
		- Menge aller Telefonnummern in verschiedenen Städten 
		- Menge aller de-Internetdomänen 
		- Menge alle Hausnummern in einer Stadt
- Welche Schutzziele existieren bei der Speicherverwaltung?
	- direkten Zugriff auf Speicher vermeiden
	- zum Schutz – keine gegenseitige Beeinflussung 
	- Relokation – zum Ausführen mehrerer Programme
- Was sind Vor- und Nachteile der Speicherabstraktion durch Basis- und Limitregister?
	-  Verwaltung beider Register nur durch das Betriebssystem 
	- Vorteil: Speicherabstraktion gelöst 
	- Nachteil: Jeder Zugriff auf Speicherreferenz erfordert 
		- Addition 
		- Vergleich
- Was geschieht, wenn mehr Prozesse als zugehöriger Speicher vorhanden?
	- Lösung: Swapping 
	- Prozess können komplett auf Festplatte ausgelagert werden
- Wie kann man mit Lücken im Speicher umgehen?
	- Speicherverdichtung (memory compaction) 
	- Bsp.: bei 4 Byte in 20ns => 1 GB in 5 Sekunden
- Wie geht man damit um, wenn Speicheranforderung nicht genau am Anfang bekannt sind?
	- mehr Speicher reservieren als anfangs nötig 
	- beim Auslagern nur genutzten Speicher auslagern 
	- beim Überschreiten: in passende Lücke verschieben oder Prozess unterbrechen bis passende Lücke vorhanden 
	- Hinweis: klassisches Erzeuger-Verbraucher-Problem
- Wie lässt sich der freie Speicher verwalten?
	- Speicherverwaltung mit Bitmaps
	- Speicherverwaltung mit verkettete Listen
- Wie funktioniert die Speicherverwaltung mit Bitmaps?
	- Unterteilung in Belegungseinheiten 
	- jeder Einheit entspricht ein Bit in Bitmap
	- Herausforderungen: 
		- Suche innerhalb Bitmap zweitaufwendig 
		- Größe je Belegungseinheit ist Entwurfsfrage
	- Komplexität: $O(n)$
- Wie funktioniert die Speicherverwaltung mit verketteten Listen?
	- jeder Eintrag der Liste enthält: 
		- P für Prozess, L für Lücke 
		- Startadresse und Länge 
		- Zeiger auf den nächsten Eintrag 
	- Liste sortiert nach Adresse
- Was sind Suchalgorithmen für verkettete Listen?
	- First Fit 
		- vom Anfang an schauen, bis erste ausreichende Lücke 
	- Next Fit 
		- wie First Fit, aber Starte bei zuletzt gefundener Lücke 
	- Best Fit 
		- suche in Gesamtliste kleinste passende Lücke 
		- erzeugt viele, sehr kleine Fragmente 
	- Worst Fit 
		- als Gegenantwort zur starken Fragmentierung von Best Fit
		- verwende den am schlechtesten passenden Bereich 
		- vernichtet große Freibereiche