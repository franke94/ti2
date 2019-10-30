# TI2: Rechnerarchitektur

## Lernziele

- Welche Komponenten hat ein Computersystem?
- Das Innenleben eines Computers kennenlernen
- Wie speichert ein Computer Daten?
- Wie wird ein Programm ausgeführt?
- Kleine Assembler-Programme schreiben
- Einfache Arithmetik kennenlernen

Dadurch verstehen wir:

- Computer im Allgemeinen
- wie höhrere Programmiersprachen in Maschinensprache übersetzt werden
- wie wir unsere Programmierfähigkeiten verbessern.

## Literatur

- Tanenbaum: Structured Computer Organization, 2013

---

Vorlesung 2 | 18.10.2019

# Vorlesung 2 | 18.10.2019

## Klassiche Architektur von Mikrocomputern

![1571404984511](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1571404984511.png)

Die Komponenten des Computers sind über den Bus verbunden und können darüber kommunizieren.

## Von-Neumann-Architektur

Die Von-Neumann-Architektur bildet die die Grundlage für viele Hardwarearchitekturen, die in diesem Kurs besprochen werden.

Sie lässt sich in folgende Komponenten zusammenfassen:

- Central Processing Unit (CPU)
  - Control unit
  - ALU / Operating unit
- Memory
- Input/Output units
- Interconnection

![1571405240958](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1571405240958.png)

- Der Computer ist nicht auf ein bestimmtes Problem zugeschnitten, sondern eine **general purpose machine**.
- Um ein Problem zu lösen, wird ein Programm im Speicher abgelegt. ("program controlled universal computer")

**Wichtig bei der Von-Neumann-Architektur:**

1. Anweisungen (das Programm) und Daten (Eingabe- und Ausgabewerte) liegen im **selben Speicher**.
2. Der Speicher besteht aus **Speicherzellen** mit jeweils festen Längen. Jede Speicherzelle kann individuell angesprochen werden.

![1571405622556](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1571405622556.png)

### Bestandteile der V.-N.-Architektur

- **Processor (central processing unit)**
  - Steuert den Fluss und Ausführung der Anweisungen
  - **Control unit**
    - Interpretiert die CPU-Anweisungen
    - Generiert alle Steuerkommandos für andere Komponenten
  - **Arithmetic Logical Unit (ALU)**
    - Führt alle Instruktionen aus
- **Input/Output system**
  - Schnittstelle zur Außenwelt
  - Eingabe und Ausgabe von Programm und Daten
- **Speicher**
  - Lagerung von Programm und Daten als Bitsequenzen
- **Interconnection**

### Vor- und Nachteile der V.-N.-Architektur

#### Vorteile

- Minimale Hardwareanforderungen
- Minimale Speicheranforderungen

#### Nachteile

- Die Hauptverbindung (Memory <-> CPU) ist ein Flaschenhals => **Von-Neumann-Flaschenhals**
- Programme müssen sich an dem sequentiellen Datenfluss durch den Flaschenhals orientieren. Dies hat Einfluss auf höhere Programmiersprachen.
- Wenig strukturierte Daten (lange Bitsequenzen)
- Die Anweisung bestimmt den Operandentyp
- Kein Speicherschutz

### Prinzipien des Computerbetriebs

#### SISD Single Instruction Single Data

Die CPU kann immer nur eine Anweisung gleichzeitig ausführen und immer nur einen einzelnen Operanden gleichzeitig verändern.

Code und Daten liegen ohne Ausnahme im **selben Speicher**. Da es keine Speicherschützenden Mechanismen gibt, können sich Programme gegenseitig zerstören oder willkürlich Daten zerstören.

Der Speicher ist unstrukturiert und wird linear angesprochen. Die Interpretation von Speicherinhalt hängt nur vom aktuellen Programm ab.

#### Zwei-Phasen-Prinzip der Anweisungsverarbeitung

- **Interpretationsphase:** Speicherzelleninhalt wird auf Basis eines **program counters** geholt. Dieser Inhalt wird dann als Anweisung interpretiert.
- **Ausführungsphase:** Speicherzelleninhalt wird auf Basis der in der Anweisung stehenden Adresse geholt. Dieser Inhalt wird dann als Daten interpretiert.

Der Anweisungsfluss folgt einer strikten sequentiellen Ordnung.

![1571406605901](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1571406605901.png)

## Harvard-Architektur

**Definition:** Trennung von Daten- und Programmspeicher.

![1571406969762](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1571406969762.png)

## Grundlegendes Konzept eines Mikro-Computers

Der IBM-PC ist eine modifizierte Von-Neumann-Architektur und wurde 1981 von IBM eingeführt.

Die Zusammenschaltung wird mit einem Bus realisiert, der die CPU mit dem Hauptspeicher, den Controllern und dem Input/Output-System verbindet.

![1571407149973](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1571407149973.png)

## Komponenten eines Computers

- **Hardware:** Alle mechanischen und elektronischen Komponenten
- **Software:** Alle auf dem Computer ausgeführten Programme
- **Firmware:** Mikroprogramme, die im ROM liegen.



# Übungsinhalte

## NASM-Cheatsheet

### Register

![1572277642658](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1572277642658.png)

![1572277678227](C:\Users\User\AppData\Roaming\Typora\typora-user-images\1572277678227.png)

### x86 NASM Assembler Befehle

| Befehl         | Semantik             | Beschreibung                                                 |
| -------------- | -------------------- | ------------------------------------------------------------ |
| MOV reg1, reg2 | reg1 = reg2          | Kopiert reg2 in reg1                                         |
| SUB reg1, reg2 | reg1 = reg1 - reg2   | Subtrahiert reg2 von reg1                                    |
| ADD reg1, reg2 | reg1 = reg1 + reg2   | Addiert reg2 zu reg1                                         |
| MUL reg1       | rdx:rax = rax * reg1 | Multipliziert reg1 mit rax und speichert 16-bit-Ergebnis in rdx:rax |
| DIV reg1       | rax = rdx:rax / reg1 | Dividert rdx:rax durch reg1 und speichert in rax (Return-Reg.) |
|                |                      |                                                              |
|                |                      |                                                              |
|                |                      |                                                              |
|                |                      |                                                              |

## Kompilierungs-Zeug

### Debugger

```shell
# Kompilieren und linken mit -gdwarf
nasm -felf64 -gdwarf programm.asm
gcc -g3 -0g -std=c11 -Wall -pedantic programm.o programm_wrapper.c -o programm

# Debugger ausführen
gdb programm
```



## Stellenwertsysteme umrechnen

### Dezimal -> Binär

#### Ganzzahlen

1. n ganzzahlig durch 2 dividieren. Rest (1 oder 0) notieren.
2. Schritt 1 wiederholen, bis n = 0.
3. Die Reste von unten nach oben ablesen. Umrechnung abgeschlossen.

#### Fließkommazahlen

1. Fließkommazahl mit 2 multiplizieren. Wenn das Ergebnis >= 1 ist, dann -1 nehmen. Wenn es kleiner 1 ist, dann +/- 0 nehmen.
2. Schritt 1 wiederholen, bis entweder das Ergebnis 0 ist, oder eine Periode erkennbar wird, also wenn sich n wiederholt.
3. Ablesen des Ergebnisses von oben nach unten.

### Binär -> Dezimal

"Das ist trivial!" für Ganzzahlen. Fließkommazahlen analog zu Ganzzahlen, aber von links nach rechts und mit den Werten 2<sup>-1</sup>, 2<sup>-2</sup>, ...

#### Hexadezimal -> Dezimal

Ziffernwerte des Hexadezimalsystems:

**[0,1, ... , 9] -> [0,1, ... , 9] und [A, B, C, D, E, F] -> [10, 11, 12, 13, 14, 15]**

#### Ganzzahlen

Wie im Binärsystem, nur mit der Basis 16: Von Rechts nach Links mit 16<sup>0</sup>, 16<sup>1</sup>, usw. multiplizieren und aufaddieren.

#### Fließkommazahlen

Wie die Ganzzahl berechnen (von rechts nach links) und dann durch die nächstgrößere 16er-Potenz teilen.