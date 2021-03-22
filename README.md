# STSb Multi MT
Machine translated multilingual STS benchmark dataset.

These are different multilingual translations and the English original of the [STSbenchmark dataset](https://ixa2.si.ehu.es/stswiki/index.php/STSbenchmark). Translation has been done with [deepl.com](https://www.deepl.com/).

- Available languages are: de, en, es, fr, it, nl, pl, pt, ru, zh
- Dataset splits are called: train, dev, test

It can be used to train [sentence embeddings](https://github.com/UKPLab/sentence-transformers) like [T-Systems-onsite/cross-en-de-roberta-sentence-transformer](https://huggingface.co/T-Systems-onsite/cross-en-de-roberta-sentence-transformer).

Please [open an issue](https://github.com/PhilipMay/stsb-multi-mt/issues/new) if you have questions or want to report problems.

## Content
- folder `raw-data`: the raw data how it was convertet with deepl.com
- folder `data`: the data: sentence1, sentence2, similarity_score
- `convert.py`: script to convert data from `raw-data` to `data`

## Examples of Use
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

## Manual Testing of Datasets
Language | 1st train | 1000st train | last train | 1st dev | 1000st dev | last dev | 1st test | 1000st test | last test
---------|-----------|--------------|------------|---------|------------|----------|----------|-------------|----------
de       | ok        | ok           | ok         |       |          |        |        |           |
en       | --        | --           | --         | --      | --         | --       | --       | --          | --
es       |         |            |          |       |          |        |        |           |
fr       |         |            |          |       |          |        |        |           |
it       |         |            |          |       |          |        |        |           |
nl       |         |            |          |       |          |        |        |           |
pl       |         |            |          |       |          |        |        |           |
pt       |         |            |          |       |          |        |        |           |
ru       |         |            |          |       |          |        |        |           |
zh       |         |            |          |       |          |        |        |           |
