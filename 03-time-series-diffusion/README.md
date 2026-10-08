# 03 — Time-Series Diffusion Forecasting

Companion notebook to the post **"Your Model's MSE Is Lying to You III: Time Series Diffusion."**

Parts I and II gave the model an honest per-step uncertainty and a way to carry it forward over a horizon. Both still assume that the next value is drawn from a **single Gaussian**. When the future is multimodal, a ball that can fall left or right from a barrier, that shape is wrong even if the mean and variance are right. This notebook replaces the Gaussian head with a **diffusion head** that can express any shape, then slots it into the sampled rollout of Part II.

## What the notebook shows

- A two-bump toy distribution where the best Gaussian has the right mean and variance, and still puts ~38% of its mass where the truth has almost none.
- How a mixture of bell curves, and then a continuous mixture driven by a hidden variable $z$, repairs the shape.
- The diffusion **forward** process (add noise with a cosine schedule) and the **reverse** process run with no network at all, a straight-line denoiser recovers one bump, an S-curve recovers two.
- Training a small `DiffusionHead` with plain MSE on the noise, then verifying it regenerates the two bumps.
- A double-well physical signal where futures split at the barrier, with **true futures** available by restarting the simulator.
- Two forecasters with the **same encoder**, differing only in the head (Gaussian vs. diffusion), trained one step ahead and rolled out as in Part II.
- Side-by-side forecasts, CRPS, barrier share, and distance to the true distribution — shape, not only a single score, is what separates the heads.

## Run it

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wesmail/probabilistic-forecasting/blob/main/03-time-series-diffusion/post3_time_series_diffusion.ipynb)

Or locally:

```bash
pip install -r ../requirements.txt
jupyter lab post3_time_series_diffusion.ipynb
```

Runs on CPU. Most cells finish in seconds; the diffusion rollout over the test set takes about one to two minutes. Seeds are fixed; the last-decimal figures may shift slightly across platforms. Figures are written to `figures/` as you run.

## Prerequisites

This notebook continues Parts I and II. You do not need to re-run them, but the ideas of Gaussian NLL and sampled autoregressive rollout are assumed:

- [01 Point vs. Probabilistic](../01-point-vs-probabilistic/)
- [02 Probabilistic Autoregressive Forecasting](../02-probabilistic-autoregressive-forecasting/)

## Read the post

[Your Model's MSE Is Lying to You III: Time Series Diffusion](https://towardsdatascience.com/your-models-mse-is-lying-to-you-iii-time-series-diffusion/)
