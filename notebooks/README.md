# Reproducible Evaluation Notebook

This folder contains the executable notebook used to reproduce the experimental results
reported in the accompanying IEEE Access manuscript.

## Notebook
- `RAG_IEEE_EVAL.ipynb`

## What the notebook does
The notebook:
1. Installs required Python dependencies
2. Writes the experiment runner (`rag_ieee_eval.py`)
3. Executes a controlled evaluation of Retrieval-Augmented Generation (RAG) configurations
4. Generates the tables and figures reported in the paper

## Experimental setup
- Dataset: 20 Newsgroups (training split, headers/footers/quotes removed)
- Retrieval methods:
  - Dense retrieval (FAISS)
  - Lexical retrieval (BM25)
  - Hybrid retrieval using Reciprocal Rank Fusion (RRF)
- Chunking strategies:
  - Fixed-length word chunking
  - Sentence-based chunking
- Generator: EleutherAI/gpt-neo-125M
- Embedder: all-MiniLM-L6-v2

## Command executed
The notebook runs the following command:

```bash
python rag_ieee_eval.py \
  --run_grid \
  --docs_limit 1000 \
  --eval_per_category 3 \
  --eval_max_total 60 \
  --out_dir outputs
```

## Outputs
The notebook produces:
- Per-query evaluation results (`detail_*.csv`)
- Aggregated summary statistics (`summary_*.csv`)
- Final paper artifacts:
  - `outputs/Table_I.csv`
  - `outputs/Fig1_*.png`
  - `outputs/Fig2_*.png`

## Notes
- Results are deterministic given the fixed random seed.
- Minor numerical variation may occur across environments due to library versions.

