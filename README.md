<!--

language: de
narrator: Deutsch Female

script:   https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js
          https://cdn.jsdelivr.net/npm/@tensorflow/tfjs
          https://cdn.jsdelivr.net/npm/danfojs@1.1.2/lib/bundle.min.js
          https://cdn.jsdelivr.net/npm/echarts/dist/echarts.min.js

-->

# Lebendige Dokumente mit LiaScript

Kontakte, links


## Agenda

1. LiaScript stellt sich vor

## LiaScript

    --{{1}}--
Hallo und herzlich willkommen zum ersten Workshop des Projekts "Lebendige Dokumente"! In diesem Workshop werden wir uns mit der Frage beschäftigen, wie wir wissenschaftliche Dokumente so gestalten können, dass sie nicht nur statisch und unveränderlich sind, sondern sich auch weiterentwickeln und anpassen können.


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
        if (rows[i].length === rows[0].length) { // Sicherstellen, dass die Zeilen korrekt formatiert sind
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

### Wo wollen wir hin?