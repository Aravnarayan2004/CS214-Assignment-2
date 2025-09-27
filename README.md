# 🧭 CS214 Assignment 2 – Traveling Salesman Problem (TSP): DP vs GA

**Course:** CS214 – Design & Analysis of Algorithms  
**Semester:** 2, 2025  

------------------------
##  Group Members
Arav Narayan - S11230967

Krishnil Prasad  - S11022399 


##  1.0 Project Overview

This project implements and compares two approaches to solving the **Traveling Salesman Problem (TSP):**

-  **Dynamic Programming (DP):** Uses the Held–Karp algorithm to find the **optimal solution**.
-  **Genetic Algorithm (GA):** Uses evolutionary search techniques to find **near-optimal solutions** efficiently.

The project analyzes the trade-offs between **deterministic** and **stochastic** approaches by:
- Running empirical tests across multiple runs
- Generating real-time graph visualizations
- Comparing metrics such as fitness, NFC, time, and success rate

---

## 🛠️ 2.0 Instructions for Running the Program

1. Clone or download the project and open it as a **Maven project** in IntelliJ or Eclipse.
2. Ensure the following dependencies are available:
   - [Apache Commons CSV](https://commons.apache.org/proper/commons-csv/)
   - [JFreeChart](https://www.jfree.org/jfreechart/)
3. Place your `.tsp` or `.atsp` dataset files into:

##  3.0 Implementation Details

###  Dynamic Programming (DP)

- Implements the **Held–Karp algorithm** with time complexity `O(n² * 2ⁿ)`.
- Guarantees the **optimal solution** but is feasible only for problem sizes `n ≤ 22` (configurable via `DP_MAX`).
- Provides key metrics:
  - `bestCost` – optimal tour cost
  - `layerBest` – best partial solution per subset layer (used for visualization)

###  Genetic Algorithm (GA)

- Uses evolutionary techniques to find near-optimal solutions efficiently.
- **Configurable parameters:**
  - `population` – population size (default: 120)
  - `generations` – number of generations (default: 800)
  - `mutation` – mutation rate (default: 0.25)
  - `inversion` – enable/disable inversion mutation
  - `earlyStop` – enable early stopping based on stagnation threshold
- **Performance metrics collected:**
  - `bestCost` – best solution cost per run
  - `nfc` – total number of function calls
  - `nfcAtBest` – function calls at which best solution first appeared
  - `genAtBest` – generation where best solution was found
  - `improvements` – number of solution improvements across generations

###  Visualization and Charts

- Real-time graph generation is implemented in `tsp.Chart`.
- Three main graph types are generated automatically:
  1. **GA Only – DP vs GA** – compares GA’s convergence trend with DP’s constant optimal solution.
  2. **DP Only (Layer Best) – DP vs GA** – shows DP’s improving partial solutions layer by layer against GA.
  3. **Combined – DP vs GA** – provides a comprehensive comparison of both algorithms.
- **Axes:**
  - **X-axis:** Number of Function Calls (NFC) or Generations
  - **Y-axis:** Fitness (Total Tour Distance)

###  Input & Output

- **Input:** `.tsp` / `.atsp` problem files located in `src/main/resources/data/`
- **Output:** Results and visualizations stored in the `output/` directory:
  - `summary.csv` – aggregated statistics per problem
  - `run_details.csv` – detailed data for each GA run
  - `plot_ga.png`, `plot_dp.png`, `plot_combined.png` – visual performance graphs


