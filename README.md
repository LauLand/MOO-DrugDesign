# MOO-DrugDesign
Jupyter Notebooks detailing the framework from our paper. This step-by-step guide covers the entire process, from ChEMBL data preparation to the analysis of the compounds obtained from the generative AI.

# Pareto-Optimized Reinforcement Learning for Multi-Objective Drug Design

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


### Requirements
* Python 3.8+
* Jupyter Notebook or JupyterLab
* Key libraries: `pandas`, `numpy`, `rdkit`, `scikit-learn`, `matplotlib`, `seaborn`


## 📁 Project Structure

The repository is organized as follows:
```
├── notebooks/
│   ├── 00_chembl_data_preparation.ipynb
│   ├── 01_kmeans_sampler.ipynb
│   ├── 02_pareto_analysis.ipynb
│   └── 03_downstream_filtering.ipynb
│   
│
├── data/
│   └── (Place your raw input CSV files here)
│
├── results/
│   └── (All outputs like cleaned data, plots, and final candidates will be saved here)
│
└── README.md
```

## 🚀 Workflow: Step-by-Step Usage

The analysis is divided into a series of notebooks that should be run in order. Before running, place your raw data files in the `data/` directory.

### Step 0: `00_chembl_data_preparation.ipynb` (Optional if needed for QSAR ML Classification model building)

**Purpose:** To clean, filter, and standardize a raw dataset from ChEMBL, making it suitable for modeling.
**Instructions:**
1.  Open the notebook.
2.  In the **Configuration** cell, set the path to your raw input file.
3.  Run all cells (`Cell` > `Run All`).
4.  A cleaned CSV file will be saved in the `results/` directory.

### Step 1: `01_kmeans_sampler.ipynb`

**Purpose:** To generate the weight configurations that will guide the generative AI.
**Instructions:**
1.  Open the notebook.
2.  Adjust parameters like `N_OBJECTIVES` and `N_CLUSTERS` in the **Configuration** cell if needed.
3.  Run all cells.
4.  The output `01_weights.csv` will be saved in the `results/` directory.


### Step 2: Run the Generative AI (External Step)

Use the `01_weights.csv` file generated in the previous step to run your multi-objective REINVENT jobs as described in the paper. This step is performed outside of this repository. Ensure all run logs and generated molecules are saved for the next analysis step.

### Step 3: `02_pareto_analysis.ipynb`

**Purpose:** To analyze the results from the generative runs, identify the Pareto front, and calculate performance metrics.
**Instructions:**
1.  Open the notebook.
2.  In the **Configuration** cell, provide the paths to the .csv generated at the end of the REINVENT run.
3.  Run all cells.
4.  Plots comparing Pareto fronts and evaluation metrics will be displayed in the notebook.


### Step 3: `03_downstream_filtering.ipynb`

**Purpose:** To apply final medicinal chemistry and property-based filters to the Pareto-optimal solutions to select the most promising candidates.
**Instructions:**
1.  Open the notebook.
2.  The notebook will automatically use the Pareto front CSV from Step 3. You can adjust the filter thresholds in the **Configuration** cell.
3.  Run all cells.
4.  A CSV file with the final list of candidate molecules will be saved in `results/`.

---

## 📄 Citing This Work

If you use this code in your research, please cite our paper:

```bibtex
@article{Landolfi2025,
  title={Finding Balance: Multi-Objective Optimization in Molecular Generative Modeling},
  author={Landolfi, L. and Janet, JP.},
  journal={Journal Name},
  year={2025},
  volume={X},
  pages={Y-Z}
}
```

## 📜 License

This project is licensed under the MIT License. See the `LICENSE` file for details.
