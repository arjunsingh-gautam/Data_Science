# **<span style="color:orange">Unsupervised Machine Learning</span>**

## **Content**

- Unsupervised Machine Learning
  - Definition
  - Features
  - Application
- Why implement Unsupervised ML
- Clustering Technique
  - Definition
  - Features
  - Eg.
  - Types of Clustering
    - Exclusive
    - Overlapping
    - Hierarchial clustering
- Explain Hierarchial Clustering in detail

  - Definition
  - Features
  - Purpose
  - Working
  - Use Cases
  - Algorithms

- Association Rule Technique

  - Definition
  - Purpose
  - Feature
  - Working
  - Eg. Recommender Systems
  - Algortihms used and their details

- Dimensionality Reduction Technique

  - Definition
  - Purpose
  - Feature
  - Working
  - Eg. Recommender Systems
  - Algortihms used and their details

- K-Means Clustering

  - Definition
  - Objective
  - Features
  - Components
  - How to choose K value in detail
    - WCSS
    - Elbow Method
  - What happens if we choose random k value
    - Random Initialisation Trap
  - Mathematics
  - Working and steps (Methodology)
  - Adv and Disadv

- DBSCAN Algorithm

  - Definition
  - Objective
  - Features
  - Components and their function in detail
  - How to vhoose parameter in DBSCAN
  - Mathematics
  - Working and steps (Methodology)
  - Adv and Disadv

- Agglomerative Clustering

  - Definition
  - Objective
  - Bottom Up approach
  - Linkage Criteria
  - Steps and Methodology
  - How to measure closest cluster
    - Mathematics
    - Working
  - Complete detail work eg.
  - Adv and Diadv

- Dendrogram
  - Definition
  - Working
  - Optimal no. of cluster

Here are detailed and organized notes on **Unsupervised Machine Learning**:

---

## 🧠 Unsupervised Machine Learning

### 🔷 Definition:

**Unsupervised Machine Learning** is a type of machine learning where the model is trained on data **without labeled output**. The algorithm tries to **discover patterns, groupings, or structures** from the input data on its own.

> 🚫 No target variable (output/label) is provided.

---

### 🌟 Key Features:

| Feature                      | Description                                                           |
| ---------------------------- | --------------------------------------------------------------------- |
| **No Labels Required**       | Learns from **input features** only, without labeled outcomes.        |
| **Pattern Discovery**        | Finds hidden patterns, similarities, or anomalies in the data.        |
| **Dimensionality Reduction** | Can reduce the number of features while preserving information.       |
| **High Exploratory Power**   | Useful for **data exploration** when you don’t know what to look for. |
| **Self-organizing**          | Clusters or transforms data **based on structure**, not rules.        |

---

### 🚀 Applications:

| Domain               | Use Case Example                                                       |
| -------------------- | ---------------------------------------------------------------------- |
| **Marketing**        | Customer segmentation (grouping customers based on behavior/purchases) |
| **Healthcare**       | Disease subtype detection                                              |
| **E-commerce**       | Product recommendation (based on similarity)                           |
| **Cybersecurity**    | Anomaly detection (fraudulent activity detection)                      |
| **Image Processing** | Image compression and pattern detection                                |
| **Search Engines**   | Document or text clustering                                            |
| **Genomics**         | Identifying gene expression patterns                                   |

---

### ❓ Why Implement Unsupervised Machine Learning?

#### ✅ Benefits:

1. **Works without labeled data**

   - Useful when labeled datasets are expensive or unavailable.

2. **Reveals hidden patterns**

   - Useful for **exploratory data analysis** and discovering unknown structures.

3. **Feature Engineering and Preprocessing**

   - Helps in **dimensionality reduction** and **data transformation** (e.g., PCA).

4. **Anomaly Detection**

   - Useful in fraud, network intrusion, and manufacturing fault detection.

5. **Real-World Applicability**

   - Most real-world data is unlabeled, making unsupervised learning highly practical.

#### 🔍 Practical Reasons:

- To **understand the structure** of large and complex datasets.
- To generate labels/clusters automatically where human labeling is infeasible.
- To **initialize supervised models** (e.g., clustering for pre-labeled datasets).

---

Here are complete and structured notes on **Clustering Technique** in Unsupervised Machine Learning:

---

## 🧩 Clustering Technique

### 🔷 Definition:

**Clustering** is an **unsupervised machine learning** technique that groups **similar data points** into **clusters** such that:

- Data points in the same cluster are **more similar** to each other.
- Data points in different clusters are **dissimilar** from each other.

> No labels are required — the algorithm automatically discovers the groupings.

---

### 🌟 Features of Clustering:

| Feature                           | Description                                                                  |
| --------------------------------- | ---------------------------------------------------------------------------- |
| **Unsupervised**                  | Works without labeled data                                                   |
| **Similarity-based grouping**     | Uses distance or similarity measures to form clusters                        |
| **Automatic structure discovery** | Helps find patterns in raw data                                              |
| **Scalable to large data**        | Can be applied to big datasets (e.g., customer segmentation, image grouping) |
| **Flexible distance metrics**     | Can use Euclidean, cosine, Manhattan distances, etc.                         |

---

### 🧠 Example Use Cases:

| Domain                | Example                                                        |
| --------------------- | -------------------------------------------------------------- |
| **Marketing**         | Customer segmentation based on purchase behavior               |
| **Healthcare**        | Grouping patients with similar symptoms or genetic profiles    |
| **Astronomy**         | Grouping galaxies or stars based on brightness, position, etc. |
| **Social Media**      | Community detection in social networks                         |
| **Document Analysis** | Grouping documents based on text/topic similarity              |

---

## 📊 Types of Clustering

---

### 1. ✅ **Exclusive Clustering** (Hard Clustering)

- **Definition:** Each data point **belongs to one and only one cluster**.
- **Example Algorithm:** **K-Means**
- **Use Case:** Simple classification-like grouping.
- **Pros:** Easy to interpret.
- **Cons:** Not suitable for overlapping classes.

---

### 2. 🔁 **Overlapping Clustering** (Soft Clustering)

- **Definition:** A data point **can belong to multiple clusters** with different degrees of membership.
- **Example Algorithm:** **Fuzzy C-Means**
- **Use Case:** When clusters are not strictly separate (e.g., customer who buys from multiple categories).
- **Pros:** More flexible and realistic in some scenarios.
- **Cons:** Computationally heavier and harder to interpret.

---

### 3. 🌳 **Hierarchical Clustering**

- **Definition:** Builds a **tree of clusters (dendrogram)** by either:

  - **Agglomerative approach** (bottom-up): Starts with individual points and merges them.
  - **Divisive approach** (top-down): Starts with all points in one cluster and splits them.

- **Example Algorithm:** Agglomerative Hierarchical Clustering
- **Use Case:** Genomics, document organization, phylogenetic trees.
- **Pros:** No need to pre-specify number of clusters.
- **Cons:** More computationally expensive for large data.

---

### 🧮 Summary Table

| Type         | Belonging | Example Algorithm | Best For                              |
| ------------ | --------- | ----------------- | ------------------------------------- |
| Exclusive    | One-only  | K-Means           | Clear separable groups                |
| Overlapping  | Multiple  | Fuzzy C-Means     | Groups with shared membership         |
| Hierarchical | Nested    | Agglomerative     | Data with inherent hierarchical order |

---

Here are **detailed and structured notes** on **Hierarchical Clustering**, a powerful unsupervised machine learning technique:

---

## 🌳 Hierarchical Clustering

---

### 📘 Definition:

**Hierarchical Clustering** is a clustering technique that builds a hierarchy of clusters either:

- **Bottom-Up (Agglomerative)** – each data point starts as its own cluster and they are **merged** step-by-step.
- **Top-Down (Divisive)** – all data starts in one cluster and is **split** recursively.

The output is a **dendrogram** – a tree-like diagram representing the nested grouping of patterns and the levels at which groupings change.

---

### 🌟 Features:

| Feature                       | Description                                                           |
| ----------------------------- | --------------------------------------------------------------------- |
| **Unsupervised**              | No need for labeled data                                              |
| **Dendrogram Output**         | Visualizes clusters at different levels of granularity                |
| **No preset `k` needed**      | Unlike K-Means, the number of clusters is **not required beforehand** |
| **Deterministic**             | Same output every time (no random initialization)                     |
| **Flexible Distance Metrics** | Works with Euclidean, Manhattan, Cosine, etc.                         |

---

### 🎯 Purpose:

- To **explore data structure** at multiple levels.
- To understand how data points **group together hierarchically**.
- Ideal for applications requiring **nested** cluster representation.

---

### ⚙️ Working

#### 🧱 1. **Agglomerative Clustering** (most commonly used)

**Steps:**

1. Start with each point as its **own cluster**.
2. Calculate **pairwise distances** between all clusters.
3. **Merge** the two closest clusters.
4. Update the distance matrix (based on linkage method).
5. Repeat steps 2–4 until **only one cluster** remains.
6. Cut the dendrogram at desired level to form clusters.

#### 🔩 2. **Divisive Clustering**

- Start with **one big cluster**.
- **Split** the cluster iteratively into smaller clusters.
- Computationally expensive → **rarely used**.

---

### 📏 Linkage Criteria (for merging clusters):

Used in Agglomerative Clustering to decide which clusters to merge:

| Linkage Type         | How Distance is Computed                                 |
| -------------------- | -------------------------------------------------------- |
| **Single Linkage**   | Minimum distance between points of two clusters          |
| **Complete Linkage** | Maximum distance between points of two clusters          |
| **Average Linkage**  | Average of all pairwise distances between cluster points |
| **Ward’s Method**    | Minimizes total within-cluster variance                  |

---

### 📉 Dendrogram:

- A **tree diagram** showing the sequence of merges/splits.
- The **height of the join** indicates the distance (dissimilarity).
- You can **"cut"** the dendrogram at any level to decide the number of clusters.

---

### 💡 Use Cases

| Domain               | Use Case Example                          |
| -------------------- | ----------------------------------------- |
| **Genomics**         | Gene expression pattern grouping          |
| **Text Mining**      | Document or topic clustering              |
| **E-commerce**       | Customer segmentation                     |
| **Social Science**   | Survey data analysis                      |
| **Image Processing** | Object grouping based on pixel similarity |

---

### 🧮 Algorithms

#### 1. **Agglomerative Hierarchical Clustering**

- Most widely used.
- Uses bottom-up strategy.
- Dendrogram is built progressively.
- Scikit-learn implementation: `sklearn.cluster.AgglomerativeClustering`

#### 2. **Divisive Hierarchical Clustering**

- Less common due to high computational cost.
- Starts from one cluster → recursively splits.

---

### ✅ Advantages

- No need to pre-specify the number of clusters.
- Good for **exploratory analysis**.
- Can capture complex cluster shapes.
- Dendrogram provides interpretability.

---

### ❌ Disadvantages

- **Scalability**: Slow for large datasets (time complexity \~ O(n³)).
- **Sensitive** to noise and outliers.
- **Non-reversible**: Once a merge or split is made, it cannot be undone.

---

Here’s a **complete, structured note** on **Association Rule Technique** used in unsupervised machine learning, particularly in **market basket analysis** and **recommendation systems**.

---

## 📊 Association Rule Technique

---

### 📘 Definition:

**Association Rule Mining** is a data mining technique used to discover **interesting relationships, patterns, or associations** among a set of items in transactional databases.

> **Example Rule**:
> `If a customer buys bread and butter, they are likely to buy milk.`
> (Bread & Butter → Milk)

---

### 🎯 Purpose:

- Discover **frequent itemsets** (items that appear together).
- Generate **rules** that highlight patterns in large datasets.
- Used for **product recommendation**, **cross-selling**, **customer profiling**, etc.

---

### 🌟 Features:

| Feature               | Description                                                             |
| --------------------- | ----------------------------------------------------------------------- |
| **Unsupervised**      | No need for labeled data                                                |
| **Interpretable**     | Rules are easy to understand                                            |
| **Pattern Discovery** | Finds relationships among features (not prediction-based)               |
| **Threshold-based**   | Depends on support, confidence, and lift values to define rule strength |

---

### ⚙️ Working:

#### Step-by-step process:

1. **Data Preparation**: Transactional data in the form:

   ```txt
   Transaction ID | Items Bought
   -------------- | ------------------------
   T1             | Milk, Bread, Butter
   T2             | Bread, Butter
   T3             | Milk, Bread
   ```

2. **Frequent Itemset Generation**:

   - Identify combinations of items that occur together **frequently** based on a threshold called **support**.

3. **Rule Generation**:

   - From frequent itemsets, generate rules like:

     ```
     {Bread, Butter} → {Milk}
     ```

4. **Evaluation** using:

   - **Support**
   - **Confidence**
   - **Lift**

---

### 📐 Metrics Used:

| Metric         | Formula                                    | Meaning                                                     |                                      |
| -------------- | ------------------------------------------ | ----------------------------------------------------------- | ------------------------------------ |
| **Support**    | `Support(A→B) = P(A ∪ B)`                  | Frequency of occurrence of both A and B                     |                                      |
| **Confidence** | \`Confidence(A→B) = P(B                    | A) = Support(A ∪ B) / Support(A)\`                          | Likelihood of B given A has occurred |
| **Lift**       | `Lift(A→B) = Confidence(A→B) / Support(B)` | Measures how much more likely B is given A than B by itself |                                      |

---

### 💡 Example: Recommender System

**Transactional Data**:

| Transaction | Items               |
| ----------- | ------------------- |
| T1          | Bread, Milk         |
| T2          | Bread, Butter       |
| T3          | Milk, Butter        |
| T4          | Bread, Butter, Milk |

**Frequent Itemset**: `{Bread, Milk}`

**Generated Rule**:
`Bread → Milk`

- Support = 2/4 = 0.5
- Confidence = 2/3 ≈ 0.67
- Lift = 0.67 / (3/4) = 0.89

---

### 🤖 Algorithms Used:

#### 1. **Apriori Algorithm**:

- **Approach**: Bottom-up – generates frequent itemsets first, then rules.
- **Key Step**: Uses **Apriori Property** – _All subsets of a frequent itemset must also be frequent_.
- **Prunes** infrequent itemsets early.

##### Pros:

- Simple and easy to implement.

##### Cons:

- Computationally expensive on large datasets (needs multiple scans).

#### 2. **ECLAT (Equivalence Class Transformation)**:

- Uses **vertical data format** (item → transaction ID).
- Faster than Apriori because it uses **intersection** rather than scanning.

#### 3. **FP-Growth (Frequent Pattern Growth)**:

- **Avoids candidate generation**.
- Builds a **compact tree (FP-tree)** of frequent patterns.
- Much more **efficient** and **scalable** than Apriori.

##### Pros:

- Better performance on large datasets.
- Less memory and time complexity.

---

### ✅ Advantages:

- Finds **non-obvious patterns** in data.
- Helps in **cross-selling** and **recommendation systems**.
- Applicable to a wide variety of industries (retail, healthcare, telecom).

---

### ❌ Disadvantages:

- Can produce **too many rules** (low-quality or redundant).
- **High time complexity** for large datasets.
- Doesn’t work well for **continuous variables** (requires binning).

---

### 🧠 Applications:

| Domain     | Example Use Case                                     |
| ---------- | ---------------------------------------------------- |
| Retail     | Market basket analysis                               |
| E-commerce | Product recommendations (Amazon, Flipkart)           |
| Banking    | Fraud detection through transaction pattern analysis |
| Healthcare | Finding co-occurrence of symptoms or diseases        |
| Telecom    | Customer behavior analysis                           |

---

Here are **detailed notes** on **Dimensionality Reduction Techniques** in machine learning, especially in the context of handling high-dimensional data (like in recommender systems, computer vision, genomics, etc.).

---

## 🧩 Dimensionality Reduction Technique

---

### 📘 Definition:

Dimensionality Reduction is the process of **reducing the number of input features or variables (dimensions)** in a dataset while **retaining as much information as possible**.

> In simple terms: it means **simplifying** the data without losing key patterns.

---

### 🎯 Purpose:

- To **eliminate redundancy** and **irrelevant features**.
- To reduce **storage**, **computation time**, and **overfitting**.
- To help **visualize** high-dimensional data (e.g., reducing 100D data to 2D).
- To improve **model performance** in high-dimensional space (curse of dimensionality).

---

### 🌟 Features:

| Feature                      | Description                                     |
| ---------------------------- | ----------------------------------------------- |
| **Data compression**         | Reduces memory and computation                  |
| **Preserves essential info** | Keeps variance and structure of the data        |
| **Noise reduction**          | Removes irrelevant or low-importance features   |
| **Improves generalization**  | Prevents overfitting in high-dimensional models |
| **Helps visualization**      | Reduces data to 2D/3D for human interpretation  |

---

### ⚙️ Working:

Dimensionality reduction works by:

1. **Identifying redundant/correlated features**.
2. **Transforming** the data into a new feature space (projection).
3. Keeping only the **top components** or **selected features**.

There are two main approaches:

- **Feature Selection**: Keep the most important features.
- **Feature Extraction**: Create new features by combining existing ones (e.g., PCA).

---

### 📌 Example: Recommender Systems

- In movie recommendation:

  - User-movie rating matrix can be **very sparse** (many zeros).
  - Using dimensionality reduction like **Matrix Factorization (SVD)**, you can:

    - Represent users and items in a **latent space**.
    - Predict missing ratings based on patterns in reduced dimensions.

---

### 🔢 Algorithms Used and Their Details:

---

### 1. **Principal Component Analysis (PCA)**

- **Type**: Feature Extraction (Linear)

- **Goal**: Find the **principal components** (directions of maximum variance).

- **Working**:

  1. Standardize the data.
  2. Compute covariance matrix.
  3. Compute eigenvectors/eigenvalues.
  4. Select top `k` components.
  5. Project data onto new axes.

- **Use Case**: Image compression, gene expression data, preprocessing for ML.

- **Pros**:

  - Captures max variance.
  - Simple and fast.

- **Cons**:

  - Linear only.
  - Components may not be interpretable.

---

### 2. **Linear Discriminant Analysis (LDA)**

- **Type**: Supervised Dimensionality Reduction

- **Goal**: Maximize class separability.

- **Works** by maximizing **between-class variance** and minimizing **within-class variance**.

- **Use Case**: Face recognition, classification problems with labeled data.

- **Pros**: Class-aware projection.

- **Cons**: Works only for labeled data.

---

### 3. **t-SNE (t-Distributed Stochastic Neighbor Embedding)**

- **Type**: Non-linear

- **Goal**: Preserves **local relationships** in lower dimension.

- **Used For**: Visualizing high-dimensional data in 2D/3D.

- **Pros**: Excellent for clustering visualization.

- **Cons**: Computationally heavy; not good for large datasets.

---

### 4. **UMAP (Uniform Manifold Approximation and Projection)**

- **Type**: Non-linear

- **Faster** and more **scalable** than t-SNE.

- Preserves both **global and local structure** of the data.

- **Use Case**: NLP embeddings, genomics, recommender systems.

---

### 5. **Autoencoders (Neural Network-based)**

- **Type**: Non-linear, deep learning

- **Architecture**:

  - Input → Encoder → Bottleneck → Decoder → Output

- The **bottleneck layer** is the reduced dimension representation.

- **Use Case**: Recommender systems, anomaly detection, image compression.

- **Pros**: Handles non-linearity and complex patterns.

- **Cons**: Requires large data and training.

---

### 6. **Singular Value Decomposition (SVD)**

- **Used in**: Recommender systems, matrix completion.
- Decomposes matrix `A` into `U * Σ * Vᵀ`.
- Retains top-k singular values to reduce dimensions.

---

### ✅ Advantages:

- Improves **model accuracy** by removing noise.
- Helps tackle **curse of dimensionality**.
- Reduces **training time and storage**.
- Enables **visualization** and **interpretability**.

---

### ❌ Disadvantages:

- Risk of **information loss**.
- Reduced interpretability (esp. in PCA, t-SNE).
- Not suitable for **streaming data** without modification.

---

### 📊 Summary Table:

| Algorithm   | Type       | Supervised | Handles Non-Linearity | Use Cases                              |
| ----------- | ---------- | ---------- | --------------------- | -------------------------------------- |
| PCA         | Linear     | ❌         | ❌                    | General preprocessing                  |
| LDA         | Linear     | ✅         | ❌                    | Classification, face recognition       |
| t-SNE       | Non-linear | ❌         | ✅                    | Clustering, data visualization         |
| UMAP        | Non-linear | ❌         | ✅                    | NLP, recommender systems               |
| Autoencoder | Non-linear | ❌         | ✅                    | Recommender systems, anomaly detection |
| SVD         | Linear     | ❌         | ❌                    | Collaborative filtering                |

---

Here are detailed notes on **K-Means Clustering**, covering all requested subtopics with concepts, mathematics, methodology, and key terminologies:

---

## 🔶 K-Means Clustering

---

### 📘 Definition:

**K-Means Clustering** is an **unsupervised learning algorithm** used to **partition a dataset into K distinct, non-overlapping clusters**. It tries to group similar data points together while minimizing the intra-cluster variance.

> It is a **centroid-based** clustering algorithm that groups data into **K clusters**, where each cluster is represented by its **centroid**.

---

### 🎯 Objective:

The **objective** of K-Means is to:

- **Minimize the sum of squared distances** (inertia) between data points and their respective **cluster centroids**.

Mathematically:

$$
\text{Objective Function (WCSS)} = \sum_{i=1}^{k} \sum_{x \in C_i} \|x - \mu_i\|^2
$$

Where:

- $k$: number of clusters
- $C_i$: data points in cluster $i$
- $\mu_i$: centroid of cluster $i$

---

### 🌟 Features:

| Feature            | Description                                   |
| ------------------ | --------------------------------------------- |
| **Unsupervised**   | No labeled output required                    |
| **Centroid-based** | Each cluster has a center (mean of points)    |
| **Iterative**      | Converges after multiple iterations           |
| **Partitioning**   | Divides data into non-overlapping clusters    |
| **Distance-based** | Relies on Euclidean or other distance metrics |

---

### 🧩 Components:

1. **Data Points**: Input features to be clustered.
2. **Centroids**: Centers of clusters.
3. **K**: Number of clusters (user-defined).
4. **Distance Metric**: Most commonly Euclidean distance.
5. **Clusters**: Final groups after convergence.

---

### ❓ How to Choose the Value of K

Choosing the correct **K** is crucial. Common methods:

#### 🔸 1. WCSS (Within-Cluster Sum of Squares)

- Total intra-cluster variance.
- Lower WCSS implies tighter clusters.

$$
WCSS = \sum_{i=1}^{k} \sum_{x \in C_i} \|x - \mu_i\|^2
$$

As $K$ increases, WCSS decreases but may lead to **overfitting**.

---

#### 🔸 2. Elbow Method

- Plot $K$ vs. WCSS.
- Look for a point (the “elbow”) where the decrease in WCSS becomes marginal.

> This elbow point gives the **optimal number of clusters**.

---

### ⚠️ What Happens If We Choose Random K Value

If K is randomly chosen:

- Might lead to **suboptimal clustering**.
- May **split meaningful clusters** or **merge distinct ones**.
- Final result may vary due to poor initialization.

---

#### 🔸 Random Initialization Trap:

- Different runs can yield different results.
- Poor initialization of centroids can trap the algorithm in **local minima**.

**Solution**: Use **K-Means++ Initialization** to choose better initial centroids.

---

### 🧮 Mathematics:

Let:

- $X = \{x_1, x_2, ..., x_n\}$ be the set of data points.
- $C_1, C_2, ..., C_k$ be the clusters.
- $\mu_i$ be the centroid of cluster $C_i$.

The algorithm tries to:

$$
\min \sum_{i=1}^{k} \sum_{x_j \in C_i} \|x_j - \mu_i\|^2
$$

Where:

- Distance is usually **Euclidean**:

$$
\|x - \mu\|^2 = \sum_{d=1}^{n} (x_d - \mu_d)^2
$$

---

### 🧭 Working and Steps (Methodology):

#### Step 1: Initialize K centroids randomly.

#### Step 2: Assign each data point to the nearest centroid (cluster assignment).

#### Step 3: Compute new centroids as the **mean** of the points in each cluster.

#### Step 4: Repeat steps 2 and 3 until:

- **No change in assignments** OR
- **Centroids converge**

---

### ✅ Advantages:

| Advantage                             | Description                           |
| ------------------------------------- | ------------------------------------- |
| Simple and easy to implement          | Intuitive and fast algorithm          |
| Fast convergence                      | Efficient on large datasets           |
| Works well with **globular clusters** | Assumes spherical (circular) clusters |
| Scalable                              | Suitable for high dimensional data    |

---

### ❌ Disadvantages:

| Disadvantage                        | Description                             |
| ----------------------------------- | --------------------------------------- |
| Must specify K manually             | Needs human intuition or elbow/WCSS     |
| Sensitive to initialization         | May get stuck in local optima           |
| Poor for non-spherical clusters     | Doesn’t handle non-globular shapes well |
| Affected by outliers and noise      | Can shift centroids drastically         |
| Not deterministic without K-Means++ | Different results on different runs     |

---

### 📌 Summary Table:

| Aspect          | K-Means Clustering                     |
| --------------- | -------------------------------------- |
| Type            | Unsupervised                           |
| Distance Metric | Usually Euclidean                      |
| Output          | K clusters with centroids              |
| Init Strategy   | Random (or K-Means++)                  |
| Best for        | Large datasets with spherical clusters |
| Main Limitation | Sensitive to outliers and bad K value  |

---

Here are the detailed and well-structured notes on the **DBSCAN Algorithm (Density-Based Spatial Clustering of Applications with Noise)**, covering every requested aspect:

---

## 🔶 DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

---

### 📘 Definition:

**DBSCAN** is an **unsupervised, density-based clustering algorithm** that forms clusters based on the **density of data points in a region**.

> Unlike K-Means, DBSCAN **does not require the number of clusters (K) to be specified in advance**, and it can **detect noise/outliers**.

---

### 🎯 Objective:

- To identify clusters of **arbitrary shapes** based on **regions of high density**, separated by regions of low density.
- Classify points as **Core**, **Border**, or **Noise** depending on their neighborhood density.

---

### 🌟 Features:

| Feature                  | Description                                               |
| ------------------------ | --------------------------------------------------------- |
| **No need to specify K** | Automatically determines the number of clusters           |
| **Density-based**        | Forms clusters from dense regions in data                 |
| **Handles noise**        | Can identify outliers and noisy data                      |
| **Cluster shape**        | Capable of detecting clusters of **arbitrary shapes**     |
| **Works well**           | With datasets containing noise or unevenly sized clusters |

---

### 🧩 Components and Their Function:

1. **Epsilon (ε)**:

   - Radius to search neighborhood.
   - Determines the neighborhood area of a point.

2. **MinPts**:

   - Minimum number of points (including the point itself) required to form a **dense region**.
   - Typical value: ≥ dimensionality of dataset + 1.

3. **Core Point**:

   - A point with **≥ MinPts** in its ε-neighborhood.

4. **Border Point**:

   - Has < MinPts in ε-neighborhood but **is within ε** of a **core point**.

5. **Noise (Outlier)**:

   - Not a core or border point; **isolated**.

---

### ❓ How to Choose Parameters in DBSCAN

- **Epsilon (ε)**:

  - Use **k-distance plot** (plot distance to k-th nearest neighbor and find "elbow" point).
  - Select ε where the curve shows a sharp bend.

- **MinPts**:

  - Common heuristic:

    $$
    \text{MinPts} \geq D + 1
    $$

    Where D is the number of dimensions in the dataset.

---

### 🧮 Mathematics (Distance Metric)

- DBSCAN uses distance to compute density.
- **Euclidean Distance** is most commonly used:

$$
d(p, q) = \sqrt{\sum_{i=1}^n (p_i - q_i)^2}
$$

For each point $p$:

- Count how many points fall within ε radius.
- If count ≥ MinPts ⇒ mark as core.

---

### 🧭 Working and Steps (Methodology):

#### Step 1: For each point P in the dataset

- Find all points within radius ε (ε-neighborhood).
- If size ≥ MinPts ⇒ mark P as **core**.

#### Step 2: For each **core point**:

- Create a new cluster.
- Add all points in its ε-neighborhood.
- Recursively add reachable **core and border points**.

#### Step 3: Repeat for unvisited points.

#### Step 4:

- Points that don’t meet core/border criteria ⇒ **noise**.

---

### ✅ Advantages:

| Advantage                             | Description                                    |
| ------------------------------------- | ---------------------------------------------- |
| No need to specify number of clusters | Unlike K-Means                                 |
| Can find arbitrarily shaped clusters  | Suitable for real-world spatial data           |
| Detects noise/outliers                | Classifies sparse regions as noise             |
| Effective in real-life applications   | Works well with geo-data, spatial points, etc. |

---

### ❌ Disadvantages:

| Disadvantage                   | Description                                           |
| ------------------------------ | ----------------------------------------------------- |
| Parameter sensitivity          | ε and MinPts need tuning                              |
| Poor for high-dimensional data | Distance metrics become less meaningful               |
| Struggles with varying density | Cannot cluster data with large differences in density |
| Memory-intensive               | ε-neighborhood search can be costly                   |

---

### 📌 Summary Table:

| Aspect            | DBSCAN                                   |
| ----------------- | ---------------------------------------- |
| Type              | Density-based clustering                 |
| Input Parameters  | ε (Epsilon), MinPts                      |
| Output            | Clusters, Noise points                   |
| Cluster Shape     | Arbitrary                                |
| Handles Outliers? | Yes                                      |
| Best For          | Spatial data, noisy datasets             |
| Limitations       | High-dimensional data, varying densities |

---

Sure! Here is a **detailed note** on **Agglomerative Clustering** covering all the points you asked for:

---

# Agglomerative Clustering

## Definition

Agglomerative Clustering is a **hierarchical clustering technique** that builds clusters **bottom-up** by progressively merging the closest pairs of clusters until all data points belong to a single cluster or a stopping criterion is met.

---

## Objective

To create a **hierarchical structure (dendrogram)** that shows how data points or clusters are merged step-by-step based on their similarity or distance.

---

## Bottom-Up Approach

- Starts with **each data point as its own cluster** (singleton clusters).
- Iteratively **merges the closest clusters**.
- Continues until:

  - A single cluster contains all points, or
  - A desired number of clusters is reached.

---

## Linkage Criteria

Linkage criteria define **how the distance between two clusters is computed**. Different linkage methods affect the shape and size of clusters.

Common linkage methods:

| Linkage Method       | Description                                                       |
| -------------------- | ----------------------------------------------------------------- |
| **Single Linkage**   | Distance between the **closest points** of two clusters           |
| **Complete Linkage** | Distance between the **farthest points** of two clusters          |
| **Average Linkage**  | Average distance between **all pairs of points** between clusters |
| **Ward’s Linkage**   | Minimizes total **within-cluster variance** after merging         |

---

## Steps and Methodology

1. **Initialize**: Assign each data point to its own cluster.
2. **Compute distances** between every pair of clusters using chosen linkage method.
3. **Merge the two closest clusters** based on linkage distance.
4. **Update the distance matrix** with new cluster distances.
5. Repeat steps 2–4 until:

   - All points belong to one cluster, or
   - The number of clusters equals a predefined number.

---

## How to measure closest cluster?

### Mathematics and Working of Distance Calculations:

Assume two clusters $C_i$ and $C_j$.

- **Single Linkage Distance** $d(C_i, C_j) = \min_{x \in C_i, y \in C_j} d(x,y)$
  (Minimum distance between any point in $C_i$ and any point in $C_j$).

- **Complete Linkage Distance** $d(C_i, C_j) = \max_{x \in C_i, y \in C_j} d(x,y)$
  (Maximum distance between any point in $C_i$ and any point in $C_j$).

- **Average Linkage Distance** $d(C_i, C_j) = \frac{1}{|C_i| \times |C_j|} \sum_{x \in C_i} \sum_{y \in C_j} d(x,y)$
  (Average of all pairwise distances between points in clusters).

- **Ward’s Method**
  Measures the increase in total within-cluster variance after merging clusters. The clusters merged minimize this increase.

---

## Complete Detailed Example

Consider 5 points: $A, B, C, D, E$ with coordinates:

| Point | Coordinates |
| ----- | ----------- |
| A     | (1, 2)      |
| B     | (2, 2)      |
| C     | (5, 6)      |
| D     | (8, 8)      |
| E     | (7, 7)      |

### Step 1: Start with individual clusters

Clusters: {A}, {B}, {C}, {D}, {E}

### Step 2: Calculate pairwise distances (Euclidean distance)

| Pairs | Distance                          |
| ----- | --------------------------------- |
| A-B   | $\sqrt{(2-1)^2 + (2-2)^2} = 1$    |
| A-C   | $\sqrt{(5-1)^2 + (6-2)^2} = 5.66$ |
| A-D   | $\sqrt{(8-1)^2 + (8-2)^2} = 9.22$ |
| A-E   | $\sqrt{(7-1)^2 + (7-2)^2} = 7.81$ |
| B-C   | $\sqrt{(5-2)^2 + (6-2)^2} = 5$    |
| B-D   | $\sqrt{(8-2)^2 + (8-2)^2} = 8.49$ |
| B-E   | $\sqrt{(7-2)^2 + (7-2)^2} = 7.07$ |
| C-D   | $\sqrt{(8-5)^2 + (8-6)^2} = 3.61$ |
| C-E   | $\sqrt{(7-5)^2 + (7-6)^2} = 2.23$ |
| D-E   | $\sqrt{(7-8)^2 + (7-8)^2} = 1.41$ |

### Step 3: Merge closest clusters

- Closest are A and B (distance = 1) → Merge → New cluster: {A,B}

### Step 4: Update distances with linkage method (say, single linkage)

Distances between {A,B} and others: minimum distance to points in cluster.

- {A,B}-C = min(distance A-C, B-C) = min(5.66, 5) = 5
- {A,B}-D = min(9.22, 8.49) = 8.49
- {A,B}-E = min(7.81, 7.07) = 7.07

### Step 5: Next closest clusters: D and E (1.41) → Merge → {D,E}

### Step 6: Update distances:

- {A,B}-{C} = 5

- {A,B}-{D,E} = min(8.49, 7.07, 3.61, 1.41) → Actually min distance between any member in {A,B} and {D,E}:

  - Distances:

    - A-D = 9.22
    - A-E = 7.81
    - B-D = 8.49
    - B-E = 7.07
      Minimum = 7.07

- {C}-{D,E} = min(C-D=3.61, C-E=2.23) = 2.23

### Step 7: Merge closest clusters: {C} and {D,E} (2.23) → New cluster {C,D,E}

### Step 8: Update distances:

- {A,B}-{C,D,E} = min({A-B}-C, {A-B}-D, {A-B}-E)
  \= min(5, 8.49, 7.07) = 5

### Step 9: Merge {A,B} and {C,D,E} at distance 5 → Single cluster with all points.

---

## Advantages

- No need to pre-specify number of clusters (can cut dendrogram at desired level).
- Produces a **dendrogram** for visual interpretation.
- Can capture **complex cluster shapes**.
- Flexible with different distance and linkage measures.

## Disadvantages

- **Computationally expensive** for large datasets (O(n³) naive).
- Sensitive to noise and outliers.
- No undoing of merges (early wrong merges affect results).
- Choice of linkage and distance metric affects results heavily.

---

Here's a detailed note on **Dendrogram** as requested:

---

# Dendrogram

## Definition

A **dendrogram** is a **tree-like diagram** that illustrates the arrangement of clusters produced by hierarchical clustering algorithms (like Agglomerative or Divisive Clustering). It visually represents the order and distances at which clusters are merged or split.

---

## Working

- Each **leaf node** at the bottom represents an individual data point or object.
- The branches represent **clusters formed at various levels** of similarity or distance.
- The **height of the branches** (vertical axis) shows the **distance or dissimilarity** between merged clusters.
- Starting from the leaves (individual points), clusters merge step-by-step until all points join into one cluster at the top.
- The dendrogram helps to **visualize the hierarchical relationships** and **how close or far apart** clusters are from each other.

---

## Optimal Number of Clusters Using Dendrogram

- To choose the optimal number of clusters:

  1. Look at the **vertical axis (distance scale)**.
  2. Find the **largest vertical gap (largest jump or longest vertical line)** between successive merges — this indicates a significant separation between clusters.
  3. Draw a **horizontal cut (threshold line)** through this gap.
  4. The number of vertical lines **intersected by the cut** equals the optimal number of clusters.

- Intuition:
  The big gap represents merging of very dissimilar clusters, so cutting just before this merge gives meaningful and distinct clusters.

---

## Example

Suppose the dendrogram has large jumps at heights 4 and 10:

- Cutting at height 4 might give 3 clusters,
- Cutting at height 10 might give 1 cluster (all data combined).
  If the jump from 4 to 10 is largest, cutting at height 4 is optimal, resulting in 3 clusters.

---

Here are **detailed notes** on three key **clustering evaluation metrics**: **Silhouette Score**, **Davies-Bouldin Index (DBI)**, and **Calinski-Harabasz Index (CHI)**.

---

# 🔍 Evaluation Metrics in Clustering

---

## 1. **Silhouette Score**

### ✅ Definition:

The **Silhouette Score** measures how similar a point is to its own cluster (cohesion) compared to other clusters (separation).

### 📐 Formula:

For a single point $i$:

$$
s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}
$$

Where:

- $a(i)$ = average intra-cluster distance (mean distance to all other points in the same cluster)
- $b(i)$ = lowest average inter-cluster distance (mean distance to all points in the nearest cluster)

### 📊 Interpretation:

- **+1**: Point is well-matched to its cluster and far from other clusters
- **0**: Point is on the decision boundary between two clusters
- **–1**: Point is closer to another cluster than to its own

> **Range**: \[-1, 1] (Higher is better)

### ✔️ Advantages:

- Gives insight into **cohesion vs. separation**
- Works for any clustering method
- Can be visualized with silhouette plots

### ❌ Disadvantages:

- Computationally expensive (requires distance calculations for all points)
- May not work well for clusters with non-convex shapes

---

## 2. **Davies-Bouldin Index (DBI)**

### ✅ Definition:

The **DB Index** evaluates the average "similarity" between each cluster and its most similar one. Lower values indicate better clustering.

### 📐 Formula:

$$
\text{DBI} = \frac{1}{k} \sum_{i=1}^{k} \max_{j \ne i} \left( \frac{\sigma_i + \sigma_j}{d(c_i, c_j)} \right)
$$

Where:

- $\sigma_i$ = average distance of points in cluster $i$ to centroid $c_i$
- $d(c_i, c_j)$ = distance between cluster centroids $i$ and $j$
- $k$ = number of clusters

### 📊 Interpretation:

- Lower DBI = better clustering
- A **score of 0** is ideal (clusters are tight and well-separated)

### ✔️ Advantages:

- Simple to compute
- Works for clusters of different sizes and densities

### ❌ Disadvantages:

- Sensitive to noise
- Assumes spherical clusters

---

## 3. **Calinski-Harabasz Index (CHI)**

### ✅ Definition:

Also known as the **Variance Ratio Criterion**, it measures how well clusters are separated while being compact.

### 📐 Formula:

$$
\text{CHI} = \frac{\text{Tr}(B_k)}{\text{Tr}(W_k)} \times \frac{n - k}{k - 1}
$$

Where:

- $\text{Tr}(B_k)$ = trace of the between-cluster dispersion matrix
- $\text{Tr}(W_k)$ = trace of the within-cluster dispersion matrix
- $n$ = total number of data points
- $k$ = number of clusters

### 📊 Interpretation:

- **Higher values** indicate better-defined clusters
- Measures **inter-cluster separation** vs **intra-cluster compactness**

### ✔️ Advantages:

- Fast and efficient
- Objective evaluation metric (no labels needed)

### ❌ Disadvantages:

- Works best with spherical clusters
- May be biased for datasets with many clusters

---

## Summary Comparison Table:

| Metric           | Best Value | Focus                 | Good For           | Sensitive To         |
| ---------------- | ---------- | --------------------- | ------------------ | -------------------- |
| Silhouette Score | Close to 1 | Cohesion & separation | Any shape clusters | Distance computation |
| DBI              | Close to 0 | Cluster similarity    | Compact clusters   | Noise                |
| CHI              | High       | Variance ratio        | Spherical clusters | Cluster count        |

---
