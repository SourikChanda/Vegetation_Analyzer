**Vegetation Dynamics Analysis with Bootstrapped Fuzzy Clustering & Chaos Metrics
**
This repository contains a Python workflow to analyze vegetation dynamics using satellite-derived indices. It includes bootstrapped synthetic data generation, fuzzy clustering of LAI (Leaf Area Index), and calculation of chaos indicators such as Lyapunov exponent, DFA, and correlation dimension.

🌱 Dataset

The dataset is collected from Henry Island, Sundarbans, using satellite data. It includes 5-day vegetation indices for the study area. The CSV file should contain at least the following columns:

center_date – Date of observation

LAI – Leaf Area Index

MVI – Moisture Vegetation Index

NDVI – Normalized Difference Vegetation Index

NDWI – Normalized Difference Water Index


Dependencies

This project requires Python 3.8+ and the following packages:

pip install scikit-fuzzy tensorflow nolds pandas matplotlib scikit-learn

Usage Instructions

Upload your dataset
The code is designed to run on Google Colab. Upload your CSV file when prompted:

from google.colab import files
uploaded = files.upload()

Preprocessing

The workflow selects the features ['LAI', 'MVI', 'NDVI', 'NDWI'].

Missing values are removed.

Features are normalized using MinMaxScaler.

Synthetic Data Generation (Bootstrap + Noise)

Simple bootstrapping is applied to conditional features (MVI, NDVI, NDWI) and target (LAI).

Gaussian noise is added for variability.

Real + synthetic datasets are combined for further analysis.

Fuzzy Clustering

The LAI values are clustered into 3 fuzzy clusters using skfuzzy.cluster.cmeans.

A scatter plot visualizes cluster membership across samples.

Chaos Indicators
The following metrics are computed on the combined LAI dataset:

Largest Lyapunov Exponent (lyap_r) – indicates chaos vs. stability.

Detrended Fluctuation Analysis (DFA) – scaling behavior.

Correlation Dimension (corr_dim) – complexity of the attractor.

Interpretation of Lyapunov exponent:

> 0: Vegetation dynamics are chaotic

< 0: Vegetation dynamics are stable or periodic

≈ 0: Likely stochastic or noise-driven
