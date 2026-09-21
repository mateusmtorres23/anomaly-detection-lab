# Server CPU Anomaly Detection

## Overview
This project explores time series anomaly detection on server CPU utilization metrics using both traditional statistical methods and Machine Learning (Isolation Forest). Developed for purely educational purposes, the objective is to analyze historical monitoring data from cloud infrastructure to identify atypical behavioral patterns that warrant further operational investigation.

> **Scope Note**: This project focuses strictly on detecting abnormal utilization patterns. It does not attempt to diagnose root causes (e.g., hardware faults, application bugs, or security incidents).

---

## Central Research Question
> *Can a Machine Learning model effectively identify anomalous server CPU behavior using only its historical utilization logs?*

---

## Dataset & Benchmark Details
The dataset is retrieved from the **Numenta Anomaly Benchmark (NAB)** repository, a standard benchmark for evaluating time series anomaly detection algorithms.

* **Source File**: `realAWSCloudwatch/ec2_cpu_utilization_24ae8d.csv`
* **Data Origin**: Real Amazon EC2 instance CPU metrics collected via AWS CloudWatch.
* **Total Observations**: 4,032 records (representing exactly 14 consecutive days of monitoring).
* **Sampling Interval**: 5 minutes.
* **Features**:
  * `timestamp`: Date and time of measurement (`YYYY-MM-DD HH:MM:SS`).
  * `value`: Server CPU utilization percentage.
* **Ground Truth Annotations**: 2 labeled anomaly events provided in `combined_labels.json`.

---

## Project Objectives

1. **Exploratory Data Analysis (EDA)**: Analyze time series trends, daily/weekly cycles, and value distributions across the 14-day window.
2. **Data Cleaning & Preprocessing**: Verify temporal regularity, handle missing values, and structure timestamps for time series analysis.
3. **Feature Engineering**: Extract rolling statistics (moving average, rolling standard deviation), time-based features (hour of day, day of week), and lag differences to capture recent temporal behavior.
4. **Baseline Statistical Detection**: Implement a threshold-based statistical method (e.g., Z-Score / IQR) as a benchmark.
5. **Machine Learning Model**: Train an **Isolation Forest** model utilizing the engineered temporal features.
6. **Evaluation**: Benchmark predictions against the ground truth labels annotated in the NAB dataset.
7. **Comparative Analysis**: Discuss trade-offs, false positives, false negatives, and model behavior under severe class imbalance.

---

## Evaluation Challenges & Limitations
Because the dataset contains only **2 annotated anomaly events** out of 4,032 points (~0.05% anomaly rate), performance metrics (such as Precision, Recall, and F1-Score) must be interpreted with extreme caution:
* Identifying or missing a single anomaly event significantly skews overall evaluation scores.
* Rather than maximizing raw benchmark scores, the project prioritizes discussing model limitations, trade-offs in operational alerting, and evaluation methods on highly imbalanced data.
