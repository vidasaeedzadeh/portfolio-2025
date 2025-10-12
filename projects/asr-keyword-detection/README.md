# Speech-to-Text / Keyword Detection (Lightweight)

Goal: Keyword spotting using Google Speech Commands (small-scale, laptop-friendly).

## Plan
1) Data: download subset of Speech Commands
2) Features: waveforms → spectrograms/MFCCs (torchaudio)
3) Baselines: logistic regression / random forest on MFCC
4) DL: 1D/2D CNN on spectrograms
5) Eval: accuracy, precision/recall/F1, confusion matrix
6) Packaging: simple CLI to run predictions on a .wav

## Repo Layout
- `notebooks/` — exploration, training, evaluation
- `src/` — reusable code (data, models, train, eval)
- `results/` — saved metrics/plots

## Setup
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt

