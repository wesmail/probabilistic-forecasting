# 01 — Point vs. Probabilistic Forecasting

Companion notebook to the post **"Your Model's MSE Is Lying to You."**

Two transformers with an **identical backbone** are trained on the same synthetic signal, one with plain MSE, one with the Gaussian negative log-likelihood. They end up with nearly identical test-set MSE, and wildly different reliability once you check calibration **by noise regime** instead of on average.

## What the notebook shows

- A synthetic signal whose **noise level varies over time** (heteroscedastic).
- The same backbone with two heads: a point head (one number) and a Gaussian head (`μ` and `log σ`).
- **Near-identical test MSE** for both models — they look interchangeable on point accuracy alone.
- **Calibration by regime:** split the test set into quiet and noisy halves and check whether a nominal 90% interval actually covers 90%. The point model's fixed band over-covers when the signal is calm and badly under-covers when it's noisy; the probabilistic model's adaptive band stays far closer in both.
- A **threshold-exceedance** example: the point model can only say yes/no, while the probabilistic model returns an actual probability.

## Run it

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wesmail/probabilistic-forecasting/blob/main/01-point-vs-probabilistic/post1_point_vs_probabilistic.ipynb)

Or locally:

```bash
pip install -r ../requirements.txt
jupyter lab post1_point_vs_probabilistic.ipynb
```

Runs on CPU in a few minutes. Seeds are fixed; the last-decimal figures may shift slightly across platforms.

## Read the post

*(Article link added on publication.)*
