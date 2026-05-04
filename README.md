# 📊 Predictive Analytics — Football Match Outcomes

## 🎯 Objective

This project aims to develop predictive models capable of estimating:

* the **match result** (home team win or loss)
* and the **number of goals**, segmented into different ranges (over/under)

More than the prediction itself, the focus is on building a structured analytical process, paying attention to data quality, variable selection, and validation of results.

---

## 🧠 Problem Framing

The problem was modeled as multiple binary classification tasks:

### Match Result:

* `1` → Home team win
* `0` → Home team lose

### Goal Ranges:

* `under_4_5`
* `under_3_5`
* `over_0_5`
* `over_1_5`

Each variable indicates, in binary form, whether or not the analyzed match falls within that goal range.

--

## 📥 Input Features

The input variables were constructed based on the teams' recent performance, considering exclusively the **last 5 games of that championship**, with values ​​expressed as percentages of success.

- All data was manually entered into a relational table from a CSV file, according to historical data acquired from the "*Sofascore*" platform (https://sofascore.com). > ### 📊 Performance Calculation

>
> A club's performance in matches is calculated as the percentage of points earned in relation to the total possible points.

>
> Considering the scoring system:
> - Win = 3 points
> - Draw = 1 point
> - Loss = 0 points
>
> **Example:**
>
> Points earned:
> - 3 wins → 3 × 3 = 9 points
> - 3 draws → 3 × 1 = 3 points
> - **Total: 12 points**
>
> Possible points:
> - 6 games → 6 × 3 = 18 points
>
> **Percentage:**

> $$\text{Percentage} = \left( \frac{\text{Points earned}}{\text{Total possible points}} \right) \times 100$$
>
> Substituting:
>
> $$\left( \frac{12}{18} \right) \times 100 \approx 66{,}67\%$$

The central idea was to capture the teams' momentum in a standardized and comparable way.

### Variables Used:

#### Input Variables:

* `pct_vit_prob`: The probability of victory for the home team, based on probabilistic concepts and shown on the official match page of the Sofascore platform.
* `aprvt_time`: The home team's performance in the last 5 games of that championship, regardless of location (home/away).
* `aprvt_adv`: The away team's performance in the last 5 games of that championship, regardless of location (home/away).
* `aprvt_time_casa`: The home team's performance playing at home in the last 5 games of that championship.
* `aprvt_adv_vis`: The away team's performance playing away in the last 5 games of that championship.
* `aprvt_time_cft`: Home team's recent record against this opponent, regardless of location.
* `aprvt_adv_cft`: Away team's recent record against the home team, regardless of location.
* `avg_goals`: Average number of goals per match in recent encounters between the two teams.
* `xg_time`: Expected Goals (xG) for the home team: the probability of the home team scoring a goal in that match, based on Sofascore's own statistics.
* `xga_time`: Expected Goals Against (xGA) for the home team: the probability of the home team conceding a goal in that match, based on Sofascore's own statistics.
* `xg_vis`: Expected Goals (xG) for the away team: the probability of the away team scoring a goal in that match, based on Sofascore's own statistics.
* `xga_vis`: Expected Goals Against (xGA) of the opposing team: the probability of the away team conceding a goal in that match, based on statistics from Sofascore itself.

Output Variables:

* `result`: Binary classification system representing the final score of the match, where "1" indicates a win or draw for the home team and "0" indicates a loss for the home team.
* `menos_4.5`: Binary classification indicating whether the number of goals in the match was below the 4.5-goal range, where "1" indicates if the score remained below and "0" if it exceeded.
* `menos_3.5`: Binary classification indicating whether the number of goals in the match was below the 3.5-goal range, where "1" indicates if the score remained below and "0" if it exceeded.
* `mais_0.5`: Binary classification indicating whether the number of goals in the match was above the 0.5-goal range, where "1" indicates if the score exceeded and "0" if it did not.
* `mais_1.5`: Binary classification indicating whether the number of goals in the match exceeded the 1.5-goal range, where "1" indicates if the score exceeded that range and "0" if it did not.

---

## 🏗️ Data Preparation & Feature Engineering

Data preparation was a central step in the project, focusing on:

* Standardization of variables in percentage format
* Handling inconsistencies and missing values
* Building context-based features (and not just raw data)
* Ensuring temporal consistency (avoiding future information leaks)

In addition, **input variable selection (X)** was performed iteratively, seeking to maximize model performance for each target variable (y), testing different feature combinations.

---

## ⚖️ Data Balance & Bias Handling

Strategies were applied to mitigate potential biases in the data, including:

* Analysis of class distribution (balancing)
* Adjustments to handle unbalanced classes
* Evaluation of the representativeness of variables
* Validation of data consistency over time

The goal was to ensure that the model did not learn distorted or biased patterns.

---

## ⚙️ Modeling Approach

The models were developed using **Python**, with the following libraries:

* Pandas
* NumPy
* Scikit-learn

### 🔹 Preparation for Modeling

* Separation of data into training and testing sets (**80% training / 20% testing**)
* Use of `train_test_split` with `random_state` to ensure reproducibility
* Standardization of input variables with **StandardScaler**

### 🔹 Models Evaluated

Different Machine Learning algorithms were tested for performance comparison:

* Logistic Regression
* Random Forest
* XGBoost
* Support Vector Machine (SVM)
* k-Nearest Neighbors (kNN)

---

## 📈 Model Evaluation

The models were evaluated based on different metrics:

* Accuracy
* Precision / Recall
* Confusion Matrix

In addition to quantitative metrics, a qualitative analysis of the results was performed, seeking to understand:

* patterns captured by the model
* limitations
* possible improvements

---

## 🔍 Key Insights

* Recent team performance proved relevant as a predictive variable
* The choice and combination of features had a direct impact on performance
* Different models showed distinct behaviors depending on the target (result vs. goals)

---

## 🤖 Use of AI

Artificial Intelligence tools were used to support development for:

* code optimization
* exploration of analytical approaches
* hypothesis validation

Always focused on accelerating the process without compromising the quality of the analysis.

---

## 🚀 Next Steps

Possible project evolutions include:

* Testing with more advanced models and ensembles
* Inclusion of new contextual variables
* Dataset expansion
* Deployment of the model in an automated pipeline

---

## 📌 Final Thoughts

This project reflects a practical approach to predictive analytics, focusing on the study and application of machine learning models in a context present in the lives of millions of people.

Developed as part of building a personal portfolio, the work seeks to consolidate analytical fundamentals and explore different modeling approaches in a structured way.

More than predicting results, the focus was on structuring a consistent, interpretable, and evolveable analytical process.
