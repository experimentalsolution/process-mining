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

The dataset contains dummy HR onboarding events with fields including:

- `Employee_ID` — unique claim identifier  
- `Activity` — process step  
- `timestamp` — event time  


These were mapped to PM4Py event-log fields:
Employee_ID is mapped to case:concept:name
Activity is mapped to concept:name
timestamp is mapped to time:timestamp


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

df = pd.read_csv('HR_Onboarding.csv')
```


##  Convert DataFrame → PM4Py Event Log

Convert your cleaned DataFrame into a PM4Py event log.
```
df = df.rename(columns={
    "Employee_ID": "case:concept:name",
    "Activity": "concept:name",
    "Timestamp": "time:timestamp"
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

<img width="1435" height="126" alt="Screenshot 2025-11-17 at 5 27 36 PM" src="https://github.com/user-attachments/assets/eae414c4-de4c-412f-8af8-ac69dbe6992e" />

---

## Frequency-Based DFG

```
from pm4py.algo.discovery.dfg import algorithm as dfg_discovery
from pm4py.visualization.dfg import visualizer as dfg_visualization

dfg_freq = dfg_discovery.apply(log, variant=dfg_discovery.Variants.FREQUENCY)
gviz_freq = dfg_visualization.apply(dfg_freq, log=log, variant=dfg_visualization.Variants.FREQUENCY)
dfg_visualization.view(gviz_freq)
```


<img width="1435" height="126" alt="Screenshot 2025-11-17 at 5 27 36 PM" src="https://github.com/user-attachments/assets/bb915922-5455-4b0d-9e10-5bbd5a6d2e1b" />

## Performance-Based DFG

```
dfg_perf = dfg_discovery.apply(log, variant=dfg_discovery.Variants.PERFORMANCE)
gviz_perf = dfg_visualization.apply(dfg_perf, log=log, variant=dfg_visualization.Variants.PERFORMANCE)
dfg_visualization.view(gviz_perf)
```
<img width="1438" height="93" alt="Screenshot 2025-11-17 at 5 29 42 PM" src="https://github.com/user-attachments/assets/d7b65528-6c99-4b79-8906-837f1ebbebff" />

# Repository Structure


| `mining.ipynb` is  Main Google Colab notebook |
| `HR_Onboarding.csv` is Input event log dataset |
| `dfg_frequency.png`  is Frequency DFG image |
| `dfg_performance.png` is Performance DFG image |
| `README.md` is Project documentation |

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


The HR Onboarding  dataset contains:

- Employee_ID 
- Activities  
- Timestamps   

These are converted into PM4Py’s event log format during preprocessing.

---

# References

- PM4Py Documentation

  # Author Satish Gupta

This project was created as part of a hands-on learning exercise in **Process Mining with Python & PM4Py**.
[Check project ](https://colab.research.google.com/github/experimentalsolution/process-mining/blob/main/mining.ipynb)


```python
!pip install pm4py
