
# **<span style="color:#FF6B6B">Major Monitoring Parameters in MLOps</span>**

Once a model is deployed, the **biggest risk is silent performance degradation**.
Unlike traditional software, ML systems can **keep running but produce worse predictions over time**.

To detect these issues, MLOps monitors several parameters:

```
Data Drift
Model Drift (Concept Drift)
Prediction Drift
Feature Drift
Data Quality Issues
Latency / Infrastructure Metrics
```

The two **most critical ones** are:

```
Data Drift
Model Drift
```

Let's understand them deeply.

---

# **<span style="color:#FFD166">1. Data Drift</span>**

## **<span style="color:#66C2FF">Simple Definition</span>**

**Data Drift occurs when the distribution of input data changes compared to the data used during training.**

In simple words:

```
Training Data ≠ Production Data
```

---

## **<span style="color:#66C2FF">Analogy</span>**

Imagine a **teacher who prepared exam questions based on last year's syllabus**.

But this year:

```
syllabus changed
topics changed
difficulty changed
```

The teacher's prepared answers no longer match the exam questions.

This is exactly what happens in **data drift**.

---

## **<span style="color:#66C2FF">Example (Loan Model)</span>**

Your loan model was trained on:

```
Salary range: 20k – 50k
Loan amount: 5k – 20k
```

But production data becomes:

```
Salary range: 80k – 200k
Loan amount: 50k – 300k
```

The model has **never seen such values** before.

So predictions become unreliable.

---

## **<span style="color:#66C2FF">Graphical View</span>**

Training distribution:

```
Salary
|
|        ███████
|      ███████████
|    █████████████
|________________________
      20k      50k
```

Production distribution:

```
Salary
|
|                    ███████
|                 ███████████
|               █████████████
|_______________________________
             80k        200k
```

The distributions shifted → **data drift occurred**.

---

## **<span style="color:#66C2FF">How Data Drift Affects ML Systems</span>**

Effects include:

```
prediction accuracy drops
unexpected predictions
biased results
model becomes unreliable
```

Example:

Fraud detection model trained on **2019 transactions**.

But fraud patterns change in **2024**.

The model fails to detect new fraud patterns.

---

## **<span style="color:#66C2FF">How Data Drift Is Detected</span>**

MLOps systems compare **training vs production data distributions**.

Common statistical methods:

```
Kolmogorov–Smirnov test (KS test)
Population Stability Index (PSI)
Jensen–Shannon divergence
```

Example tools:

* **Evidently AI**
* **WhyLabs**
* **Arize AI**

---

## **<span style="color:#66C2FF">How Data Drift Is Handled</span>**

When drift is detected:

```
collect new data
retrain the model
update feature engineering
deploy updated model
```

Pipeline example:

```
Drift detected
     ↓
Trigger retraining
     ↓
Validate new model
     ↓
Deploy updated model
```

---

# **<span style="color:#FFD166">2. Model Drift (Concept Drift)</span>**

## **<span style="color:#66C2FF">Simple Definition</span>**

Model Drift happens when **the relationship between input features and target variable changes**.

```
X → Y relationship changes
```

Even if the data distribution remains similar.

---

## **<span style="color:#66C2FF">Analogy</span>**

Imagine a **doctor diagnosing diseases**.

Earlier rule:

```
High fever + cough → Flu
```

But a new virus appears.

Now:

```
High fever + cough → COVID
```

The relationship between **symptoms and disease changed**.

The doctor's old rule becomes wrong.

This is **concept drift**.

---

## **<span style="color:#66C2FF">Example (Recommendation System)</span>**

Before pandemic:

```
People watch movies on weekends
```

Model learns:

```
Weekend → High watch probability
```

After pandemic:

```
People watch movies every day
```

The **relationship changed**.

The model becomes inaccurate.

---

## **<span style="color:#66C2FF">Why Model Drift Is Dangerous</span>**

Unlike data drift:

```
data distribution may look normal
```

But predictions become wrong because:

```
patterns changed
relationships changed
```

This is harder to detect.

---

## **<span style="color:#66C2FF">How Model Drift Is Detected</span>**

Monitoring metrics such as:

```
accuracy
precision
recall
F1 score
R²
```

If performance drops:

```
model drift suspected
```

Monitoring tools:

* **Evidently AI**
* **Arize AI**

---

## **<span style="color:#66C2FF">How Model Drift Is Handled</span>**

Solutions include:

```
continuous retraining
online learning
feature updates
model redesign
```

Typical pipeline:

```
performance monitoring
      ↓
performance drop detected
      ↓
trigger retraining
      ↓
deploy updated model
```

---

# **<span style="color:#FFD166">3. Prediction Drift</span>**

Prediction drift occurs when **model predictions distribution changes over time**.

Example:

Fraud detection model normally predicts:

```
fraud probability: 1–5%
```

But suddenly predictions become:

```
fraud probability: 30–50%
```

This indicates something abnormal in:

```
data
model
feature pipeline
```

---

# **<span style="color:#FFD166">4. Data Quality Monitoring</span>**

MLOps systems also monitor:

```
missing values
invalid values
schema changes
data pipeline failures
```

Example:

```
salary column missing
age column renamed
new categorical values appear
```

Tools used:

* **Great Expectations**
* **Deequ**

---

# **<span style="color:#FF6B6B">Summary</span>**

| Monitoring Parameter | What Changes                             | Effect on Model             |
| -------------------- | ---------------------------------------- | --------------------------- |
| Data Drift           | input data distribution                  | predictions unreliable      |
| Model Drift          | relationship between features and target | model becomes incorrect     |
| Prediction Drift     | prediction distribution                  | indicates model instability |
| Data Quality Issues  | missing or incorrect data                | pipeline failure            |

---

# **<span style="color:#7DFFB3">Key Insight</span>**

Traditional software monitoring checks:

```
CPU
memory
latency
errors
```

But ML monitoring must check:

```
data distributions
model accuracy
feature behavior
prediction patterns
```

This is why **ML monitoring is much harder than normal system monitoring**.

---

If you want, I can also explain **the 6 types of drift that occur in ML systems (data drift, concept drift, covariate drift, label drift, prediction drift, feature drift)** with **clear diagrams and real production examples**, which is extremely important for **ML system design interviews**.
