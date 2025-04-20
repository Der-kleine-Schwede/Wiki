# Client 

# Api/Backend
## Common-Klasse
    Kontext
        Hier sollten Methoden, Klassen und Konstanten untergebracht werden, die von anderen Klassen benutzt werden.
    
    TODO:
        - Klasse Problem aus ProblemSolver sollte hierhin verschoben werden.
        - Klasse Kästchen für ein einzelnes Kästchen in der Kreuzworträtsel-Matrix sollte hier definiert werden. In dieses Kästchen soll unter anderem Info über eingetragene Buchstaben und bei Fragestellungen die Pfeilrichtung und ggf. betroffene Kästchen notiert werden.
        - Klasse für das gesamte Kreuzworträtsel sollte hier definiert sein. Hier sollte eine Zweidimensionale Matrix bereitgestellt werden, die Kästchen beinhaltet.

## Backend-Datenbank
    Kontext
        Eine Datenbank soll bereitgestellt werden, die mindestens folgende Spalten besitzt: Frage aus Kreuzworträtseln, zugehörige Antwort.
        Diese Datenbank befindet sich auf einem Server, auf die über eine Rest-Api zugegriffen wird.
        Falls eine neue Lösung zu einer Frage gefunden wird, etwa weil sie auf einer Website, beim Scrapen, gefunden wird, oder beim manuellen eingeben aus dem Client, dann soll diese Frage mit Antwort in die Datenbank eingetragen werden.

    TODO: 
        - geeignetes Datenbank-produkt auswählen (MySQL, NoSQL, ...) und einrichten, sodass das Backend darauf zugreifen kann.
        - Tabellen und zugehörige Spalten definieren.
        - Datenbank in Klasse Problemsolver einbinden.

## Klasse Problemsolver
    Kontext
        Die Klasse ProblemSolver ist dafür Zuständig eine Antwort für eine Frage aus dem Kreuzworträtsel zu lösen.
        Für die aktuelle Version war folgender Ablauf vorgesehen:
        - ProblemSolver.Solve() bekommt folgende Parameter string question und int expectedLength
        - Solve() sucht auf der Internetseite https://www.kreuzwort-raetsel.net anhand der URL-Parameter nach einer Lösung.
            Hierbei werden möglicherweise mehrere Antwortern geliefert.
        - Die zur URL gehörige HTML wird geladen und geparsed.
        - Gefundene Antworten sollen in eine Datenbank eingefügt werden, damit sie beim nächsten mal oder für andere Fragen zur Verfügung stehen.
        - Eine geeignete Antwort soll aus der Datenbank und aus den, von der Website geparsten Antworten, ausgewählt und zurückgegeben werden.

    TODO:
        - Die Aktuelle Implementation gibt noch kein brauchbares ergebnis zurück. Aus der List<Problem> problems muss noch eine geeignete Antwort ausgesucht und zurückgegeben werden.
        
        - ProblemSolver soll Abstrakt sein und die aktuelle Implementation soll davon erben.
        Somit können alternative Ansätze zur Lösung von einzelnen Fragen implementiert werden.
        Dies ist auch nötig, falls die Internet-Seite https://www.kreuzwort-raetsel.net in Zukunft nicht mehr erreichbar ist oder für dieses Projekt nicht mehr ausreichend ist.

        - Class Problem sollte ausgelagert werden in eine neue Klasse. Da diese Klasse vorraussichtlich von mehreren Klassen benötigt wird, diese Klassen aber möglicherweise nicht die Funktionen aus Problemsolver benötigen.
        Beispielsweise muss die Klasse zum auslesen der Keuzworträtsel-Bilder die Klasse Problem um die eingelesenen Daten bereitzustellen, muss sie aber nicht lösen.

        - Auf der Website https://www.kreuzwort-raetsel.net/ hat man die Möglichkeit eine Frage oder ein Begriff angeben und die erwartete Länge der Lösung. Die Seite listet dann alle möglichen Lösungen auf. Hier sollte recherchiert werden, ob andere Seiten diese Informationen leichter zur verfügung stellen. Etwa durch eine Api, mit der man dieselben Abfragen stellen kann, ohne dass die HTML dafür geparsed werden muss. Alternativ könnte es Seiten geben, die eine ganze Datenbank zum Runterladen anbieten.

# Python

# Plan

# Lessons Learned
- Für jeden Schulblock sollte pro Person ein Ziel gesteckt werden, an dem diese arbeiten wird, welche auch in dem Block erledigt werden sollte. Dabei sollte die Aufgabe so kleinteilig wie möglich definiert werden.

- Zu Anfang wurde zu diesem Projekt ein Klassendiagramm erstellt. Da zwischen jedem Schulblock viel Zeit liegt, in der man nicht an dem Projekt arbeitet, sollte sich strikt an die vorgegebene Doku gehalten werden. Gegebenenfalls kann dazu das Klassendiagramm jeden Schulblock gepflegt werden, an dem man sich im neuen Schulblock orientieren kann.

- Im Verlauf des Projektes kann es vorkommen, dass sich ein benötigtes Arbeitspacket verzögert. Um trotzdem das eigene Arbeitspacket zu testen, sollte falls möglich eine Testklasse für das eigene Arbeitspacket/Klasse gepflegt werden, welche die Ausführung simuliert und passender Parameter bereitstellt.
