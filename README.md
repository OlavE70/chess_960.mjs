# ♟️ chess_960.mjs — Chess960-Erweiterung für chess.js

**chess_960.mjs** ist eine erweiterte Version der JavaScript-Schachbibliothek [chess.js](https://github.com/jhlywa/chess.js) von **Jeff Hlywa**.
Die Hauptmodifikation besteht in der Integration und Unterstützung der Regeln für **Chess960 (Fischer Random Chess)**. 

Alle grundlegenden Funktionalitäten von *chess.js* (Zuggenerierung, FEN-Parsing, Spielstatus usw.) bleiben erhalten, wurden jedoch erweitert, um die Besonderheiten von Chess960 – insbesondere die variablen Rochaderechte – korrekt zu behandeln.

Die Bibliothek basiert auf einer älteren Version von chess.js von November / Dezember 2022.

---

## 🛠️ Funktionen & Erweiterungen

Zusätzlich zu den Kernfunktionen von *chess.js* bietet diese Erweiterung:

* **✅ Chess960-Kompatibilität:** Korrekte Handhabung aller 960 möglichen Startpositionen.
* **♜ Dynamische Rochade:** Die Logik zur Erkennung und Ausführung von Rochaden wurde angepasst. Der König landet stets auf der *g-* oder *c-Linie*, der Turm entsprechend auf *f-* oder *d-Linie* – unabhängig von der Startposition.
* **📄 Shredder-FEN-Parsing:** Lesen und Schreiben von Rochaderechten im *Shredder-FEN*-Format (z. B. `AaHh` anstelle von `KQkq`), d.h. es sind die Turm-Positionen anzugeben.
* **🎲 Positionserzeugung:** Neue Funktionen zur Generierung von Chess960-Startstellungen.

---

## 🚀 Installation & Verwendung

Da dies eine Modifikation von *chess.js* ist, orientiert sich die Verwendung an der Originalbibliothek.

### 1️⃣ Zufällige Chess960-Position laden

```js
import { Chess, generateStartPositionFEN } from './chess.js'; // Pfad anpassen

// Generiert eine zufällige Chess960-Start-FEN (z.B. "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/BRNQKNBR w Qkq - 0 1")
const randomFen = generateStartPositionFEN({ chess960: true });

// Initialisierung der Partie mit Chess960-Modus
const game = new Chess(randomFen, { chess960: true });

console.log(game.fen());
```

### 2️⃣ Position mit spezifischer ID laden

Chess960-Startpositionen sind von **0 bis 959** durchnummeriert.

```js
// Generiert die FEN für Startposition ID 518
const fen518 = generateStartPositionFEN({ id: 518 });
const game518 = new Chess(fen518, { chess960: true });
```

---

## 💻 API-Erweiterungen

### `generateStartPositionFEN(options)`

Erzeugt eine FEN-Zeichenkette für die Startstellung.

| Parameter                | Typ       | Beschreibung                                                                                 |
| ------------------------ | --------- | -------------------------------------------------------------------------------------------- |
| `options.id`             | `number`  | *(Optional)* Die Chess960-ID (0–959). Wird eine ID weggelassen, wird eine zufällige gewählt. |
| `options.chess960`       | `boolean` | *(Optional, Standard: false)* Wenn `true`, wird eine Chess960-Stellung generiert.            |
| `options.includePGNTags` | `boolean` | *(Optional, Standard: false)* Wenn `true`, wird die FEN in eine PGN-Tag-Sektion eingebettet. |

---

### `decodeChess960IdFromFEN(fen)`

Versucht, die Chess960-ID aus einer Start-FEN (mit Shredder-FEN Rochaderechten) zu bestimmen.

| Parameter | Typ      | Beschreibung                                                        |
| --------- | -------- | ------------------------------------------------------------------- |
| `fen`     | `string` | FEN-Zeile der Startstellung (nur die erste Reihe wird ausgewertet). |

**Rückgabe:** `number | null`

---

### `game.isVariant960()`

Eine neue Methode auf der `Chess`-Instanz.

| Rückgabe  | Typ                                                                                 | Beschreibung |
| --------- | ----------------------------------------------------------------------------------- | ------------ |
| `boolean` | Gibt `true` zurück, wenn die aktuelle Partie im Chess960-Modus initialisiert wurde. |              |

---

## 🧩 Beispielausgabe

```text
Start-FEN (ID 518):
nrkbbqnr/pppppppp/8/8/8/8/PPPPPPPP/NRKBBQNR w HAha - 0 1
```

---

## 📜 Lizenz & Danksagungen

Dieses Projekt basiert auf der Arbeit von **Jeff Hlywa**
und steht unter der gleichen Lizenz.

### Original Chess.js Lizenz

```
Copyright (c) 2022, Jeff Hlywa (jhlywa@gmail.com)
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice,
   this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
POSSIBILITY OF SUCH DAMAGE.
```

---

## 🙏 Credits

* **Autor der Originalbibliothek:** [Jeff Hlywa](https://github.com/jhlywa)
* **Erweiterung & Chess960-Integration:** *[OlavEe1970](https://github.com/OlavE70)*

---
