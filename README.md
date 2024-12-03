# Italian Dialects: NLP for Local Linguistics

## Introduction

This project explores the classification and translation of Italian dialects using Natural Language Processing (NLP) techniques. Inspired by the GeoLingIt Shared Task, our goal was to classify regional dialects based on geotagged social media posts and translate them into standard Italian to foster appreciation for Italy's rich linguistic diversity.

## Models Used

### Oversampling Models

To address class imbalance, we experimented with both custom and pre-trained models:

#### Custom Models (Built from Scratch)
1. **N-GRAM Model**: A probabilistic model predicting the next word based on the previous sequence. Results were unsatisfactory, generating incoherent sentences.
2. **LSTM**: A recurrent neural network capable of modeling long-term dependencies. It failed to produce meaningful sequences beyond the input text.
3. **VAE (Variational Autoencoder)**: Used for generating synthetic text. However, the limited dataset size hindered its performance.

#### Pre-trained Models
1. **Gemini-Pro**: Showed promise in generating dialect-specific text.
2. **GPT-2**: Performed well but occasionally output sentences in English.
3. **LLaMAntino-3-ANITA-8B-Inst-DPO-ITA**: Selected for its superior performance in generating accurate dialectal sentences.

### Classification Model
- **Support Vector Machine (SVM)**: Applied to classify tweets by their regional dialect.

### Translation Model
- **LLaMAntino-3-ANITA-8B-Inst-DPO-ITA**: Used for translating dialect phrases into Italian, ensuring semantic and syntactic fidelity.

## Dataset

We utilized the GeoLingIt dataset, which contains geotagged Twitter posts in non-standard Italian. The dataset includes:

- Training set (`train`) and validation set (`dev`).
- Posts labeled by region, showcasing dialectal expressions, code-switching, and entire posts in dialect.

### Preprocessing
Non-essential elements such as hashtags, emojis, and tags were removed for better model performance.

### Oversampling
After oversampling with **LLaMAntino-3-ANITA-8B-Inst-DPO-ITA**, the dataset contained 34,479 examples, with at least 1,000 samples per region.

## Tasks

### Main Task: Dialect Classification by Region
The SVM algorithm classified posts based on their linguistic characteristics, leveraging Scikit-learn's implementation.

### Extra Task: Dialect Translation
The **LLaMAntino-3-ANITA-8B-Inst-DPO-ITA** model was employed to translate dialect phrases into Italian, preserving their meaning and structure.

## Evaluation

### Main Task
- **Accuracy**: 70%
- **Average Recall**: 65%
- **F1 Score**: 67%

The Sardinian dialect achieved the highest classification accuracy, while Emilia-Romagna showed the lowest.

### Extra Task
Translation quality was evaluated using BLEU scores, yielding a score of **0.17**, indicating room for improvement in capturing dialect nuances.

## Conclusions and Limitations

While classification performed well, translation faced challenges due to synthetic data quality. Future improvements include:

1. Expanding the dataset with diverse and accurate examples.
2. Incorporating manual translations from native speakers.
3. Fine-tuning the **LLaMAntino-3-ANITA-8B-Inst-DPO-ITA** model for dialect-specific translations.
