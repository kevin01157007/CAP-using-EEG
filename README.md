# CAP-using-EEG

Cyclic Alternating Pattern (CAP) detection from EEG signals using deep learning and machine learning. CAP is a physiological activity occurring during NREM sleep, and abnormal CAP patterns are associated with various sleep-related disorders.

## Overview

This project implements automated CAP detection using the [CAP Sleep Database from PhysioNet](https://physionet.org/content/capslpdb/1.0.0/). It extracts features from EEG signals (Lp-norm, standard deviation, skewness, kurtosis, entropy, Hjorth parameters) and classifies sleep epochs as CAP (MCAP-A1, MCAP-A2, MCAP-A3) or NonCAP events.

## Installation

```bash
# Clone the repository
git clone https://github.com/lucky-verma/CAP-using-EEG.git
cd CAP-using-EEG

# Create conda environment from env.yml
conda env create -f env.yml
conda activate cuda

# Or install dependencies via pip
pip install -r requirements.txt
```

## Usage

1. **Download the CAP Sleep Database** from [PhysioNet](https://physionet.org/content/capslpdb/1.0.0/)
2. **Data Exploration**: Run `notebooks/data/data_exploration.ipynb` to understand the dataset structure
3. **Model Training**: Run notebooks in `notebooks/train/` for training and evaluation:
   - `tsai_paper_subjectwise.ipynb` - Subject-wise training with balanced data
   - `tsai_paper_subjectwise_unb.ipynb` - Subject-wise training with unbalanced data
   - `tsai_raw_subjectwise.ipynb` - Training on raw EEG signals

## Repository Structure

```
CAP-using-EEG/
├── README.md                 # Project documentation
├── requirements.txt          # Python dependencies
├── env.yml                   # Conda environment file
├── dataset.py                # PyTorch DataLoader for CAP Sleep Database
├── saved_annotations.csv     # Saved annotation data
├── .gitignore
└── notebooks/
    ├── data/                 # Data exploration and preprocessing
    │   ├── data_exploration.ipynb
    │   ├── rough.ipynb
    │   ├── balanced_data.csv
    │   ├── saved_annotations.csv
    │   ├── saved_features.csv
    │   └── timeseries.csv
    └── train/                # Model training notebooks
        ├── tsai_paper_subjectwise.ipynb
        ├── tsai_paper_subjectwise_unb.ipynb
        ├── tsai_raw_subjectwise.ipynb
        ├── models/           # Saved model checkpoints
        └── catboost_info/    # CatBoost training logs
```

## Tech Stack

- **Language**: Python 3.10+
- **Deep Learning**: PyTorch, tsai (time series AI), fastai
- **Machine Learning**: scikit-learn, PyCaret, CatBoost
- **EEG Processing**: MNE-Python, pyedflib
- **Data Analysis**: pandas, NumPy, SciPy
- **Visualization**: matplotlib, seaborn

## Models

The project explores multiple architectures for CAP classification:
- **Deep Learning**: InceptionTime, XceptionTime, LSTM, LSTM-FCN, ResCNN, FCN, OmniScaleCNN, mWDN
- **Machine Learning**: Various classifiers via PyCaret (CatBoost, LightGBM, XGBoost, etc.)

## Dataset

This project uses the [CAP Sleep Database](https://physionet.org/content/capslpdb/1.0.0/) from PhysioNet, which contains polysomnographic recordings with CAP annotations from subjects with various sleep disorders.

## License

This project is for research and educational purposes.
