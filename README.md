
# Logistic Regression with Stochastic Gradient Descent (SGD) — Explained! 📊🤖

## 1. The Problem Setup 🎯

- You have **features** (input variables):  
  $$ \mathbf{x} = [x_1, x_2, ..., x_n] $$ 🔢
- You want to predict a binary **label** $$y \in \{0,1\}$$ (e.g., spam or not spam) 📨❌✅

## 2. The Logistic Model 🔍

- Compute the linear combination of features and weights plus a bias:  
  $$
  z = \mathbf{w} \cdot \mathbf{x} + b = \sum_{j=1}^n w_j x_j + b
  $$  
  where:  
  - $$\mathbf{w}$$ = weights ⚖️  
  - $$b$$ = bias (intercept) 🎯  
  - $$\mathbf{x}$$ = features 🧮

- Pass this through the **sigmoid function** (also called logistic function) to squash into a probability between 0 and 1:  
  $$
  \hat{y} = \sigma(z) = \frac{1}{1 + e^{-z}}
  $$  
  The sigmoid looks like a soft switch 🔄 turning linear inputs into probabilities.

## 3. Making Predictions 🤔

- $$\hat{y}$$ is now the model’s predicted **probability** that the data point belongs to class 1.  
- Decision boundary with threshold 0.5:  
  - If $$ \hat{y} \geq 0.5 $$, predict class 1 ✅  
  - Else, predict class 0 ❌

## 4. How Do We Know If Predictions Are Good? 📉

- Use the **binary cross-entropy loss (log loss)** to measure error:  
  $$
  L = - \big( y \log(\hat{y}) + (1 - y) \log(1 - \hat{y}) \big)
  $$  
- Intuition:  
  - If prediction $$\hat{y}$$ is close to true label $$y$$, loss is low ✔️  
  - If it's far, loss is high ❌

## 5. Learning by Updating Parameters — Gradient Descent 🔄

- To minimize the loss, adjust weights and bias using **gradients** (derivatives indicating how to change values to reduce error).

- For one training example $$ (\mathbf{x}_i, y_i) $$, the gradients are:  
  - For weight $$w_j$$:  
    $$
    \frac{\partial L}{\partial w_j} = (\hat{y}_i - y_i) x_{ij}
    $$  
  - For bias $$b$$:  
    $$
    \frac{\partial L}{\partial b} = \hat{y}_i - y_i
    $$

## 6. What’s *Stochastic Gradient Descent*? ⚡️

- **Batch Gradient Descent** computes gradients over the entire dataset each time before updating.

- **Stochastic Gradient Descent (SGD)** updates parameters for **every single training example** immediately after computing its gradient.

- This “stochastic” (random) step often helps:  
  - Faster convergence 🏃‍♂️  
  - Escapes shallow local minima 🚀  
  - Works well with large datasets 📊

## 7. SGD Update Equations 💡

For each training example:  
- Update weights:  
  $$
  w_j := w_j - \eta \cdot (\hat{y}_i - y_i) \cdot x_{ij}
  $$  
- Update bias:  
  $$
  b := b - \eta \cdot (\hat{y}_i - y_i)
  $$

Where:  
- $$\eta$$ = learning rate (small positive number) 📉 — controls how big the update step is.

## 8. Example 🧑‍🏫

Imagine the following for one sample:

| Variable        | Value          | Explanation                     |
|-----------------|----------------|--------------------------------|
| Feature vector  | $$ \mathbf{x} = [2][3] $$ | Inputs/features                      |
| True label     | $$y = 1$$        | The actual class                   |
| Current weights | $$ \mathbf{w} = [0.1, -0.2] $$ | Model's current weights              |
| Bias           | $$b = 0.05$$      | Model's current bias                  |
| Learning rate  | $$ \eta = 0.1 $$ | Step size for updates             |

**Step 1:** Calculate linear output:  
$$
z = 0.1\times2 + (-0.2)\times3 + 0.05 = 0.2 - 0.6 + 0.05 = -0.35
$$

**Step 2:** Compute predicted probability:  
$$
\hat{y} = \frac{1}{1 + e^{0.35}} \approx 0.413
$$

**Step 3:** Calculate error:  
$$
\hat{y} - y = 0.413 - 1 = -0.587
$$

**Step 4:** Update weights:  
- $$ w_1 = 0.1 - 0.1 \times (-0.587) \times 2 = 0.1 + 0.1174 = 0.2174 $$  
- $$ w_2 = -0.2 - 0.1 \times (-0.587) \times 3 = -0.2 + 0.1761 = -0.0239 $$

**Step 5:** Update bias:  
$$
b = 0.05 - 0.1 \times (-0.587) = 0.1087
$$

This update nudges parameters closer to minimizing error for this example! 🎯

## 9. Repeat Over Dataset & Epochs 🔁

- Process **each training example** similarly, updating weights immediately.
- Shuffle the data each epoch to improve learning and avoid cycles 🔀.
- After many epochs, the model converges to weights that best classify the data.

## 10. Summary Table 📚

| Concept                      | Formula / Description                                      | Emoji Representation      |
|------------------------------|------------------------------------------------------------|---------------------------|
| Linear Combination            | $$ z = \mathbf{w} \cdot \mathbf{x} + b $$                  | ⚖️➕🧮                     |
| Sigmoid Function             | $$ \sigma(z) = \frac{1}{1 + e^{-z}} $$                     | 🔄                         |
| Cross-Entropy Loss           | $$L = -[y \log(\hat{y}) + (1 - y) \log(1-\hat{y})]$$       | 📉                         |
| Gradient for weights         | $$ (\hat{y} - y) \times x_j $$                             | 📏                         |
| Gradient for bias            | $$ \hat{y} - y $$                                          | 📐                         |
| SGD Weight Update            | $$ w_j := w_j - \eta (\hat{y} - y) x_j $$                  | ⚡️                         |
| SGD Bias Update              | $$ b := b - \eta (\hat{y} - y) $$                          | ⚡️                         |
| Learning Rate                | Step size controlling update amount                        | 🎚️                         |

