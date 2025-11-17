#  Process Mining with PM4Py  
A Hands-On Tutorial Using Real Insurance Claims Event Log Data

This project demonstrates how to perform **process discovery**, **bottleneck detection**, and **visual analysis** using the **PM4Py** process mining library in Python.  
The notebook processes an insurance claims event log, converts it into an event log structure, and generates multiple Directly-Follows Graphs (DFGs).

---

## Project Overview

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

##  Dataset Description

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

##  Technologies Used

- **Python 3**
- **PM4Py** – Process Mining for Python  
- **Pandas** – Data handling  
- **Google Colab** – Runtime environment  

---

## Installation

Inside the notebook, PM4Py is installed with:

```
!pip install pm4py
```


##  Import Libraries & Load Dataset

Load your CSV event log and inspect the initial data.

```
import pm4py

import pandas as pd

df = pd.read_csv('Insurance_claims_event_log.csv')
```


##  Convert DataFrame → PM4Py Event Log

Convert your cleaned DataFrame into a PM4Py event log.
```
df = df.rename(columns={
    "case_id": "case:concept:name",
    "activity_name": "concept:name",
    "timestamp": "time:timestamp"
})
df["time:timestamp"] = pd.to_datetime(df["time:timestamp"])
```

## Discover Standard Directly-Follows Graph (DFG)

Generate and visualize the initial DFG.

```
import pm4py
from pm4py.algo.discovery.dfg import algorithm as dfg_discovery
from pm4py.visualization.dfg import visualizer as dfg_visualization
log = pm4py.convert_to_event_log(df)
dfg = dfg_discovery.apply(log)
```

### Standard DFG Visualization  

```
gviz = dfg_visualization.apply(dfg, log=log)
dfg_visualization.view(gviz)
```

It will display image 
---

## Frequency-Based DFG

```
from pm4py.algo.discovery.dfg import algorithm as dfg_discovery
from pm4py.visualization.dfg import visualizer as dfg_visualization

dfg_freq = dfg_discovery.apply(log, variant=dfg_discovery.Variants.FREQUENCY)
gviz_freq = dfg_visualization.apply(dfg_freq, log=log, variant=dfg_visualization.Variants.FREQUENCY)
dfg_visualization.view(gviz_freq)
```
## Performance-Based DFG

```
dfg_perf = dfg_discovery.apply(log, variant=dfg_discovery.Variants.PERFORMANCE)
gviz_perf = dfg_visualization.apply(dfg_perf, log=log, variant=dfg_visualization.Variants.PERFORMANCE)
dfg_visualization.view(gviz_perf)
```

# Repository Structure

| File | Description |
|------|-------------|
| `mining.ipynb` | Main Google Colab notebook |
| `Insurance_claims_event_log.csv` | Input event log dataset |
| `dfg_frequency.png` | *(optional)* Frequency DFG image |
| `dfg_performance.png` | *(optional)* Performance DFG image |
| `README.md` | Project documentation |

#  Purpose of the Notebook

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

  # Author Satish Gupta

This project was created as part of a hands-on learning exercise in **Process Mining with Python & PM4Py**.
[Check project ](https://colab.research.google.com/github/experimentalsolution/process-mining/blob/main/mining.ipynb)


```python
!pip install pm4py
