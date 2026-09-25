# 02 — Probabilistic Autoregressive Forecasting

Companion notebook to the post **"Your Model's MSE Is Lying to You — Part II: Autoregressive Rollout and Uncertainty Propagation."**

The Part 1 model predicts $\mu$ and $\sigma$ **one step ahead**. Here we roll it forward over many steps and ask whether the uncertainty stays honest. The naive approach (feed $\mu$ back as if it were truth) systematically underestimates uncertainty; sampling and feeding the sample back — barely more code — keeps the bands calibrated across the horizon.

## What the notebook shows

- The same heteroscedastic signal and Gaussian-head transformer from Part 1, reused as a one-step building block.
- **Deterministic rollout:** at each step, plug $\mu$ into the context. The band barely widens with horizon — it only sees local noise and ignores inherited uncertainty.
- **Stochastic rollout:** draw a sample from $(\mu, \sigma)$, feed it back, repeat $M$ times. Trajectories fan out; the band widens automatically as uncertainty compounds.
- **Coverage across the horizon:** from many test starting points, check whether a nominal 90% band actually covers ~90% at every step $h$. Stochastic stays near 90%; deterministic drops as $h$ grows.
- **PIT histograms:** a sharper check on the full predictive distribution — roughly flat for stochastic, typically U-shaped (overconfident) for deterministic.
- How many trajectories you need: the median stabilizes quickly; 90% band edges need more samples ($M \approx 200$ is a safe default).

## Run it

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/wesmail/probabilistic-forecasting/blob/main/02-probabilistic-autoregressive-forecasting/post2_autoregressive_rollout.ipynb)

Or locally:

```bash
pip install -r ../requirements.txt
jupyter lab post2_autoregressive_rollout.ipynb
```

Runs on CPU in a few minutes. Seeds are fixed; the last-decimal figures may shift slightly across platforms.

## Read the post

[Your Model's MSE Is Lying to You — Part II](https://towardsdatascience.com/your-models-mse-is-lying-to-you-part-ii/)
