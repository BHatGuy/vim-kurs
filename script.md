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


# Kommandos
Der command line mode kann mit : geöffnet werden.

TODO:
- w, e, q
- help
- !
- set
  - spell
  - Mouse
  - number


# Navigation

## Word / Text object Motions
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

Mit marks können Zeilen markiert werden, um zu ihnen springen zu können.

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

# Suchen und Ersetzen

## Suchen
- /
- "* #"

