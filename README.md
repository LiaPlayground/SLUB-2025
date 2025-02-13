<!--

author:  Sebastian Zug; André Dietrich

language: de

narrator: Deutsch Female

import:   https://raw.githubusercontent.com/LiaTemplates/LiveEdit-Embeddings/refs/tags/0.0.1/README.md

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

[![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://raw.githubusercontent.com/Cross-Lab-Project/presentations/refs/heads/main/TUC_digital_2024/presentation.md)

# Lebendige Daten mit LiaScript

<h2>LiaScript Tutorial im Rahmen der _Love Data Week_ 2025</h2>

---------------------

QRCODE des Kurses

----------------------

<h5>
<p>Dr. Andre Dietrich, Dr. Ines Aubel, Prof. Dr. Sebastian Zug</p>
<p>TU Bergalakdemie Freiberg</p>
<p>Februar 2025</p>
</h5>

<div>

---

</div>

## Warum LiaScript?

                        {{0-3}}
*******************************************************

> _"Another approach is to use a system like LiaScript [2], which enables the creation of __interactive online courses__ based on Markdown and JavaScript. It allows for embedding external elements including interactive elements, e.g. videos. The courses themselves can be developed in a decentralized way."_ 
>
> (Sebastian Speiser, "Composition of Open Educational Resources through Dynamic Linking of Modular Components", Proceedings of the 2024 16th International Conference on Education Technology and Computers)

*******************************************************

                        {{1-3}}
*******************************************************

> ... und was hat das mit Forschungsdatenmanagement zu tuen?


*******************************************************

                        {{1-2}}
*******************************************************


```ascii


| Aspekte des Forschungsdatenmanagements | Einsatz von LiaScript  |
|                                        | Lehre      | Anwendung |  
| -------------------------------------- | ---------- | --------- |
| 1. Datenmanagement & Speicherung       |    ┓       |           |
| 2. Metadaten & Dokumentation           |    ┃       |     ✅    |
| 3. Datenanalyse & Verarbeitung         |    ┃       |     ✅    |
| 4. Datenversionierung & Kollaboration  |    ┣ ✅    |           |
| 5. Datenpublikation & Open Science     |    ┃       |           |
| 6. Langzeitarchivierung                |    ┛       |           |                                             .

```

*******************************************************

                        {{2-3}}
*******************************************************

```ascii
                                                                              .-.
                                                                             ( 0 ) "__LiaScript als Konzept__"
| Aspekte des Forschungsdatenmanagements | Einsatz von LiaScript  |           .-.

|                                        | Lehre      | Anwendung |    .-.
| -------------------------------------- | ---------- | --------- |   ( 1 ) "__LiaScript Grundlagen__" 
| 1. Datenmanagement & Speicherung       |    ┓       |           |    .-.
| 2. Metadaten & Dokumentation           |    ┃       |     ✅  .-.
| 3. Datenanalyse & Verarbeitung         |    ┃       |     ✅ ( 2 ) "__LiaScript für die Datenanalyse__" 
| 4. Datenversionierung & Kollaboration  |    ┣ ✅    |         .-.
| 5. Datenpublikation & Open Science     |    ┃  .-.  |           |
| 6. Langzeitarchivierung                |    ┛ ( 3 ) "__LiaScript meets OER__"                                  .
                                                 .-.
 
```

*******************************************************

## 0. LiaScript als Konzept

                        {{0-1}}
*******************************************************

> __1. Wir trennen Darstellung und Inhalt! Alle Elemente werden soweit wie möglich durch eine rein textuelle Repräsentation ausgedrückt.__

```markdown @embed.style(height: 550px; min-width: 100%; border: 1px black solid)
# Vom Text zur Darstellung

__Text__

Hallo Welt!

__Mathematik__

$f(x) = x^2$

__Tabellen__

| X | B(y) | C(y) |
|---|:----:|:----:|
| 1 |   2  |   3  |
| 4 |   5  |   6  |

```

*******************************************************

                        {{1-2}}
*******************************************************

> __2. Lehre lebt von Interaktion__

```markdown @embed.style(height: 550px; min-width: 100%; border: 1px black solid)
# Lehre lebt von Interaktion

__Tabellen als Grafiken__

| X | B(y) | C(y) |
|---|:----:|:----:|
| 1 |   2  |   3  |
| 4 |   5  |   6  |

__Sprache__

> Click to run!
>
> {{|> Deutsch Female}}
> Markdown ist eine vereinfachte Auszeichnungssprache, die der Ausgangspunkt unserer Entwicklung von LiaScript war.

__Quizze__

Wann wurde die Slub gegründet?

- [(X)] 1996
- [( )] 1896
```

*******************************************************

                        {{2-3}}
*******************************************************

> __3. Der Browser kann viel mehr als Webseiten anzuzeigen.__

````markdown @embed.style(height: 550px; min-width: 100%; border: 1px black solid)

<!--
import: https://raw.githubusercontent.com/liaTemplates/ABCjs/main/README.md
-->

# Browserfeatures / JavaScript

__Sprache__

> Click to run!
>
> {{|> Deutsch Female}}
> Markdown ist eine vereinfachte Auszeichnungssprache, die der Ausgangspunkt unserer Entwicklung von LiaScript war.

__Datenspeicherung__

``` abc  @ABCJS.render
X:353
T: GLUECK AUF DER STEIGER KOEMMT
N: E1512
O: Europa, Mitteleuropa, Deutschland
R: Staende -, Bergmanns - Lied
M: 4/4
L: 1/16
K: G
 | G8F4asdfasA4 | G8z8 |
B8A4c4 | B8z4
G2A2 | B4B4B4A2B2 | c4A3AA4
A2B2 | c4c4c4B2c2 | d4B3BB4
A4 | G8F8 | G4e4d4
c2A2 | B8A8 | G8z8
```

````


## 1. LiaScript Tutorial

QR Code und Link 



## 2. LiaScript in der Datenanalyse

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

## 3. LiaScript meets OER




## Selbst Weiterlernen

Workshop auf der DELFI-Tagung in Aachen (am 11.09.2023)

!?[Delfi Workshop - 1](https://www.youtube.com/watch?v=2FGRRC5lTNQ)

!?[Delfi Workshop - 2](https://www.youtube.com/watch?v=GrXanapDLYA)

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