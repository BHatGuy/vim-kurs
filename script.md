# Basics
Navigation mit
- h: links
- j: runter
- k: hoch
- l: rechts

Editieren mit i oder a

Verlassen / Speichern:
- :wq
- :q
- :q!

# Modi

Vim hat verschiedene Modi:

- normal mode
  - Standard Modus nach dem Starten
  - Für Navigation und verschiedene Operationen
  - Erreichbar mit ESC oder ctrl-[
- insert mode
  - Texteingabe wie in normalem Editor
  - Erreichbar mit
    - i, a, c, s, ...
- visual mode
  - Wird zur Auswahl von Text benutzt
  - Erreichbar mit v, V, CTRL-v
- command line mode
  - Zum Ausführen von Kommandos (q, w, etc.)
  - Erreichbar mit :

# Operatoren

Es gibt viele verschiedene Operatoren. Hier eine Auswahl von häufig verwendeten:
- i insert vor dem Cursor
- a insert nach (after) dem Cursor
- d löschen (delete)
- x Zeichen unterm Cursor löschen
- c wie d und anschließend insert
- s wie x und anschließend insert
- r einzelnes Zeichen unterm Cursor ersetzen
- o neue Zeile und anschließend insert
- y Kopieren (yank)
- p Einfügen (put / paste)
- u undo
- CTRL-r redo

d und y  brauchen eine Richtung (siehe Navigation).

Die meisten Operatoren haben Varianten:
- Uppercase Variante
  - I, A, S: der Operator bezieht sich auf die ganze Zeile
  - D, C, Y: bis ans Ende der Zeile
  - X, O, P: andere Richtung
- Doppelte Variante
  - dd, yy, cc: der Operator bezieht sich auf die ganze Zeile

Ein Zahl vor einem Operator führt den Operator n mal aus. 3dl löscht nächsten drei Zeichen.

Der letzte Operator kann mit . wiederholt werden.

# Visual Mode

Der Visual Mode wird zum Auswählen von Text benutzt.
- v: kontinuierliche Auswahl
- V: zeilenweise Auswahl
- CTRL-V: Block-Auswahl

Auf den Ausgewählten Bereich können dann Operatoren angewendet werden.

# Kommandos
Der command line mode kann mit : geöffnet werden. Es gibt sehr viele Kommandos, unter anderem auch von Plugins.
Hier nur ein paar Beispiele. Später kommen auch noch mehr dazu.

- e w wq q q!: wie gehabt
- qa: Schließt alle Windows
- h(elp): Ruft Hilfe zu angegebenem Thema auf
- !: führt das angegebene Programm in der Shell aus
- te(erminal): öffnet eine interaktive Shell oder führt ein Programm in einem eigenen Buffer aus
- set: Setzt und liest Optionen
  - Optionen können mit no abgeschaltet werden
  - Optionen können mit ? ausgelesen werden
  - z.B.: spell, mouse, number
- nor(mal): Führt die gegebenen Kommandos wie in normal mode aus
- map: Erstellt eigene Keymappings
  - Vairanten für modi (n,v,i) und nicht-Rekursion (nore)
  - nnoremap <C-p> :

# Suchen und Ersetzen (innerhalb eines Buffers)

## Suchen
- /: sucht vorwärts nach gegebenen Regex
- ?: sucht rückwärts nach gegebenen Regex
- *: sucht vorwärts nach dem Wort unterm Cursor
  - im visual mode wird nach der ganze Auswahl gesucht
- #: sucht rückwärts nach dem Wort unterm Cursor
  - im visual mode wird nach der ganze Auswahl gesucht
- n: wiederholt die letzte Suche
- N: wiederholt die letzte Suche in die andere Richtung
- :nohlsearch: Schaltet die Markierung der letzten Suche aus

## Ersetzen

- :%s/suche/ersetze(/gc...)
  - % wählt den gesamten Buffer aus
  - im visual mode kann in der Selektion ersetzt werden
  - g: alle matches in einer Zeil
  - c: jedes Ersetzen muss bestätigt werden


# Textobjekte

Textobjekte werden im Visual Mode oder nach einem Operator benutzt um Objekt auszuwählen oder den Operator auf das Objekt anzuwenden.

Eine Auswahl an Textobjekten ist (:h text-objects für ein längere liste):
- w/W: Wort
- s: Satz
- p: Paragraph
- ()[]{}<>: Verschiedene Klammern
- "'`: Verschiedene Quotes
- t: Tags (<a></a>)

Ein a (around) vor dem Textobjekt wählt das Objekt mit Whitespace oder inklusive Klammern aus.
Ein i (inner) vor dem Textobjekt wählt das Objekt ohne Whitespace oder nur den Teil in Klammern aus.

Textobjekte können auch wie Kommandos wiederholt werden. Beispiel: d3w


# Navigation

## Word / text object Motions
Es kann auch anhand von Textobjekten navigiert werden.
Um zwischen Wörtern zu springen gibt es folgende Möglichkeiten:

- w W: springt zum nächsten Wortanfang
- e E: springt zum nächsten Wortende
- b B: springt zum vorherigen Wortanfang
- ge gE: springt zum vorherigen Wortende
- ( ): springt einen Satz nach vorne/hinten
- { }: springt einen Paragraph nach vorne/hinten

Wie immer auch wiederholbar: 3w

## Horizontale Navigation

- 0: springt zum Anfang der Zeile
- $: springt zum Ende der Zeile
- ^: springt zum ersten nicht-leeren Zeichen
- f F: springt auf das entsprechende Zeichen
  - f nach rechts, F nach rechts
- t T: springt vor das entsprechende Zeichen
  - f nach rechts, F nach rechts
- ; ,: wiederholt letztes t f T F
  - ; in die selbe Richtung
  - , in die andere Richtung


## Vertikale Navigation

- gg: springt an den Anfang des Buffers
- G: springt ans Ende des Buffers
- ":<Zeilennummer>": springt in die entsprechende Zeile
- %: Springt zum matching Zeichen. Zum Beispiel Klammern oder <a> </a>
- Entfernung + j oder k
  - Hilfreich: set relativenumber

## Marks

Mit Marks können Zeilen markiert werden, um zu ihnen springen zu können.

- m + (a-zA-Z): setzt einen mark in der aktuellen Zeile
  - a-z: kann nur aus der selben Datei angesprungen werden
  - A-Z: kann von überall angesprungen werden
- ': springt den gegeben mark an
- Marks 0-9 sind die Positionen beim vorherigen schließen von Vim

## Jumplist

Alle Sprünge werden in der jumplist aufgezeichnet:
- CTRL-o: Springt zur vorherigen/älteren Position in den jumplist
- CTRL-i: Springt zur nächsten/neueren Position in den jumplist
- :ju : zeigt die jumplist an

# Advanced Editing

## Multiple files

- buffer: geöffnete Datei, terminal, ...
  - :e, :enew : neuer Buffer
  - :bn, :bp : Navigation
  - :ls, :buffers : listet Buffer
  - :bdelete : schließt Buffer
- window: Zeigt ein Buffer an
  - <CTRL-w>s : horizontaler split
  - <CTRL-w>v : vertikaler split
  - <CTRL-w>(hjkl) : Navigation
  - <CTRL-w>(HJKL) : Verschiebt das aktuelle Window
  - <CTRL-w>r : rotiert Windows
  - :q : schließt Window
- tab page: Enthält Windows
  - :tabe, :tabnew : neue tab page
  - :tabn, :tabp, gt: Navigation
  - :tabc : schließt aktuelle tab page

## Verschiedenes
Verschiedene Operationen die ich häufiger benutze.

- << >>: ändert Einrückung der Zeile
  - Im visual mode nur < >
- J: fügt nächste Zeile mit der aktuellen zusammen (join)
  - behandelt Kommentare, Einrückung, Listen, ...
  - auch im visual mode
- u U ~: Verändert Groß- und Kleinschreibung
  - u: Lowercase
  - U: Uppercase
  - ~: toggle
- CTRL-x CTRL-a: dekrementiert / inkrementiert die Zahl unter dem Cursor
  - g CTRL-a: zählt visual mode mehrere Zahlen nacheinander
- CTRL-o im visual mode: one shot normal mode
- zz: positioniert aktuelle Zeile in der Bildschirmmitte
- bufdo: führt ein Kommando für jeden offenen Buffer aus

## Spellchecking

- set (no)spell: Spellchek ein- / ausschalten
- set spelllang=de: Sprache festlegen
- ]s [s: Springt zu falschen Wörtern
- z=: Liste mit Korrekturen anzeigen

## Register

Register können beliebigen Text enthalten, der später wiederverwendet werden kann. Es gibt u.a. folgende Register:

- "0 bis "9
  - "0: letzter yank
  - "1 -"9: letzte gelöschten Texte > 1 Zeile
- "-: letzter gelöschter Text < 1 Zeile
- "a to "z or "A to "Z
  - können beliebig vom User genutzt werden
  - lowercase um Inhalt zu ersetzen
  - uppercase um Inhalt anzufügen
- ": : zuletzt ausgeführte Kommandozeile
- ". : zuletzt eingefügter Text
- "% : Name der geöffneten Datei
- "*, "+: Die System-Clipboards
- "/: Die letzte Suche


Interaktion mit Registern:
- "r: benutzt das Register r für das nächste Einfügen oder Löschen
- CTRL-r im insert / command line mode: Einfügen aus Register

## Macros

Mit Macros können eingaben aufgezeichnet und noch mal ausgeführt werden.
Das ist zum Beispiel parktisch, um kompliziertere Bearbeitungen für viele Zeilen zu wiederholen.

- qa: Zeichet Macro in Register a auf
  - q: beendet Aufzeichnung
- @a: Führt Macro in Register a aus
  - @@: Führt letzten Macro noch einmal aus

## Quickfix

Vim kann Fehler oder ähnliches in einer Liste Sammeln. Man kann dann durch die Liste navigieren oder gesammelt Kommandos ausführen.

- :make : Führt make aus und befüllt quickfix list mit Fehlern
  - Programm und Errorformat können eingestellt werden
- :grep : Sucht mit grep und befüllt die quickfix list
  - vimgrep für internes grep
- :cw : Öffnet ein Window mit der quickfix list
- :cn : springt zum nächsten Eintrag
- :cp : springt zum vorherigen Eintrag
- :cdo : Führt Kommando für alle Einträge aus

# Config

Vim kann persistent konfiguriert werden:
- .vimrc
- ~/.config/neovim/init.(vim|lua)

In der Config stehen Kommandos für den command line mode. Es können zum Beispiel Optionen festgelegt oder Keymappings definiert werden.


# Plugins
Es gibt eine Vielzahl von Pulugins für Vim und Neovim. Zum installieren empfiehlt sich ein Plugin-Manager: plug (vim), lazy (nvim), ...
Um direkt mit einer sinnvollen Konfiguration einsteigen zu können gibt es auch Distrtibutionen, die Plugins, Keymappings und Optionen voreingestellt haben: z.B. lazyvim oder lunarvim.

# Misc
- hardtime-vim: Blockt "ineffizientes" Navigieren
- Mehr zu LazyVim: https://lazyvim-ambitious-devs.phillips.codes/
