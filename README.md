# CSCE-676-project

# Tackling the Yelp Cold Start Problem

https://www.youtube.com/watch?v=17tlF5lbhCw

## 1. Project Overview
This project tackles the "Cold Start" problem within recommender systems using the Yelp 2018 Academic Dataset. Recommender systems traditionally rely on deep historical user profiles (dense matrices) to generate cross-domain suggestions. However, the vast majority of Yelp users have left two or fewer reviews. This project demonstrates that when direct transaction history is mathematically insufficient, structural network connectivity can successfully replace it. While traditional course methods like PageRank identify global authorities and FP-Growth gets trapped by semantic redundancies, Non-parametric Graph Convolution bypasses text entirely. It utilizes pure mathematical topology to help inactive users.

The main deliverable is main_notebook.ipynb.

## 2. Key Research Questions Answered
* **RQ1 (Graph Centrality):** Does raw business popularity (review count) perfectly align with structural network authority, or do hidden hubs exist within the Yelp ecosystem?
* **RQ2 (Itemset Mining):** Can traditional Association Rule Mining (FP-Growth) generate reliable cross-domain recommendations?
* **RQ3 (External Technique):** Can Non-parametric Graph Convolution bypass the 99.99% sparsity of "Cold Start" users to generate accurate recommendations?

## 3. Dataset & Preprocessing
**Data Source:** Yelp Academic Dataset (2018)
To optimize memory and execution time, the raw JSON files were parsed line-by-line to extract structural data while discarding heavy textual review columns. The dataset was segmented to explicitly identify "Cold Start" users (<= 2 reviews) versus "Power Users" (>= 10 reviews). Business categories were formatted into standard lists to allow for itemset processing.

## 4. Key dependencies and versions
* Python 3.9+
* Pandas 2.2.0
* Numpy 2.0.2
* Matplotlib 3.10.0
* Seaborn 0.13.2
* Mlxtend 0.23.4
* Scipy 1.16.3

## 5. Installation & Usage
1. Clone the repository.
2. Install dependencies: `pip install -r requirements.txt`
3. Download the Yelp 2018 Academic Dataset JSON files from https://www.kaggle.com/datasets/yelp-dataset/yelp-dataset.
4. Save the dataset into your google drive.
4. Run `main_notebook.ipynb`.

## 6. Repo Structure
```text
CSCE-676-project/
│
├── README.md                 # Project overview, results, and setup instructions
├── main_notebook.ipynb       # The final, fully optimized code and evaluation
├── requirements.txt          # Python package dependencies needed to run the code
│
└── checkpoints/              # Historic project milestones
    ├── checkpoint_1.ipynb    # Phase 1: EDA and Preprocessing
    └── checkpoint_2.ipynb    # Phase 2: Baseline models (PageRank & FP-Growth)
```

## 7. Results Summary
Traditional recommender systems completely collapse on users with 2 or fewer reviews due to 99.99% data sparsity. By bypassing traditional collaborative filtering and utilizing 2-hop network topology, the Graph Convolution model successfully generated accurate cross-domain recommendations, outperforming the mathematical baseline of random chance (~0.03%) by a factor of 100x.
