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