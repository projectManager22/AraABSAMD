# AraABSAMD: Arabic Aspect-Based Sentiment Analysis Dataset for Moroccan Education

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

## 📌 Overview

**AraABSAMD** is the first publicly available dataset for Aspect-Based Sentiment Analysis (ABSA) in the Moroccan education domain. It contains **1,360 manually annotated tweets** in Modern Standard Arabic (MSA), covering discussions about education in Morocco.

This dataset was created to address the lack of Arabic ABSA resources in the education sector and to enable fine-grained opinion mining for educational stakeholders, policymakers, and researchers.

## 📊 Dataset Features

| Feature | Description |
|---------|-------------|
| **Language** | Modern Standard Arabic (MSA) |
| **Domain** | Moroccan education |
| **Size** | 1,360 annotated tweets |
| **Sentiment polarities** | Positive, Negative, Neutral, Conflict |
| **Aspect categories** | 5 categories: Curriculum & Instruction, Student Experience, Faculty & Staff, Outcomes & Performance, Technology Integration |
| **Annotations** | Aspect term extraction (ATE),Aspect sentiment classification (ASC), Aspect category detection (ACD), and Aspect category polarity (ACP |
| **Format** | XML (see `/data` folder) |

## 📁 Repository Structure
AraABSAMD/
│
├── data/ # Annotated dataset files
│ ├── araabsamd.xml # Full dataset in XML format
│ └── README.md # Detailed data description
│
├── guidelines/ # Annotation guidelines
│ └── annotation_guidelines.pdf
│
├── code/ # Preprocessing and evaluation scripts
│ ├── preprocessing/
│ ├── iob_encoding/
│ └── evaluation/
│
├── LICENSE # CC BY 4.0 license
└── README.md # This file

## 📜 License

This dataset is licensed under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**.

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made.

For more details, see the full license deed at: https://creativecommons.org/licenses/by-nc/4.0/ or read the [LICENSE](LICENSE) file included in this repository.

## 📖 How to Cite

If you use this dataset in your research, please cite the following paper:

Example BibTeX:
```bibtex
@article{Lachhab2025araabsamd,
  title={AraABSAMD: The First Arabic Aspect-Based Sentiment Analysis Dataset for Moroccan Education},
  author={Lachhab, Youssef and Ziyati, Elhoussaine},
  journal={[ARRAY]},
  year={2026}
}
1.Clone this repository:
git clone https://github.com/projectManager22/AraABSAMD.git
cd AraABSAMD
 **Important Notes**
Raw tweet text: The repository contains the full text of publicly available tweets collected in compliance with Twitter's terms of service at the time of collection.

Privacy: All personally identifiable information (user mentions, URLs, phone numbers) has been removed from the released text.

Research use only: This dataset is intended for non-commercial academic research.
**Contributing**
Contributions to improve the dataset or code are welcome! Please open an issue or submit a pull request.
**Contact**
For questions or collaboration, please contact:

Youssef Lachhab: youssef.lachhab.2020@gmail.com

Elhoussaine Ziyati: ziyati@gmail.com
**Related Publications**

**Acknowledgements**
We thank the annotators for their valuable contributions.
