# 🚀 Logistic Regression using Stochastic Gradient Descent (SGD)

A clear and engaging explanation of how logistic regression works—optimized via **SGD**, with math, intuition, and emoji-powered clarity! 📊🤖

---

## 1. Problem Setup 🎯

- **Input Features**  
  `x = [x₁, x₂, ..., xₙ]`

- **Target Label**  
  `y ∈ {0,1}`  
  (e.g., spam vs. not spam)

---

## 2. Logistic Model 🔍

- **Linear Combination**  
  `z = w · x + b`

- **Sigmoid Activation**  
  `ŷ = 1 / (1 + exp(-z))`

---

## 3. Prediction Rule 🤖

- If `ŷ ≥ 0.5` → predict **class 1**  
- Else → predict **class 0**

---

## 4. Loss Function 📉

**Binary Cross-Entropy**  
`L = - [ y log(ŷ) + (1 - y) log(1 - ŷ) ]`

---

## 5. Gradients 🔁

- Weight Gradient  
  `∂L/∂wⱼ = (ŷ - y) · xⱼ`

- Bias Gradient  
  `∂L/∂b = ŷ - y`

---

## 6. What is SGD? ⚡

Unlike batch gradient descent, which uses the entire dataset, **SGD** updates parameters after each training example.

✨ Benefits:
- Faster updates 🏃‍♂️  
- Escapes local minima 🚀  
- Efficient with large data 📊

---

## 7. Update Rules 💡

- Weight Update  
  `wⱼ := wⱼ - η · (ŷ - y) · xⱼ`

- Bias Update  
  `b := b - η · (ŷ - y)`

Where `η` = learning rate 🎚️

---

## 8. Example Walkthrough 🧑‍🏫

| Parameter   | Value       |
|------------|-------------|
| `x`        | `[2, 3]`     |
| `y`        | `1`         |
| `w`        | `[0.1, -0.2]`|
| `b`        | `0.05`      |
| `η`        | `0.1`       |

**Step-by-step:**
- `z = 0.1·2 + (-0.2)·3 + 0.05 = -0.35`
- `ŷ ≈ 1 / (1 + exp(0.35)) ≈ 0.413`
- Error: `ŷ - y = -0.587`
- Update:
  - `w₁ = 0.1 + 0.1174 = 0.2174`
  - `w₂ = -0.2 + 0.1761 = -0.0239`
  - `b = 0.05 + 0.0587 = 0.1087`

---

## 9. Training Loop 🔁

- Repeat over dataset  
- Shuffle each epoch 🔀  
- Iterate until convergence 📈

---

## 10. Summary Table 📚

| Concept             | Formula                          | Emoji |
|---------------------|----------------------------------|--------|
| Linear Combination  | `z = w · x + b`                  | ⚖️     |
| Sigmoid Activation  | `σ(z) = 1 / (1 + exp(-z))`       | 🔄     |
| Cross-Entropy Loss  | `L = -[ y log(ŷ) + (1-y) log(1-ŷ) ]` | 📉 |
| Weight Gradient     | `(ŷ - y) · xⱼ`                   | 📏     |
| Bias Gradient       | `ŷ - y`                          | 📐     |
| SGD Weight Update   | `wⱼ := wⱼ - η (ŷ - y) xⱼ`         | ⚡     |
| SGD Bias Update     | `b := b - η (ŷ - y)`             | ⚡     |
| Learning Rate       | `η` – step size                  | 🎚️    |
