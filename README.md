<!--

language: de
narrator: Deutsch Female

@style
@keyframes burn {
  0% {
    text-shadow: 0 0 5px #ff0, 0 0 10px #ff0, 0 0 15px #f00, 0 0 20px #f00,
      0 0 25px #f00, 0 0 30px #f00, 0 0 35px #f00;
  }
  50% {
    text-shadow: 0 0 10px #ff0, 0 0 15px #ff0, 0 0 20px #ff0, 0 0 25px #f00,
      0 0 30px #f00, 0 0 35px #f00, 0 0 40px #f00;
  }
  100% {
    text-shadow: 0 0 5px #ff0, 0 0 10px #ff0, 0 0 15px #f00, 0 0 20px #f00,
      0 0 25px #f00, 0 0 30px #f00, 0 0 35px #f00;
  }
}

.burning-text {
  font-weight: bold;
  color: #fff;
  animation: burn 1.5s infinite alternate;
}
@end

@burn: <span class="burning-text">@0</span>

script:   https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js
          https://cdn.jsdelivr.net/npm/@tensorflow/tfjs
          https://cdn.jsdelivr.net/npm/danfojs@1.1.2/lib/bundle.min.js
          https://cdn.jsdelivr.net/npm/echarts/dist/echarts.min.js

import:   https://raw.githubusercontent.com/liaTemplates/ABCjs/main/README.md

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

     {{1-2}}
<section>

    --{{1}}--
Also haben sich meine Väter daran gemacht, Markdown von Grund auf neu zu denken...

?[Giorgio Moroder](https://music.youtube.com/watch?v=zhl-Cs1-sG4&si=fwB6LT2I0rQ0_CGE&start=300&end=312)<!-- style="border-radius: 10px; border: none" -->

> ... Once you free your mind about a concept of Harmony and of music being "correct" You can do whatever you want ...
>
> -- Giorgio Moroder (Erfinder der Disco-Musik)

</section>

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
??[Esther’s scroll in a cover](https://sketchfab.com/3d-models/esthers-scroll-in-a-cover-21a13eba33cb4343bab56f0c0f982876 "Historical Museum of the City of Kraków")

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

### Grundlagen

### Multimedia

### Quizze

### Interaktive Diagramme

## Titanic - Datenanalyse

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

  send.lia("LIASCRIPT: <!-- data-type='none' -->\n" + markdownTable);
}

csvToMarkdownTable("https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv")

"LIA: wait"
</script>

### Python - Survival of the Richest
<!--
persistent: true
-->


`import: https://raw.githubusercontent.com/liaTemplates/PyScript/main/README.md`

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

https://github.com/liaScript/coderunner

`import: https://raw.githubusercontent.com/LiaScript/CodeRunner/master/README.md`

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

### JavaScript

> “Any application that can be written in JavaScript, will eventually be written in JavaScript.”
>
> -- [Atwood's Law](https://en.wikipedia.org/wiki/Jeff_Atwood)

``` js
async function csvToMarkdownTable(csvFile) {
    const response = await fetch(csvFile);
    const text = await response.text();

    const results = Papa.parse(text);

    const data = results.data.filter(row => row.Age !== null);
            
    // Gruppieren der Überlebensrate nach Altersgruppen
        const ageBins = [0, 10, 20, 30, 40, 50, 60, 70, 80];
        const survivalRates = ageBins.map((bin, i) => {
            if (i === ageBins.length - 1) return null;
            const ageGroup = data.filter(d => d.Age >= bin && d.Age < ageBins[i + 1]);
            const survivalRate = ageGroup.length ? ageGroup.filter(d => d.Survived === 1).length / ageGroup.length : 0;
            return { bin: `${bin}-${ageBins[i + 1]}`, survivalRate: survivalRate * 100 };
        }).filter(d => d !== null);
            
        const option = {
            title: { text: "Überlebenswahrscheinlichkeit nach Alter" },
            xAxis: { type: "category", data: survivalRates.map(d => d.bin) },
            yAxis: { type: "value", name: "Überlebensrate (%)" },
            series: [{ data: survivalRates.map(d => d.survivalRate), type: "bar" }]
        };
        
        console.log(option);


    console.html(`<lia-chart options="${option}"></lia-chart>`);
    send.lia("LIA: stop");
}

csvToMarkdownTable("https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv")

"LIA: wait"
```
<script>
@input
</script>

## Wo wollen wir hin?