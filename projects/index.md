---
layout: homepage
---


## Projects

In the following, I will share some projects that I have been working on as part of my PhD.

### Opensource EDA Flow
The classes from our chair cover digital circuit design, from computer arithmetics to filter design. Students learn how adders, multipliers, rate conversion and other filters are implemented. To bridge the gap from purely theoretical to actual applying this, we want students to implement circuits in Verilog themselves. 

Inspired by [Eda Playground](https://edaplayground.com/), we developed a website where students choose an exercise, upload their verilog and we run a testbench in the background (using iverilog), perform synthesis (using yosys and open-source standard-cells), and perform power and timing analysis (using OpenSTA).

Click [here](/projects/website_flow.html) to learn more!

### Digital Flow for Efficient Design Space Exploration
For the research we are doing at our chair, in addition to the actual novelty proposed, appropriate hyperparameters have to be chosen to achieve best performance: Different to commercial designs, we are not so much bound by area constraints or power budgets, but we aim for "as good as possible". Thus, clock frequency, latency and other area are not hard constraints. To achieve best performance, we can freely choose our constraints (within reason). To find optimal parameters, there are two aspects: An efficient hands-off RTL2GDS flow that can be run in parallel, parameterized and interrupted, and a way to select suitable parameters to run through the flow.

As part of my work at the IDS, I have created a Cadence based RTL2GDS flow, which is controlled from an [Optuna](htpps://optuna.org) based python environment. Optuna proposes hyperparameters such as clock frequency, standard-cells, supply voltage, and design specific ones such as number of pipeline stages (if code is written flexible for that with retiming) and will launch the flow in parallel. The flow is split into 8 steps: Four steps for synthesis: Generic, Mapping, Optimization, Post-Synthesis Simulation and four steps for pnr: Placement, CTS, Routing, Post-Layout Simulation. After every step, PPA reports are generated and loaded by Optuna. If the results indicate that this set of hyperparameters does not result in good performance, the run is prematurely killed to speed up the optimization.

To learn more about the flow and the Optuna based optimization of designs with it, click [here](/projects/efficient_flow.html).
