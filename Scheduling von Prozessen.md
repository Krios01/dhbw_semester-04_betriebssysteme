- Was ist der Scheduler?
	- Unterste Schicht eines prozessstrukturierten Betriebssystems
	- verwaltet: Zeitablauf und Interrupts
- Wofür ist die Prozesstabelle zuständig?
	- liefert Infos über alle Prozesse
	- Prozessverwaltung (Prozess-ID, Elternprozess, Prozessgruppe, Priorität, ...)
	- Speicherverwaltung (Zeiger auf Textsegment, Datensegment und Stacksegment)
	- Dateiverwaltung (Benutzer-ID, Gruppen-ID, Arbeitsverzeichnis, ...)
- Welche Problematiken gibt es beim Scheduling?
	- CPU-lastige Prozesse, rechenintensiv
	- E/A-lastige Prozesse, datenintensiv
- Was ist das Einsatzgebiet einer Stapelverarbeitung?
	- in Geschäftswelt: Banken (Überweisungen), Gehaltsabrechnungen, …
	- meist periodisch auftretende Aufgaben
	- keine ungeduldigen Nutzer
- Was ist das Einsatzgebiet interaktiver Systeme?
	- Desktop-Rechner
	- Personal-Computer
	- Web-Server
- Was ist das Einsatzgebiet von Echtzeitsystemen?
	- meist nur kurze Prozesse
	- zeitkritische Ausführungen (Sicherheitschecks, Multimedia-Systeme - z.B. Abspielung mehrer Videos)
- Welche Unterteilung gibt es bei Echtzeitsystemen?
	- harte Echtzeitsysteme -> absolute Deadlines
	- weiche Echtzeitsysteme -> Abweichungen nicht erwünscht, aber in gewissen Maßen tolerierbar
- Welche Bedingungen gibt es für das Scheduling in Echtzeitsystemen?
	- Laufzeitverhalten der Prozesse bekannt
	- meist kurzlebige Prozesse
	- Unterteilung von Programmen in kürzere Prozesse
- Welche Herausforderungen gibt es für das Scheduling in Echtzeitsystemen?
	- aperiodische Ereignisse
	- periodische Ereignisse (z.B. Multimedia-Systeme)
- Was sind Ziele von Schedulingstrategien aller Systeme?
	- Fairness: fairen Anteil Rechenzeit für jeden
	- Policy Enforcement: Durchsetzung vorgegebener Strategien
	- Balance: Gleichauslastung
- Was sind Ziele von Schedulingstrategien für die Stapelverarbeitung?
	- Durchsatz: max. Anzahl Jobs pro Stunde
	- Durchlaufzeit: min. Zeit zwischen Prozessstart und -ende
	- CPU-Ausnutzung: max. Auslastung der CPU
- Was sind Ziele von Schedulingstrategien für interaktive Systeme?
	- Antwortzeit: schnelle Antwort auf Anfragen
	- Proportionalität: Erwartungen des Benutzers erfüllen
- Was sind Ziele von Schedulingstrategien für Echtzeitsysteme?
	- Deadlines einhalten: Datenverlust vermeiden
	- Vorhersagbarkeit: z.B. Qualitätseinbußen vermeiden
- Wann soll ein Scheduler arbeiten?
	- bei Erzeugung eines Prozesses
	- bei Beendigung eines Prozesses
	- wenn ein Prozess blockiert wird
	- bei Auftreten von E/A-Interrupts
	- Zyklische Interrupts / Timerinterrupts
- Welche Kategorien für Schedulingstrategien unter Voraussetzung eines Timerinterrupts gibt es?
	- nicht-unterbrechend (präemptiv)
		- Prozess rechnet solange bis blockiert oder beendet
	- unterbrechend (präemptiv)
		- Prozess darf nur gewisse Zeit laufen
		- oder Prozess mit höherer Priorität steht an
- Was ist First-Come-First-Served Scheduling?
	- Prozesse nacheinander abgearbeitet
	- nicht-unterbrechende Strategie
	- einfach programmierbar
	- aber: Konflikt bei CPU-lastigen und E/A-lastigen Prozessen
	- für Stapelverarbeitung
- Was ist Shortest-Job-First Scheduling?
	- kürzeste Job wird zuerst abgearbeitet
	- nicht-unterbrechende Strategie
	- Laufzeiten müssen bekannt sein
	- für Stapelverarbeitung
- Was ist Shortest-Remaining-Time-Next Scheduling?
	- Prozess mit kürzester verbleibender Zeit wird abgearbeitet
	- unterbrechende Variante von Shortest-Job-First
	- Überprüfung jedes neuen Prozesses
- Was ist Round-Robin Scheduling?
	- Prozess ist für gewisse Zeit (Quantum) dran oder wird vor Ablauf blockiert oder beendet
	- einfachstes Verfahren bei interaktiven Systemen
	- Round-Robin nicht fair gegenüber E/A-lastigen Prozessen
- Was ist bei der Wahl des Quantums zu beachten?
	- Kurzes Quantum: schneller Prozesswechsel, schlechte Prozessornutzung
	- Langes Quantum: lange Antwortzeiten, bessere Prozessornutzung
	- Herausforderung: Trade-Off finden
- Wie funktioniert Priorität-basiertes Scheduling?
	- Zusammenfassung von Prozessen in Prioritätsklassen
		- innerhalb der Klasse z.B. Round-Robin
	- Verhinderung von ewig laufenden Prozessen
		- Verringerung der Priorität nach jedem Quantum
		- Zuweisung eines maximalen Quantums abhängig von Priorität
	- Priorisierung: statisch oder dynamisch
- Was ist Shortest-Process-Next-Scheduling?
	- Verwendung bei interaktiven Systemen
	- aufgrund Interaktivität -> Laufzeit im Vorfeld nicht bekannt
	- Abschätzung möglich durch Laufzeitmessung
