# Tank Robot Pathfinding with A* and Greedy Search Algorithms

This project implements a pathfinding solution for a tank robot equipped with an Arduino Uno and a gyroscope for precise navigation. The robot operates on a 5x5 grid matrix, avoiding obstacles and finding the most optimal path from the start point (0,0) to a designated goal using two algorithms: **A*** and **Greedy Best-First Search**.

---

## Table of Contents
1. [Problem Formulation](#problem-formulation)
2. [EDA and Data Preprocessing](#eda-and-data-preprocessing)
3. [Implementation](#implementation)
   - [Hardware Setup](#hardware-setup)
   - [Main Algorithm](#main-algorithm)
   - [Environment Representation](#environment-representation)
   - [A* Algorithm Implementation](#a-algorithm-implementation)
4. [Evaluation](#evaluation)
5. [Comparison with Greedy Best-First Search](#comparison-with-greedy-best-first-search)
6. [Discussion of Results](#discussion-of-results)
7. [Repository Contents](#repository-contents)

---

## Problem Formulation
The robot navigates a 5x5 grid where obstacles are marked as `1` and free cells as `0`. The goal is to find the most optimal path from the top-left corner (0,0) to a predefined end point while avoiding obstacles. This is a classic pathfinding problem solved using **A*** and **Greedy Best-First Search** algorithms.

---

## EDA and Data Preprocessing
No external dataset was used. The grid environment was manually designed, with obstacles and traversal costs predefined. This allowed us to focus on implementing and testing the algorithms in a controlled setting.

---

## Implementation

### Hardware Setup
- **Core Component**: Arduino Uno.
- **Motors**: Four DC motors for movement (forward, backward, and turning).
- **Gyroscope**: MPU6050 for orientation tracking (I2C interface with Wire library).
- **User Input**: Push-button to start the pathfinding process.
- **Motor Control**: Adjustable motor speed for fine-tuning responsiveness.

### Main Algorithm
The **A*** algorithm was implemented to find the shortest path by considering:
- **gCost**: Actual movement cost from the start.
- **hCost**: Estimated cost to the goal (Manhattan distance heuristic).
- **fCost**: Total cost (`gCost + hCost`).

### Environment Representation
- **Grid Definition**: A 5x5 matrix with obstacles (`1`) and free cells (`0`).
- **Cost Matrix**: Each cell has a traversal cost, with higher values representing more challenging paths.
- **Start and End Points**: (0,0) to (4,4).

### A* Algorithm Implementation
1. **Heuristic Function**: Manhattan distance.
2. **Node Structure**: Contains coordinates, movement costs, and parent index.
3. **Open and Closed Lists**: Arrays to manage nodes for evaluation.
4. **Path Reconstruction**: Tracing back from the goal to the start using parent nodes.

---

## Evaluation
1. **Path Verification**: The reconstructed path was printed to the Serial Monitor to ensure logical progression.
2. **Real-World Testing**: The code was uploaded to the Arduino and tested on the predefined grid. Movements were optimized after each run.
3. **Comparison with Greedy Best-First Search**: Both algorithms were tested on the same grid setups.

---

## Comparison with Greedy Best-First Search
- **Greedy Search**: Focuses solely on the heuristic (`hCost`), ignoring movement costs. It is faster but may produce suboptimal paths.
- **A***: Balances movement cost (`gCost`) and heuristic (`hCost`), ensuring optimal paths even with varying traversal costs.

---

## Discussion of Results
- In simple cost distributions, both algorithms produced the same path.
- When traversal costs varied, **A*** adapted and found the optimal path, while **Greedy Search** failed to account for increased costs.
- **A*** is more computationally intensive but reliable for complex environments.

---

## Repository Contents
- `detailed_report.pdf`: Detailed project report.
- `a_star.ino`: Arduino code for the A* algorithm.
- `greedy.ino`: Arduino code for the Greedy Best-First Search algorithm.
- `skeleton.png`: Image of the robot's hardware setup.
