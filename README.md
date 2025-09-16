# RailMind
SIH Problem 

🚆 Railway Train Dispatch Optimization
📌 Overview

This project implements an optimized train scheduling and dispatch algorithm for railway junctions using Google OR-Tools (CP-SAT).
It automatically decides which train should go first, which track/platform it should use, and how to minimize delays while ensuring safety and efficiency.

Think of it as a Google Maps for trains — it doesn’t just show conflicts, it recommends the best path and dynamically replans when disruptions occur.

✨ Key Features

Track Directionality & Loop Line Handling
Supports bidirectional tracks, one-way tracks, and a loop line (penalized but used for congestion relief).

Platform Management
Assigns trains to available platforms of sufficient length. Freight trains pass through without platforms.

Train Prioritization

Express → highest priority

Passenger → medium priority

Special → flexible

Freight → lowest priority

Delay Modeling

Trains cannot start before ETA.

Soft max-delay penalties instead of hard caps.

Weighted penalties ensure express trains suffer the least delay.

Buffers & Safety
Includes approach, dwell, exit times, train length factors, and ETA uncertainty margins.

KPIs (Performance Metrics)

Average Delay → overall punctuality

Maximum Delay → worst-case passenger experience

Track Utilization % → efficiency of track usage

Disruption Handling
Handles:

Platform closures

Unscheduled trains

Track blocks

Piling delays

🛠️ System Architecture

Data Ingestion
Collects ETAs, train types, delays, track/platform availability, and disruptions.

Conflict Detection
Identifies overlaps in track/platform usage or headway violations.

Optimization (CP-SAT)
Solves a weighted objective:

Minimize Σ(weight × delay) + penalties(loop usage, platform changes)


Safety Verification
Ensures no violation of buffers, track rules, or headways.

Output

Optimized train order & track assignment

Human-readable explanation

KPIs (delay, throughput, utilization)

Gantt chart visualization

📊 Example Output

Optimized Schedule (CSV export) with planned entry/exit times, assigned track/platform, and delay.

Gantt Chart showing train flows across tracks.

KPIs:

Avg delay = 3.2 min

Max delay = 12 min

Track B utilization = 87%

🚀 Tech Stack

Backend: Python (FastAPI)

Optimization: OR-Tools CP-SAT, Pyomo MILP

Simulation: SimPy

Database: PostgreSQL + TimescaleDB

Frontend: React + Tailwind, D3.js for Gantt charts

Monitoring: Grafana / Metabase

🧪 Testing & Evaluation

Unit tests for scoring, buffers, constraints

Integration tests (API + solver + verifier)

Scenario tests (platform closure, unscheduled arrivals, track blockages)

A/B testing: manual vs optimized schedules

🔮 Future Enhancements

Multi-junction & multi-section optimization

Predictive maintenance integration

Operator UI with what-if simulations

Machine learning to improve scoring weights from historical data

📌 Conclusion

This project demonstrates a real-time, disruption-aware train dispatch optimizer that balances efficiency, punctuality, and safety. By combining constraint programming, weighted delay penalties, and dynamic replanning, it acts as a powerful decision-support tool for railway controllers, reducing delays and improving throughput at congested junctions.
