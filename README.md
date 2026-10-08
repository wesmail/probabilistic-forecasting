# Probabilistic Forecasting for Physical Signals

Code and notebooks accompanying a series on probabilistic forecasting, moving from single-number point predictions to models that report calibrated, input-dependent uncertainty and, when a single Gaussian is not enough, to diffusion heads that can express multimodal futures.

The early posts use a synthetic signal with **heteroscedastic noise** (a noise level that varies over time). [Part III](https://towardsdatascience.com/your-models-mse-is-lying-to-you-iii-time-series-diffusion/) switches to a **double-well** signal, where the next value can sit in either of two modes and a Gaussian head is forced to put its peak where the truth has a dip.

## Posts in the series

| # | Post | Notebook | Status |
|---|------|----------|--------|
| 1 | [*Your Model's MSE Is Lying to You*](https://towardsdatascience.com/your-models-mse-is-lying-to-you/): why MSE can't express uncertainty, and the Gaussian NLL that fixes it | [`01-point-vs-probabilistic/`](01-point-vs-probabilistic/) | ✅ published |
| 2 | [*Your Model's MSE Is Lying to You: II*](https://towardsdatascience.com/your-models-mse-is-lying-to-you-part-ii/): autoregressive rollout, stochastic trajectories, and whether the bands stay calibrated | [`02-probabilistic-autoregressive-forecasting/`](02-probabilistic-autoregressive-forecasting/) | ✅ published |
| 3 | [*Your Model's MSE Is Lying to You III*](https://towardsdatascience.com/your-models-mse-is-lying-to-you-iii-time-series-diffusion/): when a Gaussian head has the wrong shape, and a diffusion head that can express any shape | [`03-time-series-diffusion/`](03-time-series-diffusion/) | ✅ published |


## Running the notebooks

```bash
git clone https://github.com/wesmail/probabilistic-forecasting.git
cd probabilistic-forecasting
pip install -r requirements.txt
jupyter lab
```

Each notebook runs top to bottom on CPU. Parts 1 and 2 finish in a few minutes; Part 3's diffusion rollout is the slowest cell (about one to two minutes). Random seeds are fixed for reproducibility, though exact figures in the last decimal place can vary across platforms and library versions.

## Requirements

- Python 3.10+
- numpy, torch, matplotlib, scipy

(Pinned in [`requirements.txt`](requirements.txt).)

## About

Written by [Waleed Esmail](https://wesmail.github.io/) alongside the article series. Machine learning for scientific and physical time-series signals.

If you spot an error or have a question, open an issue, corrections welcome.

## License

Released under the [MIT License](LICENSE). You're free to reuse the code with attribution.
