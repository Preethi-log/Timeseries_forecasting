Advanced Time Series Forecasting with Attention-Based RNN & SARIMAX
Multivariate Synthetic Dataset • Attention BiLSTM • SARIMAX Baseline • End-to-End Pipeline
Overview

This project presents a complete time-series forecasting pipeline that integrates both deep learning and classical statistical modeling. It demonstrates how modern architectures like Attention-based BiLSTM can learn complex patterns from multivariate temporal data, while also comparing performance with a traditional SARIMAX model.

The workflow includes dataset generation, preprocessing, model development, forecasting, and evaluation.

1️ Multivariate Synthetic Data Generation

A fully synthetic dataset is created to mimic real-world time series behavior. The dataset contains 2000 time steps and 5 engineered features, each representing a different type of temporal behavior:

 Feature descriptions
Feature	Description
f1	Sine wave with added noise (Primary target for forecasting)
f2	Correlated sine wave derived from f1
f3	Trend-like behavior with noise
f4	Seasonal repeating pattern
f5	A mixed signal combining multiple feature patterns

This dataset helps simulate realistic forecasting challenges such as:

Non-linearity

Periodicity

Seasonal fluctuations

Noise

Correlated variables


2️ Deep Learning Model – Luong Attention-Based BiLSTM

The deep learning component of the project is a Bidirectional LSTM model integrated with Luong-style Attention. This model is designed to capture long-term dependencies, identify important timesteps, and extract relevant features from multivariate sequences.

 Key Design Concepts
 Sequence Modeling with LSTM Layers

The model processes historical data sequences to learn temporal relationships between features.

 Bidirectional Architecture

Stacked BiLSTMs allow learning from both:

forward time direction

backward time direction

making the network more comprehensive.

 Luong Multiplicative Attention

The attention mechanism identifies which timesteps are most important for making the final prediction.
This makes the model more interpretable and enhances forecasting accuracy.

 Fully Connected Output Layer

Produces the next predicted value of the target variable (f1).

 Model Output Includes

Forecasted values

True values

Attention weights (visualizable for interpretability)

3️ Classical Baseline – SARIMAX Model

A SARIMAX model is included as a classical statistical baseline to compare against the deep learning model.

 Features of the SARIMAX Implementation

Configurable seasonal ARIMA components

Relaxed invertibility constraints to reduce convergence issues

Increased iteration limits

Multiple optimization algorithms tested

Forecasting performed on normalized and original scales

This helps evaluate:

How classical time-series models perform on the same dataset

Whether deep learning offers advantages

Whether certain behaviors (seasonality, trend) are better captured by SARIMAX

 Dataset Pipeline & Processing
 Standardization

All five features are standardized using Z-score normalization so that:

Deep learning models train efficiently

SARIMAX optimization becomes more stable

 Sliding Window Sequence Generation

A windowing approach is applied:

Sequence Length: 50 timesteps

Input Shape: 50 × 5 (multivariate input)

Output: Next future value of the scaled target (f1)

This converts the data into supervised learning format suitable for RNN models.

 Train/Test Split

80% used for training

20% used for testing

 Deep Learning Model — What It Learns

The Attention BiLSTM model learns:

Correlations between features

Long-term temporal relationships

Seasonal and periodic patterns

Which timesteps are most relevant (via attention weights)

The model outputs:

Predictions

Ground truth comparisons

Visualizable attention vectors for interpretability

 SARIMAX Baseline — Why It's Used

SARIMAX is included because it:

Provides a strong classical baseline

Works well for seasonal or trend-heavy data

Helps evaluate whether attention-based deep learning offers meaningful improvement

SARIMAX Evaluation Includes:

Predictions in normalized space

Predictions converted back to the original scale

RMSE + MAE calculation

This ensures a fair comparison with the BiLSTM model.

 Evaluation Metrics

Both models are evaluated using the following metrics:

RMSE — Root Mean Squared Error

Measures overall error magnitude.

MAE — Mean Absolute Error

Measures average prediction error.

MAPE — Mean Absolute Percentage Error

(Used mainly for the LSTM model)
Measures error relative to the true values, useful for interpretability.

These metrics make it easy to compare deep learning vs statistical forecasting approaches.

 Project Structure
 # Generated multivariate dataset
 # Full pipeline (processing, models, training, SARIMAX)
 # Project documentation


Each component is modular and clearly separated for easy understanding and reuse.

 Skills & Concepts Demonstrated

This project showcases expertise in:

Data Processing & Engineering

 Multivariate synthetic data generation
 Sliding-window sequence creation
 Scaling and normalization

Deep Learning

 LSTM-based sequence modeling
 Attention mechanism (Luong)
 Time-series forecasting with RNNs
 Interpretation using attention weights

Statistical Modeling

 SARIMAX structure
 Parameter tuning
 Handling convergence challenges

Model Evaluation

 RMSE, MAE, MAPE comparison
 Forecast visualization
 Baseline vs advanced model analysis

 Future Extensions

Possible enhancements include:

Transformer-based forecasting (Self-Attention)

N-BEATS or TCN (Temporal Convolutional Networks)

Multi-step forecasting

Hyperparameter optimization

Feature importance visualizations

Attention heatmaps

These extensions can improve performance, interpretability, and range of forecasting capabilities.

 Final Summary

This project provides a complete, advanced forecasting pipeline that:

Generates realistic multivariate time series

Builds an interpretable deep learning model with Attention-BiLSTM

Implements a stable and optimized SARIMAX baseline

Evaluates both models fairly using multiple metrics

Demonstrates how attention mechanisms improve forecasting and interpretability

It is an excellent example of combining modern AI techniques with traditional statistical modeling for time-series forecasting.
