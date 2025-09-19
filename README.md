# Metaphor Generation with Billy Woods–Fine-Tuned LLM

This project explores whether large language models can generate or evaluate **metaphorical creativity**, and whether fine-tuning them on a **stylistically rich corpus** — in this case, the abstract, politically-charged lyrics of hip-hop artist Billy Woods — improves their performance.

> “A thousand plateaus, a constellation of prisons / An ocean of archipelagos, an algorithm…”  
> — *Billy Woods, “Wishing Bad”*

---

## Project Summary

- Fine-tuned a **Mistral 7B** language model on the complete lyrical archive of Billy Woods.
- Prompted the model with metaphor stems like:
  - `A police badge is like...`
  - `A bullet is like...`
  - `A jail cell is like...`
- Compared completions from the fine-tuned model with a **base model**.
- Evaluated metaphor creativity using a **GPT-2–based scoring model**, trained on human-rated metaphor data.
- Reflected on authorship, voice simulation, and ethical implications of using AI to mimic human artistic expression.

---

## Model Access

| Model | Hugging Face Link |
|-------|-------------------|
| **Fine-tuned Mistral 7B** on Billy Woods lyrics | https://huggingface.co/cwagaman/billy_woods-mistral7b  |
| **GPT-2 Creativity Scorer** (https://huggingface.co/cwagaman/metaphor_scorer-GPT2) |

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
```
## Metaphor Scoring Model

The creativity scorer used in this project is based on a methodology from:

**Di Stefano, Peter, et al.**  
_"Automatic Scoring of Metaphor Creativity with Large Language Models"
[Paper link](https://www.tandfonline.com/doi/full/10.1080/10400419.2024.2326343)

We re-implemented and fine-tuned a GPT-2 model using their dataset of metaphors rated by human annotators (-1 to +2).  
Our implementation achieved a Pearson correlation of 0.68 on the original test set.


billy-woods-metaphor-llm/
│
├── README.md                  ← You are here
├── requirements.txt
├── final_script.md           ← Full symposium presentation
│
├── notebooks/
│   ├── evaluate_finetuned_model.ipynb  ← Load model & score metaphor completions
│   └── metaphor_scorer_training.ipynb  ← (Optional) Fine-tune GPT-2 scorer
│
├── outputs/
│   ├── metaphor_outputs.csv   ← Base vs. fine-tuned model outputs
│   └── creativity_scores.csv  ← Scores assigned by the GPT-2 scorer
