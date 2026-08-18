# Code Switching NLP — Roman Urdu / English Language Identification

Identifies whether each word in a mixed-language sentence is Roman Urdu, English, or a mix of both.

## Why this matters

Pakistani social media, chat, and everyday text messaging constantly switches between Roman Urdu and English mid-sentence ("code-switching") — something standard NLP language-ID tools aren't built to handle. This project builds a labeled dataset and a token-classification model that tags each word's language, a foundational step for building better NLP tools (sentiment analysis, chatbots, translation) for Roman Urdu-English text.

## Live Demo

🔗 https://huggingface.co/Moazamzf/code-switching-si26-model

## How it works

A custom dataset of 150+ Roman Urdu/English code-switched sentences was collected and manually labeled at the word level (URD, ENG, or MIX), then published as a public HuggingFace dataset. An XLM-RoBERTa model was fine-tuned on this dataset as a token-classification task, learning to predict the language label for each word in a sentence.

## Results

- **Accuracy: 94.6%**
- **F1 Score (weighted): 92.9%**

| Label | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| ENG   | 0.88      | 0.99   | 0.93     | 87      |
| URD   | 0.99      | 0.98   | 0.98     | 161     |
| MIX   | 0.00      | 0.00   | 0.00     | 9       |

**Known limitation:** the model struggles with the MIX label, largely due to class imbalance — MIX made up only ~4% of the test set. Both URD and ENG classification are strong.

## How to run locally

```bash
git clone https://github.com/moazamzf/code-switching-codesaviours-si26-moazam.git
cd code-switching-codesaviours-si26-moazam
pip install transformers datasets torch pandas scikit-learn
python train.py
```

*(Adjust the repo URL and entry point filename to match what's actually in your repo.)*

## Demo Video

🎥 [ADD YOUR LOOM VIDEO LINK HERE, IF INCLUDED]

## Built by

[Your Name] | Code Saviours SI-26 | 2026
