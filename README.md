# Dokumentation zur Lösung d. ESA 10 (MMDE 10W)

Responsive Webseite, erstellt nach dem Mobile-First-Prinzip und unter Verwendung von Media-Queries.

## Inhalt

- [Dokumentation zur Lösung d. ESA 10 (MMDE 10W)](#dokumentation-zur-lösung-d-esa-10-mmde-10w)
  - [Inhalt](#inhalt)
  - [Aufbau von "index.html"](#aufbau-von-indexhtml)
  - [Wesentliche Konfigurationen in "style.css"](#wesentliche-konfigurationen-in-stylecss)
    - [Einbindung von Schriften](#einbindung-von-schriften)
    - [Farben und Einstellungen](#farben-und-einstellungen)
    - [Layout](#layout)

___

## Aufbau von "index.html"

Im `head` findet sich die obligatorische Angabe von `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.  
Ferner ist dort auch das Stylesheet ["style.css"](#wesentliche-konfigurationen-in-stylecss) mit `<link rel="stylesheet" href="style/style.css">` verlinkt.

Alle Elemente der Seite werden von einem DIV mit der `id="pageWrapper"` umschlossen. Diser Container befindet sich im `body`-Element.  
Innerhalb von `pageWrapper` finden sich die Hauptelemente `header` (`id="pageHeader"`), `nav` (`id="pageNav"`) und `main`.

Der Content von `main` ist in vier `section`-Elemente (`class="mainSection"`), von denen jedes seine individuelle ID besitzt, gegliedert. (Im Rahmen dieser Demonstration sind lediglich die ersten beiden von Relevanz.)  
Jede Sektion ist in zwei Bereiche eingeteilt, einem `header` (`class="secHeader"`) und einem oder mehere DIV(s) der `class="seContent"`, bzw. der `class="seContent artContainer"`.

Innerhalb der ersten Sektion mit der `id="welcome"` findet sich ein `img`-Element welches von einem `figcaption`-Element begleitet und von einem `figure`-Element umschossen ist. An diesem `figure`-Element wird nachfolgend die Anwendung der CSS-Regel `float: left;` demonstriert.  
Das `figure`-Element befindet sich zwischen zwei DIVs der `class="contTxt"` welche `p`-Elemente beinhalten.

In der folgenden Sektion mit der `id="locations"` findet sich neben einem DIV mit der `class="seContent"` ein weiteres mit der `class="seContent artContainer"`. Dieses beherbergt drei `article`-Elemente der `class="secArt"`. Ähnlich wie bei den `section`-Elementen gliedern sich auch die `article` in einen `header`-Bereich und einen Content-Bereich (DIV der `class="artContent"`). Innerhalb der Content-Bereiche befinden sich Texte und Bilder. Auch hier findet die CSS-Regel CSS-Regel `float: left;` Anwendung.

___

## Wesentliche Konfigurationen in "style.css"

### Einbindung von Schriften

Mittels `@import`-Anweisung werden zwei Schriftarten von [GoogleFonts](https://fonts.google.com/?category=Sans+Serif) importiert. Die Schriftart "Nunito" als Standard-Schriftart und "Kaushan Script" für Titel, Überschriften und Bildunterschriften.

### Farben und Einstellungen

Durch Verwendung von CSS-Variablen werden vier Farben und einige Einstellungen definiert.

| CSS-Variable(n) | Erläuterung |
|-|-|
| `--sand: #FFEBE0;`<br> `--canarianGreen: #00A017;` <br> `--canarianBlue: #0F45AE;`<br> `--contentFontColor: #2B0008;` | Farben |
| `--borderR: 1rem;` | Definition des Radius f. Rahmenecken. |
| `--borderPattern: 0 var(--borderR) 0 var(--borderR);` | Definition einer Standardkonfiguration f. Rahmenrundungen (nur unten links und oben rechts) |
| `--sVPmargin: .25rem;` | Definition eines Basis-Abstandswert |
| `--sVPVmargin: var(--sVPmargin) 0;` | Vertikale Abstandskonfiguration f. kleine Viewports |
| `--sVPHmargin: 0 calc(var(--sVPmargin) * 2);` | Horizontale Abstandskonfiguration f. kleine Viewports |
| `--sVPgap: .125rem;` | Definition eines Abstandes zwischen `flex`-Items (kleine VP) |
| `--sVPtitleFontSize: 4.25rem;` | Definition einer Basis-Schriftgröße f. Titel u. Überschriften |
| `--mVPmargin: calc(var(--sVPmargin) * 4) calc(var(--sVPmargin) * 2);` | Definition einer Abstandskonfiguration f. mittlere und große Viewports |
| `--mVPgap: calc(var(--sVPgap) * 5);` | Definition eines Abstandes zwischen `flex`-Items (mittlere und große VP) |

### Layout

Die Konzeption dieser Webseite erfolgt nach dem **Mobile-First-Prinzip**. Dementsprechend wird f. kleine VP ein lineares Layout verwendet. Diese Tatsache hat zur Folge, dass die Elemente `pageHeader`, `pageNav` und `main` bzgl. dessen Layout keine spezifische Konfiguration, bezogen auf das primäre Container-Element `pageWrapper` wie beispielsweise durch `display: flex` erfordern. Erst bei erreichen des ersten Breakpoints bei `min-width: 48em` wird `pageWrapper` zum `flex`-Container.