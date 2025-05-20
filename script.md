# Vimkurs

## Basics
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

## Modi

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

## Operatoren

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

d und y  brauchen eine Richtung:
- h j k l: ein Zeichen in entsprechende Richtung
- 0: Anfang der Zeile
- $: Ende der Zeile
- ^: erstes nicht-leere Zeichen
- (oder Textobjekt -> später mehr)

Die meisten Operatoren haben Varianten:
- Uppercase Variante
  - I, A, S: der Operator bezieht sich auf die ganze Zeile
  - D, C, Y: bis ans Ende der Zeile
  - X, O, P: andere Richtung
- Doppelte Variante
  - dd, yy, cc: der Operator bezieht sich auf die ganze Zeile

Ein Zahl vor einem Operator führt den Operator n mal aus. 3dl löscht nächsten drei Zeichen.

