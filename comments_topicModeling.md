### Research questions
- würde die deutschen Übersetzungen rausnehmen, hast ja auch die ganze Arbeit auf Englisch geschrieben

### 1
- Warum sind die ganzen Imports auskommentiert? Dann löschen wenn nicht gebraucht
- Dass PyPDF2 nicht alles top erkannt hat sollte auch nicht hier stehen, sondern in der MA
- Was ist das für ein Kommentar hier?
  - c:\Users\luisa\AppData\Local\Programs\Python\Python310\lib\site-packages\joblib\backports.py:22: DeprecationWarning: The distutils package is deprecated and slated for removal in Python 3.12. Use setuptools or check PEP 632 for potential alternatives
  import distutils  # noqa

### General functions
- Die hast du doch alle schon im PreProcessing erwähnt: warum hier nochmal?

### Topic Modeling Parameters
- "[i]f you" - ist die eckige Klammer da richtig bei Topic number?
- Gleiches bei Eta: "[D]istributional"

### 9: modeling_and_equality
- könntest du noch besser erklären was die genau macht. Sehr rudimentär
- Generell könntest du drüber nachdenken Sachen zu loggen statt print() zu nutzen 

```
import logging

logging.basicConfig(level=logging.INFO)
logging.info("test")
```
- insbesondere weil du das Logging auch in [10] selbst einführst, allerdings mit "CRITICAL". Musst ein höheres Log-Level nehmen

### Finding the best topic number k:
- im Text: "good topic model", besser wäre sowas wie "meaningful topic modeling"
- den Part mit "liefert keine guten Ergebnisse" solltest du noch löschen

### Plotting the results for optimizing k:
- Wofür steht im Pfad hier und auch vorher schon das "HanTa"?

### Alpha and Beta Parameter Optimization with Optimal k:
- Typo: paramters 
- Gibts ein Grund für die 0,3 Schritte in den beiden Parametern? Warum nicht bspw. 0,1?

### Research Question 1: Topic Modeling
- Logging statt Print in "get_model_info"
- Sind die inline-Kommentare in "get_main_topics" noch relevant?
- Solltest noch in einem Ersatz erklären, wo der Wert "0.475" herkommt
- Auch hier Logging statt Print
- Das Berechnen von dem besten Modell würde ich nochmal umimplementieren.. das ist so nicht so schön -> können wir separat nochmal drüber reden
- [18] Logging statt Print!


- [12] Muss der Part mit?
```
Serving to http:// [...]
```
- kannst du ```gensim.models.ldamodel.LdaModel.load()``` nicht per Import schöner reinbekommen? Also so dass du dann bspw. nur noch ```ldamodel.load()```
- "Further analyses with the optimal topic model ~~from above~~" 
- Wie spielt hier der Github Link rein?
  - hast du dir da alles abgeguckt?
  - nur einzelne Methoden kopiert?
  - Also wenn du da ganze Algorithmen kopiert hast solltest du das deutlicher kenntlich machen
- [...] belong to the topics, e.g. the word "lexikalisch"

### Research Question 2: Hierarchical Clustering and Topic Similarity
- würde hier im empfehlen, dass du beim Term document bleibst und nicht noch text reinbringst. Macht das ganze lesbarer
```
def find_topics_for_each_document(corpus, model):
  topics_in_document = []
  i = 0
  
  for document in corpus:
    document_topics = model.get_document_topics(document)
    propabilities = []
    
    for topic in document_topics:
      topic_num, probability = topic
      propabilities.append(propability)
    topics_in_document.append(propabilities)
    i += 1
    
  return topics_in_document
```
- das dann natürlich auch in den anderen Methoden fortsetzen
- [32] Gibts ein Grund warum du hier die Reihenfolge der Laufvariablen j und i getauscht hast?
- Könntest die Berechnung der euklidischen Distanz noch in eine eigene Methode packen: würde die hier schlanker machen
  - Insbesondere weil du das ja auch mehrfach machst kannst du hier Synergien nutzen (siehe [33])
- Ist das alles hier in einer größeren Methode? (bspw. der Main?) Falls ja lieber in eine eigene packen
- Auch hier hängt noch der Python-Output drin. Den bekommt man doch beim Jupyter Notebook bestimmt raus oder?
- Bzgl. auskommentierter Code
  - entweder musst du das drin lassen und nicht auskommentieren, dann aber auch eine entsprechende Grafik ergänzen
  - oder du löscht den Code und schreibst, dass du im Repo noch die Hellinger Distanz gemacht hast. Dann kann man sich das immer noch angucken kann wenn man will

### Research Question 3: Mann-Kendall-Test
- Typo: "coprus" statt corpus
- "calculate_topic_average"
  - das erste Inline Kommentar kann weg, genau das sagt ja bereits der Methodenname bzw. die Beschreibung obendrüber
  - all_probs kannst du auch in all_probabilities umbenennen, tut nicht weh und ist lesbarer
- Könntest die ganze Line Plot Visualization in eine eigene Methode packen (so wie bei RQ4)

### Research Question 4: Use and Development of Research Methods
- "find_popular_methods" könntest du auch in "find_five_most_popular_methods"
- Im Text hast du "chart_and_cv" statt "chart_and_csv" stehen
- Methode "information_on_keywords" umbennenn mit noch irgendeinem Verb davor, bspw. retrieve_ oder load_

### Research Question 5: Analysis of Authors and Teams of Authors
- Methode "count_appearances" umbennenen in "count_appearances_descending"
- "rank_authors"
  - Text
    - "[...], and turns it into one large [...] in the respective year."
  - Code
    - Warum definierst du "authors_list_per_year" 2x, einmal außerhalb und einmal innerhalb der For-Schleife
    - Besser wäre die Definition zwischen den beiden For-Schleifen, also:
```
all_counted_authors = []
for year in authors:
  authors_list_per_year = []
  for team in year:
    ...
```
- "find_coauthors"
  - Hier das Gleiche wie in der vorherigen Methode mit der Liste "coauthors_list"
- "determine_edge_color"
  - Welche Farben sind das? Könntest du im Text nochmal erwähnen, weil das auf Basis des Hexadezimal-Codes zu sehen ist sportlich
- "determine_node_shape"
  - Dazu hast du oben keinen eigenen Text-Absatz
- Network Visualizations Methode finde ich etwas zu lang, könntest du nochmal in kleinere Methoden aufteilen, bspw. die For-Schleifen würden sich anbieten oder überall da wo du ein Inline-Kommentar hast
- Data Frame
  - "total_no_authors" <- wtf, lieber -> "total_number_authors"
- Auch hier Visualisierung als eigene Methode

### Research Question 6: Clustering of (Teams of) Authors and Certain Research Topics
- "get_authors_and_topics"
  - die 231 hier erschließt sich mir nicht: ist das weil erst ab hier die Autoren im Markdown hinterlegt sind? Solltest du nochmal kommentieren
  - Auch das solltest du noch als Konstante machen, weil das ja an mehreren Stellen vorkommt
    - Hat den Vorteil, dass das Notebook dann zukünftig leicher angepasst werden kann weil alle Konstanten an einer Stelle sind
    - bspw. wenn der Index sich verändert weil neue Dokumente aus der DhD-Konferenz 2024 dazu kommen
- "create_vectors"
  - Könntest die 8 noch als Konstante speichern, bspw. ```minimum_number_of_contributions = 8```
- "main"
  - Auch hier wieder die 231
  - 1202 = ?
- Visualisierungen auch gerne in eigene Methoden
- 
