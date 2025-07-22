# 🚀 Logistic Regression using Stochastic Gradient Descent (SGD)

A clear and engaging explanation of how logistic regression works—optimized via **SGD**, with math, intuition, and emoji-powered clarity! 📊🤖

---

## 1. Problem Setup 🎯

- **Input Features**  
  $$ \mathbf{x} = [x_1, x_2, ..., x_n] $$

- **Target Label**  
  $$ y \in \{0,1\} $$  
  (e.g., spam vs. not spam)

---

## 2. Logistic Model 🔍

- **Linear Combination**  
  $$ z = \mathbf{w} \cdot \mathbf{x} + b $$

- **Sigmoid Activation**  
  $$ \hat{y} = \frac{1}{1 + e^{-z}} $$

---

## 3. Prediction Rule 🤖

- If $$ \hat{y} \geq 0.5 $$ → predict **class 1**  
- Else → predict **class 0**

---

## 4. Loss Function 📉

**Binary Cross-Entropy**  
$$ L = - \left[ y \log(\hat{y}) + (1 - y) \log(1 - \hat{y}) \right] $$

---

## 5. Gradients 🔁

- Weight Gradient  
  $$ \frac{\partial L}{\partial w_j} = (\hat{y}_i - y_i) x_{ij} $$

- Bias Gradient  
  $$ \frac{\partial L}{\partial b} = \hat{y}_i - y_i $$

---

## 6. What is SGD? ⚡

Unlike **batch gradient descent**, which uses the entire dataset, **SGD** updates parameters after each training example.

✨ Benefits:
- Faster updates 🏃‍♂️  
- Escapes local minima 🚀  
- Efficient with large data 📊

---

## 7. Update Rules 💡

- Weight Update  
  $$ w_j := w_j - \eta \cdot (\hat{y}_i - y_i) \cdot x_{ij} $$

- Bias Update  
  $$ b := b - \eta \cdot (\hat{y}_i - y_i) $$

Where $$ \eta $$ = learning rate 🎚️

---

## 8. Example Walkthrough 🧑‍🏫

| Parameter         | Value             |
|------------------|-------------------|
| $$ \mathbf{x} $$ | $$ [2, 3] $$       |
| $$ y $$          | $$ 1 $$           |
| $$ \mathbf{w} $$ | $$ [0.1, -0.2] $$  |
| $$ b $$          | $$ 0.05 $$        |
| $$ \eta $$       | $$ 0.1 $$         |

**Step-by-step:**
- $$ z = 0.1 \cdot 2 + (-0.2) \cdot 3 + 0.05 = -0.35 $$
- $$ \hat{y} = \frac{1}{1 + e^{0.35}} \approx 0.413 $$
- $$ \hat{y} - y = -0.587 $$
- Update:
  - $$ w_1 = 0.2174 $$
  - $$ w_2 = -0.0239 $$
  - $$ b = 0.1087 $$

---

## 9. Training Loop 🔁

- Repeat over dataset  
- Shuffle each epoch 🔀  
- Iterate until convergence 📈

---

## 10. Summary Table 📚

| Concept                   | Formula                              | Emoji |
|---------------------------|---------------------------------------|-------|
| Linear Combination        | $$ z = \mathbf{w} \cdot \mathbf{x} + b $$ | ⚖️   |
| Sigmoid Activation        | $$ \frac{1}{1 + e^{-z}} $$              | 🔄   |
| Binary Cross-Entropy      | $$ -[y \log(\hat{y}) + (1-y) \log(1-\hat{y})] $$ | 📉 |
| Weight Gradient           | $$ (\hat{y} - y) x_j $$                 | 📏   |
| Bias Gradient             | $$ \hat{y} - y $$                      | 📐   |
| Weight Update (SGD)       | $$ w_j := w_j - \eta (\hat{y} - y) x_j $$ | ⚡   |
| Bias Update (SGD)         | $$ b := b - \eta (\hat{y} - y) $$      | ⚡   |
| Learning Rate             | $$ \eta $$ – step size                 | 🎚️  |

---

