# 📊 Process Mining with PM4Py  
A Hands-On Tutorial Using Real Insurance Claims Event Log Data

This project demonstrates how to perform **process discovery**, **bottleneck detection**, and **visual analysis** using the **PM4Py** process mining library in Python.  
The notebook processes an insurance claims event log, converts it into an event log structure, and generates multiple Directly-Follows Graphs (DFGs).

---

## 🚀 Project Overview

This notebook covers:

- Loading and preparing a real event log dataset (insurance claims)
- Converting a CSV file into a PM4Py-compatible event log
- Discovering the process model using:
  - **Standard DFG**
  - **Frequency-based DFG**
  - **Performance-based DFG**
- Visualizing each discovered model
- Understanding process flow and identifying inefficiencies

---

## 📂 Dataset Description

The dataset contains real (simulated) insurance claims events with fields including:

- `case_id` — unique claim identifier  
- `activity_name` — process step  
- `timestamp` — event time  
- Claimant and adjuster information  
- Claim amount, policy type, accident type, etc.

These were mapped to PM4Py event-log fields:

| Original Column | PM4Py Required Column |
|------------------|------------------------|
| `case_id`        | `case:concept:name`    |
| `activity_name`  | `concept:name`         |
| `timestamp`      | `time:timestamp`       |

---

## 🔧 Technologies Used

- **Python 3**
- **PM4Py** – Process Mining for Python  
- **Pandas** – Data handling  
- **Google Colab** – Runtime environment  

---

## 📥 Installation

Inside the notebook, PM4Py is installed with:


##  Import Libraries & Load Dataset

Load your CSV event log and inspect the initial data.


##  Convert DataFrame → PM4Py Event Log

Convert your cleaned DataFrame into a PM4Py event log.

## Discover Standard Directly-Follows Graph (DFG)

Generate and visualize the initial DFG.

### Standard DFG Visualization  

image
---

## Frequency-Based DFG

Generate a DFG showing how often each transition occurs.


# Repository Structure

| File | Description |
|------|-------------|
| `mining.ipynb` | Main Google Colab notebook |
| `Insurance_claims_event_log.csv` | Input event log dataset |
| `dfg_frequency.png` | *(optional)* Frequency DFG image |
| `dfg_performance.png` | *(optional)* Performance DFG image |
| `README.md` | Project documentation |

# 🎯 Purpose of the Notebook

This notebook helps you:

- Understand event logs and their structure  
- Transform raw process data into PM4Py format  
- Discover process models using DFGs  
- Analyze bottlenecks using performance metrics  
- Build a reproducible process mining workflow  

---

# How to Use This Notebook

1. Open the notebook in **Google Colab**  
2. Upload the event log CSV  
3. Run all cells sequentially  
4. Visualizations (DFGs) will appear automatically


The insurance claims dataset contains:

- Case IDs  
- Activities  
- Timestamps  
- Claimant / agent / adjuster info  
- Policy and accident details  

These are converted into PM4Py’s event log format during preprocessing.

---

# References

- PM4Py Documentation

  # 🙌 Author Satish Gupta

This project was created as part of a hands-on learning exercise in **Process Mining with Python & PM4Py**.
Check project https://colab.research.google.com/github/experimentalsolution/process-mining/blob/main/mining.ipynb


```python
!pip install pm4py
