# Assignment: Selection of Best Pre-trained Model using TOPSIS

## Step 1: Selection of Task

Task Selected: **Text Generation**

Since the roll number ends with 6, the assigned task category is Text Generation.

The objective is to identify the best pre-trained Hugging Face model using a multi-criteria decision-making approach (TOPSIS).

---

## Step 2: Installation and Exploration

The following libraries were used in Google Colab:

- transformers
- datasets
- evaluate
- torch
- numpy
- pandas
- matplotlib

Pre-trained models were loaded using the Hugging Face `transformers` library.

Models evaluated:

1. facebook/bart-base  
2. gpt2  
3. google/flan-t5-small  

Dataset used:
- CNN/DailyMail (subset: test[:20])
- Sampling was applied to reduce computational cost.

---

## Step 3: Identification of Evaluation Criteria

The following evaluation criteria were selected:

| Criterion | Type |
|------------|------|
| BLEU Score | Benefit ↑ |
| ROUGE-L | Benefit ↑ |
| Perplexity | Cost ↓ |
| Inference Time | Cost ↓ |
| Model Size | Cost ↓ |

Benefit criteria are maximized.  
Cost criteria are minimized.

Weights assigned to criteria:

```python
weights = [0.25, 0.25, 0.20, 0.15, 0.15]
```

---

## Step 4: Model Evaluation

For each pre-trained model:

1. Generate output for dataset samples.
2. Compute:
   - BLEU score
   - ROUGE-L score
   - Perplexity
   - Average inference time
   - Model size (number of parameters)

These values were stored in a decision matrix.

---

## Step 5: Application of TOPSIS

TOPSIS was implemented manually using the following steps:

1. Normalize the decision matrix.
2. Multiply normalized values by assigned weights.
3. Determine ideal best and ideal worst solutions:
   - Maximum values for benefit criteria
   - Minimum values for cost criteria
4. Compute separation distance from ideal best and worst.
5. Calculate relative closeness score:

Cᵢ = S⁻ / (S⁺ + S⁻)

Where:
- S⁺ = distance from ideal best
- S⁻ = distance from ideal worst

Models were ranked based on highest closeness score.

---

## Step 6: Model Comparison and Best Model Selection

The final TOPSIS ranking was:

| Model | TOPSIS Score | Rank |
|--------|--------------|------|
| facebook/bart-base | 0.629 | 1 |
| gpt2 | 0.604 | 2 |
| google/flan-t5-small | 0.569 | 3 |

Best Model Selected: **facebook/bart-base**

---

## Conclusion

Using a structured multi-criteria decision-making approach, multiple Hugging Face pre-trained text generation models were objectively compared. Based on evaluation metrics and TOPSIS ranking, facebook/bart-base achieved the highest overall performance and was selected as the best model for the task.
