# **<span style="color:orange">EDA and Statistical Methods</span>**

## **Content**

- Data Wrangling

  - Definition
  - Importance of Data-Wrangling
  - Data Wrangling Processes
    - Data Collection
    - Data Cleaning
    - Data Transformation
    - Data Normalisation
    - Data Enrichment
    - Data Validation
      - Types of Data Validaton
        - Schema Validation
        - Range Validation
        - Consistency Validation
        - Uniqueness Validation
        - Cross Field Validation
    - Handling Missing Values
    - Data Publishing

- Data Visualisation
  - Definition
  - Importance of Data Visualisation
  - Types of Data Visualisation
  1. Basic Visualizations:
     - Bar Charts, Line Charts, Pie Charts
     - Used for descriptive analytics.
  2. Advanced Visualizations:
     - Scatter Plots, Box Plots, Heatmaps, Histograms
     - Used for deeper data analysis.
  3. AI & ML-Specific Visualizations:
     - Confusion Matrix, ROC Curve
     - Feature Importance plots, PCA visualizations.
  - Tools For Data-Visualisation
    - Matplotlib,Plotly,Seaborn:Python Libraries
    - R Libraries:ggplot2,Shiny
    - Dashboard Tools:PowerBI,Tableau
  - Best Practices in Data Visualisation
  - Future Trends in Data Visualisation
- Exploratory Data Analysis(EDA)

  - Definition
  - Importance of EDA
  - Key EDA Techniques
    - Descriptive Statistics
    - Data Visualisation
    - Data Cleaning
    - Correlation Analysis
  - Tools For EDA
    - Python:Numpy,Pandas,Matplotlib,Seaborn,Plotly
    - R:ggplot2,Shine,tidyr,dplyr
    - Jupyter Notebook
    - Tableau,PowerBI
  - Challenges in EDA
  - Application of EDA
  - Univariate Analysis

    - Definition
    - Example
    - Univariate Statistcal Analysis Techniques
      - Central Tendency
        - Mean
        - Mode
        - Media
      - Dispersion
      - Range
      - Quartiles
        - IQR
      - Variance
      - Standard Deviation
    - Univariate Graphical Techniques
      - Histogram
        - Definition
        - What information it convey
        - When to use
        - How to interpret graph
        - Eg
      - What is skewness
        - Explain in depth with eg.
      - Kurtosis
        - Explain in depth wiht eg.
      - Shapes and Data Distribution
        - Normal Distribution
        - Uniform Distribution
        - Exponential Distribution
        - Bimodal Distribution
    - Outliers and their impact

  - Bivariate Analysis
    - Introduction
    - Eg.
    - Types of Relation in Bivariate Analysis
      - Positive Correlation
      - Negative Correlation
      - No Correlation
    - Visualisation Techniques in Bivariate Analysis
      - Scatter Plot
      - Box Plot
      - Heatmaps
    - Statistical Techniques in Bivariate Analysis
      - Correlation Analysis
        - Parametric
          - Pearson Correlation
        - Non Parametric
          - Kendall's Tau
          - Spearman Correlation
      - Regression Analysis
      - Chi-Square Test
    - Monotonic vs Linear Relationship
    - Visualising Techniques for Correlation
    - Limitations of Correlation Analysis
  - Multvariate Analysis
    - Introduction
    - Techniques
      - Exploratory Technique
        - Principal Component Analysis (PCA): Dimensionality reduction while preserving variance.
        - Cluster Analysis: Groups similar data points into clusters.
      - Predictive Techniques:
        - Multiple Regression: Models the relationship between one dependent variable and multiple independent variables.
        - Discriminant Analysis: Classifies data points into predefined categories.
      - Confirmatory Techniques:
        - Structural Equation Modelling (SEM): Tests hypothesized relationships among variables.
    - Normalisation vs Standardisation
      - Min-Max Scaling
      - Max Abs Scaler
      - Z-Score Normalisation

Here's a **detailed explanation of Data Wrangling** and its associated processes, broken down into clearly structured sections:

---

## <span style="color:orange">Data Wrangling</span>

### 🧾 **Definition**

Data wrangling (also known as **data munging**) is the process of transforming and mapping raw data into a format that is appropriate and valuable for analysis or machine learning.

---

### 💡 **Importance of Data Wrangling**

- **Improves Data Quality**: Ensures the data is clean, accurate, and usable.
- **Enhances Model Performance**: Well-prepared data helps models learn better and faster.
- **Saves Time**: Reduces manual effort during analysis.
- **Increases Reliability**: Results in more accurate and repeatable outcomes.

---

## <span style="color:orange">Data Wrangling Processes</span>

---

### 📥 **1. Data Collection**

The first step is gathering raw data from various sources:

- **Sources**: Databases, APIs, CSV files, IoT devices, web scraping.
- **Challenges**: Data formats may vary; data may be incomplete or noisy.

---

### 🧹 **2. Data Cleaning**

Cleansing data to remove errors, duplicates, and irrelevant entries:

- **Removing duplicates**
- **Fixing incorrect or inconsistent formatting**
- **Filtering out outliers or irrelevant records**

---

### 🔄 **3. Data Transformation**

Modifying the structure, format, or values of the data:

- Converting data types
- Aggregating values
- Creating new features (feature engineering)

---

### 📏 **4. Data Normalisation**

Standardizing the range and scale of data features:

- **Why**: Prevents domination of large-range features over smaller ones.
- **Techniques**:

  - **Min-Max Scaling**: Scales data to \[0, 1]
  - **Z-score Standardization**: Centers around mean = 0 and standard deviation = 1

---

### 📈 **5. Data Enrichment**

Enhancing data by adding relevant information from external sources:

- **Example**: Adding weather data to sales data to understand seasonal trends.
- **Benefit**: Improves prediction and understanding by adding context.

---

### ✅ **6. Data Validation**

Ensures the data is accurate and conforms to defined rules.

#### 🔍 **Types of Data Validation**

| Type                       | Description                                                                 |
| -------------------------- | --------------------------------------------------------------------------- |
| **Schema Validation**      | Ensures data types, field names, and structures match expected schema.      |
| **Range Validation**       | Values fall within specified acceptable ranges.                             |
| **Consistency Validation** | Checks if the same value is represented consistently across records.        |
| **Uniqueness Validation**  | Ensures values that should be unique (e.g., IDs) are not duplicated.        |
| **Cross-Field Validation** | Validates logical relationships between fields (e.g., StartDate < EndDate). |

---

### ❓ **7. Handling Missing Values**

Addressing nulls, NaNs, or incomplete entries in datasets:

- **Techniques**:

  - **Remove** rows or columns (if data loss is acceptable)
  - **Impute** with mean, median, mode
  - **Use algorithms** that can handle missing data (e.g., decision trees)
  - **Flag** missing values with a new feature (binary indicator)

---

### 🌐 **8. Data Publishing**

Making the final cleaned and processed dataset available:

- **Formats**: CSV, JSON, Excel, SQL tables, or APIs.
- **Tools**: Data warehouses, BI dashboards, cloud storage
- **Includes**: Documentation, data dictionary, and versioning.

---

Here is a **complete and detailed explanation of Data Visualization** with all requested sections:

---

## <span style="color:orange">Data Visualization</span>

---

### 🧾 **Definition**

Data visualization is the graphical representation of information and data using visual elements like charts, graphs, maps, and dashboards. It enables users to **understand complex data** through intuitive visual formats.

---

### 💡 **Importance of Data Visualization**

- **Quick Understanding**: Allows fast interpretation of large volumes of data.
- **Pattern Recognition**: Helps identify trends, outliers, and correlations.
- **Better Decision Making**: Enables data-driven decisions based on visual evidence.
- **Enhanced Communication**: Simplifies the sharing of insights with stakeholders.

---

## <span style="color:orange">Types of Data Visualization</span>

---

### 1. 📊 **Basic Visualizations**

Used for **descriptive analytics** and simple comparisons.

| Type           | Description                       | Example Use Case                 |
| -------------- | --------------------------------- | -------------------------------- |
| **Bar Chart**  | Compares categories of data       | Sales by region                  |
| **Line Chart** | Displays data trends over time    | Stock prices, temperature change |
| **Pie Chart**  | Shows part-to-whole relationships | Market share distribution        |

---

### 2. 📈 **Advanced Visualizations**

Used for **deep analysis** and data distribution understanding.

| Type             | Description                                        | Example Use Case                        |
| ---------------- | -------------------------------------------------- | --------------------------------------- |
| **Scatter Plot** | Shows relationships/correlation between variables  | Age vs Income                           |
| **Box Plot**     | Displays data spread and outliers                  | Comparing salaries across departments   |
| **Heatmap**      | Visualizes matrix-like data with color intensities | Correlation matrix                      |
| **Histogram**    | Shows frequency distribution of data               | Age distribution of survey participants |

---

### 3. 🤖 **AI & ML-Specific Visualizations**

Used for **evaluating machine learning models** and features.

| Type                   | Description                                                 | Example Use Case                       |
| ---------------------- | ----------------------------------------------------------- | -------------------------------------- |
| **Confusion Matrix**   | Displays model prediction accuracy for classification tasks | Evaluate a spam detection model        |
| **ROC Curve**          | Shows true vs false positive rate trade-offs                | Comparing classifiers                  |
| **Feature Importance** | Ranks which features influenced the model the most          | Feature selection in tree-based models |
| **PCA Visualization**  | Reduces data dimensions for visual interpretation           | Visualizing high-dimensional datasets  |

---

## <span style="color:orange">Tools for Data Visualization</span>

---

### 🐍 **Python Libraries**

- **Matplotlib**: Basic static plots (bar, line, pie)
- **Seaborn**: Statistical data visualization built on Matplotlib
- **Plotly**: Interactive, web-based visualizations (3D plots, dashboards)

---

### 📊 **R Libraries**

- **ggplot2**: Elegant grammar of graphics for complex plots
- **Shiny**: Builds interactive web apps directly from R

---

### 🖥️ **Dashboard Tools**

- **Tableau**: Powerful drag-and-drop interface for dashboards
- **Power BI**: Microsoft’s business analytics service with real-time insights

---

## <span style="color:orange">Best Practices in Data Visualization</span>

- Use **clear labels and legends**
- Choose the **right chart type** for the data
- Avoid **chartjunk** (unnecessary 3D effects or decorations)
- Keep it **simple, yet informative**
- Use **color meaningfully** (e.g., red for danger, green for success)
- Always consider your **audience and context**

---

## <span style="color:orange">Future Trends in Data Visualization</span>

- **Augmented Analytics**: AI-generated visuals and insights
- **Narrative Visualization**: Combining storytelling with data
- **Real-Time Dashboards**: Instant updates for live data
- **3D and Immersive Visualizations**: Use of VR and AR
- **Natural Language Queries**: Conversational tools to explore data (e.g., ChatGPT + Power BI)

---

Here is a **detailed explanation** of **Exploratory Data Analysis (EDA)** with all the requested components:

---

## <span style="color:orange">Exploratory Data Analysis (EDA)</span>

---

### 📘 **Definition**

**Exploratory Data Analysis (EDA)** is the process of **analyzing datasets to summarize their main characteristics**, often with visual methods. It helps to **discover patterns**, detect **anomalies**, and check **assumptions** using **statistical graphics and plots** before applying machine learning models.

---

### 🎯 **Importance of EDA**

- Understand the **structure** and **distribution** of data.
- Detect **missing values**, **outliers**, and **errors**.
- Test assumptions and validate **hypotheses**.
- Inform feature engineering and model selection.
- Avoid costly mistakes in later stages of analysis.

---

## <span style="color:orange">Key EDA Techniques</span>

---

### 1. 🧮 **Descriptive Statistics**

- Provides basic summaries about the dataset:

  - Mean, Median, Mode
  - Standard Deviation, Variance
  - Min, Max, Range
  - Skewness, Kurtosis

- Helps in identifying **central tendency** and **spread** of data.

---

### 2. 📊 **Data Visualization**

- Uses charts and graphs to **visualize patterns**:

  - Histograms, Boxplots: Understand distributions
  - Scatter Plots: Show relationships between variables
  - Heatmaps: Display correlations and feature interactions

- Makes data **intuitive and accessible**.

---

### 3. 🧹 **Data Cleaning**

- Detect and handle:

  - **Missing values** (null, NaN)
  - **Duplicate rows**
  - **Inconsistent entries** (e.g., "M", "Male", "m")
  - **Incorrect data types**

- Ensures data **quality** and **reliability**.

---

### 4. 🔗 **Correlation Analysis**

- Measures relationships between features:

  - **Pearson Correlation** for linear relationships
  - **Spearman/Kendall** for non-linear

- Identifies **redundant** or **highly influential** features for model building.

---

## <span style="color:orange">Tools for EDA</span>

---

### 🐍 **Python**

- **NumPy**: Basic numerical operations.
- **Pandas**: Data manipulation and summary stats.
- **Matplotlib**: Base plotting library.
- **Seaborn**: Statistical plots (heatmaps, violin plots).
- **Plotly**: Interactive visualizations and dashboards.

---

### 🧪 **R**

- **ggplot2**: Layered grammar of graphics for elegant visuals.
- **Shiny**: Interactive web applications.
- **tidyr** & **dplyr**: Tidy data and manipulation tools.

---

### 📓 **Other Platforms**

- **Jupyter Notebook**: Ideal for interactive EDA combining code + visuals.
- **Tableau & Power BI**: Drag-and-drop business intelligence tools for interactive dashboards.

---

## <span style="color:orange">Challenges in EDA</span>

- Large-scale datasets can be **slow** and **computationally expensive** to analyze.
- Dealing with **unclean or incomplete data** can be time-consuming.
- Risk of **confirmation bias** if analysis is not objective.
- Misinterpretation of visuals or correlations as causation.

---

## <span style="color:orange">Applications of EDA</span>

- **Business Intelligence**: Revenue trend analysis, customer segmentation.
- **Healthcare**: Understanding patient demographics, treatment response.
- **Finance**: Fraud detection, portfolio risk analysis.
- **Marketing**: Campaign performance analysis.
- **Machine Learning**: Informs feature selection, model assumptions, and pre-processing.

---

Here’s a detailed explanation of **Univariate Analysis**, as requested:

---

## <span style="color:orange">Univariate Analysis</span>

---

### 📘 **Definition**

**Univariate analysis** is the simplest form of data analysis where the data being analyzed consists of **only one variable**. The purpose is to **describe** and **summarize** the characteristics of that single variable using:

- **Statistical measures** (mean, median, mode, variance)
- **Visualizations** (histograms, box plots, bar charts)

This technique helps in understanding the **distribution**, **central tendency**, and **spread** of the variable.

> "**Uni**" means **one**, so **univariate** = **analyzing one variable at a time**.

---

### 🧠 **What It Helps Identify**

- **Nature of the variable**: categorical or numerical
- **Frequency or count** of values
- **Outliers**
- **Missing values**
- **Data skewness**

---

### ✅ **Example 1 (Numerical Data)**

**Dataset:** Heights (in cm) of 100 students.

```plaintext
Height = [160, 162, 165, 168, 170, 172, 174, 175, 177, 180, ...]
```

**Univariate Analysis Steps:**

- **Mean**: Average height
- **Median**: Middle value
- **Standard Deviation**: How spread out the heights are
- **Histogram**: Plot to show frequency distribution
- **Box Plot**: Identify outliers in height data

---

### ✅ **Example 2 (Categorical Data)**

**Dataset:** Favorite Fruits of students

```plaintext
Fruit = [Apple, Banana, Mango, Banana, Apple, Orange, Apple, ...]
```

**Univariate Analysis Steps:**

- **Frequency Table**: Count of each fruit
- **Bar Chart**: Visual representation of preferences
- **Mode**: Most common fruit

---

Here's a detailed explanation of **Univariate Statistical Analysis Techniques**, including their **mathematics**, **meaning**, **importance**, and **exam-style numerical examples**:

---

## <span style="color:orange">Univariate Statistical Analysis Techniques</span>

---

### 📊 **1. Central Tendency**

These measure the **center or average** of a dataset.

---

#### 📍 **Mean (Arithmetic Mean)**

**Definition**: The average of all values.

**Formula**:

$$
\text{Mean} (\mu) = \frac{\sum_{i=1}^{n} x_i}{n}
$$

**Use**: Represents the "typical" value.

**Example**:
Find the mean of: `5, 8, 12, 6, 9`

$$
\text{Mean} = \frac{5 + 8 + 12 + 6 + 9}{5} = \frac{40}{5} = 8
$$

---

#### 📍 **Median**

**Definition**: The **middle value** in an ordered dataset.

**Steps**:

- Arrange data in ascending order.
- If **odd** number of items: median = middle value.
- If **even**: median = average of two middle values.

**Example**:
Data: `6, 8, 9, 12, 14` → Median = `9` (middle value)

Data: `4, 7, 9, 10` → Median = $\frac{7+9}{2} = 8$

**Use**: Best when data has **outliers**.

---

#### 📍 **Mode**

**Definition**: The **most frequently occurring value**.

**Example**:
`2, 4, 4, 5, 7, 4, 8` → Mode = `4` (appears 3 times)

**Use**: Works well for **categorical data**.

---

### 🎯 **2. Dispersion (Spread of Data)**

Indicates how **spread out** values are from the center.

---

#### 📍 **Range**

**Definition**: Difference between the **maximum** and **minimum** values.

**Formula**:

$$
\text{Range} = \text{Max} - \text{Min}
$$

**Example**:
`5, 7, 10, 15, 18` → Range = $18 - 5 = 13$

---

#### 📍 **Quartiles**

Divide the dataset into **four equal parts**:

- **Q1**: 25% of data is below this point
- **Q2**: 50% (Median)
- **Q3**: 75% of data is below this point

**Use**: Helps in understanding distribution.

---

#### 📍 **Interquartile Range (IQR)**

**Definition**: Range of the **middle 50%** of the data.

**Formula**:

$$
\text{IQR} = Q3 - Q1
$$

**Example**:
Data: `5, 7, 10, 12, 14, 18, 20`

- Q1 = 7
- Q3 = 18
- IQR = $18 - 7 = 11$

**Use**: Detects **outliers** and data spread.

---

#### 📍 **Variance**

**Definition**: Average of **squared deviations** from the mean.

**Formula** (Population):

$$
\sigma^2 = \frac{\sum (x_i - \mu)^2}{n}
$$

**Example**:
Data: `2, 4, 6` → Mean = 4

$$
\sigma^2 = \frac{(2-4)^2 + (4-4)^2 + (6-4)^2}{3} = \frac{4 + 0 + 2^2}{3} = \frac{8}{3} \approx 2.67
$$

**Use**: Measures data **spread** around the mean.

---

#### 📍 **Standard Deviation**

**Definition**: Square root of variance. Indicates how much each value **deviates** from the mean.

**Formula**:

$$
\sigma = \sqrt{\text{Variance}}
$$

From above example:

$$
\sigma = \sqrt{2.67} \approx 1.63
$$

**Use**: Lower SD means data is **closer to the mean**; higher SD means **more spread out**.

---

### 📝 Summary Table

| Measure            | Indicates                 | Formula                        | Exam Tip                  |
| ------------------ | ------------------------- | ------------------------------ | ------------------------- |
| Mean               | Average                   | $\frac{\sum x}{n}$             | Sensitive to outliers     |
| Median             | Middle value              | —                              | Best with skewed data     |
| Mode               | Most frequent value       | —                              | Use for categorical data  |
| Range              | Total spread              | $\text{Max} - \text{Min}$      | Easy marks                |
| Quartiles          | Percentile cut-offs       | Q1, Q2 (Median), Q3            | Box plot understanding    |
| IQR                | Spread of central data    | $Q3 - Q1$                      | Used in outlier detection |
| Variance           | Average squared deviation | $\frac{\sum (x_i - \mu)^2}{n}$ | Practice with small data  |
| Standard Deviation | Avg. deviation from mean  | $\sqrt{\text{Variance}}$       | Must-know for ML exams    |

---

Here's a **detailed guide** on how to find **Q1, Q2, and Q3** (also called quartiles), with **formulas and numerical examples**:

---

## 🧠 **What Are Quartiles?**

Quartiles divide a dataset into **four equal parts** after it is sorted:

- **Q1 (Lower Quartile)**: 25% of the data lies **below** this value.
- **Q2 (Median)**: 50% of the data lies **below** this value.
- **Q3 (Upper Quartile)**: 75% of the data lies **below** this value.

---

## 🔢 **Formulas to Find Q1, Q2, and Q3**

1. **Sort** the data in **ascending order**.

2. Use the following positions:

- **Q1 Position**:

  $$
  Q1 = \text{Value at position } \frac{(n+1)}{4}
  $$

- **Q2 (Median) Position**:

  $$
  Q2 = \text{Value at position } \frac{(n+1)}{2}
  $$

- **Q3 Position**:

  $$
  Q3 = \text{Value at position } \frac{3(n+1)}{4}
  $$

> 🔹 If the position is not a whole number, interpolate between values.

---

## 🧮 **Numerical Example 1 (Odd number of values)**

Data:
`5, 7, 8, 10, 12, 14, 18`

**Step 1**: Arrange (already sorted)
**n = 7**

### Q1 Position = (7+1)/4 = 2nd

→ **Q1 = 7**

### Q2 Position = (7+1)/2 = 4th

→ **Q2 = 10**

### Q3 Position = 3(7+1)/4 = 6th

→ **Q3 = 14**

✅ Final Answer:

- Q1 = 7
- Q2 = 10
- Q3 = 14

---

## 🧮 **Numerical Example 2 (Even number of values)**

Data:
`4, 6, 8, 10, 12, 14, 16, 18`

**n = 8**

### Q1 Position = (8+1)/4 = 2.25

→ Interpolate between 2nd and 3rd value:

$$
Q1 = 6 + 0.25 \times (8 - 6) = 6 + 0.25 \times 2 = 6.5
$$

### Q2 (Median) = (8+1)/2 = 4.5

→ Between 4th and 5th value:

$$
Q2 = \frac{10 + 12}{2} = 11
$$

### Q3 = 3(8+1)/4 = 6.75

→ Between 6th and 7th value:

$$
Q3 = 14 + 0.75 \times (16 - 14) = 14 + 1.5 = 15.5
$$

✅ Final Answer:

- Q1 = 6.5
- Q2 = 11
- Q3 = 15.5

---

## 📝 Tips

- **Always sort** the data first.
- For **even datasets**, the quartiles may require **interpolation**.
- In exams, if a position is a fraction like 3.25, interpolate using:

  $$
  \text{Value at } 3.25 = x_3 + 0.25 \times (x_4 - x_3)
  $$

---

Here’s a **complete explanation of Univariate Graphical Techniques**, including **histograms, skewness, kurtosis, and shapes of data distributions**, with **examples and interpretations** to help you understand what information each conveys.

---

## 🟠 **Univariate Graphical Techniques**

Univariate graphical techniques are visual tools used to analyze and understand the distribution, central tendency, and variability of **a single variable (one feature)** in a dataset.

---

### 🔶 **1. Histogram**

#### 🧾 **Definition**

A **histogram** is a bar graph that represents the **frequency distribution** of continuous numerical data. It shows how often each range of values occurs.

#### ℹ️ **What Information It Conveys**

- Spread of data (how values are distributed)
- Frequency of ranges (bins)
- Skewness (asymmetry)
- Central tendency (where data clusters)
- Presence of outliers

#### 📅 **When to Use**

- When analyzing the distribution of continuous numerical data.
- During **Exploratory Data Analysis (EDA)**.
- To check for normality, skewness, or multimodality.

#### 📊 **How to Interpret**

- **Tall bars** → many data points in that range
- **Short bars** → fewer data points
- Symmetric shape → normal distribution
- Skewed shape → presence of skewness

#### 🧮 **Example**

Dataset: `5, 6, 7, 7, 8, 8, 8, 9, 10, 10, 12, 15`

Histogram (bins of size 2):

| Bin (Range) | Frequency |
| ----------- | --------- |
| 5–6         | 1         |
| 7–8         | 4         |
| 9–10        | 3         |
| 11–12       | 1         |
| 13–15       | 1         |

From this, we can tell:

- Most values lie between **7–10**.
- Few extreme values (like **15**) may be outliers.

---

### 🔷 **2. What is Skewness?**

#### 🧾 **Definition**

**Skewness** refers to the **asymmetry** of a distribution.

#### 🧭 **Types of Skewness**

1. **Positive Skew (Right-skewed)**:

   - Tail is longer on the right.
   - Mean > Median > Mode
   - Eg: Income distribution

2. **Negative Skew (Left-skewed)**:

   - Tail is longer on the left.
   - Mean < Median < Mode
   - Eg: Age at retirement

3. **Zero Skew (Symmetric)**:

   - Mean ≈ Median ≈ Mode
   - Eg: Heights of adults in a population

#### 🧮 **Example (Positive Skew)**

Values: `2, 3, 3, 4, 5, 6, 8, 12, 20`

- Mean = 7
- Median = 5
- Mode = 3
  Right tail is longer → Positive Skew.

---

### 🔶 **3. Kurtosis**

#### 🧾 **Definition**

**Kurtosis** describes the **"tailedness"** or **peakedness** of a distribution.

#### 📚 **Types of Kurtosis**

1. **Mesokurtic** (Normal)

   - Moderate tails
   - Eg: Standard Normal Distribution
   - Kurtosis ≈ 3

2. **Leptokurtic** (High peak)

   - Sharp peak and heavy tails
   - More extreme values
   - Kurtosis > 3
   - Eg: Stock market returns

3. **Platykurtic** (Flat)

   - Broad, flat peak and light tails
   - Kurtosis < 3
   - Eg: Uniform distribution

#### 🧮 **Example**

- Mesokurtic: `[10, 12, 14, 12, 10]` (bell-shaped)
- Leptokurtic: `[5, 5, 12, 20, 20]` (sharp peak at 12)
- Platykurtic: `[5, 7, 9, 11, 13]` (flat spread)

---

## 🟣 **4. Shapes of Data Distribution**

### 📌 **a. Normal Distribution**

- Symmetrical bell-shaped curve
- Mean = Median = Mode
- 68% data within 1 SD, 95% within 2 SD
- Eg: Heights of people, IQ scores

### 📌 **b. Uniform Distribution**

- All values equally likely
- Flat histogram
- Eg: Rolling a fair die (1–6)

### 📌 **c. Exponential Distribution**

- Right-skewed
- Models time between events in a Poisson process
- Eg: Time until failure of machines, arrival of buses

### 📌 **d. Bimodal Distribution**

- Two peaks (modes)
- Indicates two different groups
- Eg: Test scores of students from two different schools

---

## 📈 **Summary Table of Graphical Techniques**

| Technique | Reveals About Data            | Best Use Case                  |
| --------- | ----------------------------- | ------------------------------ |
| Histogram | Frequency, spread, skewness   | Continuous numerical variables |
| Box Plot  | Median, IQR, outliers         | Comparison between groups      |
| Line Plot | Trends over time              | Time series analysis           |
| Bar Chart | Category comparisons (counts) | Categorical variables          |
| Pie Chart | Proportion                    | Simple categorical data        |

---

Here's a complete explanation of **Outliers and Their Impact** in data analysis and machine learning:

---

## 🟠 **Outliers and Their Impact**

---

### 🔷 **What are Outliers?**

**Outliers** are data points that deviate significantly from the rest of the dataset. They appear far from the mean or the central cluster of values and do not follow the general pattern.

#### 📌 **Definition:**

> An outlier is an observation point that is **distant from other observations** in the data. It can be unusually high or low compared to the rest of the dataset.

---

### 🔍 **How to Detect Outliers**

#### 📐 1. **Using Interquartile Range (IQR) Method:**

- **Q1** = First Quartile (25th percentile)
- **Q3** = Third Quartile (75th percentile)
- **IQR** = Q3 − Q1

> **Lower Bound** = Q1 − 1.5 × IQR
> **Upper Bound** = Q3 + 1.5 × IQR
> Any data point below the lower bound or above the upper bound is considered an outlier.

**🧮 Example:**

```
Data: 5, 6, 7, 8, 9, 10, 11, 35
Q1 = 6.5, Q3 = 10.5, IQR = 4
Lower Bound = 6.5 - (1.5 × 4) = 0.5
Upper Bound = 10.5 + (1.5 × 4) = 16.5
=> 35 is an outlier.
```

---

#### 📊 2. **Using Box Plot:**

- Points outside the “whiskers” of a box plot are outliers.
- Easily identifies data skew and spread.

#### 🧮 3. **Using Z-Score:**

> Z = (X - Mean) / Standard Deviation
> If **|Z| > 3**, it is usually an outlier.

---

### 🔄 **Types of Outliers**

1. **Global Outliers (Point Outliers)**: Far outside overall pattern
2. **Contextual Outliers**: Abnormal in specific context (e.g., low temp in summer)
3. **Collective Outliers**: A set of values together behaves abnormally

---

### ⚠️ **Impact of Outliers**

| **Area**                      | **Effect of Outliers**                                                     |
| ----------------------------- | -------------------------------------------------------------------------- |
| 🧮 **Descriptive Statistics** | Skews mean and standard deviation                                          |
| 📈 **Visualizations**         | Distorts plots, makes patterns hard to see                                 |
| 📊 **Regression Models**      | Affects slope of line, model overfits or underfits                         |
| 🧠 **ML Algorithms**          | Reduces model accuracy, especially in distance-based models (KNN, K-means) |
| 📉 **Data Integrity**         | May signal data entry errors, fraud, or rare events                        |

---

### ✅ **When to Remove or Keep Outliers**

| **Decision**      | **Reason**                                           |
| ----------------- | ---------------------------------------------------- |
| ✅ **Remove**     | Data entry error, sensor glitch, or irrelevant noise |
| 🔄 **Cap/Impute** | Replace with boundary values or predicted values     |
| ❌ **Keep**       | Represents important rare events or anomalies        |

---

### 🔧 **Handling Outliers**

1. **Transformation** (log, square root)
2. **Clipping/Capping** (Winsorization)
3. **Removing them** if valid reason
4. **Using robust algorithms** (e.g., median-based, tree-based)

---

### 🧠 **Example in Machine Learning**

In a dataset for predicting house prices:

- Most houses: ₹50–₹70 lakhs
- 1 house: ₹5 crores

→ This outlier can **skew the regression line**, misleading predictions.

---

### 🟩 **Summary**

| Aspect              | Outlier Effect                        |
| ------------------- | ------------------------------------- |
| Mean                | Skewed heavily by outliers            |
| Median              | Not affected                          |
| Std Deviation       | Increased                             |
| Linear Regression   | Coefficients distorted                |
| Distance Algorithms | Misclassified or misclustered results |

---

Here is a **detailed explanation of Bivariate Analysis**, its types, and visualization techniques — with examples included:

---

## 🟠 **Bivariate Analysis**

---

### 🔷 **Introduction**

**Bivariate Analysis** is the statistical analysis of **two variables** to determine relationships or patterns between them.

> **Objective:** To understand the **association**, **correlation**, or **cause-effect** between the two variables.

---

### 📌 **Example**

| Study Hours | Exam Score |
| ----------- | ---------- |
| 2           | 45         |
| 4           | 55         |
| 6           | 65         |
| 8           | 75         |
| 10          | 85         |

You can observe that **as study hours increase, exam scores also increase**. This is a **positive correlation** — and this insight comes from bivariate analysis.

---

## 🔄 **Types of Relationships in Bivariate Analysis**

---

### 1. ✅ **Positive Correlation**

- Both variables increase together.
- Example: Hours Studied vs. Marks Scored
- 📈 Graphically: An upward-sloping line.

### 2. 🔻 **Negative Correlation**

- One variable increases while the other decreases.
- Example: Stress Level vs. Sleep Hours
- 📉 Graphically: A downward-sloping line.

### 3. ⚫ **No Correlation**

- No observable relationship between the two variables.
- Example: Shoe Size vs. Intelligence Score
- Random scatter in the plot.

---

## 📊 **Visualization Techniques in Bivariate Analysis**

---

### 1. **Scatter Plot**

- **Definition**: A graph of plotted points that shows the relationship between two numerical variables.
- **Use**: Identify correlation and outliers.
- **Example**:

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.scatter(x, y)
plt.xlabel("Hours Studied")
plt.ylabel("Marks Scored")
plt.title("Scatter Plot - Positive Correlation")
plt.show()
```

> Interpretation: The closer the points are to forming a straight line, the stronger the relationship.

---

### 2. **Box Plot (Grouped Box Plot)**

- **Definition**: Shows distribution of one variable grouped by categories of another variable.
- **Use**: Compare distributions across groups.
- **Example**: Income across different education levels.

> Interpretation: Visual comparison of medians, IQRs, and outliers for two groups.

---

### 3. **Heatmaps (for Correlation Matrix)**

- **Definition**: Color-coded matrix showing correlation coefficients between multiple variables.
- **Use**: Identify which variable pairs are strongly correlated.
- **Example**:

```python
import seaborn as sns
import pandas as pd

data = {
    'study_hours': [1, 2, 3, 4, 5],
    'exam_score': [50, 60, 65, 75, 85],
    'sleep_hours': [8, 7, 6, 5, 4]
}

df = pd.DataFrame(data)

corr_matrix = df.corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
```

> Interpretation: Values close to 1 or -1 indicate strong correlation. Values near 0 indicate weak or no correlation.

---

## 📈 **Numerical Measures Often Used**

- **Pearson Correlation Coefficient (r)**
  Measures strength and direction of linear relationship.
  Range: `-1 ≤ r ≤ 1`

- **Covariance**
  Indicates how two variables change together (not scaled, hard to interpret directly).

---

## 🧠 **Summary Table**

| Technique    | Data Type                  | Purpose                             | Example                        |
| ------------ | -------------------------- | ----------------------------------- | ------------------------------ |
| Scatter Plot | Continuous vs. Continuous  | Show trend or correlation           | Height vs. Weight              |
| Box Plot     | Categorical vs. Continuous | Compare distributions across groups | Income vs. Education Level     |
| Heatmap      | Matrix of continuous       | Show correlations among many vars   | All numeric columns in dataset |

---

## ✅ Example for Practice

**Dataset**:

| Temperature (°C) | Ice Cream Sales (₹) |
| ---------------- | ------------------- |
| 20               | 200                 |
| 25               | 300                 |
| 30               | 450                 |
| 35               | 600                 |

**Q: What is the relation?**

- As temperature increases, sales increase → **Positive Correlation**
- **Scatter Plot** would show an upward trend.

---

Here's a **detailed explanation of statistical techniques in Bivariate Analysis**, including **Correlation Analysis**, **Regression**, and the **Chi-Square Test**, along with **numerical examples**:

---

## 🟠 Statistical Techniques in Bivariate Analysis

---

### 🔷 1. **Correlation Analysis**

> Measures the **degree and direction** of relationship between two variables.

#### ✅ Parametric Method: **Pearson Correlation Coefficient (r)**

- **Use**: Both variables must be **quantitative and normally distributed**.
- **Formula**:

$$
r = \frac{ \sum (x_i - \bar{x})(y_i - \bar{y}) }{ \sqrt{ \sum (x_i - \bar{x})^2 } \sqrt{ \sum (y_i - \bar{y})^2 } }
$$

- **Range**: -1 to +1

  - `r = +1`: Perfect positive linear relationship
  - `r = -1`: Perfect negative linear relationship
  - `r = 0`: No linear relationship

**🧮 Example:**

| x (Hours) | y (Marks) |
| --------- | --------- |
| 2         | 50        |
| 4         | 60        |
| 6         | 70        |
| 8         | 80        |

Use the formula or calculator:

- `r ≈ 1.0` → perfect positive correlation.

---

#### 🔶 Non-Parametric Methods (for ordinal or non-normal data):

---

#### 🔹 **Spearman's Rank Correlation (ρ)**

- **Use**: For **ordinal data** or non-linear monotonic relationships.
- **Steps**:

  1. Rank both variables
  2. Use the formula:

$$
\rho = 1 - \frac{6 \sum d^2}{n(n^2 - 1)}
$$

Where:

- $d$ = difference between ranks
- $n$ = number of pairs

**🧮 Example:**

| Student | Math Rank | Science Rank | d   | d²  |
| ------- | --------- | ------------ | --- | --- |
| A       | 1         | 2            | -1  | 1   |
| B       | 2         | 3            | -1  | 1   |
| C       | 3         | 1            | 2   | 4   |

$$
\rho = 1 - \frac{6(1+1+4)}{3(3^2 - 1)} = 1 - \frac{36}{24} = -0.5
$$

> Interpretation: Moderate negative rank-based correlation.

---

#### 🔹 **Kendall's Tau (τ)**

- **Use**: For **small datasets** or ties.
- **Interpretation** similar to Spearman's.
- Based on **concordant and discordant pairs**.

---

### 🔷 2. **Regression Analysis**

> Estimates how a **dependent variable (Y)** changes with an **independent variable (X)**.

#### ✅ **Simple Linear Regression**:

$$
y = a + bx
$$

Where:

- `a` = intercept
- `b` = slope

**Formula for b:**

$$
b = \frac{\sum (x - \bar{x})(y - \bar{y})}{\sum (x - \bar{x})^2}
$$

Then:

$$
a = \bar{y} - b\bar{x}
$$

**🧮 Example:**

| x (Hours) | y (Marks) |
| --------- | --------- |
| 1         | 50        |
| 2         | 60        |
| 3         | 70        |
| 4         | 80        |

$$
\bar{x} = 2.5,\quad \bar{y} = 65
$$

$$
b = \frac{(1-2.5)(50-65) + ... }{(1-2.5)^2 + ...} = 10
$$

$$
a = 65 - (10 × 2.5) = 40
$$

$$
\text{Regression Line: } y = 40 + 10x
$$

> For 5 hours of study → predicted marks = `40 + 10×5 = 90`.

---

### 🔷 3. **Chi-Square Test (χ² Test)**

> Tests **association between two categorical variables**.

#### ✅ **Chi-Square Test of Independence**

- Compares **observed** vs. **expected frequencies**.
- **Formula**:

$$
\chi^2 = \sum \frac{(O - E)^2}{E}
$$

---

**🧮 Example:**

|           | Likes Tea | Likes Coffee | Total |
| --------- | --------- | ------------ | ----- |
| Male      | 30        | 10           | 40    |
| Female    | 20        | 40           | 60    |
| **Total** | 50        | 50           | 100   |

**Step 1: Compute Expected Values:**

E (Male, Tea) = (40×50)/100 = 20
E (Male, Coffee) = 20
E (Female, Tea) = 30
E (Female, Coffee) = 30

**Step 2: Apply Formula:**

$$
\chi^2 = \frac{(30-20)^2}{20} + \frac{(10-20)^2}{20} + \frac{(20-30)^2}{30} + \frac{(40-30)^2}{30} = 5 + 5 + 3.33 + 3.33 = 16.66
$$

> Compare with critical χ² value at df = 1 → **If χ² > critical value, reject H₀ → variables are dependent**.

---

## 🔚 Summary Table

| Technique           | Data Type        | Output                          | Example Use                     |
| ------------------- | ---------------- | ------------------------------- | ------------------------------- |
| Pearson Correlation | Numeric          | Strength of linear relationship | Height vs. Weight               |
| Spearman Rank       | Ordinal/Numeric  | Monotonic correlation           | Satisfaction Rank vs. Test Rank |
| Regression          | Numeric (Y \~ X) | Predictive Equation             | Sales vs. Ads Spend             |
| Chi-Square Test     | Categorical      | Association measure             | Gender vs. Product Preference   |

---

Here’s a **detailed explanation** of:

---

## 🟠 Monotonic vs Linear Relationship

### 🔹 Monotonic Relationship

- A **monotonic relationship** is one where as one variable **increases**, the other **consistently** increases or decreases, but **not necessarily at a constant rate**.
- It can be **non-linear**, but still move in one direction.

**🧾 Example:**

- Relationship between **age** and **blood pressure**: as age increases, blood pressure tends to increase (but not linearly).
- **Visual**: Curve that always increases or decreases.

### 🔹 Linear Relationship

- A **linear relationship** implies a **straight-line** relationship between two variables.
- Change in one variable leads to **proportional change** in the other.

**🧾 Example:**

- Hours studied vs. marks obtained — if 2 extra hours gives +10 marks every time.

---

### 📊 Difference Summary

| Feature            | Monotonic                      | Linear                     |
| ------------------ | ------------------------------ | -------------------------- |
| Direction          | One-directional (↑ or ↓)       | One-directional            |
| Form               | Can be curved                  | Straight line              |
| Correlation method | Spearman, Kendall’s            | Pearson                    |
| Visual Example     | Increasing curve or flat slope | Straight line (y = mx + c) |

---

## 🔵 Visualizing Techniques for Correlation

### 🔹 1. **Scatter Plot**

- Plots individual data points.
- Shows **direction**, **strength**, and **form** of relationship.
- **Interpretation**:

  - Tight upward cluster → strong positive
  - Tight downward cluster → strong negative
  - Scattered cloud → weak or no correlation

### 🔹 2. **Heatmap**

- Used to visualize **correlation matrices**.
- Shows strength using **color gradients**.
- Useful for multivariable datasets.

```python
import seaborn as sns
import matplotlib.pyplot as plt
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
```

### 🔹 3. **Pairplot**

- Multiple scatter plots to show relationship between each pair of variables.

```python
sns.pairplot(df)
```

### 🔹 4. **Line Plot (for time series)**

- Helpful to observe **trends over time**.
- Multiple lines can reveal co-movement of variables.

---

## 🔴 Limitations of Correlation Analysis

| Limitation                             | Description                                                                   |
| -------------------------------------- | ----------------------------------------------------------------------------- |
| ❌ **Causation vs Correlation**        | Correlation does **not imply causation**. A third variable could affect both. |
| ❌ **Only Linear Relationships**       | Pearson only detects linear; misses non-linear patterns.                      |
| ❌ **Affected by Outliers**            | Outliers can **distort** correlation values.                                  |
| ❌ **Doesn’t Handle Categorical Data** | Can't apply to nominal/categorical variables.                                 |
| ❌ **Ignores Direction of Causality**  | Doesn’t show if X causes Y or vice versa.                                     |

---

Here is a comprehensive explanation of **Multivariate Analysis**, including all key concepts and examples:

---

## 🟠 **Multivariate Analysis**

### 🔹 **Introduction**

Multivariate Analysis involves examining **more than two variables simultaneously** to uncover patterns, relationships, and structures in complex datasets.

- **Used when**: Multiple variables influence an outcome.
- **Applications**: Machine Learning, Business Intelligence, Healthcare, Social Sciences, etc.

---

## 🔵 **Techniques in Multivariate Analysis**

### 🔹 1. **Exploratory Techniques**

#### ✅ **Principal Component Analysis (PCA)**

- **Purpose**: Reduce high-dimensional data while retaining most variance.
- **How**: Projects data onto new axes (principal components) that capture maximum variance.
- **Use Case**: Dimensionality reduction before clustering or visualization.

**Example**: Reducing a dataset with 100 features to 2 principal components to visualize.

---

#### ✅ **Cluster Analysis**

- **Purpose**: Group similar observations based on feature similarity.
- **Types**: K-Means, Hierarchical Clustering, DBSCAN.
- **Use Case**: Customer segmentation, pattern detection.

**Example**: Grouping customers by buying behavior into 3 clusters.

---

### 🔹 2. **Predictive Techniques**

#### ✅ **Multiple Regression**

- **Purpose**: Predict a **continuous** outcome using multiple input variables.
- **Formula**:

  $$
  Y = \beta_0 + \beta_1X_1 + \beta_2X_2 + \dots + \beta_nX_n + \epsilon
  $$

- **Use Case**: Predicting house prices using size, location, age.

---

#### ✅ **Discriminant Analysis**

- **Purpose**: Predict a **categorical** outcome based on continuous variables.
- **Use Case**: Email classification (spam/not spam), disease diagnosis.

---

### 🔹 3. **Confirmatory Techniques**

#### ✅ **Structural Equation Modeling (SEM)**

- **Purpose**: Test hypothesized models involving relationships among variables (observed & latent).
- **Used for**: Behavioral sciences, psychometrics.
- **Includes**: Factor analysis + path analysis.

**Example**: Testing how motivation and teaching methods affect student performance.

---

## 🔵 **Normalization vs Standardization**

These techniques **scale data** for better model performance and comparability.

### 🔹 **1. Min-Max Scaling (Normalization)**

- **Formula**:

  $$
  X' = \frac{X - X_{\text{min}}}{X_{\text{max}} - X_{\text{min}}}
  $$

- **Range**: \[0, 1]
- **Use Case**: Neural networks, distance-based models.

---

### 🔹 **2. Max-Abs Scaler**

- **Formula**:

  $$
  X' = \frac{X}{\text{max}(|X|)}
  $$

- **Range**: \[-1, 1] (Preserves sparsity)
- **Use Case**: Text data (e.g., TF-IDF values)

---

### 🔹 **3. Z-Score Normalization (Standardization)**

- **Formula**:

  $$
  Z = \frac{X - \mu}{\sigma}
  $$

- **Mean = 0, Standard Deviation = 1**
- **Use Case**: SVM, PCA, logistic regression.

---

## 🧠 Summary Table

| Technique             | Type          | Use Case Example                           |
| --------------------- | ------------- | ------------------------------------------ |
| PCA                   | Exploratory   | Dimensionality reduction before clustering |
| Cluster Analysis      | Exploratory   | Customer segmentation                      |
| Multiple Regression   | Predictive    | House price prediction                     |
| Discriminant Analysis | Predictive    | Medical diagnosis                          |
| SEM                   | Confirmatory  | Testing behavioral hypotheses              |
| Min-Max Scaling       | Preprocessing | Normalize features for neural nets         |
| Z-Score Scaling       | Preprocessing | Standardizing for PCA or regression        |

---

Here's a clear comparison of **Univariate**, **Bivariate**, and **Multivariate Analysis**:

---

## 🟠 **Univariate vs Bivariate vs Multivariate Analysis**

| Feature                    | **Univariate Analysis**                               | **Bivariate Analysis**                                  | **Multivariate Analysis**                                  |
| -------------------------- | ----------------------------------------------------- | ------------------------------------------------------- | ---------------------------------------------------------- |
| 🔹 **Definition**          | Analyzing **one** variable at a time                  | Analyzing the relationship between **two** variables    | Analyzing relationships among **three or more** variables  |
| 🔹 **Purpose**             | Understand distribution, central tendency, and spread | Understand correlation or association between variables | Understand complex interactions, patterns, or predictions  |
| 🔹 **Focus**               | Frequency, mean, median, variance, outliers           | Relationship: correlation, dependency                   | Dimensionality reduction, clustering, regression, etc.     |
| 🔹 **Visualization Tools** | Histogram, Box Plot, Bar Chart                        | Scatter Plot, Heatmap, Box Plot                         | 3D Plots, Pair Plots, PCA plots, Heatmaps, etc.            |
| 🔹 **Statistical Tools**   | Mean, Median, Mode, SD, Variance                      | Correlation, Covariance, Regression                     | PCA, Regression, Discriminant Analysis, Cluster Analysis   |
| 🔹 **Example**             | Analyzing income of individuals                       | Studying relation between income and education          | Studying how income, education, and location affect health |

---

## ✅ **Examples**

- **Univariate**:
  Analyzing the **average height** of students in a class.

- **Bivariate**:
  Investigating how **height and weight** are related in students.

- **Multivariate**:
  Exploring how **height, weight, diet, and exercise frequency** affect student health.

---
