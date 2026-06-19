# **CVRP Metaheuristics: GA, ACO, and GA + K-means**

This repository contains the implementation and analysis of several metaheuristic algorithms applied to the **Capacitated Vehicle Routing Problem (CVRP)**.  
The work is based on the project documented in `Report_ACO_GA.pdf`.

The original objective was to build a hybrid GA–ACO algorithm.  
Due to time constraints, the hybrid version was not completed; instead, the project includes **independent implementations** and a full comparative study.


# **Problem Description**

The project focuses on solving the **Capacitated Vehicle Routing Problem (CVRP)** using:

- **Genetic Algorithm (GA)**  
- **Ant Colony Optimization (ACO)**  
- **GA with K-means initialization**  

The models aim to minimize total travel cost while respecting vehicle capacity constraints and ensuring that each customer is served exactly once.

The full mathematical formulation is included in the project report (`Report_ACO_GA.pdf`).

---

# **Included Algorithms**

### **1. Genetic Algorithm (GA)**  
Located in: `src/GA.ipynb`

Features:
- Route-based chromosome representation  
- Tournament selection  
- Elitism  
- Crossover and mutation  
- Optional K-means clustering for structured initialization  

---

### **2. Ant Colony Optimization (ACO)**  
Located in: `src/app_ACO.py`

Features:
- Pheromone matrix and heuristic distance (η = 1/d)  
- Probabilistic transition rule with α, β weights  
- Exploration vs exploitation parameter q₀  
- Pheromone evaporation and update rule  
- Dynamic route construction with capacity handling  

---

# **Interactive ACO Application**

The file `app_ACO.py` includes an **interactive interface** that allows users to:

- Upload their own dataset (Excel or CSV)  
- Visualize nodes on the map  
- Modify ACO parameters  
- Run the algorithm with real-time updates  
- Experiment with route construction and convergence behaviour  

No code changes are required.  
Just run the script and upload your file.

---

# 📊 **Using Your Own Data**

You can run both algorithms with custom coordinates.  
Your input file must contain **exactly two columns** in this order:

| longitud | latitud |
|----------|---------|
| -100.41  | 20.65   |
| -100.38  | 20.67   |
| ...      | ...     |

The algorithm also accepts English column names:

- **latitude, longitude**
- **latitud, longitud**

> **No extra columns.  
> Only coordinates.**

An example file is included in the repository.

---

#  **How to Use the ACO App With Your File**

1. Run `app_ACO.py`.  
2. Use the upload button inside the interface.  
3. Select your `.xlsx`.  
4. Adjust ACO parameters as desired.  
5. View the generated routes, parameters, and results in real time.

The ACO app automatically detects the required columns.

---

# ⚙️ **How to Run the GA With Your File**

Inside `src/GA.ipynb`, you must load your dataset **before** running the Genetic Algorithm.  
Use the following cell to load your Excel or CSV file:

```python
import pandas as pd

# Path to your file inside the /data/ folder
path = "../data/example_.xlsx"   # Replace with your own filename if needed

# Load automatically depending on file type
if path.endswith(".xlsx"):
    df = pd.read_excel(path)
else:
    df = pd.read_csv(path)

df.head()
