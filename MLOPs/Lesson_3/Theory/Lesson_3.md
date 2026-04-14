# **<span style="color:#FF6B6B">Simple MLflow Workflow and Mechanics</span>**

To understand **MLflow**, the best way is to see **how it fits inside a normal ML workflow**.

A typical ML development process looks like this:

```
Prepare Data
     ↓
Train Model
     ↓
Run Experiments
     ↓
Track Results
     ↓
Select Best Model
     ↓
Register Model
     ↓
Deploy Model
```

MLflow manages the **middle part of this workflow**.

---

# **<span style="color:#FFD166">High-Level MLflow Workflow</span>**

The simple MLflow workflow looks like this:

```
Experiment
     ↓
Run
     ↓
Log Parameters
     ↓
Log Metrics
     ↓
Log Model
     ↓
Store Artifacts
     ↓
Register Model
     ↓
Deploy
```

Let's understand each step.

---

# **<span style="color:#FFD166">Step 1: Create an Experiment</span>**

An **experiment** groups multiple training runs.

Example:

```
Experiment: Loan Default Prediction
```

Inside this experiment you may try different models:

```
Random Forest
XGBoost
Logistic Regression
```

MLflow organizes them under the same experiment.

Example code:

```python
import mlflow

mlflow.set_experiment("loan_prediction")
```

---

# **<span style="color:#FFD166">Step 2: Start a Run</span>**

A **run** represents one experiment execution.

Example run:

```
Model: RandomForest
max_depth: 10
n_estimators: 100
```

Code example:

```python
with mlflow.start_run():
    # training code here
```

Every run gets a **unique run ID**.

---

# **<span style="color:#FFD166">Step 3: Log Parameters</span>**

Parameters are **model configuration values**.

Examples:

```
learning_rate
max_depth
n_estimators
batch_size
```

MLflow records them using:

```python
mlflow.log_param("max_depth", 10)
mlflow.log_param("n_estimators", 100)
```

Now the system remembers exactly **how the model was trained**.

---

# **<span style="color:#FFD166">Step 4: Log Metrics</span>**

Metrics measure **model performance**.

Examples:

```
accuracy
precision
recall
F1 score
R²
```

Example logging:

```python
mlflow.log_metric("accuracy", 0.92)
```

MLflow stores these values for **experiment comparison**.

---

# **<span style="color:#FFD166">Step 5: Log Artifacts</span>**

Artifacts are **files generated during training**.

Examples:

```
trained model
plots
feature importance charts
datasets
evaluation reports
```

Example:

```python
mlflow.log_artifact("model.pkl")
```

Artifacts are stored in an **artifact store**.

---

# **<span style="color:#FFD166">Step 6: Log the Model</span>**

MLflow supports multiple frameworks:

```
scikit-learn
TensorFlow
PyTorch
XGBoost
```

Example with **Scikit-learn**:

```python
import mlflow.sklearn

mlflow.sklearn.log_model(model, "loan_model")
```

This saves the model with:

```
model file
environment dependencies
metadata
```

---

# **<span style="color:#FFD166">Step 7: Register the Model</span>**

After training the best model can be stored in the **model registry**.

Example versions:

```
loan_model_v1
loan_model_v2
loan_model_v3
```

Code example:

```python
mlflow.register_model(
    "runs:/run_id/loan_model",
    "loan_prediction_model"
)
```

Registry stages:

```
Staging
Production
Archived
```

---

# **<span style="color:#FFD166">Step 8: Deploy the Model</span>**

MLflow allows easy model serving.

Example command:

```
mlflow models serve -m models:/loan_prediction_model/Production
```

This starts a **REST API** for predictions.

Example request:

```
POST /invocations
```

Applications can now use the model.

---

# **<span style="color:#FF6B6B">Full MLflow Mechanics</span>**

Internally MLflow works with **four core components**.

```
Training Code
      ↓
MLflow Tracking Client
      ↓
Tracking Server
      ↓
Backend Store + Artifact Store
```

---

# **<span style="color:#FFD166">1. Tracking Client</span>**

Your training script interacts with MLflow.

Example:

```
mlflow.log_param()
mlflow.log_metric()
mlflow.log_model()
```

This client sends data to the **tracking server**.

---

# **<span style="color:#FFD166">2. Tracking Server</span>**

The tracking server manages experiment data.

Responsibilities:

```
store experiment metadata
manage runs
store parameters and metrics
```

It exposes an API used by MLflow clients.

---

# **<span style="color:#FFD166">3. Backend Store</span>**

Stores **experiment metadata**.

Examples:

```
parameters
metrics
run IDs
timestamps
```

Usually stored in:

```
SQLite
PostgreSQL
MySQL
```

---

# **<span style="color:#FFD166">4. Artifact Store</span>**

Stores **large files**.

Examples:

```
model files
plots
datasets
logs
```

Typical storage locations:

```
local filesystem
AWS S3
Azure Blob Storage
Google Cloud Storage
```

---

# **<span style="color:#FF6B6B">Complete MLflow Workflow Diagram</span>**

```
Training Script
      ↓
Start Run
      ↓
Log Parameters
      ↓
Log Metrics
      ↓
Log Artifacts
      ↓
Log Model
      ↓
Tracking Server
      ↓
Backend Store + Artifact Store
      ↓
Model Registry
      ↓
Deployment
```

---

# **<span style="color:#7DFFB3">Example MLflow Workflow Code</span>**

A minimal MLflow workflow:

```python
import mlflow
import mlflow.sklearn
from sklearn.ensemble import RandomForestClassifier

mlflow.set_experiment("loan_prediction")

with mlflow.start_run():

    model = RandomForestClassifier(max_depth=10)
    model.fit(X_train, y_train)

    accuracy = model.score(X_test, y_test)

    mlflow.log_param("max_depth", 10)
    mlflow.log_metric("accuracy", accuracy)

    mlflow.sklearn.log_model(model, "model")
```

This single script automatically creates:

```
experiment
run
parameter log
metric log
model artifact
```

---

# **<span style="color:#7DFFB3">Key Insight</span>**

Machine learning development involves **hundreds of experiments**.

Without tools like **MLflow**:

```
experiments become disorganized
models become unreproducible
deployment becomes risky
```

MLflow acts like a **central control system for ML experiments**.

---

If you'd like, I can also show you **a real production MLflow pipeline architecture (training → registry → CI/CD → deployment)** which is how **large companies structure ML systems**.
