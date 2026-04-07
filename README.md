# 🚌 Discrete Event Simulation — Estació del Nord (Barcelona)
> Passenger Queue Analysis and Bus Frequency Optimization using FlexSim
> Master's Degree in Industry 4.0 · Universitat Politècnica de Catalunya (UPC)

---

## 📌 Project Overview
This project applies Discrete Event Simulation (DES) to model passenger flow 
and bus boarding operations at Estació del Nord — Barcelona's main intercity 
bus terminal, serving over 3.2 million passengers per year.

The simulation evaluates how bus service frequency affects passenger queue 
formation, wait times, and unmet demand under peak and off-peak conditions, 
with the goal of identifying the optimal frequency policy for a defined 
service level target.

## 🎯 Business Problem
As passenger volumes at Estació del Nord grew from ~1 million to ~3.2 million 
travelers, congestion at boarding platforms increased significantly. 
This study addresses the question: what bus service frequency achieves an 
average passenger wait time of ≤ 20 minutes, while minimizing operational 
overcapacity?

## 🛠️ Tools & Technologies
- **FlexSim** — Discrete Event Simulation (DES), General Process Flow, 
  Global List, FlexScript, Experimenter
- **Python / Excel** — Arrival table construction, demand profiling
- **Methodology** — Queuing theory, experimental design, 
  linear interpolation for adaptive frequency policy

## 📊 Key Results

| Scenario | Demand | Frequency | Avg. Wait Time | Outcome |
|---|---|---|---|---|
| Peak hour — optimal | 2 pax/min | **8 min** | ~12 min | ✅ Target met |
| Peak hour — saturated | 2 pax/min | 10 min | >200 min | ❌ System collapse |
| Valley hour — optimal | 0.2 pax/min | **13 min** | ~20 min | ✅ Target met |
| Variable frequency (full day) | Adaptive | Adaptive | **~10 min avg** | ✅ Best overall |

**Derived frequency policy formula:**
Interval (s) = 813.3 − 166.6 × arrival_rate (pax/min)

This formula allows any operator to calculate the recommended bus interval 
for any intermediate demand level, balancing service quality and efficiency.

## 🏗️ System Architecture
- 3 bus lines (Barcelona–Berga, Line e12, Line 602), each with a dedicated 
  boarding point
- Entities: passengers and buses generated via deterministic Excel 
  Arrival Tables
- Global List for real-time passenger-bus matching (filtered by route type)
- Custom FlexScript for dispatch logic and left-behind passenger tracking
- Statistics Collectors + live Dashboard for KPI monitoring
- FlexSim Experimenter for sensitivity analysis (3 frequency scenarios)

## 📂 Repository Structure
/model        → FlexSim model file (.fsm)
/data         → Excel arrival tables (passengers and buses by scenario)
/results      → Output charts and KPI summaries per scenario
/docs         → Full academic report (Memoria Final)
/images       → FlexSim 3D simulation screenshots

## 📚 Methodology Summary
Passenger demand was modeled using two representative levels: 
peak (2 pax/min) and valley (0.2 pax/min), discretized into 
10-minute intervals over a 24-hour horizon (2,808 total passengers/day, 
3 lines). Eight experimental scenarios were evaluated. The optimal 
frequencies identified (8 min peak, 13 min valley) were combined via 
linear interpolation to produce a variable frequency policy validated 
against all defined KPIs.
 
