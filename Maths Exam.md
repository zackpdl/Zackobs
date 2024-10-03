# Machine Learning Cheatsheet - Page 1

## Regression Analysis
- Fits a model to observed data
- Predicts a continuous outcome variable
- Types: Linear, Non-linear, Polynomial

### Linear Regression
y = β₀ + β₁x + ε
- β₀: y-intercept
- β₁: slope
- ε: error term

### Least Squares Method
- Minimizes sum of squared residuals
- Used to find best-fit line

### Gradient Descent
- Iterative optimization algorithm
- Steps:
  1. Start with initial weights
  2. Calculate error
  3. Compute gradient
  4. Update weights
  5. Repeat until convergence

Weight update rule: w_i = w_i + η * (t - o) * x_i
- η: learning rate
- t: target output
- o: actual output
- x_i: input feature

### Evaluation Metrics
- Mean Squared Error (MSE)
- R-squared (Coefficient of Determination)

## Cluster Analysis
- Groups similar data points
- Unsupervised learning technique

### Types of Clustering
1. Hierarchical
2. Centroid-based (e.g., K-means)
3. Distribution-based
4. Density-based (e.g., DBSCAN)

### Evaluation Metrics
- Silhouette Coefficient
- V-measure
- Homogeneity and Completeness

### Distance Measures
- Euclidean Distance
- Cosine Similarity

## Vector Spaces
- Represent data as vectors
- Used in various ML algorithms

### Vector Operations
- Addition, subtraction
- Dot product
- Vector projection

# Machine Learning Cheatsheet - Page 2

## Decision Trees
- Tree-like model of decisions
- Used for classification and regression

### Algorithm Steps
1. Select best attribute using Information Gain
2. Create a decision node using that attribute
3. Recursively create sub-trees for each branch
4. Stop when leaf node criteria met

### Entropy
H(S) = -Σ p_i * log₂(p_i)
- Measures impurity in a group of examples

### Information Gain
IG(S, A) = H(S) - Σ ((|S_v| / |S|) * H(S_v))
- S: dataset
- A: attribute
- v: possible values of A

## Naive Bayes
- Probabilistic classifier based on Bayes' Theorem
- Assumes feature independence

### Bayes' Theorem
P(A|B) = (P(B|A) * P(A)) / P(B)

### Naive Bayes Classifier
C_NB = argmax_c_j ∈ C P(c_j) * Π P(e_i|c_j)

## K-Nearest Neighbors (KNN)
- Instance-based learning algorithm
- Used for classification and regression

### Algorithm Steps
1. Choose K value
2. Calculate distance to all training examples
3. Select K nearest neighbors
4. Assign label (classification) or average (regression)

### Distance-Weighted KNN
w_i = 1 / d(x_q, x_i)²
- Assigns higher weight to closer neighbors

## Machine Learning Process
1. Data collection and preparation
2. Feature selection/engineering
3. Model selection
4. Training
5. Evaluation
6. Hyperparameter tuning
7. Deployment

## Evaluation Metrics
- Accuracy, Precision, Recall, F1-score
- Confusion Matrix
- ROC Curve and AUC

## Overfitting and Underfitting
- Overfitting: Model too complex, poor generalization
- Underfitting: Model too simple, fails to capture patterns

## Regularization Techniques
- L1 (Lasso)
- L2 (Ridge)
- Dropout (for neural networks)

## Feature Scaling
- Normalization: Scales to [0, 1]
- Standardization: Scales to mean=0, std=1

## Dimensionality Reduction
- PCA (Principal Component Analysis)
- t-SNE (t-Distributed Stochastic Neighbor Embedding)

# Machine Learning Cheatsheet - Page 1

## Data Preparation and Exploration

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# Load data
data = pd.read_csv('your_dataset.csv')

# Basic exploration
print(data.head())
print(data.info())
print(data.describe())

# Split features and target
X = data.drop('target_column', axis=1)
y = data['target_column']

# Split data into train and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Scale features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Visualize data (example for 2D data)
plt.scatter(X['feature1'], X['feature2'], c=y)
plt.xlabel('Feature 1')
plt.ylabel('Feature 2')
plt.title('Data Visualization')
plt.show()
```

## Linear Regression

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

# Create and train the model
model = LinearRegression()
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"Mean squared error: {mse}")
print(f"R-squared score: {r2}")

# Plot results (for simple linear regression)
plt.scatter(X_test, y_test, color='black')
plt.plot(X_test, y_pred, color='blue', linewidth=3)
plt.xlabel('X')
plt.ylabel('y')
plt.title('Linear Regression Results')
plt.show()
```

## Logistic Regression

```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, classification_report

# Create and train the model
model = LogisticRegression()
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy}")
print(classification_report(y_test, y_pred))
```

# Machine Learning Cheatsheet - Page 2

## K-Nearest Neighbors (KNN)

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score

# Create and train the model
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train, y_train)

# Make predictions
y_pred = knn.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy}")
```

## Decision Tree

```python
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.metrics import accuracy_score

# Create and train the model
dt = DecisionTreeClassifier(max_depth=5, random_state=42)
dt.fit(X_train, y_train)

# Make predictions
y_pred = dt.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy}")

# Visualize the tree
plt.figure(figsize=(20,10))
plot_tree(dt, filled=True, feature_names=X.columns, class_names=dt.classes_)
plt.show()
```

## K-Means Clustering

```python
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score

# Create and fit the model
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(X)

# Get cluster labels
labels = kmeans.labels_

# Evaluate the model
silhouette_avg = silhouette_score(X, labels)
print(f"Silhouette Score: {silhouette_avg}")

# Visualize the clusters (for 2D data)
plt.scatter(X[:, 0], X[:, 1], c=labels, cmap='viridis')
centers = kmeans.cluster_centers_
plt.scatter(centers[:, 0], centers[:, 1], c='red', marker='x', s=200, linewidths=3)
plt.title('K-Means Clustering')
plt.show()
```

## Principal Component Analysis (PCA)

```python
from sklearn.decomposition import PCA

# Create and fit PCA
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X)

# Visualize the results
plt.scatter(X_pca[:, 0], X_pca[:, 1], c=y)
plt.xlabel('First Principal Component')
plt.ylabel('Second Principal Component')
plt.title('PCA of Dataset')
plt.show()

# Print explained variance ratio
print(f"Explained Variance Ratio: {pca.explained_variance_ratio_}")
```

## Model Evaluation

```python
from sklearn.model_selection import cross_val_score
from sklearn.metrics import confusion_matrix, roc_curve, auc

# Cross-validation
scores = cross_val_score(model, X, y, cv=5)
print(f"Cross-validation scores: {scores}")
print(f"Mean CV score: {scores.mean()}")

# Confusion Matrix
cm = confusion_matrix(y_test, y_pred)
print("Confusion Matrix:")
print(cm)

# ROC Curve and AUC (for binary classification)
y_pred_proba = model.predict_proba(X_test)[:, 1]
fpr, tpr, _ = roc_curve(y_test, y_pred_proba)
roc_auc = auc(fpr, tpr)

plt.figure()
plt.plot(fpr, tpr, color='darkorange', lw=2, label=f'ROC curve (AUC = {roc_auc:.2f})')
plt.plot([0, 1], [0, 1], color='navy', lw=2, linestyle='--')
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.05])
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('Receiver Operating Characteristic (ROC) Curve')
plt.legend(loc="lower right")
plt.show()
```

Here’s how you can format these problems in Obsidian using Markdown for clarity and structure. Obsidian supports LaTeX for equations, so I’ve included that as well.

---

## 1. **Linear Regression (Simple Case)**

**Problem**:  
Suppose we have the following data points:  
(1, 2), (2, 2.8), (3, 3.6), (4, 4.4).  
Find the best-fit line using linear regression.

**Solution**:  
The equation for linear regression is:  
$$ y = \beta_0 + \beta_1 x $$

### Step 1: Compute the means of \( x \) and \( y \):  
$$ \bar{x} = \frac{1 + 2 + 3 + 4}{4} = 2.5 $$  
$$ \bar{y} = \frac{2 + 2.8 + 3.6 + 4.4}{4} = 3.2 $$

### Step 2: Calculate \( \beta_1 \) (slope):  
$$ \beta_1 = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sum (x_i - \bar{x})^2} $$  
$$ \beta_1 = \frac{(1-2.5)(2-3.2) + (2-2.5)(2.8-3.2) + \dots}{(1-2.5)^2 + (2-2.5)^2 + \dots} = 0.8 $$

### Step 3: Calculate \( \beta_0 \) (intercept):  
$$ \beta_0 = \bar{y} - \beta_1 \bar{x} = 3.2 - (0.8)(2.5) = 1.2 $$

### Final Equation:  
$$ y = 1.2 + 0.8x $$

---

## 2. **K-Means Clustering (2 Points)**

**Problem**:  
We have two points A (2, 2) and B (8, 8). Run one iteration of K-Means clustering with initial centroids at \( C_1 = (1, 1) \) and \( C_2 = (9, 9) \).

**Solution**:  

### Step 1: Calculate the Euclidean distance from each point to the centroids:

- $$ d(A, C_1) = \sqrt{(2 - 1)^2 + (2 - 1)^2} = \sqrt{1 + 1} = \sqrt{2} \approx 1.41 $$
- $$ d(A, C_2) = \sqrt{(2 - 9)^2 + (2 - 9)^2} = \sqrt{49 + 49} = \sqrt{98} \approx 9.9 $$
- $$ d(B, C_1) = \sqrt{(8 - 1)^2 + (8 - 1)^2} = \sqrt{49 + 49} = \sqrt{98} \approx 9.9 $$
- $$ d(B, C_2) = \sqrt{(8 - 9)^2 + (8 - 9)^2} = \sqrt{1 + 1} = \sqrt{2} \approx 1.41 $$

### Step 2: Assign points to the nearest centroid:
- A is closer to \( C_1 \), so A belongs to cluster 1.
- B is closer to \( C_2 \), so B belongs to cluster 2.

### New Centroids:
- $$ C_1' = \text{mean of points in cluster 1} = (2, 2) $$
- $$ C_2' = \text{mean of points in cluster 2} = (8, 8) $$



---

## 3. **Naive Bayes Classification**

**Problem**:  
We want to classify whether a patient has a disease based on a symptom. We know the following probabilities:  
- $$ P(\text{Disease}) = 0.1 $$
- $$ P(\text{No Disease}) = 0.9 $$
- $$ P(\text{Symptom} | \text{Disease}) = 0.8 $$
- $$ P(\text{Symptom} | \text{No Disease}) = 0.2 $$

What is \( P(\text{Disease} | \text{Symptom}) \)?

**Solution**:  

Use Bayes’ Theorem:  
$$ P(\text{Disease} | \text{Symptom}) = \frac{P(\text{Symptom} | \text{Disease}) \cdot P(\text{Disease})}{P(\text{Symptom})} $$

### Step 1: Calculate \( P(\text{Symptom}) \):
$$ P(\text{Symptom}) = P(\text{Symptom} | \text{Disease}) \cdot P(\text{Disease}) + P(\text{Symptom} | \text{No Disease}) \cdot P(\text{No Disease}) $$
$$ P(\text{Symptom}) = (0.8)(0.1) + (0.2)(0.9) = 0.08 + 0.18 = 0.26 $$

### Step 2: Calculate \( P(\text{Disease} | \text{Symptom}) \):
$$ P(\text{Disease} | \text{Symptom}) = \frac{(0.8)(0.1)}{0.26} = \frac{0.08}{0.26} \approx 0.31 $$

---

## 4. **Entropy and Information Gain (Decision Trees)**

**Problem**:  
You have a dataset with 10 instances. Out of them, 6 are positive and 4 are negative. Calculate the entropy of the dataset.

**Solution**:  

The formula for entropy is:  
$$ H(S) = -\sum p_i \log_2(p_i) $$  
Where \( p_i \) is the proportion of positive and negative examples.

- For the positive class:  
$$  ( p_+ = \frac{6}{10} = 0.6 )$$
- For the negative class:  
$$  ( p_- = \frac{4}{10} = 0.4 )$$

### Entropy Calculation:  
$$ H(S) = -(0.6 \log_2(0.6) + 0.4 \log_2(0.4)) $$  
Using approximate values:  
$$ H(S) = -(0.6 \times -0.737 + 0.4 \times -1.322) $$  
$$ H(S) = 0.442 + 0.529 = 0.971 $$

---

## 5. **Principal Component Analysis (PCA)**

**Problem**:  
You have the following data points:  
(2, 4), (3, 3), (4, 2), (5, 1).  
Find the first principal component.

**Solution**:  

### Step 1: Compute the mean of the data:
- \( \bar{x} = \frac{2 + 3 + 4 + 5}{4} = 3.5 \)
- \( \bar{y} = \frac{4 + 3 + 2 + 1}{4} = 2.5 \)

### Step 2: Center the data:
- \( (2 - 3.5, 4 - 2.5) = (-1.5, 1.5) \)
- \( (3 - 3.5, 3 - 2.5) = (-0.5, 0.5) \)
- ...

### Step 3: Calculate the covariance matrix:
$$ \text{Cov} = \begin{bmatrix} \text{Cov}(x, x) & \text{Cov}(x, y) \\ \text{Cov}(y, x) & \text{Cov}(y, y) \end{bmatrix} = \begin{bmatrix} 1.6667 & -1.6667 \\ -1.6667 & 1.6667 \end{bmatrix} $$

### Step 4: Find the eigenvalues and eigenvectors.  
The largest eigenvalue corresponds to the first principal component.


Here’s the same note with proper LaTeX formatting using `$$` for equations, suitable for Obsidian:

---

### Title: Entropy and Information Gain: Outlook (Sunny Branch)

---

#### 1. **Outlook Attribute - Sunny Branch**

When calculating the entropy and information gain for the **Sunny** branch in the **Outlook** attribute:

- **Data Split**: The data splits into:
  - **Sunny**: 2 "yes", 3 "no"

#### 2. **Entropy Calculation**

The formula for entropy is:

$$
H(\text{Sunny}) = - \sum_{i} p_i \log_2(p_i)
$$

Where \( p_i \) is the probability of each class (yes/no).

For **Sunny**:
- $$Probability of "yes" ( p(text{yes}) = frac{2}{5} )$$
- $$ Probability of "no" ( p(text{no}) = frac{3}{5} )$$

The entropy for the Sunny branch is:

$$
H(\text{Sunny}) = -\left(\frac{2}{5} \log_2 \left( \frac{2}{5} \right) + \frac{3}{5} \log_2 \left( \frac{3}{5} \right)\right)
$$

Simplifying:

$$
H(\text{Sunny}) \approx -\left(0.528 \times (-1.3219) + 0.471 \times (-0.73696)\right) \approx 0.971 \, \text{bits}
$$

#### 3. **Information Gain**

We calculate the weighted entropy of all branches of the Outlook attribute and compare it to the initial entropy of the full dataset to determine the information gain.

If the initial entropy \( H(D) \) of the dataset is 0.94, and the weighted entropy for all branches is calculated (say 0.693 for Outlook as a whole), the information gain for **Outlook** is:

$$
\text{Gain(Outlook)} = 0.94 - 0.693 = 0.247 \, \text{bits}
$$

The "Sunny" branch contributes a partial amount to this overall gain based on its entropy and the number of instances it contains.
