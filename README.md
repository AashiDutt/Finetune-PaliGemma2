# Finetuning Paligemma2 for Vision-Language Task

This repository contains code for fine-tuning **Paligemma2**, a vision-language model, to solve the problem introduced in the paper [*Vision-Language Models are Blind*](https://arxiv.org/abs/2407.06581). The specific task addressed here is:

> **"Which letter is being circled in a word?"** 

---

## Table of Contents
1. [Overview](#overview)
2. [Dataset](#dataset)
3. [Model and Training](#model-and-training)
4. [Setup and Requirements](#setup-and-requirements)
5. [Usage](#usage)
6. [Results](#results)
7. [References](#references)

---

## Overview

The **"letter circling task"** is used to analyze limitations of vision-language models (VLMs). This task involves:
- A word being presented visually.
- A letter in the word being circled.
- The model predicting **which letter is circled**.
  
The paper introduces a problem stating that VLMs turn blind eye to problems that humans perform unknowingly such as identifying the letter circled in a word. Although humans find it easy to identify circled word, even if the circle is overlapping or word has differnt font. But VLMs struggle at this task altogether.

The code fine-tunes **Paligemma2** to address this problem by combining **vision** and **language** understanding.

---

## Dataset

The dataset for this task is synthetically generated:
- **Words** are sourced from the `nltk` word corpus.
- **Images** are created programmatically using the `PIL` library, with letters in words being visually circled. These words have different fonts and lengths as well as size to complicate the task. 

**Example Dataset Layout**:

| Image | Word  | Circled Letter |
|-------|-------|----------------|
| ![Screenshot 2024-12-18 at 10 02 51 AM](https://github.com/user-attachments/assets/7180a0a5-30cb-425f-a448-908373cc3672)| "facilely" | "c" |


---

## Model and Training

We use **Paligemma2**, a pre-trained **vision-language model**, as the backbone for fine-tuning. Key steps include:
1. **Dataset Preparation**: Synthetic image-word-label pairs are generated.
2. **Fine-Tuning**: The model is fine-tuned using:
   - **Transformers** library (HuggingFace)
   - Mixed-precision training via **bitsandbytes** and **accelerate**.
3. **Evaluation**: Accuracy is measured by the model's ability to predict the correct letter being circled.

---

## Setup and Requirements

### Prerequisites:
- Python 3.8+
- CUDA-compatible GPU for faster training.

### Install Dependencies:
```bash
pip install -U transformers datasets accelerate bitsandbytes peft freetype-py
```

---

## Usage

### 1. Clone the Repository:
```bash
git clone https://github.com/AashiDutt/Finetune-PaliGemma2.git
cd Finetune-PaliGemma2
```

### 2. Run the Notebook:
Launch the Jupyter Notebook to execute the code and fine-tune Paligemma2:
```bash
jupyter notebook Finetune_Paligemma2.ipynb
```

---

## Results

![Screenshot 2024-12-18 at 10 12 15 AM](https://github.com/user-attachments/assets/9ed60dcc-3628-426f-97df-19e15ca20c79)

---

## References

1. **Paper**: [Vision-Language Models are Blind](https://arxiv.org/abs/2407.06581)
2. **Model**: Paligemma2 from HuggingFace
3. **Libraries**: 
   - Transformers
   - Datasets
   - Accelerate
   - BitsAndBytes

---

## Contributing
Contributions are welcome! Please open an issue or a pull request.

---

## License
This repository is licensed under the MIT License.

