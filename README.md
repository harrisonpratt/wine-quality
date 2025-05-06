# Harrison Pratt  
**Professor Lopez**  
**Principles of Data Science**  
**April 28, 2025**

## Exploratory Data Analysis in R

---

### 1) Business Understanding

When determining if a wine is considered high-quality, there are certain attributes that good wines often have. One of these is **acidity** — a medium amount can add freshness and structure, while too much or too little can unbalance a wine. 

Another factor is **pH**. A pH that is too low or too high can negatively impact the taste, making the wine lower-quality.  

Finally, **residual sugar** also plays a critical role. Too much or too little can create imbalanced flavors.  

Having a balance between these attributes helps create a **balanced wine with complexity**, which are hallmarks of high-quality wine.

**Sources for Understanding:**
- [Perceiving Acidity in Wine – Wine Spectator](https://www.winespectator.com/articles/perceiving-acidity-in-wine)
- [Sugar in Wine – Decanter China](https://www.decanterchina.com/en/news/Decanter%20Features/sugar-in-wine)
- [Sugar Content in Wine – Farang Wine](https://www.farangwine.com/sugar-content-in-wine-explained-which-wines-have-the-most-and-least-sugar)
- [What Makes a Wine Good – Medium (Data Science)](https://medium.com/data-science/what-makes-a-wine-good-ea370601a8e4)

---

### 2) Data Understanding

This dataset gathers information from red and white *Vinho Verde* wine samples from Northern Portugal.

- **Red wine samples**: 1,599  
- **White wine samples**: 4,898  
- **Total samples**: 6,497

There are:
- **11 continuous variables**
- **1 ordinal (integer) variable**
- **1 categorical variable**

| Variable Name         | Measurement Scale | Type        | Description                            |
|----------------------|-------------------|-------------|----------------------------------------|
| fixed_acidity        | Ratio             | Continuous  | Tartaric acid level                    |
| volatile_acidity     | Ratio             | Continuous  | Acetic acid (wine fault)               |
| citric_acid          | Ratio             | Continuous  | Citric acid level                      |
| residual_sugar       | Ratio             | Continuous  | Sugar left after fermentation          |
| chlorides            | Ratio             | Continuous  | Salt content                           |
| free_sulfur_dioxide  | Ratio             | Continuous  | Preservative for freshness             |
| total_sulfur_dioxide | Ratio             | Continuous  | Total sulfur dioxide                   |
| density              | Ratio             | Continuous  | Density of the wine                    |
| pH                   | Interval          | Continuous  | Acidity level (lower = more acidic)    |
| sulphates            | Ratio             | Continuous  | Wine preservative                      |
| alcohol              | Ratio             | Continuous  | Alcohol content                        |
| quality              | Ordinal           | Integer     | Wine quality score (0–10)              |
| color                | Nominal           | Categorical | Type of wine: red or white             |

---

### 3) Data Preparation

The data was downloaded from the [UCI Wine Quality Dataset](https://archive.ics.uci.edu/dataset/186/wine+quality).

The ZIP file included:
- `winequality-red.csv`: Red wine data
- `winequality-white.csv`: White wine data
- `winequality.names`: Metadata and citation info

I merged and labeled the datasets with a `color` column to distinguish between red and white wines.

---

### 4) Modeling + Evaluating (Exploratory Data Analysis)

We investigated the following hypotheses based on wine chemistry and expert knowledge.

#### Hypotheses:

- **Acidity Hypothesis (Fixed Acidity)**  
  - H₀: No significant relationship between fixed acidity and wine quality  
  - H₁: Moderate fixed acidity improves wine quality

- **pH Hypothesis**  
  - H₀: No significant relationship between pH and wine quality  
  - H₁: Moderate pH levels improve wine quality

- **Residual Sugar Hypothesis**  
  - H₀: No significant relationship between residual sugar and wine quality  
  - H₁: Balanced residual sugar improves wine quality

---

### White Wine Results

#### 1. Fixed Acidity vs. Quality
- **Correlation (r)**: -0.1137  
- **t-statistic**: -8.005  
- **p-value**: 1.48 × 10⁻¹⁵  
- **CI (95%)**: [-0.1412, -0.0859]  
🟡 Weak **negative** correlation — higher acidity slightly lowers quality.

#### 2. pH vs. Quality
- **Correlation (r)**: 0.0994  
- **t-statistic**: 6.992  
- **p-value**: 3.08 × 10⁻¹²  
- **CI (95%)**: [0.0716, 0.1271]  
🟢 Weak **positive** correlation — balanced pH slightly improves quality.

#### 3. Residual Sugar vs. Quality
- **Correlation (r)**: -0.0976  
- **t-statistic**: -6.860  
- **p-value**: 7.72 × 10⁻¹²  
- **CI (95%)**: [-0.1252, -0.0698]  
🔴 Weak **negative** correlation — excessive sugar slightly reduces quality.

---

### Red Wine Results

#### 1. Fixed Acidity vs. Quality
- **Correlation (r)**: 0.1241  
- **t-statistic**: 4.996  
- **p-value**: 6.50 × 10⁻⁷  
- **CI (95%)**: [0.0755, 0.1720]  
🟢 Weak **positive** correlation — slight quality increase with acidity.

#### 2. pH vs. Quality
- **Correlation (r)**: -0.0577  
- **t-statistic**: -2.311  
- **p-value**: 0.02096  
- **CI (95%)**: [-0.1065, -0.0087]  
🟡 Slight **negative** correlation — lower pH (higher acidity) slightly improves quality.

#### 3. Residual Sugar vs. Quality
- **Correlation (r)**: 0.0137  
- **t-statistic**: 0.5488  
- **p-value**: 0.5832  
- **CI (95%)**: [-0.0353, 0.0627]  
⚪ **No significant correlation** — residual sugar does not affect quality.

---

### Conclusion

This analysis explored how **acidity**, **pH**, and **residual sugar** relate to wine quality in both red and white wines.

- For **white wines**, acidity and sugar both had a small **negative** impact on quality, while a balanced pH had a **positive** impact.
- For **red wines**, fixed acidity showed a **positive** effect, lower pH slightly improved quality, and residual sugar had **no impact**.

These findings align with expert insights: balance is crucial. Although statistically significant, the **correlations were weak**, suggesting **other factors and personal taste play a large role** in wine quality evaluation.

---

### 5) Deployment

This markdown report was prepared with clear headings, formatting, and structure for GitHub display. Findings are logically organized and statistically supported. All data preparation steps, hypotheses, and interpretations are explained in a clean, readable manner.
