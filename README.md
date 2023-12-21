# STSb Multi MT
Machine translated multilingual STS benchmark dataset.

These are different multilingual translations and the English original of the [STSbenchmark dataset](https://ixa2.si.ehu.es/stswiki/index.php/STSbenchmark). Translation has been done with [deepl.com](https://www.deepl.com/).

- Available languages are: de, en, es, fr, it, ja, nl, pl, pt, ru, zh
- Dataset splits are called: train, dev, test

It can be used to train [sentence embeddings](https://github.com/UKPLab/sentence-transformers) like [T-Systems-onsite/cross-en-de-roberta-sentence-transformer](https://huggingface.co/T-Systems-onsite/cross-en-de-roberta-sentence-transformer).

Please [open an issue](https://github.com/PhilipMay/stsb-multi-mt/issues/new) if you have questions or want to report problems.

This dataset provides pairs of sentences and a score of their similarity.

score | 2 example sentences | explanation
------|---------|------------
5 | *The bird is bathing in the sink.<br/>Birdie is washing itself in the water basin.* | The two sentences are completely equivalent, as they mean the same thing.
4 | *Two boys on a couch are playing video games.<br/>Two boys are playing a video game.* | The two sentences are mostly equivalent, but some unimportant details differ.
3 | *John said he is considered a witness but not a suspect.<br/>“He is not a suspect anymore.” John said.* | The two sentences are roughly equivalent, but some important information differs/missing.
2 | *They flew out of the nest in groups.<br/>They flew into the nest together.* | The two sentences are not equivalent, but share some details.
1 | *The woman is playing the violin.<br/>The young lady enjoys listening to the guitar.* | The two sentences are not equivalent, but are on the same topic.
0 | *The black dog is running through the snow.<br/>A race car driver is driving his car through the mud.* | The two sentences are completely dissimilar.

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
none

## Manual Testing of Datasets
Language | 1st train | 1000st train | last train        | 1st dev | 1000st dev | last dev | 1st test | 1000st test | last test
---------|-----------|--------------|-------------------|---------|------------|----------|----------|-------------|----------
de       | ok        | ok           | ok                | ok      | ok         | ok       | ok       | ok          | ok
en       | ok        | ok           | ok                | ok      | ok         | ok       | ok       | ok          | ok
es       |           |              |                   |         |            |          |          |             |
fr       |           |              |                   |         |            |          |          |             |
it       |           |              |                   |         |            |          |          |             |
ja       |           |              |                   |         |            |          |          |             |
nl       | ok        | ok           | partially English | ok      | ok         | ok       | ok       | ok          | poor grammar
pl       |           |              |                   |         |            |          |          |             |
pt       |           |              |                   |         |            |          |          |             |
ru       |           |              |                   |         |            |          |          |             |
zh       |           |              |                   |         |            |          |          |             |
