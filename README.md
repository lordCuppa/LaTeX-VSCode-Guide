# Installationsanleitung für LaTeX in VS Code
**Erstellungsdatum**: 28. Juni 2025<br>
**Version**: 1.0

## Inhaltsverzeichnis
- [Einleitung](#id-section0)
- [1. Download & Installation von TeX Live](#id-section1)
- [2. Download & Installation von VS Code](#id-section2)
- [3. Installation & Konfiguration von LaTeX Workshop](#id-section3)
- [4. Installation einer Grammatikprüfung](#id-section4)
- [5. Schreiben & Kompilieren](#id-section5)
- [6. Optional: Literatursoftware](#id-section6)
    - [Verwendung MacOS](#id-section6_1)
    - [Verwendung unter Windows und Linux](#id-section6_2)
- [7. Optional: GitHub Repository](#id-section7)
- [Quellenangaben](#id-section-reference) 

<div id = 'id-section0' />

## Einleitung
Diese Anleitung basiert auf einem GitHub-Beitrag von Jia Jia und wurde um mehrere Punkte erweitert. Die einzelnen Schritte wurden unter MacOS durchgeführt, wodurch Abweichungen zu anderen Betriebssystemen vorhanden sein können.

<div id='id-section1'/>

## 1. Download & Installation von TeX Live
Der Download & die Installation basiert auf dem verwendeten Betriebssystem. Dazu nachfolgend Links zu den jeweiligen Websiten. Bei der Installation sind den Angaben der Software zu folgen.
- **MacOS** Nutzer*innen: [MacTeX.pkg](https://www.tug.org/mactex/)
- **Windows & Linux** Nutzer*innen: [texlive.iso](https://www.tug.org/texlive/)

Unter Windows wird empfohlen, die ausführbare TeX Live-Datei in den System-`PATH` zu integrieren.

<div id='id-section2'/>

## 2. Download & Installation von VS Code
VS Code ist ein kostenloser Quelltext-Editor von Microsoft und kann unter folgendem Link: [VS Code](https://code.visualstudio.com/) heruntergeladen werden.

<div id='id-section3'/>

## 3. Installation & Konfiguration von LaTeX Workshop
`LaTeX Workshop` ist eine Erweiterung in VS Code.

<img src="images/LTEX_Step_1.png" width="50%" height="auto" alt="Installation der LaTeX-Erweiterung unter VS Code." title="Screenshot der Extensions in VS Code mit dem Suchbegriff LaTeX Workshop."></br>
*LaTeX Workshop installieren*

1. `Extensions` öffnen
2. LaTeX eingeben
3. Erweiterung installieren

Anschließend mit `Shift + Strg + P` (Windows) oder `Shift + Cmd + P` (macOS) das Befehlsmenü öffnen. Hier `Open User Settings JSON` eingeben und den ersten Eintrag, wie nachfolgend dargestellt, öffnen.

<img src="images/LTEX_Step_2.png" width="50%" height="auto" alt="LaTeX-Benutzereinstellungen JSON unter VS Code mithilfe des Befehlsmenü öffnen." title="Screenshot des Befehlsmenüs von VS Code mit dem Suchbegriff Open User Settings JSON."></br>
*LaTeX Benutzereinstellungen festlegen*

In diese JSON-Datei nun beide folgenden Schnipsel innerhalb der Klammern `{}` der Datei einfügen.

<details><summary>JSON 1</summary>

```
"latex-workshop.latex.tools": [
 {
  "name": "latexmk",
  "command": "latexmk",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "-pdf",
   "-outdir=%OUTDIR%",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "xelatex",
  "command": "xelatex",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "pdflatex",
  "command": "pdflatex",
  "args": [
   "-synctex=1",
   "-interaction=nonstopmode",
   "-file-line-error",
   "%DOC%"
  ],
  "env": {}
 },
 {
  "name": "bibtex",
  "command": "bibtex",
  "args": [
   "%DOCFILE%"
  ],
  "env": {}
 }
],
```

</details>

<details><summary>JOSN 2</summary>

```
"latex-workshop.latex.recipes": [
 {
  "name": "pdfLaTeX",
  "tools": [
   "pdflatex"
  ]
 },
 {
  "name": "latexmk 🔃",
  "tools": [
   "latexmk"
  ]
 },
 {
  "name": "xelatex",
  "tools": [
   "xelatex"
  ]
 },
 {
  "name": "pdflatex ➞ bibtex ➞ pdflatex`×2",
  "tools": [
   "pdflatex",
   "bibtex",
   "pdflatex",
   "pdflatex"
  ]
 },
 {
 "name": "xelatex ➞ bibtex ➞ xelatex`×2",
 "tools": [
   "xelatex",
   "bibtex",
   "xelatex",
   "xelatex"
  ]
 }
]
```

</details>

<div id='id-section4'/>

## 4. Installation einer Grammatikprüfung
Standardmäßig ist keine Grammatikprüfung für Markup-Sprachen integriert. Aus diesem Grund kann die VS Code-Erweiterung: `LTeX` installiert werden. Sie ermöglicht nicht nur eine grundlegende Grammatikprüfung, sondern bietet auch eine Option zur Erstellung eines eigenen Wörterbuchs, das als zusätzliche Datei dem Projekt beigefügt wird.

Zum Installieren von `LTeX` gehen Sie wie folgt vor.


<img src="images/LTEX_Step_3.png" width="50%" height="auto" alt="Installation der LTeX-Erweiterung unter VS Code." title="Screenshot der Extensions in VS Code mit dem Suchbegriff LTeX."></br>
*LTeX installieren*

Mit dem Zahnrad-Symbol neben der Erweiterung können nun die Einstellungen von `LTeX` geöffnet werden.

<img src="images/LTEX_Step_4.png" width="50%" height="auto" alt="Installation der LTeX Erweiterung unter VS Code." title="Screenshot der Extensions in VS Code mit dem Kontextmenü von LTeX"></br>
*LTeX-Einstellungen öffnen*

Es gibt verschiedene Einstellungsmöglichkeiten, wobei die wichtigste im unteren Bereich der Einstellungen zu finden ist.

<img src="images/LTEX_Step_5.png" width="50%" height="auto" alt="Installation der LTeX Erweiterung unter VS Code." title="Screenshot der Einstellungen von LTeX im Abschnitt Ltex: Language."></br>
*LTeX Sprache festlegen*

Hier kann die gewünschte Sprache ausgewählt werden. Die gewählte Sprache gilt für alle Dokumente, die in VS Code geöffnet werden. Wenn Sie in einer anderen Sprache schreiben möchten, muss diese in den Einstellungen umgestellt werden.

<div id='id-section5'/>

## 5. Schreiben & Kompilieren
Jetzt kann eine `.tex`-Datei geöffnet oder eine neue erstellt werden. Zum Kompilieren der Datei, falls dies nicht bereits automatisch geschieht, verwenden Sie `Strg + Alt + B` (Windows) oder `Option + Cmd + B` (macOS). Zudem befindet sich in der rechten oberen Ecke eine Schaltfläche zur Vorschau der PDF-Datei.

<div id = 'id-section6' />

## 6. Optional: Literatursoftware
Die Installation einer Literatursoftware ist nicht zwingend nötig. Sie erleichtert jedoch das Verwalten von Quellen, die direkt im LaTeX-Dokument verwendet werden können.

<div id = 'id-section6_1' />

### Verwendung unter MacOs
Die Verwendung der Literatursoftware ermöglicht eine schnelle Erfassung wissenschaftlicher Quellen.. Unter MacOS ist im `MacTeX.pkg` [BibDesik](https://bibdesk.sourceforge.io) standardmäßig in der Installation enthalten. Damit können Literatursammlungen, `.bib`-Dateien, einfach geöffnet und bearbeitet werden (z. B. die in den LaTeX FH-Vorlagen vorhandene `references.bib`). Des Weiteren besteht die Möglichkeit neue Sammlungen zu erstellen.

Dazu die gewünschte Literatur z. B. auf [ACM](https://dl.acm.org) oder [IEEE Xplore](https://ieeexplore.ieee.org/Xplore/home.jsp) öffnen und im oberen linken Bereich `Cite This`auswählen. Anschließend öffnet sich ein Pop-Up, in dem das gewünschte Format ausgewählt werden kann.

<img src="images/BibDesk_Step_1.png" width="50%" height="auto" alt="Herunterladen der BibTeX-Datei im IEEE Xplore." title="Screenshot der IEEE Xplore Website mit geöffnetem 'Cite This' Pop-Up."><br>
*BibTeX downloaden*

1. `Cite This` auswählen
2. `BibTeX` auswählen
3. Datei herunterladen

Unter der Nutzung von BibDesk auf MacOS kann nun die `BibTex`-Version heruntergeladen werden. Dies kann anschließend in BibDesk unter `Puplikation` > `Neue Puplikation aus Datei ...` in die aktuelle Sammlung hinzugefügt werden. Anschließend kann in der Quelle der `Cite Key` noch angepasst werden (siehe z. B. LaTeX FH-Vorlage), damit die weitere Arbeit damit erleichtert wird.

Nach der Integration der Quelle kann das zugehörige PDF per "Drag and Drop" mit der Quelle verknüpft werden. Dazu das PDF in das markierte Vorschaufenster in der nachfolgenden Abbildung ziehen. Hierbei ist zu beachten, dass sich dabei der Speicherort der PDF nicht verändert.

<img src="images/BibDesk_Step_2.png" width="50%" height="auto" alt="Quelle in BibDesik mit Markierung des Vorschaufensters zur Ablage der PDF." title="Screenshot einer BibDesk Quelle mit markiertem Vorschaufenster zur Ablage der PDF."><br>
*PDF in BibDesk einbinden*

<div id = 'id-section6_2' />

### Verwendung unter Windows und Linux
Da diese Anleitung unter MacOS erstellt wurde, kann nicht garantiert werden, dass die zuvor beschriebenen Schritte identisch sind. Aus diesem Grund nachfolgend alternative Verlinkungen zu möglichen Literatursoftware-Optionen.
- [Zotero](https://www.zotero.org)
    - [Interessante Zotero Erweiterung](https://github.com/retorquere/zotero-better-bibtex)
- [JabRef](https://www.jabref.org)

Bei Fragen zur Verwendung der genannten Software wird auf die jeweilige Dokumentation verwiesen.

<div id = 'id-section7' />

## 7. Optional: GitHub Repository
Damit die erstellten Daten nun nicht verloren gehen, wird empfohlen ein GitHub-`Repository` zu erstellen. Dies eröffnet zudem die Möglichkeit, auf mehreren Geräten am Dokument zu arbeiten und dabei nicht die Übersicht zu verlieren.

Zur Erstellung einer Repository wird zuerst ein kostenloses Konto auf [GitHub](https://github.com) benötigt. Anschließend gibt es mehrere Möglichkeiten, ein Repository zu erstellen. Aufgrund des Umfangs wird dabei auf die offizielle Dokumentation von GitHub verwiesen. Zur einfacheren Umsetzung kann zudem die Software **GitHub Desktop** installiert werden. Diese nimmt die Konsolenbefehle ab und bietet eine Übersicht über die verknüpften Repositorys sowie deren aktuellen Stand.

Im Zusammenhang mit einem `Repository` ist es geläufig, eine `.gitignore`-Datei im jeweiligen Ordner zu integrieren. Diese beinhaltet Muster, die Git mitteilen, welche Dateien und Verzeichnisse ignoriert werden sollen. Als Basis nochfolgend ein Muster, das nicht benötigte System-/LaTeX- und BibTeX-Dateien ignoriert.

**HINWEIS**: Die `.gitignore`-Datei muss vor dem ersten Commit/Upload vorhanden sein, um diese Daten von Beginn an auszuschließen. Andernfalls müssen diese nachträglich auf GitHub gelöscht werden.

<details><summary>.gitignore</summary>

```
## Systemfiles
Thumbs.db
.DS_Store
desktop.ini
ehthumbs.db


## Core latex/pdflatex auxiliary files:
*.aux
*.lof
*.log
*.lot
*.fls
*.out
*.toc
*.fmt
*.fot
*.cb
*.cb2
.*.lb

## Intermediate documents:
*.dvi
*.xdv
*-converted-to.*
# these rules might exclude image files for figures etc.
# *.ps
# *.eps
# *.pdf

## Generated if empty string is given at "Please type another file name for output:"
.pdf

## Bibliography auxiliary files (bibtex/biblatex/biber):
*.bbl
*.bbl-SAVE-ERROR
*.bcf
*.bcf-SAVE-ERROR
*.blg
*-blx.aux
*-blx.bib
*.run.xml

## Build tool auxiliary files:
*.fdb_latexmk
*.synctex
*.synctex(busy)
*.synctex.gz
*.synctex.gz(busy)
*.pdfsync
*.rubbercache
rubber.cache

## Build tool directories for auxiliary files
# latexrun
latex.out/

## Auxiliary and intermediate files from other packages:
# algorithms
*.alg
*.loa

# achemso
acs-*.bib

# amsthm
*.thm

# attachfile2
*.atfi

# beamer
*.nav
*.pre
*.snm
*.vrb

# changes
*.soc
*.loc

# comment
*.cut

# cprotect
*.cpt

# elsarticle (documentclass of Elsevier journals)
*.spl

# endnotes
*.ent

# fixme
*.lox

# feynmf/feynmp
*.mf
*.mp
*.t[1-9]
*.t[1-9][0-9]
*.tfm

#(r)(e)ledmac/(r)(e)ledpar
*.end
*.?end
*.[1-9]
*.[1-9][0-9]
*.[1-9][0-9][0-9]
*.[1-9]R
*.[1-9][0-9]R
*.[1-9][0-9][0-9]R
*.eledsec[1-9]
*.eledsec[1-9]R
*.eledsec[1-9][0-9]
*.eledsec[1-9][0-9]R
*.eledsec[1-9][0-9][0-9]
*.eledsec[1-9][0-9][0-9]R

# glossaries
*.acn
*.acr
*.glg
*.glo
*.gls
*.glsdefs
*.lzo
*.lzs
*.slg
*.slo
*.sls

# uncomment this for glossaries-extra (will ignore makeindex's style files!)
# *.ist

# gnuplot
*.gnuplot
*.table

# gnuplottex
*-gnuplottex-*

# gregoriotex
*.gaux
*.glog
*.gtex

# htlatex
*.4ct
*.4tc
*.idv
*.lg
*.trc
*.xref

# hypdoc
*.hd

# hyperref
*.brf

# knitr
*-concordance.tex
# TODO Uncomment the next line if you use knitr and want to ignore its generated tikz files
# *.tikz
*-tikzDictionary

# listings
*.lol

# luatexja-ruby
*.ltjruby

# makeidx
*.idx
*.ilg
*.ind

# minitoc
*.maf
*.mlf
*.mlt
*.mtc[0-9]*
*.slf[0-9]*
*.slt[0-9]*
*.stc[0-9]*

# minted
_minted*
*.data.minted
*.pyg

# morewrites
*.mw

# newpax
*.newpax

# nomencl
*.nlg
*.nlo
*.nls

# pax
*.pax

# pdfpcnotes
*.pdfpc

# sagetex
*.sagetex.sage
*.sagetex.py
*.sagetex.scmd

# scrwfile
*.wrt

# svg
svg-inkscape/

# sympy
*.sout
*.sympy
sympy-plots-for-*.tex/

# pdfcomment
*.upa
*.upb

# pythontex
*.pytxcode
pythontex-files-*/

# tcolorbox
*.listing

# thmtools
*.loe

# TikZ & PGF
*.dpth
*.md5
*.auxlock

# titletoc
*.ptc

# todonotes
*.tdo

# vhistory
*.hst
*.ver

# easy-todo
*.lod

# xcolor
*.xcp

# xmpincl
*.xmpi

# xindy
*.xdy

# xypic precompiled matrices and outlines
*.xyc
*.xyd

# endfloat
*.ttt
*.fff

# Latexian
TSWLatexianTemp*

## Editors:
# WinEdt
*.bak
*.sav

# Texpad
.texpadtmp

# LyX
*.lyx~

# Kile
*.backup

# gummi
.*.swp

# KBibTeX
*~[0-9]*

# TeXnicCenter
*.tps

# auto folder when using emacs and auctex
./auto/*
*.el

# expex forward references with \gathertags
*-tags.tex

# standalone packages
*.sta

# Makeindex log files
*.lpz

# xwatermark package
*.xwm

# REVTeX puts footnotes in the bibliography by default, unless the nofootinbib
# option is specified. Footnotes are the stored in a file with suffix Notes.bib.
# Uncomment the next line to have this generated file ignored.
#*Notes.bib

```

</details><br>

**Verweis auf die Offizielle Dokumentation & GitHub Desktop**
- [Ein neues Repository erstellen](https://docs.github.com/de/repositories/creating-and-managing-repositories/creating-a-new-repository)
- [GitHub Desktop](https://github.com/apps/desktop)


<div id = 'id-section-reference' />

## Quellenangaben
Diese Anleitung basiert auf dem GitHub-Beitrag von Jia Jia (贾甲).<br>
Link zum Beitrag: [A Fast Guide on Writing LaTeX with LaTeX Workshop in VS Code](https://mathjiajia.github.io/vscode-and-latex/)

Autor: Dominik Altmann (HCC-Studiengang, FH Hagenberg)

---

*Dieses Dokument wurde im Interesse von Studierenden für Studierende erstellt und steht in keinem Zusammenhang mit der FH Hagenberg. Jeglicher Inhalt basiert auf persönlicher Erfahrung oder den in den Quellenangaben genannten Ressourcen. Aus diesem Grund gilt die Nutzung auf eigene Verantwortung.*