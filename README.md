# Thesis

In this repository, the code and all other documents of my Master's thesis are stored.

The two Jupyter notebooks, *MA_Preprocessing* and *MA_TopicModeling* are the core files. 

Conducting all preprocessing steps and producing all variables needed for further use, *MA_Preprocessing* should be executed first.
The corpus consisting of all DHd books of abstracts and on which the preprocessing is conducted, is given in the folder *Corpus*
Since some steps in the preprocessing pipeline are time-consuming, the final variables are stored and given in the folder *Variables*.

*MA_TopicModeling*, then, loads the saved variables from the preprocessing notebook and uses them to conduct Topic Modeling.
The resulting models are stored in the folder *Models*.
The visualizations for answering the research questions are stored in a separate folder for each question in *Figures*.

The code was created and executed in Python 3.10.5.


### Known issues:
When executing the import of several functions from *MA_Preprocessing* into *MA_TopicModeling* in the import cell takes a considerable amount of time (> 5 minutes), it usually helps to stop the cell execution and restart. 