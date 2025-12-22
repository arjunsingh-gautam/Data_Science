# <span style="color:#a4ac86">**Lesson-3 Vector Addition**</span>

## <span style="color:#a7c957">Table of Contents</span>

- [Vector Addition & Properties](#t1)
- [Application of Vector Addition in ML](#t2)
- [Numerical](#t3)

## <span style="color:#ff0054" id="t1">**Vector Additon & Properties**</span>

### ✅ **Definition:**

If you have two vectors of the same dimension:

$$
\vec{u} = \begin{bmatrix} u_1 \\ u_2 \\ \cdots \\ u_n \end{bmatrix}, \quad
\vec{v} = \begin{bmatrix} v_1 \\ v_2 \\ \cdots \\ v_n \end{bmatrix}
$$

Then their **sum** $\vec{u} + \vec{v}$ is defined as:

$$
\vec{u} + \vec{v} = \begin{bmatrix} u_1 + v_1 \\ u_2 + v_2 \\ \cdots \\ u_n + v_n \end{bmatrix}
$$

---

### 📐 2. Geometric Interpretation

- **Graphically**, vector addition is like placing the **tail of $\vec{v}$** at the **head of $\vec{u}$**.
- The resulting vector $\vec{u} + \vec{v}$ goes from the **tail of $\vec{u}$** to the **head of $\vec{v}$**.
- This is called the **"tip-to-tail"** or **triangle rule**.

---

### 🧮 3. Numerical Example

Let:

$$
\vec{u} = \begin{bmatrix} 2 \\ 5 \end{bmatrix}, \quad
\vec{v} = \begin{bmatrix} 3 \\ -1 \end{bmatrix}
$$

### ▶️ Add them:

$$
\vec{u} + \vec{v} = \begin{bmatrix} 2 + 3 \\ 5 + (-1) \end{bmatrix}
= \begin{bmatrix} 5 \\ 4 \end{bmatrix}
$$

This new vector points to a new location after "walking" along $\vec{u}$, then $\vec{v}$.

---

### 📘 4. Properties of Vector Addition

Let $\vec{u}, \vec{v}, \vec{w} \in \mathbb{R}^n$

---

### 🔹 1. **Commutativity**

$$
\vec{u} + \vec{v} = \vec{v} + \vec{u}
$$

✅ Order doesn’t matter — you end at the same place.

Example:

$$
\begin{bmatrix} 2 \\ 5 \end{bmatrix} + \begin{bmatrix} 3 \\ -1 \end{bmatrix}
= \begin{bmatrix} 5 \\ 4 \end{bmatrix}
= \begin{bmatrix} 3 \\ -1 \end{bmatrix} + \begin{bmatrix} 2 \\ 5 \end{bmatrix}
$$

---

### 🔹 2. **Associativity**

$$
(\vec{u} + \vec{v}) + \vec{w} = \vec{u} + (\vec{v} + \vec{w})
$$

✅ Grouping doesn’t affect the sum.

Let:

$$
\vec{w} = \begin{bmatrix} 1 \\ 2 \end{bmatrix}
$$

Then:

$$
(\vec{u} + \vec{v}) + \vec{w} = \begin{bmatrix} 5 \\ 4 \end{bmatrix} + \begin{bmatrix} 1 \\ 2 \end{bmatrix}
= \begin{bmatrix} 6 \\ 6 \end{bmatrix}
$$

$$
\vec{u} + (\vec{v} + \vec{w}) = \begin{bmatrix} 2 \\ 5 \end{bmatrix} + \begin{bmatrix} 4 \\ 1 \end{bmatrix}
= \begin{bmatrix} 6 \\ 6 \end{bmatrix}
$$

---

### 🔹 3. **Additive Identity**

There exists a **zero vector** $\vec{0} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$, such that:

$$
\vec{v} + \vec{0} = \vec{v}
$$

✅ Zero vector does not change anything.

---

### 🔹 4. **Additive Inverse**

Every vector $\vec{v}$ has an **opposite vector** $-\vec{v}$ such that:

$$
\vec{v} + (-\vec{v}) = \vec{0}
$$

Example:

$$
\vec{v} = \begin{bmatrix} 3 \\ -1 \end{bmatrix}, \quad -\vec{v} = \begin{bmatrix} -3 \\ 1 \end{bmatrix}
\Rightarrow \vec{v} + (-\vec{v}) = \begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

---

### 🔚 Summary Table

| Property          | Equation                                                        | Meaning                          |
| ----------------- | --------------------------------------------------------------- | -------------------------------- |
| **Commutativity** | $\vec{u} + \vec{v} = \vec{v} + \vec{u}$                         | Order doesn’t matter             |
| **Associativity** | $(\vec{u} + \vec{v}) + \vec{w} = \vec{u} + (\vec{v} + \vec{w})$ | Grouping doesn’t matter          |
| **Identity**      | $\vec{v} + \vec{0} = \vec{v}$                                   | Zero vector doesn’t change value |
| **Inverse**       | $\vec{v} + (-\vec{v}) = \vec{0}$                                | Opposite vector cancels it out   |

---

## <span style="color:#ff0054"  id="t2">**Application of Vector Addition in ML**</span>

### 🔷 1. 📊 Use of Vector Addition in **EDA (Exploratory Data Analysis)**

### ✅ What Happens in EDA?

During EDA, we often:

- Combine features
- Compute averages
- Add vectors to center or scale data
- Apply transformations for PCA, clustering, etc.

### 🔹 Use of Vector Addition:

To compute **mean vectors**, **sum of data points**, or **centroids**.

### 🧮 Numerical Example:

Suppose we have 3 student data points (each a vector of 2 features: hours studied & test score):

$$
\vec{x}^{(1)} = \begin{bmatrix} 2 \\ 60 \end{bmatrix}, \quad
\vec{x}^{(2)} = \begin{bmatrix} 4 \\ 70 \end{bmatrix}, \quad
\vec{x}^{(3)} = \begin{bmatrix} 6 \\ 80 \end{bmatrix}
$$

To compute the **mean vector** (centroid):

$$
\vec{\mu} = \frac{1}{3} (\vec{x}^{(1)} + \vec{x}^{(2)} + \vec{x}^{(3)})
= \frac{1}{3} \left( \begin{bmatrix} 2 \\ 60 \end{bmatrix} + \begin{bmatrix} 4 \\ 70 \end{bmatrix} + \begin{bmatrix} 6 \\ 80 \end{bmatrix} \right)
= \frac{1}{3} \begin{bmatrix} 12 \\ 210 \end{bmatrix}
= \begin{bmatrix} 4 \\ 70 \end{bmatrix}
$$

✅ Vector addition helped combine samples → find the center → used for clustering, PCA, anomaly detection.

---

### 🔷 2. 💬 Use of Vector Addition in **NLP (Word Embeddings)**

### ✅ Word Embeddings (like Word2Vec, GloVe):

Each word is mapped to a **vector** in a high-dimensional space (e.g., 300-D). These vectors **capture semantic meaning**.

### 🔹 Use of Vector Addition:

- Combine words to represent phrases/sentences
- Analogies: king - man + woman ≈ queen
- Average embeddings to represent documents

### 🧮 Numerical Example (Simplified 3D):

Let:

- $\text{king} = \begin{bmatrix} 0.7 \\ 0.5 \\ 0.1 \end{bmatrix}$
- $\text{man} = \begin{bmatrix} 0.6 \\ 0.4 \\ 0.1 \end{bmatrix}$
- $\text{woman} = \begin{bmatrix} 0.6 \\ 0.5 \\ 0.2 \end{bmatrix}$

Then:

$$
\text{king} - \text{man} + \text{woman}
= \begin{bmatrix} 0.7 - 0.6 + 0.6 \\ 0.5 - 0.4 + 0.5 \\ 0.1 - 0.1 + 0.2 \end{bmatrix}
= \begin{bmatrix} 0.7 \\ 0.6 \\ 0.2 \end{bmatrix} \approx \text{queen}
$$

✅ Vector addition lets us capture **semantic relationships** and **composite meaning** in language.

---

### 🔷 3. 🖼️ Use of Vector Addition in **Image Processing**

### ✅ Images as Vectors

Each image is a **matrix of pixels**, but in ML, we often **flatten** it into a **vector**.

### 🔹 Use of Vector Addition:

- Combine image vectors (e.g., averaging images)
- Add noise, filters, or masks
- In autoencoders: reconstruct images using vector addition
- In GANs: interpolate between faces, styles using vector addition

---

### 🧮 Numerical Example:

Let’s say we have 2 grayscale images (flattened to 4 pixels each):

$$
\text{Image A} = \vec{a} = \begin{bmatrix} 100 \\ 150 \\ 200 \\ 250 \end{bmatrix}, \quad
\text{Image B} = \vec{b} = \begin{bmatrix} 50 \\ 100 \\ 150 \\ 200 \end{bmatrix}
$$

### Average image (blending):

$$
\text{Average} = \frac{1}{2} (\vec{a} + \vec{b}) = \frac{1}{2} \begin{bmatrix} 150 \\ 250 \\ 350 \\ 450 \end{bmatrix}
= \begin{bmatrix} 75 \\ 125 \\ 175 \\ 225 \end{bmatrix}
$$

✅ Vector addition allows image blending, noise injection, and style mixing in vision tasks.

---

### ✅ Summary Table

| Area            | Use of Vector Addition                             | Example                              |
| --------------- | -------------------------------------------------- | ------------------------------------ |
| **EDA**         | Combine data points, compute mean, centroids       | Mean of multiple student records     |
| **NLP**         | Combine word meanings, analogies, sentence vectors | king - man + woman = queen           |
| **Image Proc.** | Add images, filters, blend noise, interpolate      | Blending face images or adding noise |

---

### 🔷 1. 🧠 **Data Representation & Preprocessing**

| Use Case                           | Description                                                           |
| ---------------------------------- | --------------------------------------------------------------------- |
| **Feature engineering**            | Combine features: e.g., `Total_Score = Exam_Score + Assignment_Score` |
| **Mean/centroid calculation**      | Used in clustering (e.g., K-means), PCA                               |
| **Standardization (Z-score)**      | Subtract mean vector, add scaling                                     |
| **Dimensionality reduction (PCA)** | Compute mean, center data using vector addition                       |
| **Data augmentation**              | Add noise or shift vectors for new samples                            |
| **Combining modalities**           | Add audio + video + text vectors in multi-modal AI                    |

---

### 🔷 2. 💬 **NLP (Natural Language Processing)**

| Use Case                               | Description                                      |
| -------------------------------------- | ------------------------------------------------ |
| **Word vector arithmetic**             | `king - man + woman ≈ queen`                     |
| **Sentence embedding**                 | Average of word vectors via addition             |
| **Context vectors in attention**       | Attention weights sum vectorized context         |
| **Positional encoding** (Transformers) | Add position vectors to word embeddings          |
| **Token-level representation fusion**  | Add or concatenate different levels of embedding |

---

### 🔷 3. 🖼️ **Computer Vision & Image Processing**

| Use Case                       | Description                                         |
| ------------------------------ | --------------------------------------------------- |
| **Blending images**            | Vector average of pixel values (e.g., style mixing) |
| **Autoencoder reconstruction** | Output = sum of learned vector components           |
| **Noise injection**            | Add random noise vector to input image              |
| **Data augmentation**          | Add small translations, brightness variations       |
| **Skip connections (ResNet)**  | Add input vector to output of convolutional layers  |

---

### 🔷 4. 🔁 **Model Architecture and Learning**

| Use Case                             | Description                                                              |
| ------------------------------------ | ------------------------------------------------------------------------ |
| **Linear models**                    | $\hat{y} = \vec{w}^\top \vec{x} + b$ uses addition of dot product + bias |
| **Neural network layers**            | $z = W \cdot \vec{x} + \vec{b}$ — bias addition                          |
| **Residual learning (ResNet, LSTM)** | Add outputs of earlier and later layers                                  |
| **Transformer layers**               | Combine query, key, value vectors with weights                           |
| **Batch normalization**              | Add mean/variance-adjusted vectors                                       |
| **Dropout layers**                   | Add masks or scale vectors in training                                   |

---

### 🔷 5. 📉 **Optimization & Training**

| Use Case                             | Description                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------------ |
| **Gradient descent**                 | $\theta = \theta - \alpha \nabla J(\theta)$ — vector subtraction (still addition under the hood) |
| **Momentum optimization**            | $v = \beta v + (1 - \beta) \nabla J(\theta)$ — vector additions to smooth learning               |
| **Adam optimizer**                   | Uses moving averages of gradients and squared gradients (vector addition involved)               |
| **Weight updates in batch training** | Add gradient vectors over mini-batches                                                           |

---

### 🔷 6. 🧠 **Deep Generative Models (GANs, VAEs)**

| Use Case                       | Description                                                    |
| ------------------------------ | -------------------------------------------------------------- |
| **Latent space interpolation** | Add latent vectors to morph between outputs                    |
| **Style mixing**               | Add different latent styles in GANs                            |
| **VAE reconstruction**         | Reconstruct input via sum of decoder outputs                   |
| **Conditioning**               | Add condition vector (like class label) to input latent vector |

---

### 🔷 7. 🎛️ **Control, Robotics, and Reinforcement Learning**

| Use Case              | Description                                                    |
| --------------------- | -------------------------------------------------------------- |
| **State updates**     | Add current state + action effect vector                       |
| **Policy networks**   | Combine state/action vectors before feeding to models          |
| **Reward shaping**    | Add shaped reward components together                          |
| **Action embeddings** | Add embeddings of similar actions or states for generalization |

---

### 🔷 8. 🧮 **Mathematical Utilities Across ML**

| Use Case                  | Description                                                 |
| ------------------------- | ----------------------------------------------------------- |
| **Dot product expansion** | Often requires partial vector addition                      |
| **Norm calculation**      | Internally sums squares: $\|\vec{v}\|^2 = \sum v_i^2$       |
| **Matrix operations**     | Matrix addition is row-wise vector addition                 |
| **Distance metrics**      | Euclidean, cosine similarity use vector sums or differences |
| **Mean Squared Error**    | Add squared vector errors over all samples                  |

---

### ✅ Summary Table (Quick Glance)

| Category              | Use Cases (with Vector Addition)          |
| --------------------- | ----------------------------------------- |
| **Data Handling**     | Feature combinations, centering, scaling  |
| **NLP**               | Word embeddings, positional encoding      |
| **Computer Vision**   | Image blending, skip connections          |
| **Neural Nets**       | Bias addition, residuals, fusion          |
| **Optimization**      | Gradient updates, Adam/momentum           |
| **Generative Models** | Latent interpolation, conditioning        |
| **RL & Robotics**     | State-action combinations, reward shaping |

---

## 🔚 Conclusion

Vector addition is **not just arithmetic** — it’s how:

- Models **learn** (gradients, optimization)
- Networks **build complexity** (layer outputs)
- Data is **structured and fused**
- Multiple input types are **integrated** (multi-modal AI)

Without vector addition, **modern ML, DL, and AI architectures would collapse** — it’s as fundamental as neurons in a brain.

---

## <span style="color:#ff0054"  id="t3">**Numerical**</span>

### 1. 🔷 Data Preprocessing (Centroid Calculation)

Imagine 3 data points (2D features: study hours, attendance):

```
x¹ = [2, 60], x² = [4, 70], x³ = [6, 80]
```

**Compute centroid**:

```
sum = x¹ + x² + x³
    = [2+4+6, 60+70+80]
    = [12, 210]

centroid = (1/3) * sum = [4, 70]
```

So, the average study hours = 4 and average attendance = 70%.

---

### 2. 💬 NLP — Word Embedding Arithmetic

Suppose simplified 3D embeddings:

```
king = [0.7, 0.5, 0.1]
man  = [0.6, 0.4, 0.1]
woman= [0.6, 0.5, 0.2]
```

Apply analogy:

```
vec = king – man + woman
    = [0.7–0.6+0.6, 0.5–0.4+0.5, 0.1–0.1+0.2]
    = [0.7,      0.6,      0.2]
```

Result is a vector close to “queen” in embedding space.

---

### 3. 🖼️ Image Processing — Blending Two Images

Consider two grayscale images flattened to 4‑pixel vectors:

```
A = [100, 150, 200, 250]
B = [50, 100, 150, 200]
```

**Blend (average)**:

```
A + B = [150, 250, 350, 450]
avg   = (1/2) * (A + B) = [75, 125, 175, 225]
```

A darker/paler combination of both images.

---

### 4. 🧠 Neural Network — Adding Bias

With feature vector `x = [3, 4]`, weights `w = [0.5, 1.2]`, bias `b = 2`:

- Dot product: `w·x = 0.5*3 + 1.2*4 = 1.5 + 4.8 = 6.3`
- Add bias (scalar): `z = 6.3 + 2 = 8.3`

The final pre-activation `z` is a scalar obtained by vector addition.

---

### 5. 🔁 Residual Connection in Deep Learning

If layer output is `y = [0.2, 0.3, 0.5]` and its input was `x = [0.1, 0.4, 0.6]`, a residual (skip) connection sums them:

```
res = y + x = [0.3, 0.7, 1.1]
```

This simple vector addition helps networks train much deeper architectures.

---

### ✅ Summary

- **Data centroid**: `[2,60]+[4,70]+[6,80] = [12,210]`, average = `[4,70]`
- **Word analogies**: `king–man+woman = [0.7, 0.6, 0.2] ≈ queen`
- **Image blending**: average of pixel vectors
- **Neural bias addition**: `w·x (vector) + b (scalar) = z`
- **Residual blocks in DL**: summing layer input & output

---
