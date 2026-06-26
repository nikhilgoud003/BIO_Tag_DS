# BIO_Tag_DS
compare two BERT-based models (a fine-tuned model and a baseline model) to see how fine-tuning changes what the model focuses on when analyzing text for adverse events.
Loads Two Models:

my_bert_model2: Your fine-tuned model, trained specifically to classify and detect adverse events.
bert-base-uncased: The baseline, off-the-shelf control model.
Fair Comparison via Attention: Since both models have the same underlying architecture (same number of heads and layers), the notebook compares their encoder attention mechanisms. The fine-tuned model has a trained classification head, while the baseline has a randomly initialized head. Therefore, the baseline's classification probability is meaningless, and the comparison strictly looks at how the attention weights shifted due to fine-tuning.

Extracts Signals & Tags (BIO Format): It calculates "saliency" (how important a word is) using attention scores (and masking for the fine-tuned model). It then translates these signals into BIO tags like B-AE (Adverse Event), B-LOC (Location), B-AFF (Affected), etc.

Interactive UI: The notebook provides a live side-by-side interactive UI (using ipywidgets). You can enter a sentence, and it will visually display which words each model focuses on (highlighting the "peaks" in attention) and how they tag the entities.

In short, the notebook is a diagnostic and visualization tool to prove that fine-tuning successfully taught the model to focus on the causal words of an adverse event, rather than just random punctuation or structural words.
