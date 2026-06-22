# Plant-and-Material-Flow-Simulation--SS25-Project

## Project  Description 

Developed a digital production model using Siemens Tecnomatix Plant Simulation. The simulation consisted of conveyors, buffers, AGV transport systems, and production workstations operating under varying conditions. Analyzed operational performance, identified process bottlenecks and evaluated improvements to material flow efficiency and throughput.

## Problem Statement

The project involved the validation and analysis of a production and logistics system for an industrial cooling system manufacturer using discrete-event simulation. The system consisted of three flexible mixed-model production lines, an AGV-based material handling system, conveyor transport systems, and pick-and-place mechanisms for sorting and packaging.

The system was divided into three main areas:

### Production Lines Area
Products were processed through three sequential workstations connected by conveyors before being buffered and collected by AGVs.

### Material Handling and Testing Area
AGVs transported products through Test, Charge, and Control stations for further processing.

### Pick-and-Place and Packaging Area
Products were transferred onto a conveyor, sorted according to product type, buffered, and packaged before leaving the system.

### Objective
The objective was to model the complete material flow, evaluate system performance under different operating conditions, and identify bottlenecks affecting throughput and efficiency.

<img width="1004" height="553" alt="image" src="https://github.com/user-attachments/assets/29b862da-e5b6-43e4-b816-3195c82f0973" />

**System Layout**

## Simulation Model Creation

The simulation model was developed using Siemens Tecnomatix Plant Simulation and consisted of production, transportation, testing, sorting, and packaging processes. Various simulation objects were used to represent material flow, resource allocation, AGV transportation, and system control logic.

### Simulation Objects Used

| Object | Quantity | Purpose |
|----------|----------|----------|
| Sources | 4 | Generated products for the three production lines and AGVs for transportation. |
| Stations | 18 | Represented production and packaging operations with defined processing times and capacities. |
| Conveyors | 10 | Connected production stations, provided temporary buffering, and transported products within the packaging area. |
| AGVs | 2 | Transported products between production, testing, and packaging areas. |
| Sensors | 10 | Controlled material flow, loading, unloading, and AGV transport requests. |
| Tracks | - | Defined AGV movement paths and ensured collision-free transportation. |
| Parallel Stations | 3 | Represented Test, Charge, and Control operations to increase throughput and reduce bottlenecks. |
| Buffers | 13 | Provided temporary storage and reduced process blocking between operations. |
| Drains | 9 | Represented completed and shipped products leaving the system. |
| Pick-and-Place Robots | 2 | Transferred and sorted products within the packaging area. |
| EventController | 1 | Managed simulation execution, timing, and reset operations. |
| DataTables | 12 | Stored product mix data and processing times for each production line. |
| DataQueue | 1 | Managed AGV transport requests and pickup locations. |
| Methods | 11 | Controlled loading, unloading, routing, and decision-making logic. |
| Reset Method | 1 | Cleared transport requests when restarting the simulation. |
| Connectors | - | Defined material flow connections between simulation objects. |
| Displays | 9 | Displayed the number of finished products at the end of the simulation. |

### Model Highlights

- Three production lines produced nine different product types.
- AGVs transported products between production, testing, and packaging areas.
- Test, Charge, and Control operations were modelled using parallel stations.
- Pick-and-place robots performed automated sorting and packaging operations.
- DataTables, DataQueue, sensors, and methods were used to implement simulation control and routing logic.
- The simulation was configured to run for an 8-hour production shift.

## Assumptions and Data Considered in the Simulation

To simplify the model and focus on system performance, several assumptions were made regarding equipment availability, transportation, routing, and process flow.

### Assumptions

| Assumption | Description |
|------------|-------------|
| Machine Availability | Machine breakdowns, failures, and maintenance activities were not considered. All stations were assumed to be continuously available. |
| Automation | All operations were assumed to be fully automated, with no human operators included in the model. |
| AGV Capacity | Each AGV was limited to transporting one product per trip. |
| AGV Characteristics | All AGVs were assumed to have identical speed and operating behavior. |
| AGV Routing | AGVs followed predefined one-way track routes to avoid congestion and collisions. |
| Buffer Capacity | Buffers were assumed to have sufficient capacity unless explicitly limited. |
| Parallel Station Buffers | Buffers connected to Test, Charge, and Control stations were set to infinite capacity. |
| Packaging Buffers | Packaging buffers were limited according to simulation requirements. |
| Handling Delay | A fixed 5-second waiting time was applied at buffers and sensors to represent handling and coordination delays. |
| Simulation Duration | The simulation was executed for an 8-hour production shift. |
| Product Routing | All products followed the same routing sequence: Production → Test → Charge → Control → Pick-and-Place → Packaging → Drain. |

### Input Data Considered

The simulation used product-dependent processing times, predefined product mix ratios, and uniform processing time distributions for testing, control, and packaging operations.

#### Production Line Processing Times

| Line | Product | ST1 (min/piece) | ST2 (min/piece) | ST3 (min/piece) |
|--------|---------|---------|---------|---------|
| Line 1 | P_1 (Pink) | 5 | 5 | 5 |
| Line 1 | P_2 (Brown) | 4 | 5 | 5 |
| Line 1 | P_3 (Grey) | 5 | 6 | 5 |
| Line 2 | P_4 (Black) | 5 | 7 | 4 |
| Line 2 | P_5 (Red) | 5 | 6 | 5 |
| Line 2 | P_6 (Yellow) | 4 | 5 | 6 |
| Line 3 | P_7 (Green) | 5 | 4 | 6 |
| Line 3 | P_8 (Blue) | 6 | 5 | 4 |
| Line 3 | P_9 (Orange) | 5 | 6 | 4 |

#### Material Handling and Testing Stations

| Station | Processing Time (min/piece) | Distribution |
|----------|----------|----------|
| Test 1 | 5 – 10 | Uniform |
| Charge | 10 – 30 | Uniform |
| Control | 15 – 20 | Uniform |

#### Packaging Stations

| Product | Processing Time (min/piece) | Distribution |
|----------|----------|----------|
| P_1 (Pink) | 4 – 6 | Uniform |
| P_2 (Brown) | 5 – 6 | Uniform |
| P_3 (Grey) | 4 – 6 | Uniform |
| P_4 (Black) | 4 – 6 | Uniform |
| P_5 (Red) | 4 – 5 | Uniform |
| P_6 (Yellow) | 4 – 5 | Uniform |
| P_7 (Green) | 4 – 6 | Uniform |
| P_8 (Blue) | 4 – 6 | Uniform |
| P_9 (Orange) | 4 – 5 | Uniform |

#### Product Mix Scenarios

| Scenario | Line 1 Mix | Line 2 Mix | Line 3 Mix |
|----------|----------|----------|----------|
| Master | P_1 30%, P_2 50%, P_3 20% | P_4 20%, P_5 30%, P_6 50% | P_7 20%, P_8 50%, P_9 30% |
| Scenario 2 | P_1 33.3%, P_2 33.3%, P_3 33.3% | P_4 33.3%, P_5 33.3%, P_6 33.3% | P_7 33.3%, P_8 33.3%, P_9 33.3% |
| Scenario 3 | P_1 50%, P_2 30%, P_3 20% | P_4 20%, P_5 50%, P_6 30% | P_7 50%, P_8 20%, P_9 30% |
| Scenario 4 | P_1 20%, P_2 20%, P_3 60% | P_4 30%, P_5 30%, P_6 40% | P_7 30%, P_8 30%, P_9 40% |

The product mix scenarios were used to evaluate how different demand distributions affected system throughput, resource utilization, and overall production performance.

## Analysed Scenarios and Simulation Results

### Master Scenario

The Master Scenario was used to determine the minimum resources required for stable system operation.

#### AGV Requirement Analysis

To determine the minimum number of AGVs required to prevent production blockage, the simulation was run with both one and two AGVs.

| Number of AGVs | Result |
|---------------|--------|
| 1 AGV | Blockage occurred in all three production lines |
| 2 AGVs | No blockage observed |

Based on the simulation results, a minimum of **2 AGVs** was required to ensure continuous material flow throughout the system.

<img width="947" height="385" alt="image" src="https://github.com/user-attachments/assets/9134ed0b-db8f-4ab6-8d1c-535810800cc4" />

**With 1 AGV (Blockage)**

<img width="907" height="401" alt="image" src="https://github.com/user-attachments/assets/2b3ca38d-6192-4a81-ab07-5ab09017901a" />

**With 2 AGV (No Blockage)** 

#### Parallel Station and Buffer Analysis

The Master Scenario was also used to determine:

- The minimum number of parallel stations required for the Test, Charge, and Control processes.
- The required buffer capacities at the packaging stations.

To achieve this, the capacities of the parallel stations and buffers were initially set to high values. After running the simulation for 8 hours, the **maximum content values** observed in the object statistics were used to identify the required capacities. Based on these results, the number of parallel stations and buffer sizes were adjusted and maintained at the identified levels.

<img width="1118" height="352" alt="image" src="https://github.com/user-attachments/assets/ef3b1aff-b361-45bb-99a2-50e298ea58bf" />

**Minimuim Number of Stations for Test, Charge and Control**

<img width="947" height="841" alt="image" src="https://github.com/user-attachments/assets/df85fb84-11ea-4bda-af58-3482c3cf7721" />

**Pieces/each buffer (Packing Area)**

### Scenario Analysis

Additional scenarios were simulated using different product mix distributions to evaluate their impact on system productivity.

| Scenario | Purpose |
|----------|----------|
| Master Scenario | Determine AGV requirements, parallel station capacities, and buffer sizes. |
| Scenario 2 | Evaluate productivity with an equal product mix distribution. |
| Scenario 3 | Evaluate productivity with an alternative product mix distribution. |
| Scenario 4 | Evaluate productivity with a higher concentration of selected products. |

The productivity of each scenario was measured over an 8-hour simulation period and compared to assess the effect of different product mixes on overall system performance.

## Simulation Outputs

### Summary of Results

| Metric | Result | Unit |
|----------|----------|----------|
| Minimum AGV Fleet Size | 2 | AGVs |
| Minimum TEST1 Stations | 6 | Stations |
| Minimum Charge Stations | 15 | Stations |
| Minimum Control Stations | 12 | Stations |
| Buffer Capacity (P_1, P_3, P_4, P_5, P_6, P_7, P_9) | 1 | Piece per Buffer |
| Buffer Capacity (P_2, P_8) | 2 | Pieces per Buffer |
| Productivity – Master Scenario | 220 | Pieces / 8 Hours |
| Productivity – Scenario 2 | 217 | Pieces / 8 Hours |
| Productivity – Scenario 3 | 221 | Pieces / 8 Hours |
| Productivity – Scenario 4 | 214 | Pieces / 8 Hours |

### Key Findings

- A minimum of **2 AGVs** was required to prevent blockage within the production system.
- The minimum number of parallel stations required was:
  - **6 TEST stations**
  - **15 Charge stations**
  - **12 Control stations**
- Most packaging buffers required a capacity of **1 piece**, while buffers **P_2** and **P_8** required a capacity of **2 pieces**.
- Productivity remained relatively stable across all product-mix scenarios, ranging from **214 to 221 pieces per 8-hour shift**.
- The highest productivity was achieved in **Scenario 3 (221 pieces)**, while **Scenario 4 (214 pieces)** produced the lowest output.

  <img width="937" height="382" alt="image" src="https://github.com/user-attachments/assets/d3019a5d-8c18-44be-9ed1-77be1e2f5996" />
  
**Productivity of Master Secanrio: (220)**

  <img width="932" height="376" alt="image" src="https://github.com/user-attachments/assets/3c6abf8e-8260-4e8f-b217-f1aeb55ea984" />
  
**Productivity of Secnario 2: (217)**

  <img width="930" height="367" alt="image" src="https://github.com/user-attachments/assets/892320f4-3cc2-4ae0-a726-b48ae0ea9796" />
  
**Productivity of Secnario 3: (221)**

  <img width="941" height="367" alt="image" src="https://github.com/user-attachments/assets/306872d7-6555-41e5-b1b2-3c2f82f41db9" />
  
**Productivity of Secnario 4:  (214)**
  

## Output Summary and Results Discussion

The simulation results were evaluated from four perspectives: maximizing productivity, minimizing work in progress (WIP), minimizing space requirements, and minimizing costs.

### Maximizing Productivity

The system maintained stable productivity across all scenarios, producing between **214 and 221 pieces per 8-hour shift**. The use of parallel Test, Charge, and Control stations prevented major bottlenecks and ensured that variations in processing times did not significantly impact throughput.

The simulation also demonstrated that **2 AGVs were required** to maintain continuous material flow. A single AGV resulted in blockage across all three production lines, while two AGVs eliminated this issue and improved overall system performance.

Although a realistic 5-second loading and unloading delay was included, transport operations were not identified as the primary throughput constraint. However, AGVs currently respond to requests based only on DataQueue order. Productivity could potentially be improved by introducing priority-based dispatching rules that consider buffer occupancy or waiting times.

### Minimizing Work in Progress (WIP)

Buffers successfully separated production, testing, and packaging processes, preventing disruptions from propagating throughout the system. The end-of-line conveyors also acted as temporary storage, allowing production to continue while waiting for AGV transport.

The highest WIP accumulation was observed in the buffers following the Test, Charge, and Control stations. This was not caused by insufficient processing capacity, but rather by AGVs serving requests without considering buffer occupancy or waiting duration.

A potential improvement would be to implement priority-based AGV routing to reduce waiting times and buffer accumulation while maintaining system stability.

### Minimizing Space Requirements

The layout effectively separated the production, testing, and packaging areas while maintaining reliable AGV access to all stations. Buffers, conveyors, tracks, and processing stations each served a specific operational purpose and contributed to stable system operation.

Although the AGV track network occupies a considerable amount of space, it is necessary to ensure collision-free transportation and accessibility throughout the system. Based on the simulation results, no clear opportunity was identified to reduce space requirements without negatively affecting throughput or flexibility.

### Minimizing Costs

The system achieved stable performance through the use of sufficient parallel processing capacity and two AGVs. While these resources increase operational costs, they are necessary to avoid blocking and maintain system robustness under different product-mix scenarios.

Future cost reductions would likely come from operational improvements rather than structural changes. Simulation data could be used to reassess station utilization and optimize the number of parallel stations once long-term production demand patterns are known.

## Conclusion

The simulation demonstrated that the production and logistics system is capable of maintaining stable throughput under varying product mixes. The selected number of AGVs, parallel stations, and buffer capacities successfully prevented major bottlenecks while supporting consistent material flow. The main opportunity for future improvement lies in optimizing AGV dispatching and transport decision-making to further improve productivity and reduce work in progress.

---
## Supported Files

[Rithik_Paul_Vaimel_Plant and Material Flow Simulation_Github.pdf](https://github.com/user-attachments/files/29222116/Rithik_Paul_Vaimel_Plant.and.Material.Flow.Simulation_Github.pdf)

[Simulation File.zip](https://github.com/user-attachments/files/29222518/Simulation.File.zip)


---

## License

Copyright (c) 2026 Rithik Paul Vaimel. All Rights Reserved.

This project is provided for viewing purposes only. No permission is granted to copy, modify, or redistribute any part of this repository without explicit written consent from the author.

![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)

---
