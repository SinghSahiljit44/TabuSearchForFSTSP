# Development of a Tabu Search Metaheuristic for the FSTSP

## Project Overview
This repository contains a **Tabu Search (TS) metaheuristic** designed to solve the **Flying Sidekick Traveling Salesman Problem (FSTSP)**. The FSTSP models a synchronized truck-drone delivery system where a truck acts as a mobile depot for a drone. While the truck travels, the drone can launch from the vehicle, serve a customer, and return to the truck at a recovery point. 

The goal is to minimize total delivery time while managing complex spatial and temporal constraints, such as limited drone battery life and parcel weight restrictions. Given that the FSTSP is NP-hard, this project focuses on a metaheuristic approach to find high-quality solutions where exact solvers struggle.

## Key Features
Our implementation is built upon the **4 Pillars of Tabu Search**:

* **Recency (Short-Term Memory):** Managed via dual Tabu Lists for truck edges and drone sorties to prevent immediate cycling.
* **Frequency (Long-Term Memory):** Utilizes **Residency** and **Transition** counters to penalize over-exploited structural patterns during reconstruction.
* **Quality:** Maintains an **Elite Pool** of the top 10 distinct solutions to guide search reconstruction when stagnation occurs.
* **Influence:** Monitors search stagnation and applies higher-influence moves to significantly perturb the current solution.

## Technical Implementation
* **Initial Solution:** Generated using greedy heuristics (Cheapest Insertion or Nearest Neighbor) followed by a greedy drone sortie insertion.
* **Neighborhood Moves:** Includes **2-Opt**, **Drone-to-Truck**, and **Truck-to-Drone** operators.
* **Adaptive Tabu Tenure:** Uses a systematic dynamic tenure (Low, Medium, High) to balance intensification near new best solutions and diversification during restarts.
* **Aspiration Criterion:** Allows a tabu move if it results in a solution better than the current incumbent.

## Performance Evaluation
The algorithm was tested on standard benchmark instances ranging from 40 to 80 customers:
* **Average Gap:** 0.611% across all tested instances.
* **Superior Results:** Outperformed Gurobi on specific instances, such as **80-1-2**, achieving a negative gap (321 vs 345).
* **Hardware:** Benchmarked on an AMD Ryzen 7 5700X with 32 GB RAM.

## Authors
* **Singh Sahiljit** (Matr. 740552) 
* **Lublanis Matteo** (Matr. 736418)

## Note
* If you wish to se the actual code developed using JAVA, kindly write me at sahiljitsingh03@gmail.com

*This project was developed for the **Optimization Algorithms** course (Academic Year 2025/2026) at the **University of Brescia**, Department of Information Engineering.*
