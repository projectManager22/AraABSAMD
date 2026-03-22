# AraABSAMD: Arabic Aspect-Based Sentiment Analysis Dataset for Moroccan Education

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Overview

**AraABSAMD** is the first publicly available dataset for Aspect-Based Sentiment Analysis (ABSA) in the Moroccan education domain. It contains **1,360 manually annotated tweets** in Modern Standard Arabic (MSA), covering discussions about education in Morocco.

This dataset was created to address the lack of Arabic ABSA resources in the education sector and to enable fine-grained opinion mining for educational stakeholders, policymakers, and researchers.

## 1. Dataset Features

| Feature | Description |
|---------|-------------|
| **Language** | Modern Standard Arabic (MSA) |
| **Domain** | Moroccan education |
| **Size** | 1,360 annotated tweets |
| **Sentiment polarities** | Positive, Negative, Neutral, Conflict |
| **Aspect categories** | 5 categories: Curriculum & Instruction, Student Experience, Faculty & Staff, Outcomes & Performance, Technology Integration |
| **Annotations** | Aspect term extraction (ATE), Aspect sentiment classification (ASC), Aspect category detection (ACD), and Aspect category polarity (ACP) |
| **Format** | XML (see XML files) |

## 2. Repository Structure
AraABSAMD/  
│
├ # Annotated dataset files  
│ ├── araabsamd.xml # Full dataset in XML format  
│ └── README.md # Detailed data description  
│
├── guidelines/ # Annotation guidelines  
│ └── annotation_guidelines.pdf    
│
├── code/ # Preprocessing and evaluation scripts  
│ └── preprocessing/  
│ └── iob_encoding/  
│ └── evaluation/  
├── requirements.txt
├── LICENSE # CC BY-NC 4.0 license for the dataset  
├── LICENSE-CODE # MIT license for the code  
└── README.md # This file  




# 2. Experimental Environment

Experiments were conducted using the following environment:

| Component | Specification   |
| --------- | --------------- |
| OS        | Ubuntu 22.04    |
| Python    | Python 3.10     |
| GPU       | NVIDIA Tesla T4 |
| Platform  | Google Colab    |

All library versions are pinned in `requirements.txt`.

---

# 3. Installation

Clone the repository:

```
git clone https://github.com/projectManager22/AraABSAMD
cd AraABSAMD
```

Install dependencies:

```
pip install -r requirements.txt
```

---

# 4. Dataset Preprocessing

The preprocessing pipeline follows several steps to clean and normalize Arabic text.

### 4.1 Cleaning Operations

The following operations are applied to each text instance:

1. Removal of HTML tags such as `<br/>`
2. Removal of non-Arabic characters
3. Normalization of whitespace
4. Retention of Arabic Unicode blocks only

The preprocessing function is implemented as:

```python
import re

def clean(text):

    text = text.replace("<br/>", " ")

    arabic_pattern = re.compile(
        r'[^\u0600-\u06FF\u0750-\u077F\u08A0-\u08FF\uFB50-\uFDFF\uFE70-\uFEFF ]'
    )

    text = re.sub(arabic_pattern, " ", text)

    text = re.sub(r'\s+', ' ', text).strip()

    return text
```

---

# 5. MSA Filtering  
To ensure linguistic consistency, a two-stage filtering process was implemented. First, the administrator curated the collected tweets by discarding those written in Moroccan dialect (Darija) or exhibiting code-switching, retaining only content composed in Modern Standard Arabic (MSA). Second, during the annotation phase, annotators were instructed to identify and flag any sentences containing dialectal features; these flagged instances were then reviewed by the administrator for potential exclusion from the final dataset.  

To ensure the dataset primarily contains **Modern Standard Arabic (MSA)**:

* Non-Arabic characters and symbols are removed using Unicode filtering.
* Tokenization is performed using regex-based token extraction.
* Only normalized Arabic tokens are retained during preprocessing.

Tokenization pattern:

```
pattern = r'\w+|[^\w\s]'
```

This step removes foreign words, emojis, and non-Arabic scripts that commonly appear in social media posts.

---

# 6. Baseline Models

Baseline experiments were conducted using pretrained Arabic language models implemented in the
HuggingFace Transformers library.

The following models were evaluated:

* **ARBERT**  
* **ARBERTv2**
* **CAMeLBERT-MSA**

These models were fine-tuned for aspect-based sentiment classification.

Example loading procedure:

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification

tokenizer = AutoTokenizer.from_pretrained("UBC-NLP/ARBERTv2")
model = AutoModelForTokenClassification.from_pretrained("UBC-NLP/ARBERTv2")
```

---

# 7. Training Configuration

| Parameter  | Value                    |
| ---------- | ------------------------ |
| Batch size | 16                       |
| Optimizer  | AdamW                    |
| Framework  | HuggingFace Transformers |
| Hardware   | NVIDIA Tesla T4          |

Random seeds used for reproducibility:

```python
import random
import numpy as np
import torch

random.seed(42)
np.random.seed(42)
torch.manual_seed(42)
```

---

# 8. Evaluation

Evaluation was conducted using:

* Accuracy
* Macro Precision
* Macro Recall
* Macro F1-score

Sequence labeling metrics were computed using the `seqeval` library.

---

# 9. Running the Experiments

To reproduce the experiments:

1. Install dependencies:

```
pip install -r requirements.txt
```

2. Run the experiment notebook:

```
experiments/baseline_models.ipynb
```

The notebook includes:

* dataset loading
* preprocessing
* tokenization
* model training
* evaluation

---

# 10. Reproducibility

To ensure full reproducibility, this repository includes:

* dataset preprocessing scripts
* baseline experiment notebooks
* pinned dependency versions
* environment configuration
* explicit preprocessing rules

All steps required to reproduce the baseline results reported in the paper are documented in this repository.

---

# 11.  📖 How to Cite

If you use this dataset in your research, please cite the following paper:

```bibtex
@article{Lachhab2026araabsamd,
  title={AraABSAMD: The First Arabic Aspect-Based Sentiment Analysis Dataset for Moroccan Education},
  author={Lachhab, Youssef and Ziyati, Elhoussaine},
  journal={[ARRAY]},
  year={2026}
}
```

## 12. Licenses

### Dataset (Annotation Data)
The annotation data in this repository is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)**.

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made.
- **NonCommercial** — You may not use the material for **commercial purposes**.

For more details, see the full license deed at [https://creativecommons.org/licenses/by-nc/4.0/](https://creativecommons.org/licenses/by-nc/4.0/) or read the [LICENSE](LICENSE) file included in this repository.

### Code
All code in the `code/` directory is licensed under the **MIT License**.  
See the [LICENSE-CODE](LICENSE-CODE) file for details.

🤝 Contributing  
Contributions to improve the dataset or code are welcome! Please open an issue or submit a pull request.

📬 Contact  
For questions or collaboration, please contact:  

Youssef Lachhab: youssef.lachhab.2020@gmail.com  

Elhoussaine Ziyati: ziyati@gmail.com      

🙏 Acknowledgements  
We thank the annotators for their valuable contributions. 

