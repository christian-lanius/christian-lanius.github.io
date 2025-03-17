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


### Tapeouts 
At the IDS, I am the main person responsible for tapeouts: From chip level conception, to chip-, IO- and floorplanning, integration of other colleagues' designs and design of the test PCB/probecard. As our capabilities at the chair increase, so does the design complexity. While the first tapeout were fully seperate designs, only sharing the IO ring, the latest design has a global AXI network, a RISC-V processor and a DMA to enable useful acceleration of software applications.

Click [here](/projects/tapeout.html) to learn more!


### Keyword Spotting on FPGA
As part of my teaching assignment, I was involved in revamping the FPGA lab, where students learn how to do FPGA programming. I was responsible for the core concepts of the new lab: A simple neural network can be used for the detection. As the implementation of a neural network accelerator is infeasible to do in a one semester lab, this part is left on the PC. Instead, all other steps are done on the FPGA: An I2S microphone is used to live capture the audio data, which is then pre-processed and overlapping windows of FFTs are computed on it, resulting in a 2D "image" of audio data. This data is converted into MEL coefficients and then sent to the PC via UART for the final neural network inference. For visualization purposes, the FFT results are shown on a VGA display.

In this lab, students write all these key components themselves, and learn how to use Xilinx IP (FFT) or HLS (computation of MEL coefficients). The integration with the I2S microphone makes the students learn about external synchronous devices, the VGA display allows them to write some FSMs and feel the constraints of the FPGA wrt. on-chip memory (the BRAM is barely enough to fit a full frame buffer, so on the fly rendering is required).

To learn more about this, click [here](/projects/fpga_lab.html)!
