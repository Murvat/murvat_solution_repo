# Problem 1

# 📊 Exploring the Central Limit Theorem (CLT) Through Simulations

## 🎯 Motivation

The **Central Limit Theorem (CLT)** states that the sampling distribution of the **sample mean** approaches a **normal distribution** as the sample size increases, **regardless of the population's original distribution**. This project demonstrates this concept using simulations on various population types.

---

## 1️⃣ Simulating Sampling Distributions

We explore the CLT using the following **population distributions**:

- **Uniform Distribution**
- **Exponential Distribution**
- **Binomial Distribution**

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

def generate_population(distribution, size=100000):
    if distribution == 'uniform':
        return np.random.uniform(0, 1, size)
    elif distribution == 'exponential':
        return np.random.exponential(1.0, size)
    elif distribution == 'binomial':
        return np.random.binomial(n=10, p=0.5, size=size)
    else:
        raise ValueError("Unsupported distribution")
```

---

## 2️⃣ Sampling and Visualization

```python
def sample_means(population, sample_size, num_samples):
    return [np.mean(np.random.choice(population, size=sample_size, replace=True)) for _ in range(num_samples)]

def plot_sampling_distribution(population_type, sample_sizes, num_samples=1000):
    population = generate_population(population_type)
    fig, axes = plt.subplots(1, len(sample_sizes), figsize=(5 * len(sample_sizes), 4))
    for i, size in enumerate(sample_sizes):
        means = sample_means(population, size, num_samples)
        sns.histplot(means, kde=True, ax=axes[i], bins=30, color='skyblue')
        axes[i].set_title(f"{population_type.capitalize()} Dist
Sample Size = {size}")
        axes[i].set_xlabel("Sample Mean")
        axes[i].set_ylabel("Frequency")
    plt.tight_layout()
    plt.show()

# Example usage
plot_sampling_distribution("exponential", [5, 10, 30, 50])
```

---

## 3️⃣ Parameter Exploration

### 🔍 Observations

- The **larger** the sample size, the **closer** the sampling distribution resembles a **normal distribution**.
- Populations with **higher variance** lead to **wider** sampling distributions.
- **Convergence is faster** for symmetric distributions (e.g., uniform) than skewed ones (e.g., exponential).

---

## 4️⃣ Practical Applications

- **Quality Control**: Detect defects using averages in manufacturing.
- **Survey Analysis**: Estimate population characteristics with a sample mean.
- **Finance**: Predict stock behavior using expected return from samples.

---

## 📈 Visualization Examples

### Uniform Distribution Example

![Uniform CLT](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7b/CLT_uniform.png/800px-CLT_uniform.png)

### Exponential Distribution Example

![Exponential CLT](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/CLT_exponential.png/800px-CLT_exponential.png)

### Binomial Distribution Example

![Binomial CLT](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4c/CLT_binomial.png/800px-CLT_binomial.png)

---

## 📁 Deliverables

- ✅ Python code for generating populations and simulating sample means.
- ✅ Plots showing convergence to normal distribution.
- ✅ Insights on how distribution shape and sample size affect convergence.

---

## 💡 Hints

- Try additional distributions like **Poisson** or **Gamma** for further insight.
- Use **standardized sample means** to directly compare convergence trends.
- Explore how the **law of large numbers** complements the CLT.

---

## 📚 Resources

- [Central Limit Theorem - Wikipedia](https://en.wikipedia.org/wiki/Central_limit_theorem)
- [Visual Explanation of CLT (YouTube)](https://www.youtube.com/watch?v=3e6YcnVZf-U)

---
