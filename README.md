# MultiAlgo-CPU-Scheduler-Visualizer

This project implements several widely used CPU scheduling algorithms in C++. It provides both visualization (`trace`) and performance evaluation (`stats`) for different algorithms under varying process and timing conditions.

---

## Overview

This simulator demonstrates how different scheduling strategies behave with processes defined by arrival times, service durations, and priorities. It supports both preemptive and non-preemptive scheduling methods, enabling users to analyze their behavior and efficiency.

---

## Supported Scheduling Algorithms

Each algorithm is identified by a number and has unique characteristics:

| Number | Algorithm Name                | Preemptive | Requires Quantum |
|--------|-------------------------------|------------|------------------|
| 1      | First Come First Serve (FCFS) | No         | No               |
| 2      | Round Robin (RR-q)            | Yes        | Yes              |
| 3      | Shortest Process Next (SPN)   | No         | No               |
| 4      | Shortest Remaining Time (SRT) | Yes        | No               |
| 5      | Highest Response Ratio Next   | No         | No               |
| 6      | Feedback - Fixed (FB-1)       | Yes        | No (q = 1 fixed) |
| 7      | Aging                         | Yes        | Yes              |

---
## Description of Algorithms

- **FCFS (First Come First Serve)**  
  Simple queue-based scheduling; processes are executed in the order they arrive.  
  **Type:** Non-preemptive

- **RR-q (Round Robin with quantum `q`)**  
  Time-sharing approach where each process gets CPU time in equal chunks defined by `q`.  
  **Type:** Preemptive

- **SPN (Shortest Process Next)**  
  Selects the process with the shortest burst (service) time.  
  **Type:** Non-preemptive

- **SRT (Shortest Remaining Time)**  
  Always runs the process with the shortest remaining execution time.  
  **Type:** Preemptive

- **HRRN (Highest Response Ratio Next)**  
  Uses the formula:  
  `Response Ratio = (Waiting Time + Service Time) / Service Time`  
  Chooses the process with the highest ratio.  
  **Type:** Non-preemptive

- **FB-1 (Feedback with Quantum = 1)**  
  Multi-level feedback queues with a fixed time quantum of 1 for each level.  
  **Type:** Preemptive

- **FB-2i (Feedback with Quantum = 2^i)**  
  Multi-level feedback with exponentially increasing time quantum for lower-priority levels.  
  **Type:** Preemptive

- **Aging**  
  Prevents starvation by gradually increasing the priority of waiting processes over time.  
  **Type:** Preemptive

## Input Format

The simulator expects input via standard input (stdin) or from a redirected file.

### Structure

- **Line 1**: Mode of operation — either `"trace"` or `"stats"`
- **Line 2**: Comma-separated list of algorithms to simulate  
  _(e.g., `2-3` means Round Robin with time quantum q = 3)_
- **Line 3**: Simulation end time  
  _(e.g., `20`)_
- **Line 4**: Number of processes  
  _(e.g., `5`)_
- **Line 5+**: One line per process description

---
