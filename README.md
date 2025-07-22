# Logistic Regression with Stochastic Gradient Descent (SGD) — Explained! 📊🤖

### 1. The Problem Setup 🎯

- You have features (input variables):

$$
\mathbf{x} = [x_1, x_2, ..., x_n]
$$ 🔢

- You want to predict a binary label:

$$
y \in \{0,1\}
$$

(e.g., spam or not spam) 📨❌✅

### 2. The Logistic Model 🔍

- Compute the linear combination of features and weights plus a bias:

$$
z = \mathbf{w} \cdot \mathbf{x} + b = \sum_{j=1}^n w_j x_j + b
$$

where  
- $$ \mathbf{w} $$ = weights ⚖️  
- $$ b $$ = bias (intercept) 🎯  
- $$ \mathbf{x} $$ = features 🧮  

- Pass this through the **sigmoid function** to squash the value into a probability between 0 and 1:

$$
\hat{y} = \sigma(z) = \frac{1}{1 + e^{-z}}
$$

The sigmoid acts as a soft switch 🔄 transforming linear inputs into probabilities.

### 3. Making Predictions 🤔

- $$ \hat{y} $$ is the predicted probability that the sample belongs to class 1.
- Classification decision rule with threshold 0.5:  
  - If $$ \hat{y} \geq 0.5 $$, predict class 1 ✅  
  - Otherwise, predict class 0 ❌

### 4. How to Measure Prediction Quality? 📉

- Use **binary cross-entropy loss** (log loss) to quantify error:

$$
L = - \big( y \log(\hat{y}) + (1 - y) \log(1 - \hat{y}) \big)
$$

- Intuition:  
  - If prediction $$ \hat{y} $$ close to true label $$ y $$, loss is low ✔️  
  - If far, loss is high ❌

### 5. Parameter Updates via Gradient Descent 🔄

- To minimize loss, we compute parameters' gradients and update accordingly.
- For one training sample $$ (\mathbf{x}_i, y_i) $$, gradients are:

For weight $$ w_j $$:

$$
\frac{\partial L}{\partial w_j} = (\hat{y}_i - y_i) x_{ij}
$$

For bias $$ b $$:

$$
\frac{\partial L}{\partial b} = \hat{y}_i - y_i
$$

### 6. What is Stochastic Gradient Descent (SGD)? ⚡️

- **Batch Gradient Descent:** computes gradient over the whole dataset before updating.
- **SGD:** updates weights **immediately after each training example**, adding randomness.

Advantages:  
- Faster convergence 🏃‍♂️  
- Can escape shallow local minima 🚀  
- Scales better for large datasets 📊

### 7. SGD Update Rules 💡

For each training example:

- Update weights:

$$
w_j := w_j - \eta \cdot (\hat{y}_i - y_i) \cdot x_{ij}
$$

- Update bias:

$$
b := b - \eta \cdot (\hat{y}_i - y_i)
$$

Here, $$ \eta $$ (eta) is the **learning rate** 📉, controlling update step size.

### 8. Example 🧑‍🏫

Given:  
| Variable         | Value               | Explanation             |
|------------------|---------------------|-------------------------|
| Feature vector   | $$ \mathbf{x} =  $$     | Input features          |
| True label      | $$ y = 1 $$            | Actual class            |
| Current weights | $$ \mathbf{w} = [0.1, -0.2] $$ | Current model weights    |
| Bias            | $$ b = 0.05 $$          | Current bias            |
| Learning rate   | $$ \eta = 0.1 $$        | Step size               |

**Step 1: Compute linear output**

$$
z = 0.1 \times 2 + (-0.2) \times 3 + 0.05 = 0.2 - 0.6 + 0.05 = -0.35
$$

**Step 2: Compute predicted probability**

$$
\hat{y} = \frac{1}{1 + e^{0.35}} \approx 0.413
$$

**Step 3: Calculate error**

$$
\hat{y} - y = 0.413 - 1 = -0.587
$$

**Step 4: Update weights**

$$
w_1 = 0.1 - 0.1 \times (-0.587) \times 2 = 0.1 + 0.1174 = 0.2174
$$

$$
w_2 = -0.2 - 0.1 \times (-0.587) \times 3 = -0.2 + 0.1761 = -0.0239
$$

**Step 5: Update bias**

$$
b = 0.05 - 0.1 \times (-0.587) = 0.1087
$$

🎯 This update pushes the parameters closer to minimizing error for this example.

### 9. Repeat for Entire Dataset & Many Epochs 🔁

- Update parameters sample by sample.
- Shuffle data each epoch 🔀 to improve learning.
- Continue iterating until convergence.

### 10. Summary Table 📚

| Concept                  | Formula / Description                                | Emoji        |
|--------------------------|----------------------------------------------------|--------------|
| Linear Combination        | $$ z = \mathbf{w} \cdot \mathbf{x} + b $$            | ⚖️➕🧮         |
| Sigmoid Function         | $$ \sigma(z) = \frac{1}{1 + e^{-z}} $$              | 🔄           |
| Binary Cross-Entropy Loss| $$ L = -[ y \log(\hat{y}) + (1-y) \log(1-\hat{y}) ] $$ | 📉           |
| Gradient for weights     | $$ (\hat{y} - y) \times x_j $$                      | 📏           |
| Gradient for bias        | $$ \hat{y} - y $$                                   | 📐           |
| SGD Weight Update        | $$ w_j := w_j - \eta (\hat{y} - y) x_j $$          | ⚡️           |
| SGD Bias Update          | $$ b := b - \eta (\hat{y} - y) $$                   | ⚡️           |
| Learning Rate            | Step size controlling update size                   | 🎚️           |

