# EditSQL for [SParC](https://yale-lily.github.io/sparc)


### Dependency

The model is tested in python 3.6 and pytorch 1.0. We recommend using `conda` and `pip`:

```
conda create -n editsql python=3.6
source activate editsql
pip install -r requirements.txt
```

Download Pretrained BERT model from [here](https://drive.google.com/file/d/1f_LEWVgrtZLRuoiExJa5fNzTS8-WcAX9/view?usp=sharing) as `model/bert/data/annotated_wikisql_and_PyTorch_bert_param/pytorch_model_uncased_L-12_H-768_A-12.bin`.

Download the database sqlite files from [here](https://drive.google.com/file/d/1a828mkHcgyQCBgVla0jGxKJ58aV8RsYK/view?usp=sharing) as `data/database`.


### Run SParC experiment

First, download [SParC](https://yale-lily.github.io/sparc). Then please follow

- use cdseq2seq: `run_sparc_cdseq2seq.sh`. We saved our experimental logs at `logs/logs_sparc_cdseq2seq`
- use cdseq2seq with segment copy:  `run_sparc_cdseq2seq_segment_copy.sh`. We saved our experimental logs at `logs/logs_sparc_cdseq2seq_segment_copy`
- use editsql: `run_sparc_editsql.sh`. We saved our experimental logs at `logs/logs_sparc_editsql`. The dev results can be reproduced by `test_sparc_editsql.sh` with the trained model downloaded from [here](https://drive.google.com/file/d/1MRN3_mklw8biUphFxmD7OXJ57yS-FkJP/view?usp=sharing) and put under `logs/logs_sparc_editsql/save_31_sparc_editsql`.

This reproduces the SParC result in "Editing-Based SQL Query Generation for Cross-Domain Context-Dependent Questions".

<table>
  <tr>
    <th></th>
    <th colspan="2">Question Match</th>
    <th colspan="2">Interaction Match</th>
  </tr>
  <tr>
    <td></td>
    <td>Dev</td>
    <td>Test</td>
    <td>Dev</td>
    <td>Test</td>
  </tr>
  <tr>
    <td>CD-Seq2Seq</td>
    <td>21.9</td>
    <td>-</td>
    <td>8.1</td>
    <td>-</td>
  </tr>
  <tr>
    <td>CD-Seq2Seq+segment copy (use predicted query)</td>
    <td>21.7</td>
    <td>-</td>
    <td>9.5</td>
    <td>-</td>
  </tr>
  <tr>
    <td>CD-Seq2Seq+segment copy (use gold query)</td>
    <td>27.3</td>
    <td>-</td>
    <td>10.0</td>
    <td>-</td>
  </tr>
  <tr>
    <td>EditSQL (use predicted query)</td>
    <td>47.2</td>
    <td>47.9</td>
    <td>29.5</td>
    <td>25.3</td>
  </tr>
  <tr>
    <td>EditSQL (use gold query)</td>
    <td>53.4</td>
    <td>54.5</td>
    <td>29.2</td>
    <td>25.0</td>
  </tr>
</table>

