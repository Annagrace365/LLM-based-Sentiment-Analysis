## LLM-based-Sentiment-Analysis
1. Introduction

This project implements a lightweight sentiment analysis pipeline using a Large Language Model (LLM) to classify text reviews into Positive, Neutral, or Negative sentiments.
It also extracts supporting cues and generates structured summaries, demonstrating strong skills in text processing, evaluation metrics, and model interpretability.

2. Methodology
   
2.1 Dataset

Custom Amazon-style dataset

30 training samples, 15 test samples

Star ratings mapped to sentiment labels:

0 → Negative

1 → Neutral

2 → Positive

2.2 Model

DistilBERT-base-uncased (HuggingFace)

Fine-tuned for 3-class sentiment classification

AdamW optimizer (lr = 5e-5)

3 training epochs

Lightweight and suitable for small-scale learning

2.3 Preprocessing

Tokenization using DistilBERT tokenizer

Max sequence length = 64 tokens

Padding + truncation applied

Loaded using a custom ReviewDataset class

2.4 Supporting Phrase Extraction

TF-IDF vectorizer fitted on all reviews

Extracts Top 3 important words per review

Provides simple and interpretable supporting cues

3. Structured Summary Generation

For each test review, a JSON output is generated containing:

Predicted Sentiment (Positive / Neutral / Negative)

Confidence Score (softmax probability)

Top 3 Supporting Phrases

Follow-up Suggestion (only for Negative sentiment)

These summaries are readable and integration-ready for dashboards or APIs.

4. Evaluation Metrics

Test Set Performance:

Accuracy: 0.8667

Macro F1 Score: 0.8611

Despite using a small dataset, the model performs reliably with balanced metrics.

5. Error Analysis
Misclassification 1

Review: “It is fine, meets expectations”

Actual: Neutral

Predicted: Positive

Reason: Mildly positive phrases misled the model.

Misclassification 2

Review: “Satisfactory overall, but could be better”

Actual: Neutral

Predicted: Positive

Reason: “Satisfactory” signals slight positivity even when tone is mixed.

Common Pattern

Neutral reviews with soft positive expressions often shift toward Positive.

Neutral is the hardest class due to subtle or mixed sentiment.

6. Key Insights

DistilBERT performs well even with limited data.

Confidence scores help understand prediction reliability.

TF-IDF supporting phrases increase explainability.

Neutral sentiment remains the most challenging category.

The entire pipeline is efficient, interpretable, and meets all task requirements.

7. Conclusion

This project successfully delivers a complete and functional LLM-based sentiment analysis pipeline:

Fine-tuned DistilBERT for 3-class classification

Extracts supporting phrases and confidence scores

Generates structured JSON summaries

Includes evaluation and error analysis
