# Wine Quality Analysis: Exploratory Data Analysis in R

**Author:** Harrison Pratt  
**Course:** Principles of Data Science  
**Professor:** Professor Lopez  
**Date:** April 28, 2025  

---

## 1. Business Understanding

High-quality wines often exhibit balance in key chemical properties. Specifically:

- **Acidity:** A medium amount adds freshness and structure. Too much or too little unbalances a wine.
- **pH Level:** An optimal pH supports stability and taste; extreme values diminish quality.
- **Residual Sugar:** Impacts flavor; both excess and deficiency can reduce wine balance.

**Sources:**
- [Wine Spectator - Perceiving Acidity in Wine](https://www.winespectator.com/articles/perceiving-acidity-in-wine)  
- [Decanter China - Sugar in Wine](https://www.decanterchina.com/en/news/Decanter%20Features/sugar-in-wine)  
- [Farang Wine - Sugar Content in Wine Explained](https://www.farangwine.com/sugar-content-in-wine-explained-which-wines-have-the-most-and-least-sugar)  
- [Medium - What Makes a Wine Good](https://medium.com/data-science/what-makes-a-wine-good-ea370601a8e4)

---

## 2. Data Understanding

The dataset combines red and white Vinho Verde wine samples from Portugal:

- **White wine samples:** 4,898  
- **Red wine samples:** 1,599  
- **Total samples:** 6,497  
- **Attributes:** 11 continuous variables, 1 integer (quality), 1 categorical (color)

| Variable Name            | Type       | Description                          |
|--------------------------|------------|--------------------------------------|
| fixed_acidity            | Continuous | Tartaric acid level                  |
| volatile_acidity         | Continuous | Acetic acid (wine fault)             |
| citric_acid              | Continuous | Citric acid content                  |
| residual_sugar           | Continuous | Sugar left after fermentation        |
| chlorides                | Continuous | Salt content                         |
| free_sulfur_dioxide      | Continuous | Free SO₂                             |
| total_sulfur_dioxide     | Continuous | Total SO₂                            |
| density                  | Continuous | Density                              |
| pH                       | Continuous | Acidity level (inverse scale)        |
| sulphates                | Continuous | Sulfate content                      |
| alcohol                  | Continuous | Alcohol content                      |
| quality                  | Integer    | Quality rating (0–10)                |
| color                    | Categorical| Wine type: red or white              |

---

## 3. Data Preparation

The data was downloaded from the UCI Machine Learning Repository:  
https://archive.ics.uci.edu/dataset/186/wine+quality

Steps:
1. Unzip the downloaded folder.
2. Load `winequality-red.csv` and `winequality-white.csv`.
3. Combine datasets for analysis and add a `color` column to distinguish types.

---

## 4. Modeling & Evaluation

We conducted exploratory data analysis (EDA) and correlation testing on three hypotheses.

### Hypotheses

| Hypothesis                    | Null Hypothesis (H₀)                                               | Alternative Hypothesis (H₁)                                               |
|------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------------------|
| Fixed Acidity                | No significant relationship with quality                           | Moderate fixed acidity contributes to higher quality                      |
| pH                           | No significant relationship with quality                           | Optimal pH contributes to higher quality                                  |
| Residual Sugar               | No significant relationship with quality                           | Balanced residual sugar contributes to higher quality                     |

---

## 5. EDA: Boxplots (White Wine)

```r
library(ggplot2)

features <- c("fixed.acidity", "volatile.acidity", "citric.acid", "pH", "residual.sugar")

for (feature in features) {
    p <- ggplot(wine_white, aes(x = factor(quality), y = .data[[feature]])) +
        geom_boxplot(fill = "skyblue") +
        labs(title = paste("Distribution of", feature, "by Wine Quality"),
             x = "Quality Score", y = feature) +
        theme_minimal()
    print(p)
}
