Teil von [[Interprozesskommunikation]]
- Was ist ein Beispiel für Semaphoren?
	- An der Tür steht eine Zahl
	- Wenn "0", "schlafen", bzw. hinsetzen
	- Niemand darf bei "0" rein.
	- Es kommt jemand raus, Zahl wird um eins erhöht, alle in der Warteschlange werden aufgeweckt
	- Eintritt durch die Tür, Zahl wird dekrementiert
- Wie ist der Aufbau eines Semaphoren?
	1. Zähler 
		- Anzeige, wie viele Prozesse in den kritischen Bereich noch dürfen 
		- Initialwert bei 1 → Binärer Semaphor 
	2. Prozesswarteschlange 
		- Enthält alle Prozesse, die aufgrund des Semaphors blockiert sind 
	3. down()-Funktion (vor dem Eintritt in den kritischen Bereich) 
		- Überprüft den Zählwert 
		- count == 0 → Blockierung und Eintragung in die Warteschlange 
		- count > 0 → Dekrementierung (count = count – 1) und Eintritt in den kritischen Bereich 
	4. up() - Funktion (beim Verlassen des kritischen Bereiches) 
		- Inkrementierung (count = count + 1) 
		- Ein oder alle Prozesse der Warteschlange werden geweckt (abhängig von konkreten Implementierung) 
		- Wecken aller Prozesse → Bessere Berücksichtigung von Wichtigkeiten
	- Hinweis:
		- down() und up() sind atomare Funktionen
		- Kein Interrupt und kein Bus
- Wie werden Semaphoren angewandt?
	- Je Randbedingung (constraint) ein Semaphor
	- Zwei Typen von Semaphoren sind möglich (binär und Zähler)
- Was ist ein Beispiel für Semaphoren?
	Deklaration
	```C
	semaphor mutex1=0; 
	semaphor mutex2=1;
	```
	Prozess 1
	```C
	while( TRUE ) 
	{ 
		down(&mutex1); 
		do_your_job_1(); 
		up(&mutex2); 
	}
	```
	Prozess 2
	```C
	while( TRUE ) 
	{ 
		down(&mutex2); 
		do_your_job_2(); 
		up(&mutex1); 
	}
	```
- Was ist das Erzeuger-Verbraucher-Problem?
	- "Problem des begrenzten Puffers"
	- Analyse der Randbedingungen:
		- Nur eine Person darf vor dem Automaten stehen
		- Nur N-Elemente dürfen in den Automaten rein
		- Es darf nur N-Leerstellen im Automaten geben
	- -> drei Semaphoren (1 binärer, 2 andere)
