# DA6401_Assignment3: Telugu Transliteration with Seq2Seq and Attention

Vishwambhar Reddy Yennam (DA24M027)

WandB Report: [](https://wandb.ai/da24m027-indian-institute-of-technology-madras/DA6401_Assignment3/reports/DA6401-Assignment-3--VmlldzoxMjg0NDk5OQ)

## Overview
This project implements and compares sequence-to-sequence (Seq2Seq) models for the task of transliterating Romanized Telugu text into native Telugu script. The project explores both vanilla Seq2Seq models and Seq2Seq models with attention mechanisms, leveraging PyTorch and Weights & Biases (wandb) for experiment tracking and hyperparameter sweeps.

## Project Structure
```
├── notebooks/
│   ├── seq2seq.ipynb              # Vanilla Seq2Seq model (no attention)
│   └── seq2seqattention.ipynb     # Seq2Seq model with Bahdanau attention
├── predictions/
│   ├── predictions_vanilla.csv    # Predictions from vanilla Seq2Seq model
│   └── predictions_attention.csv  # Predictions from attention-based model
├── Visualizations/
│   ├── attention_heatmaps_grid.png        # Attention heatmap visualizations
│   └── connectivity_visualizations_grid.png # Connectivity visualizations
├── README.md
```

## Notebooks
- **seq2seq.ipynb**: Implements a character-level Seq2Seq model (RNN/GRU/LSTM) for transliteration. Includes data preprocessing, model definition, training, evaluation, and wandb sweeps for hyperparameter optimization.
- **seq2seqattention.ipynb**: Extends the vanilla model by adding Bahdanau (additive) attention, allowing the decoder to focus on relevant parts of the input sequence. Also includes visualizations of attention weights and connectivity.

## Data
- The models are trained and evaluated on the [Dakshina Telugu dataset](https://github.com/google-research-datasets/dakshina), specifically the `te.translit.sampled.train.tsv` and `te.translit.sampled.dev.tsv` files.
- Data is preprocessed at the character level, and vocabularies are built for both source (Romanized) and target (Telugu) scripts.

## Outputs
- **predictions_vanilla.csv** and **predictions_attention.csv**: Each file contains three columns: `input` (Romanized word), `prediction` (model output in Telugu), and `target` (ground truth in Telugu). These files allow for direct comparison between model predictions and true transliterations.
- **Visualizations**: PNG files in the `Visualizations/` directory show attention heatmaps and model connectivity, providing insight into model behavior and interpretability.

## Experiment Tracking
- The project uses [Weights & Biases (wandb)](https://wandb.ai/) for experiment tracking, logging, and hyperparameter sweeps. Sweep configurations are defined in the notebooks, and results can be visualized on the wandb dashboard.

## How to Run
1. **Install dependencies** (in your Python environment):
   - torch
   - pandas
   - matplotlib
   - seaborn
   - wandb
   - (and other standard scientific Python libraries)
2. **Download the Dakshina dataset** and update the dataset paths in the notebooks if needed.
3. **Run the notebooks** in order:
   - `notebooks/seq2seq.ipynb` for the vanilla model
   - `notebooks/seq2seqattention.ipynb` for the attention-based model
4. **View predictions and visualizations** in the respective output folders.
5. **Track experiments** and sweeps on your wandb account (set up your API key as shown in the notebooks).

## Results
- The attention-based Seq2Seq model generally outperforms the vanilla model, as seen in the prediction outputs and validation accuracy tracked by wandb.
- Visualizations help interpret which parts of the input the model attends to during transliteration.
