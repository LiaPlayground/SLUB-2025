<!--

author:  Sebastian Zug; André Dietrich

language: de

narrator: Deutsch Female


@CSV
<script run-once style="display:block" modify="false">
async function csvToMarkdownTable(csvFile) {
  const response = await fetch(csvFile);
  const text = await response.text();
  const rows = Papa.parse(text).data;
  let markdownTable = "| " + rows[0].join(" | ") + " |\n"; // Header
  markdownTable += "| " + rows[0].map(() => "---").join(" | ") + " |\n"; // Separator
  for (let i = 1; i < rows.length; i++) {
    if (rows[i].length === rows[0].length) {
      markdownTable += "| " + rows[i].join(" | ") + " |\n";
    }
  }
  send.lia("LIASCRIPT: <!-- data-type='none' --" + ">" + markdownTable);
}
csvToMarkdownTable("@0")
"LIA: wait"
</script>
@end

@burn: <span class="burning-text">@0</span>

link:     style.css

script:   https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js
          https://cdn.jsdelivr.net/npm/@tensorflow/tfjs
          https://cdn.jsdelivr.net/npm/danfojs@1.1.2/lib/bundle.min.js
          https://cdn.jsdelivr.net/npm/echarts/dist/echarts.min.js

import:   https://raw.githubusercontent.com/liaTemplates/ABCjs/main/README.md
import:   https://raw.githubusercontent.com/LiaTemplates/GGBScript/refs/heads/main/README.md

-->

# Lebendige Dokumente mit LiaScript

Kontakte, links


## Agenda

1. LiaScript stellt sich vor

2. Tutorial

    - Grundlagen
    - Multimedia
    - Quizze
    - Interaktive Diagramme

3. Titanic - Datenanalyse

    - Python
    - R
    - JavaScript

4. Wo wollen wir hin?


## LiaScript stellt sich vor

    --{{0}}--
Hallo, mein Name ist LiaScript, ich bin eine auf Markdown basierende Sprache, die speziell entwickelt wurde um Lehrmaterialien zu erstellen.
Der Vorteil von Markdown ist, dass es bereits weit verbreitet ist, einfach zu schreiben und zu lesen ist, und dass es von vielen Plattformen unterstützt wird.
Der größte Nachteil ist jedoch, dass es @burn(statisch wie die Hölle) und keine Interaktivität bietet.

    --{{1}}--
Also haben sich meine Väter daran gemacht, Markdown von Grund auf neu zu denken...

     {{1-2}}
*******************************

?[Giorgio Moroder](https://music.youtube.com/watch?v=zhl-Cs1-sG4&si=fwB6LT2I0rQ0_CGE&start=300&end=312)<!-- style="border-radius: 10px; border: none" -->

> ... Once you free your mind about a concept of Harmony and of music being "correct" You can do whatever you want ...
>
> -- Giorgio Moroder (Erfinder der Disco-Musik)

******************************

    --{{2}}--
Eigentlich sind Tabellen in Markdown einfach zu erstellen und wie schon erwähnt, sind sie ganz schön @burn(statisch).
Eine Tabelle kann aber auch einen Datensatz representieren, der nach seiner idealen Visualisierung strebt.

      {{2}}
| Tier                      | Gewicht in kg | Lebensdauer (Jahre) | Mitogen |
| ------------------------- | ------------: | ------------------: | ------: |
| Maus                      |        0.028  |                02   |      95 |
| Fliegendes Eichhörnchen   |        0.085  |                15   |      50 |
| Braune Fledermaus         |        0.020  |                30   |      10 |
| Schaf                     |           90  |                12   |      95 |
| Mensch                    |           68  |                70   |      10 |


    --{{3}}--
Eine andere tabellarische Struktur kann eine andere Visualisierung erzeugen, die vom Ersteller feinabgestimmt werden kann.
Insgesamt beherrsche ich 10 unterschiedliche arten von Visualisierungen.

      {{3}}
<!--
data-type="heatmap"
data-title="Seattle Durchschnittstemperatur in Fahrenheit"
data-show
-->
| Seattle |  Jan |  Feb |  Mär |  Apr |  Mai |  Jun |  Jul |  Aug |  Sep |  Okt |  Nov |  Dez |
| -------:| ----:| ----:| ----:| ----:| ----:| ----:| ----:| ----:| ----:| ----:| ----:| ----:|
|       0 | 40.7 | 41.5 | 43.6 | 46.6 | 51.4 | 56.0 | 60.5 |  61.2 | 57.0 | 50.1 | 44.1 | 39.6 |
|       2 | 40.2 | 40.7 | 42.7 | 45.3 | 50.0 | 54.4 | 58.5 |  59.2 | 55.4 | 49.2 | 43.5 | 39.3 |
|       4 | 39.7 | 40.0 | 41.9 | 44.4 | 48.9 | 53.2 | 57.0 |  57.7 | 54.2 | 48.6 | 43.1 | 38.9 |
|       6 | 39.6 | 39.5 | 41.3 | 44.2 | 49.5 | 54.2 | 57.8 |  57.4 | 53.6 | 48.2 | 42.8 | 38.7 |
|       8 | 39.6 | 39.9 | 42.9 | 47.1 | 52.7 | 57.3 | 61.3 |  61.1 | 56.7 | 49.5 | 43.1 | 38.7 |
|      10 | 41.3 | 42.7 | 46.4 | 50.7 | 56.4 | 60.9 | 65.2 |  65.4 | 60.9 | 52.8 | 45.5 | 40.4 |
|      12 | 43.8 | 46.0 | 49.5 | 53.8 | 59.6 | 64.3 | 69.4 |  69.8 | 65.1 | 56.0 | 47.8 | 42.6 |
|      14 | 45.1 | 47.7 | 51.3 | 55.9 | 61.9 | 66.9 | 72.6 |  73.2 | 67.7 | 57.8 | 48.8 | 43.6 |
|      16 | 44.5 | 47.5 | 51.4 | 55.9 | 62.3 | 67.5 | 73.9 |  74.3 | 68.2 | 57.4 | 47.8 | 42.6 |
|      18 | 42.6 | 44.7 | 48.7 | 53.8 | 60.3 | 65.9 | 72.3 |  72.2 | 64.6 | 53.9 | 46.0 | 41.2 |
|      20 | 42.0 | 43.3 | 46.4 | 50.2 | 56.0 | 61.4 | 66.9 |  66.6 | 60.7 | 52.3 | 45.2 | 40.7 |
|      22 | 41.4 | 42.5 | 45.0 | 48.3 | 53.5 | 58.2 | 63.2 |  63.5 | 58.7 | 51.1 | 44.5 | 40.1 |

    --{{4}}--
Was Markdown immer gefehlt hat, war das Einbetten von multimedialen Inhalten ...

    --{{5}}--
Ich beherrsche Audio-Inhalte ...

     {{5-6}}
?[Sofia Rutaru: Червона рута](https://soundcloud.com/user-324560360/i1jlmnpatoro)

   --{{6}}--
Video kann ich auch und natürlich funktioniere ich auch auf Feature-Phones auch wenn diese offline sind.

     {{6-7}}
!?[LiaScript auf Nokia](https://www.youtube.com/watch?v=U_UW69w0uHE)

    --{{7}}--
Ich kann auch versuchen andere Arten von Inhalten einzubetten, die unter keine der beiden Kategorien fallen

      {{7}}
??[Plant Cell | Biology](https://sketchfab.com/3d-models/plant-cell-biology-0640c7a14f41400fbdac382c7de1d776 "A model of a plant cell with all major organelles.")

    --{{8}}--
Und noch viel viel mehr... Wir werden gleich zeigen wie alles funktioniert.

      {{8}}
```abc
X: 1
M: 4/4
L: 1/8
K: Emin
|:D2|"Em"EBBA B2 EB|~B2 AB dBAG|"D"FDAD BDAD|FDAD dAFD|
"Em"EBBA B2 EB|B2 AB defg|"D"afe^c dBAF|"Em"DEFD E2:|
```
@ABCJS.eval

    --{{9 US English Female}}--
You might have noticed that this document is being used like a PowerPoint presentation.
However, our intention was to utilize LiaScript in various contexts.
With LiaScript, you can create presentations, enable self-study through browser-based text-to-speech output, or read the content as simple yet interactive textbook, without animations.


## Tutorial

![](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExMGpnbDQ0NXl1cGc5MmR5bjU2NjA4aHIwMmF6a2NvbjBjY3M0dWxucCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/aRCHu0KPdSpGZB3bSZ/giphy.gif)<!-- style="width: 100%" -->


### Grundlagen

#Überschriften

Überschriften werden durch ein oder mehrere Rautezeichen # definiert.
Gliedere den folgenden Text in Abschnitte und Unterabschnitte!

#Absätze

Ein Absatz in Markdown wird durch eine Leerzeile definiert.
Ich kann auch Text **fett** oder *kursiv* darstellen.
Bitte teile mich in kleinere Abschnitte auf, damit ich besser verstanden werde!


#Listen

##Ungeordnete Listen

Eine ungeordnete Liste beginnt mit einem Sternchen.
Einem Bindestrich ader einem Pluszeichen
Füge weitere Elemente und Unterpunkte hinzu!

##Geordnete Listen

Eine geordnete Liste beginnt mit einer Zahl.
Füge weitere Absätze und ungeordnete Listen hinzu!

#Zitate

Ein Zitat wird durch ein Größerzeichen > eingeleitet.

Füge ein weiteres Zitat mit hinzu! -- Mit Quellenangabe.


### Multimedia

- __Markdown__

  - Links oder Verweise:
    `[name](url "title")`

    [Open Educational Resources](https://de.wikipedia.org/wiki/Open_Educational_Resources)

  - Ein Bild ist ein wichtiger Link __!__ :
    `![alt-text](url)`

    [OER-Logo](https://upload.wikimedia.org/wikipedia/commons/2/20/Global_Open_Educational_Resources_Logo.svg)

- __LiaScript__

  - Ist Audio genauso wichtig __?__ :
    `?[alt-text](...mp3 oder soundcloud-url)`

    [zugehOERt 104: How to OER-Policy](https://open-educational-resources.de/podlove/file/1666/s/webplayer/c/episode/OER104.mp3 "zugehOERt 104: How to OER-Policy? Das OER-Policy Kit gibt Antworten ... Mehr Informationen zum Podcast gibt es hier: https://open-educational-resources.de/oer104/ ")

  - Dann bestehen Videos aus Bild__!__ und Ton__?__:
    `!?[alt-text](...mp4 oder YouTube-url)`

    [Kollaborativer Online Editor für LiaScript](https://www.youtube.com/watch?v=EZuxYsMBKO4)

  - Last but not least, wenn man irgendwas anderes einbinden möchte:
    `??[alt-text](beliebige-url)`

    [Phet: Baue einen Atomkern](https://phet.colorado.edu/sims/html/build-a-nucleus/latest/build-a-nucleus_all.html?locale=de)

    [SketchFab: Astraea (Orbicella) curta](https://sketchfab.com/3d-models/astraea-orbicella-curta-bb767cd759fc428081ec9c302baf1ed1)

    [Irgendeine Schaltung](https://www.falstad.com/circuit/circuitjs.html?ctz=CQAgzCAMB0l3BWEBGATLBlWTADjagCzK4CcSmIFkVApgLTLIBQAhioYSEbt0d4V69kSRkmTx4HaKVmyA7NhyEAbAmSkU4yZGYB3Dl1RhUh7nCjMAxmaV8jFmjEnJCc9x7nTFcMCQSoyPKkgVCwkCwGqPx20UaClgauRiYoqLzGprrIKjRMphJc+SgqvDTYKDo6+mnCpbXcqboA5iCkKiW87Si4XE7MAE4NmSAqKVklcMwAlihoVB3FhVBhEcwASnOmCB1jCys0hOVOB9AIbPbce36mqHu8SHlVYajB7QhggjnyYJDkHU9JMxWnFuLhyjFuv0REgblcuGB5B07kVEuB5ukaHCwLk0YiOtikeBcboDPjiVj5jj+ptsbj0rxqShuKMLOgkOzTuckukUDjwETkPzSQLFvzyagocwclxCKlfrLweBIKi+gcqCAAC4DACutEsmzlpiOWKJJpWt3KZ241voMCChA+ktQ6lkRvIYVIG1se2KKPVRy06pg3Ip3G6EqlOV4gixKqoVPjEC4jwOzAAslReQqFnG1eyM1nGRUEESTCcC5mAoz+QgQuBhTbzlXswFWYy21bQ7HiTGleaRUbwG2hwPvT3zROmiyKpzOfQwNBXCIQmowAgyMEICHvXsRoGRodmfJrSfUzuRBByTmhznkCyaOcAPbgUx7Q5-DLW5yQFQui2vuAzAvv+74gEcpBlOEcBIpKYCkI6NyPNBfxIjs-73iwIG7GqEFQZIsGkPBiFoMhkikGhf7iCgwHcPIoy4Z+qzwIRxEfKRzFwBRahUcyWFggxKx4RqP5cZRGE0UAA)


### Quizze

Welche Farbe hat der Himmel, Mehrfachauswahl möglich?

- [[X]] Blau

------------------------------------------------------

Wann wurde die erste Mondlandung durchgeführt?

- [(X)] 1969

------------------------------------------------------

Wer hat die Relativitätstheorie entwickelt?

[[ Albert Einstein | Isaac Newton | Stephen Hawking | (Dieter Nuhr) ]]

------------------------------------------------------

Bestimmen Sie den Wert des folgenden Integrals:
$ I = \int_{0}^{\infty} \frac{e^{-x} - e^{-e^2 x}}{x}\, dx. $

[[2]]


### Interaktive Diagramme

Was haben diese beiden Darstellungen gemeinsam?


    9 |                                       (* dots)
      |
    y |                              *
    - |
    a |                    *
    x |
    i |          *
    s |
      |*
    0 +------------------------------------
      0            x-axis                 36


|   x | dots |
| ---:| ----:|
|   0 |    0 |
|  10 |    2 |
|  20 |    4 |
|  30 |    6 |


#### Mehr Tabellen

| Animal          | weight in kg | Lifespan years | Mitogen |
| --------------- | ------------:| --------------:| -------:|
| Mouse           |        0.028 |              2 |      95 |
| Flying squirrel |        0.085 |             15 |      50 |
| Brown bat       |        0.020 |             30 |      10 |
| Sheep           |           90 |             12 |      95 |
| Human           |           68 |             70 |      10 |

> [Spaß mit Tabellen](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/docs/master/README.md#Fun-With-Tables)


### Selber Weiterlernen

Workshop auf der DELFI-Tagung in Aachen (am 11.09.2023)

!?[Delfi Workshop - 1](https://www.youtube.com/watch?v=2FGRRC5lTNQ)

!?[Delfi Workshop - 2](https://www.youtube.com/watch?v=GrXanapDLYA)

## Titanic - Datenanalyse

[CSV](https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv)

> LiaScript Funktionalität importieren hat immer was mir \@ zu tun.
>
> https://github.com/topics/liascript-template


### Python - Survival of the Richest
<!--
persistent: true
-->

> Quelle: https://github/LiaTemplates/PyScript
>
> `import: https://raw.githubusercontent.com/liaTemplates/PyScript/main/README.md`

``` python @PyScript.repl
import pyodide.http
import pandas as pd
from io import StringIO

async def fetch_data(url):
    response = await pyodide.http.pyfetch(url)  # Daten abrufen
    csv_data = await response.string()  # Inhalt als String laden
    df = pd.read_csv(StringIO(csv_data))  # In DataFrame umwandeln
    return df

# Funktion direkt aufrufen mit `await` (NICHT `asyncio.run()`)
url = "https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv"
Titanic = await fetch_data(url)

# Ausgabe
Titanic
```

---


```python @PyScript.repl
import matplotlib.pyplot as plt

# Absolute Häufigkeit der Überlebenden und Nicht-Überlebenden berechnen
absolute_counts = Titanic.groupby(["Pclass", "Sex"])["Survived"].value_counts().unstack()

# Visualisierung der absoluten Häufigkeiten
absolute_counts.plot(kind="bar", stacked=True, figsize=(10,6), edgecolor="black")
plt.title("Absolute Häufigkeit der Überlebenden nach Passagierklasse und Geschlecht")
plt.xlabel("Passagierklasse und Geschlecht")
plt.ylabel("Anzahl der Passagiere")
plt.xticks(rotation=0)
plt.legend(["Nicht Überlebt", "Überlebt"], title="Status")
plt.grid(axis="y", linestyle="--", alpha=0.7)
plt.show()
plt
```

---

``` python @PyScript.repl
# Überlebenswahrscheinlichkeit nach Passagierklasse und Geschlecht berechnen
survival_rates = Titanic.groupby(["Pclass", "Sex"]) ["Survived"].mean().unstack()

# Visualisierung der Überlebenswahrscheinlichkeit
plt.figure(figsize=(10,6))
survival_rates.plot(kind="bar", edgecolor="black")
plt.title("Überlebenswahrscheinlichkeit nach Passagierklasse und Geschlecht")
plt.xlabel("Passagierklasse")
plt.ylabel("Überlebensrate")
plt.xticks(rotation=0)
plt.legend(title="Geschlecht")
plt.ylim(0, 1)
plt.grid(axis="y", linestyle="--", alpha=0.7)
plt.show()
plt
```

### R - Frauen und Kinder zuerst?

> https://github.com/LiaScript/CodeRunner
>
> `import: https://raw.githubusercontent.com/LiaScript/CodeRunner/master/README.md`

``` r
library(ggplot2)
library(dplyr)

# CSV-Datei einlesen
df <- read.csv("https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv")

# Alter bereinigen (NA-Werte entfernen)
df <- df %>% filter(!is.na(Age))

# Überlebenswahrscheinlichkeit nach Geschlecht und Alter (inkl. Männer)
women_children_men <- df %>% 
  mutate(Category = case_when(
    Sex == "female" & Age < 18 ~ "Female Child",
    Sex == "female" & Age >= 18 ~ "Female Adult",
    Sex == "male" & Age < 18 ~ "Male Child",
    Sex == "male" & Age >= 18 ~ "Male Adult"
  )) %>%
  group_by(Category) %>% 
  summarise(SurvivalRate = mean(Survived), .groups = 'drop')

# PNG-Datei für Analyse speichern
png("women_children_men_survival.png", width = 800, height = 400)

ggplot(women_children_men, aes(x = Category, y = SurvivalRate, fill = Category)) +
  geom_bar(stat = "identity", position = "dodge") +
  ggtitle("Überlebenswahrscheinlichkeit von Frauen, Männern und Kindern") +
  xlab("Kategorie") +
  ylab("Überlebensrate") +
  scale_fill_manual(values = c("blue", "red", "green", "purple"), name = "Kategorie") +
  theme_minimal()

dev.off()
```
@LIA.r

---

``` r
library(ggplot2)
library(dplyr)

# CSV-Datei einlesen
df <- read.csv("https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv")

# Alter bereinigen (NA-Werte entfernen)
df <- df %>% filter(!is.na(Age))

# PNG-Datei für Density Plot speichern
png("density_plot_survival.png", width = 800, height = 400)

ggplot(df, aes(x = Age, fill = as.factor(Survived))) +
  geom_density(alpha = 0.5) +
  ggtitle("Dichteverteilung des Alters unter Überlebenden und Verstorbenen") +
  xlab("Alter") +
  ylab("Dichte") +
  scale_fill_manual(values = c("red", "blue"), name = "Überlebt", labels = c("Nein", "Ja")) +
  theme_minimal()

dev.off()
```
@LIA.r

## JavaScript

> “Any application that can be written in JavaScript, will eventually be written in JavaScript.”
>
> -- [Atwood's Law](https://en.wikipedia.org/wiki/Jeff_Atwood)

---

``` markdown
Russland startete seinen Überfall auf die Ukraine
<script format="relativetime" unit="day" locale="de">
// Datum der Invasion
const invasionStartDate = new Date('2022-02-24');
// Erhalten der aktuellen Zeit
const currentDate = new Date();
// Berechnung der Differenz in Millisekunden
const differenceInMs = currentDate - invasionStartDate;

// Umrechnung von Millisekunden in Tage
const differenceInDays = differenceInMs / (1000 * 60 * 60 * 24);
// Berchnung der Anzahl der vollen Tage
const daysSinceInvasion = Math.floor(differenceInDays);

// Rückgabeergebnis
-daysSinceInvasion
</script>.
```

### Datensätze & Echtzeitdaten

Hier findest Du eine Übersicht einiger öffentlicher Plattformen, über die Regierungen und Behörden in Deutschland und der EU Daten kostenfrei zur Verfügung stellen:

1. **GovData – Open Data Portal der deutschen Verwaltung**

   - **Link:** https://www.govdata.de
   - **Beschreibung:** Zentraler Zugang zu offenen Daten der Bundes-, Landes- und Kommunalverwaltungen in Deutschland.

2. **EU Open Data Portal**  

   - **Link:** https://data.europa.eu/euodp/de/home
   - **Beschreibung:** Offizielles Portal der Europäischen Union, das Daten und Informationen der EU-Institutionen und -Organe bereitstellt.

3. **Destatis GENESIS-Online – Daten des Statistischen Bundesamts**  

   - **Link:** https://www-genesis.destatis.de
   - **Beschreibung:** Offizielle Datenbank des Statistischen Bundesamts (Destatis) mit umfangreichen statistischen Informationen zu Deutschland.

4. **Eurostat**  

   - **Link:** https://ec.europa.eu/eurostat
   - **Beschreibung:** Statistisches Amt der Europäischen Union, das vergleichbare europäische Statistiken zu Wirtschaft, Bevölkerung, Umwelt und mehr anbietet.

5. **Geoportal.de – Geodatenportal für Deutschland**

   - **Link:** https://www.geoportal.de
   - **Beschreibung:** Zentrales Portal für Geoinformationen in Deutschland, das Geodaten aus verschiedenen öffentlichen Stellen bündelt.

6. **Umweltbundesamt (UBA) – Offene Daten**

   - **Link:** https://www.umweltbundesamt.de/daten
   - **Beschreibung:** Hier werden umweltbezogene Daten, Berichte und Statistiken des Umweltbundesamtes bereitgestellt.

#### Open-Meteo API

> Open-Meteo ist ein Anbieter einer kostenfreien Wetter-API, die es Entwicklern ermöglicht, ohne API-Schlüssel oder Registrierung präzise und anpassbare Wettervorhersagen in ihre Anwendungen zu integrieren.
> Die API liefert eine Vielzahl von Wetterparametern – wie Temperatur, Niederschlag und Windgeschwindigkeit – und lässt sich dank klarer Dokumentation und eines Open-Source-Ansatzes problemlos in Projekte einbinden.
>
> Link: https://open-meteo.com/

``` markdown
longitude: <script default="13.33125" input="range" output="longitude">@input</script>

latitude: <script default="50.92558" input="range" output="latitude">@input</script>

<script run-once="true" style="display: block">
  fetch("https://api.open-meteo.com/v1/forecast?latitude=@input(`latitude`)&longitude=@input(`longitude`)&hourly=temperature_2m")
    .then(response => response.json())
    .then(data => {
      let table = "<!-- data-show data-type='line' data-title='Open-Meteo Wheather API' -->\n"

      table += "| Time | Temperature |\n"
      table += "| ---- | ----------- |\n"

      for (let i=0; i < data.hourly.time.length; i++) {
        table += "| " + data.hourly.time[i] + " | " + data.hourly.temperature_2m[i] + " |\n"
      }
      send.lia("LIASCRIPT: "+table) }
    )
    .catch(e => {
      send.lia("ups, something went wrong")
    })
  "waiting for the weather"
</script>
```

### Code Verstehen
<!--
@val: <script input="range" min="-10" max="10" value="@1" step="0.1" default="@1" output="@0">@input</script>
-->

https://github.com/LiaTemplates/GGBScript/


    {{1}}
``` js @GGBScript
Titel("Punkt A & B")

// Definiere zwei Punkte
const A = Punkt(1, 2, "A")
const B = Punkt([4, 6], "B")
```

    {{2}}
``` js @GGBScript
Titel("Strecke S")

// Definiere Punkte
const A = Punkt(1, 2, "A")
const B = Punkt(4, 6, "B")

// Erzeuge eine Strecke
const S = Strecke(A, B, "S")
```

    {{3}}
*************************************

Gegeben sei ein Dreieck, dass durch die folgenden Punkte definiert ist

- $A$ = (@val(A0,1), @val(A1,2))
- $B$ = (@val(B0,4), @val(B1,2))
- $C$ = (@val(C0,2), @val(C1,5))

Berechne den Mittelpunkt

``` js @GGBScript
// Definiere Punkte
let A = Punkt(@input(`A0`), @input(`A1`), "A")
let B = Punkt(@input(`B0`), @input(`B1`), "B")
let C = Punkt(@input(`C0`), @input(`C1`), "C")

// Erzeuge ein Polygon
const P = Polygon(A, B, C)

// Berechne den Mittelpunkt
const M = Mittelpunkt(P)

Rotation(P, M, 0)
```

*************************************


## Wie mache ich weiter?

Wir hoffen, dass wir Sie überzeugen konnten. Falls Sie nun von den vielen Funktionen überwältigt sind und sich fragen, wo Sie anfangen sollen – wie Sie einen Kurs erstellen und teilen – empfehlen wir Ihnen als Einstieg die LiaScript-Website, die wir kostenlos auf GitHub hosten:

https://liascript.github.io

Dort finden Sie weitere Informationen sowie die Dokumentation, die ebenfalls als LiaScript-Kurs geschrieben ist, ebenso wie Vorschläge und Neuigkeiten in unserem Blog.

Wer direkt aus der [Dokumentation](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaScript/docs/master/README.md) heraus starten möchte, kann dies tun, indem er auf den folgenden Link klickt:

https://liascript.github.io/LiveEditor/?/show/file/https://raw.githubusercontent.com/LiaScript/docs/master/README.md

Außerdem existiert ein YouTube-Kanal, auf dem wir regelmäßig neue Funktionen und Anwendungsbeispiele vorstellen:

https://www.youtube.com/@liascript4180

... Mit einer sich selbst erklärenden Dokumentation ...

https://www.youtube.com/watch?v=ElxYssylmaw&list=PL7LrRfaZulhc3w4rebIl8Dnck6zqdKeNn

Das gesamte Projekt wird auf GitHub gehostet:

https://github.com/LiaScript

Dort können Sie uns Feedback geben, Fehler melden oder Ihre eigenen Erweiterungen beitragen. Für schnelle Antworten und Diskussionen haben wir zudem einen Chat auf Gitter:

https://app.gitter.im/#/room/#LiaScript_community:gitter.im

… oder senden Sie uns einfach eine E-Mail an:

LiaScript@web.de

Oder folgen und kontaktieren Sie uns auf Twitter/X:

https://twitter.com/LiaScript