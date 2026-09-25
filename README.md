# Probabilistic Forecasting for Physical Signals

Code and notebooks accompanying a series on probabilistic forecasting, moving from single-number point predictions to models that report calibrated, input-dependent uncertainty, and checking whether that uncertainty can actually be trusted.

The running example throughout is a synthetic physical signal with **heteroscedastic noise** (a noise level that varies over time), which is where ordinary point
forecasting quietly falls apart.

## Posts in the series

| # | Post | Notebook | Status |
|---|------|----------|--------|
| 1 | [*Your Model's MSE Is Lying to You*](https://towardsdatascience.com/your-models-mse-is-lying-to-you/) — why MSE can't express uncertainty, and the Gaussian NLL that fixes it | [`01-point-vs-probabilistic/`](01-point-vs-probabilistic/) | ✅ published |
| 2 | [*Your Model's MSE Is Lying to You — Part II*](https://towardsdatascience.com/your-models-mse-is-lying-to-you-part-ii/) — autoregressive rollout, stochastic trajectories, and whether the bands stay calibrated | [`02-probabilistic-autoregressive-forecasting/`](02-probabilistic-autoregressive-forecasting/) | ✅ published |


## What's here

Each post has its own folder with a self-contained notebook and a short README. Code shared across posts (the transformer backbone, the signal generator, the training and calibration helpers) lives in [`shared/`](shared/) once more than one post needs it.

## Running the notebooks

```bash
git clone https://github.com/wesmail/probabilistic-forecasting.git
cd probabilistic-forecasting
pip install -r requirements.txt
jupyter lab
```

Each notebook runs top to bottom on CPU in a few minutes. Random seeds are fixed for reproducibility, though exact figures in the last decimal place can vary across
platforms and library versions.

## Requirements

- Python 3.10+
- numpy, torch, matplotlib, scipy

(Pinned in [`requirements.txt`](requirements.txt).)

## About

Written by [Waleed Esmail](https://wesmail.github.io/) alongside the article series. Machine learning for scientific and physical time-series signals.

If you spot an error or have a question, open an issue, corrections welcome.

## License

Released under the [MIT License](LICENSE). You're free to reuse the code with attribution.
