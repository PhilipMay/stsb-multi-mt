# STSb Multi MT
Machine translated multilingual STS benchmark dataset.

This is a multilingual translation of the [STSbenchmark dataset](https://ixa2.si.ehu.es/stswiki/index.php/STSbenchmark). Translation has been done with [deepl.com](https://www.deepl.com/). It can be used to train [sentence embeddings](https://github.com/UKPLab/sentence-transformers) like [T-Systems-onsite/cross-en-de-roberta-sentence-transformer](https://huggingface.co/T-Systems-onsite/cross-en-de-roberta-sentence-transformer).

## Content
- folder `raw-data`: the raw data how it was convertet with deepl.com
- folder `data`: the data: sentence1, sentence2, similarity_score
- `convert.py`: script to convert data from `raw-data` to `data`

## Example: load the Data
```python
import csv

with open(filepath, newline="", encoding="utf-8") as csvfile:
    csv_dict_reader = csv.DictReader(
        csvfile,
        dialect='excel',
        fieldnames=["sentence1", "sentence2", "similarity_score"],
    )
    for row in csv_dict_reader:
       print(row)
```

## Known Issues
- the chinese dataset has an error with text that is missing - see https://github.com/PhilipMay/stsb-multi-mt/issues/1
