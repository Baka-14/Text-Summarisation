# AI3106 Foundations of NLP — Course Project

This repository is of my junior year coursework for **AI3106: Foundations of Natural Language Processing**. It captures multiple iterations of my attempt to solve a core NLP problem **text summarization** starting from simpler baselines and gradually moving toward modern transformer based approaches.

The work is **not a polished library**; it’s an experiment trail that shows how my understanding of NLP evolved while building, debugging and comparing approaches.

## What this repo does

- **Summarises text** using a Hugging Face `transformers` summarisation pipeline (defaulting to `sshleifer/distilbart-cnn-12-6` in the notebook).
- **Explores earlier approaches** (and their limitations), including:
  - Frequency/statistical baselines and language-modeling style token analysis
  - Early seq2seq/LSTM-style experimentation (worked on but left incomplete/rough)
- **Applies summarisation to real text corpora**, including Warren Buffett shareholder letters.

## Folder structure (updated)

```
.
├── notebooks/
│   ├── 01_language_modelling.ipynb
│   ├── 02_text_summarization_seq2seq.ipynb
│   ├── 03_transformer_summarization_pipeline.ipynb
│   └── 99_assignment2.ipynb
├── data/
│   └── raw/
│       ├── data.csv
│       ├── white_house_speeches.csv
│       └── warren_buffett_letters/
├── outputs/
│   └── blogsummary.txt
├── docs/
│   ├── Readme_legacy.txt
│   └── SE20UARI164.pdf
└── submissions/
    └── Sai Srikar-Se20uari164.zip
```

## Notebooks tour

- **`notebooks/01_language_modelling.ipynb`**

  - Tokenization + basic NLP preprocessing (NLTK)
  - Experiments around “language modelling / frequency math” style baselines
  - References a `news_summary.csv` dataset path used during development; that dataset is **not currently committed** to this repo.
- **`notebooks/02_text_summarization_seq2seq.ipynb`**

  - A rougher “learning notebook” with attempts toward seq2seq-style summarisation
  - Uses multiple text sources (Buffett letters + a speeches dataset)
  - Contains some captured local tracebacks from my machine (kept as-is for history)
- **`notebooks/03_transformer_summarization_pipeline.ipynb`**

  - The most “complete” working approach in this repo
  - Uses `transformers.pipeline("summarization")`
  - Demonstrates pulling an article from the web (example URL in notebook) and summarizing it
  - Writes output to `outputs/blogsummary.txt`

## Data

- **Warren Buffett letters**: `data/raw/warren_buffett_letters/` (text files + combined text files)
- **White House speeches**: `data/raw/white_house_speeches.csv`
- **`data/raw/data.csv`**: despite the extension, this is primarily **text content** (kept in its original form because the notebooks reference it)

## How to run

This project is notebook first.

1. Create an environment (venv/conda).
2. Install dependencies (see `requirements.txt` if present; otherwise install as needed while running notebooks).
3. Open and run notebooks from the `notebooks/` folder.

Notes:

- Some notebooks download NLTK resources (e.g., `punkt`, `stopwords`) at runtime.
- If a notebook references a dataset you don’t have (e.g., `news_summary.csv`), you can either add it under `data/raw/` or skip those sections.

## What I was learning (AI3106 reflection)

Working on this in college was my first “end-to-end” NLP experience where I had to go beyond theory and make things actually run:

- **Preprocessing is a project by itself**: tokenization choices, encodings (`latin-1`, `cp1252`), and cleaning mattered more than I expected.
- **Baselines teach you intuition**: simple frequency/statistical methods helped me understand why summarisation is hard (relevance vs. redundancy vs. coherence).
- **Seq2seq felt conceptually clear but practically tricky**: data shaping, teacher forcing, and debugging training loops made me realize why people lean on strong pretrained models.
- **Transformers were a turning point**: using a pretrained summarizer let me focus on inputs/outputs, evaluation, and failure modes rather than only model training.
- **Iteration is the real workflow**: the repo keeps multiple attempts because that’s how the learning happened—try, fail, read, adjust, and try again.

## Report / submission artifact
- Submission zip: `submissions/Sai Srikar-Se20uari164.zip`
