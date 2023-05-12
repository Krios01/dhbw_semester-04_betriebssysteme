- Wie sieht der optimale Algorithmus aus?
	- ersetzt die Seite, auf die am spätesten in der Zukunft zugegriffen wird
	- verlangt aber Blick in die Zukunft
	- Nutzung als Referenzalgorithmus
		- Wenn Algorithmus A bis auf 1% an optimalen Algorithmus heranreicht, wie gut könnte ein besserer Algorithmus sein?
- Was ist der Not-Recently-Used Algorithmus (NRU)?
	- Ausnutzung des Referenced- und Modified-Bit (R- und M-Bit)
	- Einteilung in vier Klassen
		1. Klasse 0: nicht referenziert, nicht modifiziert
		2. Klasse 1: nicht referenziert, modifiziert
		3. Klasse 2: referenziert, nicht modifiziert
		4. Klasse 3: referenziert und modifiziert
	- Achtung: Klasse 1 möglich, da R-Bit nach gewisser Zeit immer auf 0 gesetzt
	- NRU-Algorithmus entfernt zufällige Seite aus niedrigsten nicht leeren Klasse
- Was ist unter Demand Paging / Einlagern nach Bedarf zu verstehen?
	- Unter Verwendung bisheriger Seitenersetzungsalgorithmen:
	- Prozessstart erzeugt viele Seitenfehler bis alle Seiten im Speicher sind
- Was ist die Lokalitätseigenschaft?
	- Prozesse neigen je Phase nur auf relativ kleinen Teil der Seiten zuzugreifen
- Was ist der Arbeitsbereich (working set)?
	- Menge der Seiten, die zu bestimmten Zeitpunkt genutzt wird
- Was ist der Page-Frame-Reclaiming Algorithmus?
	- Seitenersetzungsalgorithmus unter Linux
	- Unterscheidung in vier Seitenarten
		- nicht anforderbare (unreclaimable) Seiten
		- auslagerbare (swappable) Seiten
			- Seiten im Hintergrundspeicher
		- synchronisierbare (syncable) Seiten
			- Seiten nicht / noch nicht im Hintergrundspeicher
		- löschbare (discardable) Seiten
	- Arbeit durch Page-Daemon (kswapd)
		- in regelmäßigen Abständen oder wenn mehr Seiten benötigt werden
		- Prüfung, ob genügend Seiten verfügbar sind
		- Clock-ähnlicher Algorithmus, um in Kategorie Seiten zum Verdrängen auszuwählen
