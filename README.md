# Lung Cancer Prediction using Apache Spark and Hadoop

A scalable machine learning pipeline for lung cancer prediction built with Apache Spark 3.5.5 and Hadoop HDFS, leveraging distributed computing for efficient data processing and model training.


## Overview

Traditional ML approaches for lung cancer prediction suffer from computational inefficiencies and scalability limitations. This project addresses those gaps by integrating Apache Spark for parallel processing and Hadoop HDFS for distributed storage — enabling faster computation and more scalable model training.

Multiple ML models were benchmarked using PySpark MLlib, with MLP achieving the highest accuracy of 99%.


## Tech Stack

| Component | Technology |
|-----------|------------|
| Distributed Computing | Apache Spark 3.5.5 |
| Distributed Storage | Hadoop HDFS |
| ML Framework | PySpark MLlib |
| Data Analysis | Jupyter Notebook |
| Language | Python |


## Cluster Setup

Single-node Spark cluster configured with Master and 2 Worker nodes:

- Spark Master: spark://172.16.72.48:7077
- Workers: 2 alive workers, 4 cores each (8 total), 4.0 GiB memory each
- Total Resources: 8 cores, 8.0 GiB memory
- Connected Jupyter Notebook to Spark for interactive analysis

**Setup Steps:**

1. Install Apache Hadoop for distributed storage (HDFS)
2. Install Apache Spark 3.5.5 for high-speed data processing
3. Configure single-node cluster with Master and Worker nodes on localhost
4. Connect Jupyter Notebook to Spark via PySpark


## Dataset

| Property | Detail |
|----------|--------|
| Source | Kaggle |
| Instances | 310 |
| Features | 16 |
| Target | Lung Cancer (YES/NO) |

Features include: Gender, Age, Smoking, Anxiety, Peer Pressure, Chronic Disease, Fatigue, Allergy, Wheezing, Alcohol, Coughing, Shortness of Breath, Swallowing Difficulty, Chest Pain


## Data Preprocessing

- Missing value check — verified no null values in dataset
- Categorical encoding — converted GENDER (M=0, F=1) and LUNGCANCER (YES=0, NO=1) to numerical values
- Class imbalance handling — applied SMOTE (Synthetic Minority Over-sampling Technique) to generate synthetic minority class samples and prevent biased predictions
- Train-Test Split — 80% training, 20% testing


## Methodology

1. Set up Hadoop and Spark cluster
2. Load dataset from HDFS
3. Data preprocessing — null checks, categorical encoding
4. Handle class imbalance using SMOTE
5. Split data into training and testing sets
6. Train ML models using PySpark MLlib
7. Evaluate and compare model performance


## Model Performance

| Model | Accuracy |
|-------|----------|
| Linear Regression | 93% |
| Logistic Regression | 94% |
| Decision Tree | 94% |
| Gradient Boosting | 95% |
| K-Nearest Neighbors | 95% |
| Random Forest | 96% |
| MLP (Proposed) | 99% |

MLP achieved the best performance, improving over traditional methods by capturing complex non-linear patterns in the data.


## How to Run

**Prerequisites:**
- Apache Hadoop installed
- Apache Spark 3.5.5 installed
- Python 3.x and PySpark
- Jupyter Notebook

**Steps:**

Step 1 — Start Hadoop

    start-dfs.sh
    start-yarn.sh

Step 2 — Start Spark cluster

    $SPARK_HOME/sbin/start-master.sh
    $SPARK_HOME/sbin/start-worker.sh spark://localhost:7077

Step 3 — Launch Jupyter

    jupyter notebook

Then open Lung_Cancer_Prediction.ipynb and run all cells.


## Key Takeaways

- Apache Spark significantly reduces computation time through parallel processing
- SMOTE effectively handles class imbalance without losing meaningful data distribution
- MLP outperformed all traditional ML models with 99% accuracy
- Spark's distributed architecture makes this pipeline scalable to larger medical datasets
