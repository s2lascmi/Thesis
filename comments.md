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
- insbesondere weil du das Logging auch in [10] selbst einführst

### Finding the best topic number k:
