# 🧠 Deep Learning for Financial Time Series Prediction
### A Systematic Literature Review — *From Classical Methods to Modern Architectures*

> **Author:** Steve Francies A · College of Engineering Trivandrum  
> **Scope:** 12 peer-reviewed & preprint studies · 2011–2025  
> **Status:** 📄 Complete — Submitted for academic review

---

## 📌 Overview

This repository contains a **systematic literature review** examining the evolutionary progression of machine learning and deep learning methods applied to **financial time series prediction**.

The review traces a coherent five-stage architectural arc:

```
ARIMA / GARCH  →  Random Forest / GBT  →  LSTM  →  CNN-LSTM  →  BiLSTM-Attention + DRL
   (Pre-2010)         (~2010–2016)          (2017–2018)   (2019–2021)      (2022–present)
```

Each generation is evaluated against its predecessor — not just academically, but through **real financial performance metrics** including Sharpe ratio, daily return, and maximum drawdown.

---

## 🎯 Research Questions

| # | Research Question |
|---|---|
| **RQ1** | How has financial time series prediction evolved from classical statistical models through conventional ML to deep learning, and what specific limitations drove each transition? |
| **RQ2** | Which deep learning architectures demonstrate the strongest empirical performance, and when do more complex models justify their additional computational cost? |
| **RQ3** | What are the principal challenges — interpretability, overfitting, non-stationarity, absent benchmarks — constraining practical deployment? |
| **RQ4** | What are the most promising future directions: explainable AI, online adaptive learning, and multi-modal temporal fusion? |

---

## 📊 Key Empirical Findings

### S&P 500 Daily Returns (Fischer & Krauss, 2018; Krauss et al., 2017)

| Model | Daily Return | Sharpe Ratio |
|---|---|---|
| Logistic Regression | 0.26% | — |
| Standard DNN | 0.32% | — |
| Random Forest | 0.43% | 4.71 |
| **LSTM** | **0.46%** | **5.83** |

> 📎 Probability of LSTM results arising by chance: **2.77 × 10⁻¹⁸⁷**

### Shanghai Composite Index — R² Score (Lu et al., 2020)

| Architecture | R² |
|---|---|
| MLP | 0.9442 |
| RNN | 0.9593 |
| LSTM | 0.9622 |
| CNN-RNN | 0.9631 |
| **CNN-LSTM** | **0.9646** |

### Other Notable Results

- 🐦 **Twitter Sentiment (Bollen et al., 2011):** 87.6% directional accuracy on DJIA using public mood — the *Calm* dimension of Twitter data Granger-causes market movements
- 💳 **Credit Scoring (Talaat et al., 2024):** DNN + SHAP achieves 0.8350 accuracy and 0.9879 specificity while remaining regulatorily interpretable

---

## 🏗️ Repository Structure

```
deep-learning-finance-review/
│
├── 📄 Literature_Review.pdf          # Full 28-page systematic review
│
├── 📁 research_notes/
│   ├── stage1_classical_models.md    # ARIMA, GARCH — baseline benchmarks
│   ├── stage2_ensemble_ml.md         # Random Forest, Gradient Boosted Trees
│   ├── stage3_lstm.md                # LSTM architecture & Fischer/Krauss analysis
│   ├── stage4_cnn_lstm.md            # CNN-LSTM hybrid (Lu et al., 2020)
│   └── stage5_bilstm_drl.md          # BiLSTM-Attention + Deep RL (Huang et al., 2024)
│
├── 📁 references/
│   └── bibliography.bib              # Full BibTeX reference list (12 studies)
│
├── 📁 figures/
│   ├── fig1_evolutionary_progression.png
│   ├── fig2_lstm_cell_architecture.png
│   ├── fig3_cnn_lstm_pipeline.png
│   ├── fig4_bilstm_drl_framework.png
│   └── fig5_comparative_performance.png
│
└── 📁 implementation/                # (Planned — see Future Work)
    └── README.md
```

---

## 🔬 Architectures Reviewed

### Stage 1 — Classical Statistical Models *(Pre-2010)*
- **ARIMA** — linear combinations of past values and lagged forecast errors; structurally incapable of capturing non-linearity
- **GARCH** — models time-varying volatility; still confined to linear mean-return relationships
- **Role:** Benchmark baseline for all subsequent comparisons

### Stage 2 — Conventional Machine Learning *(~2010–2016)*
- **Random Forest** — decorrelated decision tree committees; captures non-linearity without explicit specification
- **Gradient Boosted Trees** — sequential residual correction; strong learner via iterative refinement
- **Key paper:** Krauss et al. (2017) — 73% annualised returns after transaction costs on S&P 500

### Stage 3 — LSTM Networks *(2017–2018)*
- **Long Short-Term Memory** — learnable forget/input/output gates for long-range temporal dependencies
- Addresses the fundamental sequential memory gap of classical ML
- **Key paper:** Fischer & Krauss (2018) — 0.46% daily return, Sharpe 5.83

### Stage 4 — CNN-LSTM Hybrid *(2019–2021)*
- **CNN** pre-processes raw sequences with shared-weight convolutional filters + max-pooling
- Compressed, denoised feature maps passed to **LSTM** for temporal modelling
- **Key paper:** Lu et al. (2020) — R² = 0.9646 on 29-year Shanghai Composite Index dataset

### Stage 5 — BiLSTM-Attention + Deep Reinforcement Learning *(2022–present)*
- **BiLSTM** — dual LSTM layers in opposite temporal directions; bidirectional context
- **Attention mechanism** — softmax-weighted time step importance; explicit temporal focus
- **DRL** — policy network directly learns buy/sell/hold actions via reward maximisation
- **Key paper:** Huang et al. (2024) — state-of-the-art trading framework

---

## ⚠️ Challenges Identified

| Challenge | Description |
|---|---|
| **Interpretability** | Neural network black-box opacity conflicts with regulatory requirements for explainable decisions |
| **Overfitting** | ~2,500 observations per asset per decade vs. millions of model parameters |
| **Non-stationarity** | Market regimes shift; static training paradigms fail to adapt |
| **No Standard Benchmarks** | Different datasets, periods, and metrics across studies prevent rigorous cross-study comparison |
| **Performance Decay** | ML trading returns peaked pre-2001, approaching zero post-2010 as strategies became commoditised |

---

## 🔭 Future Research Directions

1. **Explainable AI Integration** — inherently interpretable architectures (beyond post-hoc SHAP/LIME); attention weights as a partial solution
2. **Online & Adaptive Learning** — continuous parameter updating as new market data arrives; adaptive to regime changes
3. **Multi-Modal Temporal Fusion** — combining price sequences + financial news (BERT/FinBERT) + social media sentiment + macroeconomic indicators + Graph Neural Networks
4. **Interval Prediction & Uncertainty Quantification** — probabilistic forecasts with calibrated confidence intervals; currently addressed in fewer than 5% of papers

---

## 📚 Studies Reviewed

| Authors | Year | Key Contribution |
|---|---|---|
| Bollen, Mao & Zeng | 2011 | Twitter sentiment predicts DJIA; Calm dimension Granger-causal |
| Krauss, Do & Huck | 2017 | Large-scale ML comparison on S&P 500; ensemble beats individual models |
| Fischer & Krauss | 2018 | LSTM beats Random Forests; EMH challenged with p = 2.77 × 10⁻¹⁸⁷ |
| Lu et al. | 2020 | CNN-LSTM hybrid outperforms standalone LSTM by 4% on Shanghai Index |
| Sezer, Gudelek & Ozbayoglu | 2020 | Survey of 140 papers; LSTM in 52.5% of all DL financial forecasting studies |
| Ozbayoglu et al. | 2020 | Deep learning for financial applications — comprehensive survey |
| Zou et al. | 2022 | Survey of DL techniques; text-augmented models consistently outperform price-only |
| Zhang, Sjarif & Ibrahim | 2024 | Review of DL price forecasting 2020–2022; uncertainty quantification identified as gap |
| Huang et al. | 2024 | BiLSTM-Attention + DRL trading framework; current state-of-the-art |
| Talaat et al. | 2024 | DNN + SHAP for credit scoring; interpretability without accuracy sacrifice |
| Mienye et al. | 2024 | Survey of deep learning in finance; volatility clustering and non-stationarity analysis |
| El Alami et al. | 2025 | Systematic review; hybrid models and XAI dominate current state-of-the-art |

---

## 🧪 Methodology

- **Review type:** Systematic literature review
- **Study period covered:** 2011–2025
- **Number of primary studies:** 12
- **Selection criteria:** Peer-reviewed journals, arXiv preprints; empirical evaluation on real financial datasets; English-language publications
- **Evaluation metrics tracked:** MAE, RMSE, R², directional accuracy, daily return, Sharpe ratio, maximum drawdown, win rate

---

## 🗺️ Theoretical Framework

This review operates against the backdrop of two competing market theories:

- **Efficient Market Hypothesis (Fama, 1970)** — prices fully reflect all available information; historical data cannot yield consistent excess profits
- **Adaptive Market Hypothesis (Lo, 2004)** — markets evolve dynamically; temporary exploitable inefficiencies exist but erode as participants adopt similar strategies

The empirical evidence reviewed consistently challenges the weak-form EMH while being consistent with the AMH's prediction that ML-based returns decay over time.

---

## 🚧 Planned Extensions

- [ ] Reproduce Fischer & Krauss (2018) LSTM baseline on public S&P 500 data
- [ ] Implement CNN-LSTM architecture (Lu et al., 2020) with open-source dataset
- [ ] Benchmark SHAP explainability on a credit scoring dataset (UCI)
- [ ] Extend comparison to Transformer / temporal attention models (post-2022)

---

## 📄 Citation

If you reference this review, please cite:

```bibtex
@misc{francies2025dlfinance,
  author    = {Francies A, Steve},
  title     = {Deep Learning for Financial Time Series Prediction: An Evolutionary Review
               from Classical Methods to Modern Architectures},
  year      = {2025},
  institution = {College of Engineering Trivandrum},
  note      = {Systematic Literature Review}
}
```

---

## 📬 Contact

**Steve Francies A**  
College of Engineering Trivandrum  

> *This repository was created as part of research work and is maintained for academic and internship portfolio purposes.*

---

<div align="center">
  <sub>Built with rigor · Reviewed with care · Shared for learning</sub>
</div>
