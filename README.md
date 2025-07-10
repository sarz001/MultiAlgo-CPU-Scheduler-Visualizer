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

The input to the simulator must follow the structure below, line by line:

### Line 1:
`"trace"` or `"stats"`  
- Use `"trace"` to generate a timeline showing how each process executes over time.  
- Use `"stats"` to output numerical results such as finish time, turnaround time, and normalized turnaround time.

### Line 2:
A comma-separated list of scheduling algorithms to be analyzed/visualized, with optional parameters where required.  
Each algorithm is represented by a number:

- `1` → FCFS (First Come First Serve)
- `2-q` → RR (Round Robin with quantum `q`)
- `3` → SPN (Shortest Process Next)
- `4` → SRT (Shortest Remaining Time)
- `5` → HRRN (Highest Response Ratio Next)
- `6` → FB-1 (Feedback where all queues have fixed `q = 1`)
- `7` → FB-2i (Feedback where time quantum = `2^i`)
- `8-q` → Aging with quantum `q`

Example: `1,2-4,3,5` means simulate FCFS, RR with q=4, SPN, and HRRN.

### Line 3:
An integer specifying the last time unit (`last instant`) to be shown in the simulation timeline.  
Example: `20`

### Line 4:
An integer specifying the number of processes to be simulated.  
Example: `5`

### Line 5 and onward:
Each subsequent line describes a process.

#### For algorithms 1 through 7:
`<ProcessName>,<ArrivalTime>,<ServiceTime>`
#### For algorithm 8 (Aging):
`<ProcessName>,<ArrivalTime>,<Priority>`

### Notes:
- Processes must be sorted in increasing order of arrival time.
- If two processes arrive at the same time, the one with **lower priority value** is assumed to arrive first (i.e., lower number = higher priority).


