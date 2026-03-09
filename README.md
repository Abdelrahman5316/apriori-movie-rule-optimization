# Apriori Association Rule Mining with Parameter Optimization

This project implements **association rule mining using the Apriori algorithm** and focuses strongly on **optimizing the algorithm’s parameters** to discover meaningful patterns in movie preferences. The experiments are conducted using the MovieLens dataset and the results are analyzed across different demographic groups.

The main analysis is implemented in:

`apriori.ipynb`

The project emphasizes **automatic optimization of Apriori parameters** to improve rule quality and computational efficiency.

---

# Project Objectives

The main objectives of this project are:

- Implement the **Apriori algorithm** for frequent itemset mining.
- Generate **association rules** between movies.
- Automatically **optimize the parameters of the Apriori algorithm**.
- Compare optimization methods.
- Analyze rule patterns across **demographic groups**.
- Produce **interpretable insights for designers and marketers**.

---

# Why Optimization is Important

The Apriori algorithm relies heavily on two parameters:
```bash
Smin – Minimum Support
Cmin – Minimum Confidence
```

These parameters strongly influence:

- The **number of frequent itemsets**
- The **number of generated rules**
- The **quality of discovered patterns**
- The **runtime of the algorithm**

If the parameters are poorly chosen:

- Support too high → almost no rules are discovered
- Support too low → combinatorial explosion of itemsets
- Confidence too high → only trivial rules appear
- Confidence too low → too many weak rules appear

This project therefore introduces **optimization algorithms to automatically find effective parameter values**.

---

# Optimization Strategies Implemented

Two optimization strategies are implemented.

## 1. Bayesian Optimization

Bayesian optimization searches the parameter space efficiently using probabilistic modeling.

The optimizer iteratively:

1. Evaluates parameter combinations  
2. Builds a probabilistic model of the objective function  
3. Selects promising parameters for the next evaluation  

This method is implemented using **Optuna**.

### Advantages

- Efficient exploration of the search space  
- Requires fewer evaluations  
- Converges quickly to good parameter values  

---

## 2. Genetic Algorithm Optimization

A **Genetic Algorithm (GA)** is also implemented to explore the parameter space.

The GA simulates natural evolution:

1. **Population initialization**  
   Random parameter pairs `(Smin, Cmin)`

2. **Fitness evaluation**  
   Each candidate runs Apriori and generates rules. A score is computed based on rule quality.

3. **Selection**  
   Higher-scoring candidates are more likely to survive.

4. **Crossover**  
   Two parameter sets combine to produce new candidates.

5. **Mutation**  
   Small random changes allow exploration of new solutions.

6. **Elitism**  
   The best candidates are preserved across generations.

### Advantages

- Good exploration of complex search spaces  
- Avoids getting stuck in local optima  
- Suitable for irregular objective functions  

---

# Optimization Objective

Each parameter combination is evaluated by running Apriori and generating rules.  
The optimizer scores candidates based on:

- number of valid rules  
- rule lift  
- rule diversity  
- constraints on rule counts  

The goal is to find parameter values that generate **meaningful, interpretable association rules**.

---

# Optimization Workflow
```bash
Initialize parameters
↓
Run Apriori with candidate parameters
↓
Generate association rules
↓
Evaluate rule quality
↓
Update optimization model
↓
Search better parameters
```

The best parameters discovered are then used for the final rule mining stage.

---

# Demographic Analysis

After optimization, Apriori is applied separately to demographic groups using `users.dat`.

Groups analyzed include:

- Female users  
- Male users  
- Students  
- Non-students  

Rules are visualized and compared using:

- Support  
- Confidence  
- Lift  

This allows identification of **differences in viewing patterns across audiences**.

---

# Visualization

Scatter plots are used to analyze rule characteristics:

- **X-axis:** Confidence  
- **Y-axis:** Support  
- **Color:** Lift  

These visualizations highlight:

- strong rules  
- frequent viewing patterns  
- niche associations  

---

# Project Structure
```bash
project/
│
├─ apriori.ipynb # main notebook
├─ data/
│ ├─ movies.dat
│ ├─ ratings.dat
│ └─ users.dat
└─ README.md
```

Support caching significantly **improves optimization speed**, since Apriori repeatedly evaluates similar itemsets during optimization.

---

# Requirements

Typical Python libraries used:
```bash
pandas
numpy
matplotlib
seaborn
optuna
pickle
```

Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn optuna
```

---

# Running the Project

1. Place the dataset files in the `data/` folder.  
2. Open the notebook:
```bash
apriori.ipynb
```

3. Run all cells to:

- preprocess the data  
- run Apriori  
- optimize parameters  
- generate association rules  
- compare demographic patterns  

---

# Applications

The insights from this project can support:

- recommendation system design  
- personalized content discovery  
- audience segmentation  
- targeted marketing strategies  

By combining **Apriori mining with parameter optimization**, the project demonstrates how data mining techniques can generate actionable insights for product design and marketing.

