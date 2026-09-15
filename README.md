# AI-based Early Detection of Cybersecurity Incidents in Medical Device Vigilance

This repository contains the code accompanying the paper **"AI-based Early Detection of Cybersecurity Incidents in Medical Device Vigilance"** submitted to npj Digital Medicine.

## Repository contents

### Classification models

- `Classic_ML_SVM.ipynb` – TF-IDF + Support Vector Machine classifier.
- `Classic_ML_XGBoost.ipynb` – TF-IDF + XGBoost classifier.
- `Classification_Bert_Longformer.ipynb` – Longformer-based text classification.
- `Classification_Gemma.ipynb` – Gemma-based classifier using parameter-efficient fine-tuning (PEFT/LoRA).

### Prompt-based LLM approaches

- `Causal_local_Gemma.ipynb` – Zero-shot/few-shot classification using Gemma locally.
- `Causal_cloud_GPT.ipynb` – Zero-shot/few-shot classification using GPT models.
- `Causal_cloud_workflow_prompt.ipynb` – Few-shot prompting workflow using GPT models.

## Data

The dataset is comprised of 2762 reports downloaded from the American 'Manufacturer and User Device Experience' (MAUDE) database (https://open.fda.gov/apis/device/event/) and annotated by the authors for cybersecurity relevance. The notebooks expect a parquet dataset located at

```
data/cybersecurity_annotated_data.pq
```

The dataset should contain at least the following columns:

- `ID` – MAUDE report identifier
- `text` – report narrative
- `label` – binary class label (`1` = cybersecurity-related, `0` = non-cybersecurity)

## Installation

Create a Python environment and install the required packages:

```bash
pip install -r requirements.txt
```

## Running the notebooks

Each notebook can be run independently:

1. Install the required packages and place the dataset in the `data/` folder.
2. Open the desired notebook in JupyterLab or VS Code.
3. Execute the notebook from top to bottom.

The classical machine learning notebooks reproduce the SVM and XGBoost experiments, the transformer notebooks reproduce the Longformer and Gemma classification experiments, and the causal notebooks reproduce the local and cloud prompt-based approaches described in the paper.

> **Note:** A CUDA-capable GPU is recommended for the Longformer, Gemma classification notebooks and the local causal notebook. The local causal workflow additionally requires a local Ollama installation. The cloud-based notebooks require access to the OpenAI API. 

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.