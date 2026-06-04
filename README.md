# GNN Stroke Outcome Prediction

Predicting 90-day functional outcome (mRS) following hemorrhagic stroke using 
structural brain connectivity and graph neural networks.

## Overview
This notebook trains and compares four models on diffusion MRI structural 
connectivity matrices from the ROSE dataset:

1. Multimodal GNN — GraphSAGE network fusing connectivity graphs with clinical features
2. Graph-Only GNN — model using structural connectivity alone
3. Clinical Baseline — logistic regression on demographic and clinical features
4. LASSO Connectivity — L1-regularised regression on flattened connectivity matrices

A post-hoc edge importance explainer identifies nodes and edges with 
greatest impact on model prediction.

## Requirements
- Python 3.10+
- TensorFlow 2.x
- TensorFlow GNN ≥ 1.0.0
- nilearn
- scikit-learn
- scipy
- pandas
- numpy
- matplotlib
- seaborn

Install dependencies:
pip install tensorflow "tensorflow-gnn>=1.0.0" nilearn scikit-learn scipy pandas numpy matplotlib seaborn

## Data
Required files:
- Structural connectivity matrices (.mat) — one per subject
- ROSE_connectivity_binary_mRS.csv — subject IDs and binarized mRS labels
- Clinical CSV — ICH volume and location per subject
- HCP/SUIT/FreeSurfer atlas CSV — ROI names and MNI coordinates

## Usage
Open gnn_stroke_outcome_prediction.ipynb in Google Colab or Jupyter.
Update the path configuration variables at the top of each model cell 
to point to your local data files, then run cells in order.

## Output
Each model cell saves:
- Model weights (.weights.h5)
- Performance plot with ROC curve, bootstrap AUC distribution, and metric summary (.png)

The explainer cell additionally saves:
- 2-D glass brain connectivity plot (.png)
- Region importance bar chart (.png)
- Edge importance chart (.png)
- Region rankings (.csv)

