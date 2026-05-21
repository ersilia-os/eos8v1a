# Antimicrobial activity prediction against Schistosoma mansoni from public ChEMBL data

Bioactivity prediction of activity against Schistosoma mansoni, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (percent inhibition) assays, among others. A ranking score is provided for each model alongside a combined consensus score.



## Information
### Identifiers
- **Ersilia Identifier:** `eos8v1a`
- **Slug:** `antimicrobial-activity-smansoni`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Schistosomiasis`
- **Target Organism:** `Schistosoma mansoni`
- **Tags:** `Helminth`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `7`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Schistosoma mansoni from 6 ChEMBL-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 6 sub-models. Recommended threshold: 0.874. |
| merged_ic50_decoys | float | high | Probability from sub-model trained on IC50 measurements merged across 11 ChEMBL assays (cutoff 10 uM; n=1360 incl. decoys). Recommended threshold: 0.861. |
| merged_activity_decoys | float | high | Probability from sub-model trained on single-point % activity measurements merged across 12 ChEMBL assays (cutoff 50 %; n=1280 incl. decoys). Recommended threshold: 0.833. |
| general_activity_decoys | float | high | Probability from sub-model trained on single-point % activity measurements aggregated across 256 ChEMBL assays (cutoff 50 %; n=2500 incl. decoys). Recommended threshold: 0.826. |
| general_ic50_decoys | float | high | Probability from sub-model trained on IC50 measurements aggregated across 46 ChEMBL assays (cutoff 10 uM; n=2080 incl. decoys). Recommended threshold: 0.856. |
| general_inhibition | float | high | Probability from sub-model trained on inhibition % measurements aggregated across 33 ChEMBL assays (cutoff 50 %; n=703). Recommended threshold: 0.655. |
| general_ec50 | float | high | Probability from sub-model trained on EC50 measurements aggregated across 38 ChEMBL assays (cutoff 10 uM; n=365). Recommended threshold: 0.487. |


### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`

### Resource Consumption


### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos8v1a
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos8v1a
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
