# Dokumentation zur Lösung d. ESA 10 (MMDE 10W)

Responsive Webseite, erstellt nach dem Mobile-First-Prinzip und unter Verwendung von Media-Queries.

## Inhalt

- [Dokumentation zur Lösung d. ESA 10 (MMDE 10W)](#dokumentation-zur-lösung-d-esa-10-mmde-10w)
  - [Inhalt](#inhalt)
  - [Aufbau von "index.html" | Inhalt](#aufbau-von-indexhtml--inhalt)
  - [Wesentliche Konfigurationen in "style.css" | Inhalt](#wesentliche-konfigurationen-in-stylecss--inhalt)
    - [Einbindung von Schriften | Inhalt](#einbindung-von-schriften--inhalt)
    - [Farben und Einstellungen | Inhalt](#farben-und-einstellungen--inhalt)
    - [Layout | Inhalt](#layout--inhalt)
      - [**Breakpoint 1 (min. 48em):** | Inhalt](#breakpoint-1-min-48em--inhalt)
      - [**Breakpoint 2 (min. 64em):** | Inhalt](#breakpoint-2-min-64em--inhalt)
      - [**Breakpoint 3 (min. 120em):** | Inhalt](#breakpoint-3-min-120em--inhalt)

___

## Aufbau von "index.html" | [Inhalt](#inhalt)

Im `head` findet sich die obligatorische Angabe von `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.  
Ferner ist dort auch das Stylesheet ["style.css"](#wesentliche-konfigurationen-in-stylecss) mit `<link rel="stylesheet" href="style/style.css">` verlinkt.

Alle Elemente der Seite werden von einem DIV mit der `id="pageWrapper"` umschlossen. Diser Container befindet sich im `body`-Element.  
Innerhalb von `pageWrapper` finden sich die Hauptelemente `header` (`id="pageHeader"`), `nav` (`id="pageNav"`) und `main`.

Der Content von `main` ist von einem zusätzlichen DIV-Container `id="mainContentWrapper"` umgeben. Hierbei handelt es sich um vier `section`-Elemente (`class="mainSection"`), von denen jedes seine individuelle ID besitzt, gegliedert. (Im Rahmen dieser Demonstration sind lediglich die ersten beiden von Relevanz.)  
Jede Sektion ist in zwei Bereiche eingeteilt, einem `header` (`class="secHeader"`) und einem oder mehere DIV(s) der `class="seContent"`, bzw. der `class="seContent artContainer"`.

Innerhalb der ersten Sektion mit der `id="welcome"` findet sich ein `img`-Element welches von einem `figcaption`-Element begleitet und von einem `figure`-Element umschossen ist. An diesem `figure`-Element wird nachfolgend die Anwendung der CSS-Regel `float: left;` demonstriert.  
Das `figure`-Element befindet sich zwischen zwei DIVs der `class="contTxt"` welche `p`-Elemente beinhalten.

In der folgenden Sektion mit der `id="locations"` findet sich neben einem DIV mit der `class="seContent"` ein weiteres mit der `class="seContent artContainer"`. Dieses beherbergt drei `article`-Elemente der `class="secArt"`. Ähnlich wie bei den `section`-Elementen gliedern sich auch die `article` in einen `header`-Bereich und einen Content-Bereich (DIV der `class="artContent"`). Innerhalb der Content-Bereiche befinden sich Texte und Bilder. Auch hier findet die CSS-Regel CSS-Regel `float: left;` Anwendung.

___

## Wesentliche Konfigurationen in "style.css" | [Inhalt](#inhalt)

### Einbindung von Schriften | [Inhalt](#inhalt)

Mittels `@import`-Anweisung werden zwei Schriftarten von [GoogleFonts](https://fonts.google.com/?category=Sans+Serif) importiert. Die Schriftart "Nunito" als Standard-Schriftart und "Kaushan Script" für Titel, Überschriften und Bildunterschriften.

### Farben und Einstellungen | [Inhalt](#inhalt)

Durch Verwendung von CSS-Variablen werden vier Farben und einige Einstellungen definiert.

| CSS-Variable(n) | Erläuterung |
|-|-|
| `--sand: #FFF6F1;`<br> `--canarianGreen: #00A017;` <br> `--canarianBlue: #0F45AE;`<br> `--canarianBlueB: #092968;`<br> `--contentFontColor: #2B0008;`<br> `--canarianBlueGrad: linear-gradient(45deg, var(--canarianBlue), var(--canarianBlueB));` | Farben / Farbverlauf |
| `--borderR: 1rem;` | Definition des Radius f. Rahmenecken. |
| `--borderPattern: 0 var(--borderR) 0 var(--borderR);` | Definition einer Standardkonfiguration f. Rahmenrundungen (nur unten links und oben rechts) |
| `--sVPmargin: .25rem;` | Definition eines Basis-Abstandswert |
| `--sVPVmargin: var(--sVPmargin) 0;` | Vertikale Abstandskonfiguration f. kleine Viewports |
| `--sVPHmargin: 0 calc(var(--sVPmargin) * 2);` | Horizontale Abstandskonfiguration f. kleine Viewports |
| `--sVPgap: .125rem;` | Definition eines Abstandes zwischen `flex`-Items (kleine VP) |
| `--sVPtitleFontSize: 4.25rem;` | Definition einer Basis-Schriftgröße f. Titel u. Überschriften |
| `--mVPmargin: calc(var(--sVPmargin) * 4)` | Definition einer Abstandskonfiguration f. mittlere und große Viewports |
| `--mVPgap: calc(var(--sVPgap) * 5);` | Definition eines Abstandes zwischen `flex`-Items (mittlere und große VP) |

### Layout | [Inhalt](#inhalt)

Die Konzeption dieser Webseite erfolgt nach dem **Mobile-First-Prinzip**. Dementsprechend wird f. kleine VP ein lineares Layout verwendet. Diese Tatsache hat zur Folge, dass die Elemente `pageHeader`, `pageNav` und `main` bzgl. dessen Layout vorerst keine spezifische Konfiguration, bezogen auf das primäre Container-Element `pageWrapper`, erfordern.

Bei den `figure`-Elementen handelt es sich um `flex`-Container. Das darin enthaltene `img`-Element und das `figcaption`-Element werden untereinander und zentriert angeordnet

#### **Breakpoint 1 (min. 48em):** | [Inhalt](#inhalt)

Bei Erreichen des ersten Breakpoints, bei `min-width: 48em`, wird `pageWrapper` zum `flex`-Container und weitere Konfigurationen werden erforderlich.

Der `pageHeader` soll die volle verfügbare Breite einnehmen und erhält dementsprechend `width: 100%;`.  
Die `pageNav` und `main` werden in einem zweispaltigen Layout angeordnet. Für die `pageNav` wird eine Breite von 20% definiert, während `main` durch das Attribut `flex: 1;` (kurz f. `flex: 0 0 1;`) der verbleibende verfügbare Platz (80%) zugewiesen wird.

Die Elemente der Navigation ändern in diesem Zusammenhang ihre Ausrichtung von horizontal nach vertikal.

`figure`-Elemente werden mittels `float: left;` linksseitig ausgerichtet und Textinhalte beginnen um den Container herumzufließen. Dies ist sowohl in der Sektion `welcome` als auch innerhalb der `article`-Elemente der Sektion `locations` zu beobachten.

Kurz vor erreichen des zweiten Breakpoints ist zu beobachten, wie das einspaltige Layout der `article`-Elmente in der Sektion `locations` aufgebrochen wird. Das ist daraf zurückzuführen, weil diese `flex`-Items mit dem Attribut `flex: 1 0 35rem;` versehen sind. Dies erlaub es ihnen zwar einerseits den zur Verfügung stehenden Platz gleichmäßig auszufüllen, es ihnen aber andererseits nicht gestattet eine kleinere Breite als 35rem einzunehmen. 

#### **Breakpoint 2 (min. 64em):** | [Inhalt](#inhalt)

Das Layout der Seite, die Position der Elemente `pageHeader`, `pageNav` und `main` verändert sich nun nicht mehr.

#### **Breakpoint 3 (min. 120em):** | [Inhalt](#inhalt)

Bei Viewports, welche eine Breite von 120em (1920px) überschreiten wird durch `align-items: flex-end;` die Ausrichtung von `ul`-Element welches in `pageNav` enthalten ist, sowie die einzelnen `li`-Elemente an der rechten Kante des jeweiligen Container-Elementes ausgerichtet. Außerdem wird die maximale Breite des `mainContentWrappers` auf 190rem begrenzt. Dies dient dazu das weitere Auseinanderdriften von Navigation und Content zu begrenzen, was ansonsten bei extrem breiten VP zu einem unansehnlichen Gesamtbild führen würde.

___

&copy; Sebastian Peschl 2023

