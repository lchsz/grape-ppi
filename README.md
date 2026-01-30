# GrapePPI

Protein–protein interaction (PPI) prediction for grape proteins using ESM2 embeddings and a PyTorch neural network.

## Setup

```bash
conda env create -f environment.yml
conda activate grape-ppi
```

## Download Data and Models

Download the `data/` and `models/` folders from [Google Drive](https://drive.google.com/drive/folders/1pXfNQ98OtSXV-WY3ZFIsWZpqFjsguLEg?usp=sharing) and place them in the project root.

## Project Structure

```
grape-ppi/
├── data/           # Per-variety data (train.tsv, val.tsv, test.tsv, esm2_t36_3B.h5)
├── models/         # Trained model checkpoints (.pt)
├── predictions/    # Prediction outputs (.csv)
├── train.ipynb     # Training notebook
├── predict.ipynb   # Prediction notebook
└── environment.yml
```

## Data Format

- **TSV**: `protein1_ID`, `protein2_ID`, `label` (0/1). For prediction, the label column is optional.
- **Embeddings**: ESM2 3B (esm2_t36_3B) pooled embeddings stored in HDF5 (`.h5`), keyed by protein ID.

Place data per variety under `data/<Grape-N>/`:
- `train.tsv`, `val.tsv`, `test.tsv`
- `esm2_t36_3B.h5`

## Training

Run `train.ipynb`:

1. Set paths (data folder, model save path).
2. Execute cells to train and evaluate.
3. Trained models are saved to `models/`.

## Prediction

Run `predict.ipynb`:

1. Load a trained model from `models/`.
2. Provide a test TSV with protein pairs.
3. Predictions are written to `predictions/`.

## Google Colab

Both notebooks support Colab. Mount Drive and set `COLAB_PROJECT_ROOT` to your project folder containing `data/` and `models/`.
