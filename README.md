# Überblick: 
Wir wollen uns zwei wichtigen Aspekten der Informatik 
• Nebenläufigkeit (Multithreading) UND 
• Netzwerke (Networking) 
auf spielerische Weise nähern. Da AI Code Assistants heute ein gebräuchliches Werkzeug in 
der Softwareentwicklung sind, wollen wir natürlich dieses einsetzen können, aber in sehr 
gezielter Art und Weise ohne orientierungsloses ‘Vibe Coding’. 
Thema: 
Die Algorithmen in den folgenden Aufgaben sind einfach, d.h. dass sie auf einfachen Regeln 
basieren, die immer wieder angewandt werden. Anders formuliert: die Regeln werden auf ein 
Ausgangsmuster angewandt, geben ein neues Muster und werden immer und immer wieder 
auf die entstehenden Muster angewandt (Generation für Generation sozusagen). Oft 
erzeugen solche Generationensysteme interessante und überraschende Muster. 
Der Komax-Käfer ist ein schönes Beispiel dafür, dass ein einfaches System mit einfachen 
Regeln sowohl komplexe chaotische als auch komplexe geordnete Strukturen aufbauen 
kann, und das ganz ohne die Verwendung des Zufalls.
Regeln: 
Ein Käfer sitzt auf einem großen weißen, quadratisch kariertem Blatt Papier (also ein 
Schachbrett mit bloss weissen Feldern), und blickt in Richtung eines Nachbarfeldes. Wenn 
das Feld, auf dem er sitzt, weiß ist, dann färbt er es schwarz, dreht sich um 90 Grad nach 
rechts, und geht auf das nächste Feld. Wenn das Feld, auf dem er sitzt, schwarz ist, dann 
färbt er es weiß, dreht sich um 90 Grad nach links, und geht auf das nächste Feld. Das 
waren dann auch schon alle Regeln. 
Der Käfer soll nach Süden (unten) starten. Immer. 
Wer nun glaubt, es werde langweilig, der irrt sich!
Aufgaben: 
Die Aufgaben sind als Win32 Applikation mittels C# / .NET im Backend und passender 
Grafikausgabe zu lösen. Fürs Frontend ist die Technologie von euch selbst zu bestimmen. 
Wichtig ist einfach, dass wir am Schluss zwei Applikationen haben. Eine als Server (das 
Backend mit passender API) und den Client (das Frontend, das die API verwendet). Das 
Ganze speichern wir in einem «privaten» Gitlab-Repository, worauf ihr dem Aufgabensteller 
Zugriff geben solltet (für Reviews). Das Repo heisst MyKomaxKaefer
MULTITHREADING
1) Programmiere einen Käfer, welcher obiges Verhalten an den Tag legt. Nimm dazu eine 
Matrix mit den Ausdehnung n x m Zellen. Jede Zelle der Käferwelt wird durch einen 
Bildschirm-Punkt / resp. gezoomt durch eine Punktwolke von n x n Pixeln (n=1..5) 
dargestellt. Der Käfer startet wie erwähnt auf einem komplett weissen Papier, beim 
Erreichen des Feldrandes gibt es einen Wrap (Umbruch) auf die gegenüberliegende 
Seite. 
a) Programmiere die Regeln und die Bildschirmausgabe für ein 300 x 300 Feld. 
b) Biete eine Funktion an, verschiedene Ausgangsmuster für die Käferwelt zu wählen 
(z.B. ein Schachbrettmuster oder ein zufälliges Muster) 
c) Biete eine Funktion an, dass der Käfer ein Feld nicht einfach schwarz einfärbt, 
sondern pro Käfer eine Farbe wählen lässt. Jeder Käfer besitzt dann seine eigene 
Farbe, wo er die Regel für die Farbe ‘schwarz’ anwendet, alle andersfarbigen Felder 
(weiss & Farbkleckse anderer Käfer) werden gemäss Regel für ‘weiss’ gehandhabt. 
Daniel Emmenegger Seite 2 13.08.2026 
2) Programmiere zwei Käfer, die in derselben Welt an zufälligen Startpunkten zu laufen 
beginnen und sich gegenseitig beeinflussen können. 
a) die Schritte für beide Käfer werden gleichzeitig gestartet und im selben Durchlauf 
berechnet. 
b) Die Käfer können beliebig neu erzeugt werden und bewegen sich völlig unabhängig 
voneinander 
c) Versuche dasselbe wie in 2b) mit "verschiedenfarbigen" Käfern 
3) Programmiere zwei (oder mehrere) Käfer die in zwei (oder mehreren) unterschiedlichen 
Fenstern, leben und jeweils für sich herumlaufen (sog. MDI-Applikation) 
4) Programmiere mehrere Käfer pro Welt in mehreren Welten (Fenstern), die wie in 2b) ihr 
Unwesen treiben also sich gegenseitig beeinflussen.
NETWORKING
5) Entwickle ein Protokoll, dass ein solches Käferprogramm auf zwei unterschiedlichen 
Rechnern läuft (daher Backend und Frontend Applikation). Ein PC verwaltet die Welt, der 
andere zeigt diese nur an. Ich kann aber Käfer anlegen und auch wieder löschen. Ich 
kann den Client auch mehrfach auf weiteren PCs starten, und sehe immer die gleiche 
Welt (mit all seinen Käfern). D.h. die Daten aller Käfer (Positionen) sowie das aktuelle 
Spielfeld müssen auf den Clients (nach jedem Käfer-Schritt) synchronisiert und grafisch 
up-to-date gebracht werden. 
6) Knacknuss Varianten 
a) Knacknuss Teil 1: Implementiere auch Variante 3 (mehrere Käfer (fixe Anzahl z.B. 5) 
werden pro Rechner gestartet, in 5 von 10 Fenstern laufen einfach die Käfer des 
Nachbarrechners) 
b) Knacknuss Teil 2: Implementiere auf Variante 3 mit einer beliebigen Anzahl Käfer pro 
Rechner (Protokoll muss dynamisch sein, da der Nachbarrechner immer wieder neue 
Käfer erzeugen kann! Allerdings können die einzelnen Fenster für sich up-to-date 
gehalten werden, d.h. eine kleine Verzögerung des Fenster-Refreshs ist erlaubt, weil 
pro Welt ja nur ein Käfer unterwegs ist) 
c) Super-Knacknuss: Variante 4 (bracht sehr komplexes Protokoll, da sehr viele Daten 
gleichzeitig ausgetauscht werden müssen um die verschiedenen Käfer, die zwar auf 
unterschiedlichen Rechnern berechnet werden, aber in derselben Welt herumlaufen, 
korrekt synchronisieren zu können) 
Tipps: 
• Versuche bereits bei Variante 5, nicht alles für die Knacknussaufgaben aus Aufgabe 
6 zu verbauen 
• Versuche möglichst wenig Daten übers Netz auszutauschen, dass es theoretisch 
auch mit hunderten parallel herumlaufenden Käfern funktionieren könnte und die 
Netzauslastung dabei eine ungeordnete Rolle spielt