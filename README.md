# Topsis-using-pretrained-models
# Text Generation Model Selection using TOPSIS

## Overview
This project applies the **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** method to select the best pre-trained Hugging Face model for text generation.

Instead of choosing a model based on a single metric, multiple quality and efficiency criteria are evaluated and ranked using a mathematical decision-making approach.

---

## Models Evaluated
- facebook/bart-base  
- gpt2  
- google/flan-t5-small  

All models were loaded using the Hugging Face `transformers` library.

---

## Dataset
- Dataset: CNN/DailyMail  
- Subset used: `test[:20]`  
- Sampling was applied to reduce computational cost while maintaining evaluation validity.

---

## Evaluation Criteria

| Criterion        | Type      |
|------------------|----------|
| BLEU Score       | Benefit ↑ |
| ROUGE-L          | Benefit ↑ |
| Perplexity       | Cost ↓    |
| Inference Time   | Cost ↓    |
| Model Size       | Cost ↓    |

---

## Weights Used

```python
weights = [0.25, 0.25, 0.20, 0.15, 0.15]
```

Higher priority was given to generation quality while still considering efficiency.

---

## Methodology

1. Load pre-trained models from Hugging Face.
2. Generate outputs for sampled dataset.
3. Compute BLEU, ROUGE-L, Perplexity, Inference Time, and Model Size.
4. Construct decision matrix.
5. Apply TOPSIS:
   - Normalize matrix  
   - Apply weights  
   - Identify ideal best & worst  
   - Compute separation distances  
   - Calculate relative closeness score  

The model with the highest TOPSIS score is ranked first.

---

## Results

| Model | TOPSIS Score | Rank |
|--------|--------------|------|
| facebook/bart-base | 0.629 | 1 |
| gpt2 | 0.604 | 2 |
| google/flan-t5-small | 0.569 | 3 |

**Selected Best Model:** facebook/bart-base

---


---

## 🏁 Conclusion
Using a multi-criteria decision-making approach, TOPSIS enabled objective comparison of multiple Hugging Face text generation models. Based on combined quality and efficiency metrics, **facebook/bart-base** was selected as the best model for the given task.
