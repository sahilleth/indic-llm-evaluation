# Indic LLM Evaluation: Hindi vs English on XQuAD

## Research Question
Do LLMs perform worse on Hindi compared to English on identical questions?
Does scaling the model reduce this performance gap?

## Dataset
- **XQuAD** (Cross-lingual Question Answering Dataset) by Google
- 100 identical questions in both Hindi and English
- Same contexts, same answers — only language differs

## Models Evaluated
- LLaMA 3.1 8B (via Groq API)
- LLaMA 3.3 70B (via Groq API)

## Key Results

| Model | English | Hindi | Gap |
|---|---|---|---|
| LLaMA 3.1 8B | 91% | 86% | -5% |
| LLaMA 3.3 70B | 93% | 94% | +1% |

## Key Finding
**Scaling reverses the Hindi-English performance gap.**
- The 8B model underperforms on Hindi by 5%
- The 70B model actually performs slightly better on Hindi than English
- This suggests larger models develop stronger cross-lingual transfer for Indic languages

## Error Analysis (8B model, Hindi failures)
1. Number confusion — Hindi word numerals misread (e.g. चार vs 24)
2. Wrong entity selection — plausible but incorrect answers
3. Negation misunderstood in Hindi context
4. Off-by-one numeric errors

## Related Work
- LLINK (Gupta & Agarwal, 2025) — cross-lingual alignment via encoder injection
- XQuAD (Artetxe et al., 2020) — cross-lingual QA benchmark

## Files
- `xquad_results.csv` — full prediction results for all 100 examples
- `summary.json` — summary statistics
- `evaluation.ipynb` — full experiment notebook

## Next Steps
- Extend to Bengali and Tamil
- Test with few-shot prompting
- Compare encoder-injected models (LLINK-style) vs vanilla LLMs
