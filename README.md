# BERT Long Document Classification
an easy-to-use interface to fully trained BERT based models for multi-class and multi-label document classification.

pre-trained models are currently available for two clinical note (EHR) phenotyping tasks: smoker identification and obesity detection.

To sustain future development and improvements, we interface [pytorch-transformers](https://github.com/huggingface/pytorch-transformers)
for all language model components of our architectures.

| Model             |          Dataset |  # Labels |  Evaluation F1 |
|-------------------|------------------|--------|----------|
|   n2c2_2006_smoker_lstm   | I2B2 2006: Smoker Identification            | 4 |      0.981        |
| n2c2_2008_obesity_lstm | I2B2 2008: Obesity and Co-morbidities Identification    | 15 |      0.997        |

# Installation

Install with pip:

```
pip install bert_document_classification
```

or directly:

```
pip install git+https://github.com/AndriyMulyar/bert_document_classification
```

# Use
Maps text documents of arbitrary length to binary vectors indicating labels.
```python
from bert_document_classification.models import SmokerPhenotypingBert
from bert_document_classification.models import ObesityPhenotypingBert

smoking_classifier = SmokerPhenotypingBert(device='cpu', batch_size=10) #defaults to GPU prediction

obesity_classifier = ObesityPhenotypingBert(device='cuda', batch_size=10) #or CPU if you would like.

smoking_classifier.predict(["I'm a document! Make me long and the model can still perform well!"])
```
More [examples](/examples).



# Notes
- You will need a GPU to apply these models if you would like any hint of speed in your predictions.
- Alternatively, for bulk document prediction where speed is not of concern lots of available memory and CPU cores would do the trick.
- Model downloads are cached in `~/.cache/torch/bert_document_classification/`. Try clearing this folder if you have issues.



# Acknowledgement
If you found this useful, consider citing our accepted extended abstract accepted at NeurIPS ML4Health 2019.

```
Format bibtex citation
```

Implementation, development and training in this project were supported by funding from the Mark Dredze Lab at Johns Hopkins University.