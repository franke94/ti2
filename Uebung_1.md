# TI2: Rechnerarchitektur

## 1. Übungsblatt

### Aufgabe 1

1. Ein **General-Purpose-Computer** nicht auf ein bestimmtes Problem zugeschnitten, sondern ist für verschiedenste Anwendungsbereiche (private wie auch wissenschaftliche oder geschäftliche) einsetzbar. Dem entgegen stehen eingebettete Systeme wie beispielsweise Steuerungscomputer von Haushaltsgeräten wie einer Waschmaschine.
2. Unter **"Programme sind auch nur Daten"** ist zu verstehen, dass sowohl Programme, als auch die darin verwendeten Daten in ein und dem selben Speicher liegen. Dieser Sichtweise folgend besitzt auch die Von-Neumann-Architektur nur einen Speicher.
3. Die Von-Neumann-Architektur setzt sich zusammen aus:
   - **Central Processing Unit (CPU)**: Bestehend aus Control Unit und Arithmetic Logical Unit: Steuerung von Fluss und Ausführung der Anweisungen
   - **Memory**: Lagerung von Programmen und Daten als Bitsequenzen
   - **Input/Output Units**: Schnittstelle zur Außenwelt, Eingabe und Ausgabe von Programmen und Daten.
4. - Der **Befehlsprozessor (Control Unit)** interpretiert die Anweisungen eines Programms und steuert die Befehlsabfolge.
   - Der **Datenprozessor (Arithmetic Logical Unit oder ALU)** führt Rechenoperationen und logische Verknüpfungen durch.
5. - Der **Datenbus** überträgt Daten zwischen CPU, Memory und I/O Unit.
   - Der **Adressbus** legt Adressen an, von der oder in die Daten gelesen oder geschrieben werden.
6. **SISD (Single Instruction Single Data)** bedeutet, dass die CPU immer nur eine Anweisung gleichzeitig ausführen kann und immer nur einen Operanden gleichzeitig verändern.
7. Durch das Konzept der universellen Programmierbarkeit lassen sich mit dem Von-Neumann-Rechnermodell Probleme verschiedener Art lösen, sofern für diese ein entsprechendes Programm geschrieben werden kann. Assemblersprachen übernehmen hier die Rolle des "Übersetzers". Sie sind die Schnittstelle für spezialisierte höhere Programmiersprachen und wandeln diese in universellen Maschinencode um.
8. Test

## Aufgabe 2

### gauss.asm

```assembly
global gauss

section .text

gauss:
	; Kopieren des Parameters n in r10, damit er durch die Addition nicht verändert wird.
	MOV rax, rdi

	; Addieren von 1 zu n.
	ADD rax, 1

	; (n+1)*n
	MUL rdi

	; Wir speichern den Divisor 2 in r11...
	MOV r11, 2

	; ((n+1)*n)/2
	DIV r11
	
	RET
```

