# toy-gpt-train

> Demonstrates, at very small scale, how a language model is trained.

This repository is part of a series of toy training repositories plus a companion client repository:

- [**Training repositories**](https://github.com/toy-gpt) produce pretrained artifacts (vocabulary, weights, metadata).
- A [**web app**](https://toy-gpt.github.io/toy-gpt-chat/) loads the artifacts and provides an interactive prompt.

## Contents

- a small, declared text corpus
- a tokenizer and vocabulary builder
- a simple next-token prediction model
- a repeatable training loop
- committed, inspectable artifacts for downstream use

## Scope

This is:

- an educational, inspectable training pipeline
- a next-token predictor trained on an explicit corpus

This is not:

- a production system
- a full Transformer implementation
- a chat interface
- a claim of semantic understanding

## Outputs

This repository produces and commits pretrained artifacts under `artifacts/`.

These artifacts are intended to be loaded by the companion client repository.

Typical artifacts include:

- `artifacts/vocab.json`
- `artifacts/weights.csv` (or similar)
- `artifacts/model_meta.json`

Training logs and evidence are written under `outputs/`
(for example, `outputs/train_log.csv`).

## Quick start

See `SETUP.md` for full setup and workflow instructions.

Run the full training script:

```shell
uv run python src/toy_gpt_train/e_infer.py
```

Run individual pipeline steps:

```shell
uv run python src/toy_gpt_train/a_tokenizer.py
uv run python src/toy_gpt_train/b_vocab.py
uv run python src/toy_gpt_train/c_model.py
uv run python src/toy_gpt_train/d_train.py
uv run python src/toy_gpt_train/e_infer.py
```

Build and serve documentation:

```shell
uv run mkdocs build --strict
uv run mkdocs serve
```

## Provenance and Purpose

The primary corpus used for training is declared in `SE_MANIFEST.toml`.

This repository commits pretrained artifacts so the client can run
without retraining.
