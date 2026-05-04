# LaTeX-Template für Bachelorarbeiten

Template für Bachelorarbeiten an der **Nordakademie Elmshorn** im Studiengang Wirtschaftsinformatik.
Entstanden aus einer echten BA (2026) und auf das Wesentliche reduziert.

---

## Voraussetzungen

### 1. LaTeX-Distribution installieren
Wähle **eine** der folgenden Optionen:

- **Windows:** [MiKTeX](https://miktex.org/download) *(empfohlen, installiert Pakete automatisch)*
- **Alternativ:** [TeX Live](https://tug.org/texlive/)

### 2. Editor installieren
- **[VS Code](https://code.visualstudio.com/)** + Extension **LaTeX Workshop** *(empfohlen)*
- Alternativ: [TeXstudio](https://www.texstudio.org/)

### 3. Biber installieren
Biber ist der Bibliography-Prozessor und wird normalerweise mit MiKTeX/TeX Live mitgeliefert.
Prüfen: `biber --version` im Terminal.

---

## Schnellstart

### Repository klonen
```bash
git clone https://github.com/DeinName/latex-ba-template.git meine-bachelorarbeit
cd meine-bachelorarbeit
```

### Anpassen
Alle Stellen mit `TODO` in den `.tex`-Dateien anpassen:

| Datei | Was anpassen |
|---|---|
| `chapters/00_frontmatter.tex` | Name, Matrikelnummer, Zenturie, Titel, Prüfer, Datum |
| `preamble.tex` | `pdftitle`, `pdfauthor`, `pdfkeywords` |
| `main.tex` | Kapitel ein-/auskommentieren |

### Kompilieren
**Reihenfolge ist wichtig** (sonst stimmen Zitate und Inhaltsverzeichnis nicht):

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

In **VS Code mit LaTeX Workshop** passiert das automatisch beim Speichern.

---

## Dateistruktur

```
latex-ba-template/
├── main.tex                    ← Hauptdatei (hier alles zusammengeführt)
├── preamble.tex                ← Alle Pakete und Einstellungen
├── references.bib              ← Literaturquellen
├── anhang.tex                  ← Anhang (optional)
├── chapters/
│   ├── 00_frontmatter.tex      ← Titelseite, Sperrvermerk, Eidesstattl. Erklärung
│   ├── 01_einleitung.tex       ← Kapitel 1
│   └── 02_grundlagen.tex       ← Kapitel 2 (mit Beispielen für Tabellen, Zitate)
├── figures/                    ← Bilder hier ablegen (.png, .pdf, .jpg)
├── tables/                     ← Optionaler Ordner für komplexe Tabellen
└── anhang/                     ← PDFs für den Anhang hier ablegen
```

---

## Literaturverwaltung

Die Datei `references.bib` enthält Beispiele für jeden Quellentyp:

| Typ | BibTeX-Schlüssel |
|---|---|
| Buch | `@book` |
| Zeitschriftenartikel | `@article` |
| Konferenzbeitrag | `@inproceedings` |
| Website / Bericht | `@misc` |

### Zitieren im Text

```latex
\autocite{schluessel}                    % Fußnote: (Autor Jahr)
\autocite[S.~42]{schluessel}             % Mit Seitenangabe
\autocite{schluessel1, schluessel2}      % Mehrere Quellen
\textcite{schluessel}                    % Im Fließtext: "Autor (Jahr) zeigt..."
```

---

## Häufige Probleme

### „Literaturverzeichnis ist leer" / Zitate erscheinen als `[?]`
→ Reihenfolge beim Kompilieren falsch. Immer: `pdflatex` → `biber` → `pdflatex` → `pdflatex`

### Wort ragt über den Seitenrand
→ Weichen Trennstrich einfügen: `Langer\-Wort\-Name`

### Umlaute werden nicht korrekt dargestellt
→ Datei muss als **UTF-8** gespeichert sein. In VS Code: unten rechts auf die Kodierung klicken.

### Biber findet die `.bib`-Datei nicht
→ Sicherstellen, dass `main.bcf` existiert (entsteht beim ersten `pdflatex`-Durchlauf).

---

## Nordakademie-spezifische Hinweise

- **Sperrvermerk**: Bei vertraulichen Unternehmensarbeiten Pflicht — Text in `00_frontmatter.tex` anpassen
- **Eidesstattliche Erklärung**: Pflicht, Unterschrift nach dem Drucken per Hand oder digital (Adobe)
- **Schriftgröße**: 12pt, A4, 2,5 cm Rand — bereits so eingestellt
- **Zitierweise**: Autor-Jahr in Fußnoten — bereits so konfiguriert

---

## Basiert auf

Bachelorarbeit „Bewertung moderner Webframeworks für die Migration von Desktop- zu Webanwendungen" (Nordakademie, 2026).
