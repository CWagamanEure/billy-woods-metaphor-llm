# Project Summary: Evaluating Metaphorical Creativity in Fine-Tuned Language Models

This project explores whether large language models (LLMs) can generate or evaluate metaphorical creativity—and whether fine-tuning such models on a highly stylized corpus improves the quality and originality of their outputs.

To investigate this, I fine-tuned the **Mistral 7B** language model on a curated corpus of lyrics from abstract hip-hop artist **Billy Woods**, whose writing is known for its metaphor density, fragmented structure, and layered political critique. This project became a study in voice simulation, stylistic flattening, and evaluative modeling: an attempt to understand how AI may imitate, distort, or reimagine the poetic voice of a singular author.

---

## Methodology

### 1. Dataset Creation

I began by scraping Billy Woods’ complete lyrical archive from Genius.com using BeautifulSoup. The resulting dataset captured Woods’ distinctive lyrical style—rich in surreal imagery, political allegory, and poetic fragmentation.

### 2. Fine-Tuning

Using this dataset, I fine-tuned Mistral 7B on the lyrics to align its generative behavior with Woods’ metaphorical cadence and tone. I then prompted both the fine-tuned model and the base (unmodified) Mistral 7B model with open-ended metaphor stems such as:

- `A police badge is like...`
- `A bullet is like...`
- `A jail cell is like...`

I manually filtered the outputs to retain only metaphorical or figurative responses for analysis.

### 3. Metaphor Evaluation

To evaluate the creativity of the generated metaphors, I implemented a scoring model based on the methodology proposed in the paper:

> Di Stefano, Peter, et al. *"Automatic Scoring of Metaphor Creativity with Large Language Models"* ACL 2020.  
> [Paper link](https://www.tandfonline.com/doi/full/10.1080/10400419.2024.2326343)

In that study, human participants generated metaphors, which were then rated by other humans for creativity on a scale from -1 to +2, considering criteria such as novelty, coherence, and surprise. These human-annotated scores were used to train a GPT-2 model to predict metaphor creativity.

I re-implemented and fine-tuned a version of this GPT-2 scorer and validated it on the original test set. It achieved a **Pearson correlation of 0.68** with human-assigned scores, with normally distributed errors—indicating strong reliability. While this scoring model was a secondary component of the project, it enabled quantitative comparisons between base and fine-tuned models.

---

## Results

The results were clear and consistent:

| Model                  | Mean Creativity Score | Standard Deviation |
|------------------------|------------------------|---------------------|
| **Base Mistral 7B**     | 0.39                   | 0.41                |
| **Fine-tuned on Woods** | **0.87**               | **0.18**            |

- The **base model** frequently failed to produce metaphors altogether, often resorting to repetitive or generic phrases (e.g., comparisons to “icing on the cake” or “rice”).
- The **fine-tuned model**, by contrast, generated metaphorical responses that were often **surreal**, **emotionally charged**, and **politically nuanced**, consistent with Billy Woods’ voice.
- It also showed **greater consistency**, indicated by a lower standard deviation in creativity scores.

Even when the fine-tuned outputs lacked perfect clarity, they frequently gestured toward **layered meaning**, capturing the ambiguity and depth characteristic of Woods' work.

---

## Why Billy Woods?

While the approach could be applied to any metaphor-rich corpus, I selected Billy Woods specifically because his lyrics are intentionally difficult to reproduce. They resist coherence, thrive in ambiguity, and often blur the line between political critique, surrealism, and poetic abstraction. This made them an ideal challenge for LLMs attempting to replicate creative voice, rather than just surface-level syntax or rhythm.

For example, consider this lyric from his track **"Wishing Bad"**:

> *“A thousand plateaus, a constellation of prisons / An ocean of archipelagos, an algorithm…”*

This line references *A Thousand Plateaus* (Deleuze and Guattari), a work that critiques hierarchical structures of knowledge. Woods applies this concept to prison systems and the digital age—describing isolation in both physical and algorithmic spaces. It’s this depth of reference and metaphorical fusion that the model attempts to mimic.

---

## Reflections

This project raised several important questions about AI, authorship, and creativity:

- **Authorship**: If a model generates something that sounds like Billy Woods, who is the author? The model? The person who fine-tuned it? Or Woods himself, whose style and content shaped the training data?
- **Understanding vs. Imitation**: The model can describe a jail cell, but it cannot *mean* anything by it. Its metaphors are not grounded in experience—only statistical correlation.
- **Preservation vs. Appropriation**: Fine-tuning models on underrepresented voices may help preserve them—but may also flatten them into aesthetic objects divorced from context or intention.

Ultimately, yes—fine-tuning made the model *more creative* in a measurable sense: it produced metaphors that were more novel, coherent, and engaging. But this creativity was a product of **reassembly**, not invention. The outputs echoed Woods’ tone and rhythm, but not his consciousness.

---

## Conclusion

This project demonstrates that large language models can be tuned to simulate stylistic creativity, but it also shows the limits of that simulation. AI can imitate voice—but not experience. It can reassemble language—but not intention.

Still, within those constraints, there is room for experimentation. This work suggests a path forward for computational creativity research that is both **technically grounded** and **critically self-aware**.

