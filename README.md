# Author Vinamra Singh
## Course - Advanced Physical Design Using OpenLane/Sky130
### Section 1 Inception of open-source EDA, OpenLANE and Sky130 PDK
#### Brief Overview
Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs
1. QFN-48 Package Overview
QFN (Quad Flat No-Lead) 48 is a surface-mount integrated circuit (IC) package with 48 pins, commonly used in modern electronic devices. It provides excellent thermal dissipation, low electrical parasitics, and a compact footprint, making it ideal for high-performance applications like microcontrollers, RF devices, and power management ICs.

2. Key Components of a QFN-48 Package
a) Chip (IC)
The chip, also called the integrated circuit (IC), is the primary functional component inside the QFN package. It contains electronic circuits that perform processing, logic operations, or signal control.

b) Pads
Pads are metallic contact points on the silicon die where electrical connections are made. These pads are connected to the package's external pins using bond wires or flip-chip technology for electrical communication with other components.

c) Core
The core is the main functional unit inside the chip. It includes logic gates, processing units, and memory elements that execute instructions or perform specific tasks (e.g., a microcontroller core).

d) Die
The die is the actual silicon wafer slice that contains the semiconductor circuits. It is manufactured through a photolithography process and then cut into individual dies before packaging.

e) IPs (Intellectual Properties)
IPs (Intellectual Property blocks) are pre-designed functional modules integrated into the chip. These include:

CPU cores (e.g., ARM Cortex cores in microcontrollers).
Memory blocks (e.g., RAM, ROM, Flash).
Analog & digital interfaces (e.g., ADC, DAC, GPIOs).
Communication blocks (e.g., SPI, I2C, UART, USB, PCIe).
3. Advantages of QFN-48 Package
Small form factor for compact devices.
Good thermal and electrical performance due to its exposed pad design.
Low parasitic inductance, ideal for high-speed applications.
Cost-effective and easy to manufacture compared to larger packages.
This package is widely used in MCUs, RF circuits, and power management ICs due to its efficiency and reliability.
Introduction to RISCV-V
What is RISC-V?
RISC-V (pronounced "risk-five") is an open-source Instruction Set Architecture (ISA) based on the Reduced Instruction Set Computing (RISC) principle. It is designed for flexibility, scalability, and efficiency, making it suitable for a wide range of computing applications, from embedded systems to high-performance computing.

Key Features of RISC-V
Open-Source: Unlike proprietary ISAs (e.g., ARM, x86), RISC-V is free to use and modify.
Modular Architecture: Supports multiple instruction set extensions (e.g., floating-point, vector, and security extensions).
Scalability: Can be used in microcontrollers, mobile devices, and even supercomputers.
Energy Efficient: Optimized for low-power consumption.
Customization: Allows companies and researchers to design custom processors without licensing restrictions.
Applications of RISC-V
Embedded systems (IoT, microcontrollers)
AI and Machine Learning accelerators
Data centers and cloud computing
Automotive and industrial automation
Custom hardware research and development
Why is RISC-V Important?
RISC-V is disrupting the semiconductor industry by providing an open, royalty-free alternative to traditional ISAs, promoting innovation and reducing development costs. It is supported by leading companies and organizations worldwide.

Introduction to All Components of Open-Source Digital ASIC Design
What is Digital ASIC Design?
An Application-Specific Integrated Circuit (ASIC) is a custom-designed semiconductor chip tailored for a specific application (e.g., CPUs, GPUs, AI accelerators). The open-source ASIC flow provides a free alternative to proprietary EDA (Electronic Design Automation) tools.

Key Components of Open-Source Digital ASIC Design
Register Transfer Level (RTL) Design

Written in Hardware Description Languages (HDL) like Verilog or VHDL.
Defines the chip’s logic and functionality.
Logic Synthesis

Converts RTL code into a gate-level netlist using tools like Yosys.
Optimizes logic gates for area, power, and performance.
Floorplanning & Power Planning

Defines the chip layout, ensuring optimal placement of functional blocks.
Includes power grid design to handle current distribution.
Placement

Arranges standard cells (basic logic gates, flip-flops, etc.) inside the chip.
Uses tools like RePLace and OpenROAD for automated placement.
Clock Tree Synthesis (CTS)

Ensures clock signals reach all sequential elements with minimal skew.
Uses tools like TritonCTS.
Routing

Establishes physical connections between components using metal layers.
Performed using FastRoute and TritonRoute.
Signoff Checks

Design Rule Check (DRC) – Ensures layout follows manufacturing rules.
Layout vs. Schematic (LVS) – Verifies that the layout matches the netlist.
Static Timing Analysis (STA) – Ensures timing constraints are met.
GDSII Export

The final chip layout (GDSII format) is sent for fabrication.

Simplified RTL-to-GDSII Flow
The RTL-to-GDSII flow is the complete ASIC design process, from writing RTL code to generating a GDSII file for fabrication.

Simplified RTL2GDS Flow:
RTL Design – Write the hardware logic in Verilog.
Logic Synthesis (Yosys) – Convert RTL to a gate-level netlist.
Floorplanning (OpenROAD) – Define chip layout constraints.
Placement (RePLace) – Arrange standard cells.
Clock Tree Synthesis (TritonCTS) – Balance clock distribution.
Routing (TritonRoute) – Connect logic components using metal layers.
DRC & LVS Checks (Magic, Netgen) – Ensure manufacturability.
GDSII Generation – Export the final layout for fabrication.
Each step uses open-source tools, eliminating the need for proprietary software.

Introduction to OpenLANE and Strive Chipsets
What is OpenLANE?
OpenLANE is an open-source ASIC design flow developed by efabless, built on tools like:

Yosys – Logic synthesis.
OpenROAD – Placement, CTS, routing.
Magic & KLayout – Layout visualization and DRC checks.
Netgen – LVS verification.
Fault – DRC rule checking.
Strive Chipsets
Strive chipsets are RISC-V based open-source designs developed using OpenLANE, demonstrating a fully open-source ASIC implementation.

Introduction to OpenLANE Detailed ASIC Design Flow
In-Depth OpenLANE Flow
The OpenLANE flow automates the ASIC design process from RTL to GDSII, integrating multiple open-source EDA tools.

Detailed Step-by-Step Flow:
1. Design Setup
Define parameters like clock speed, power budget, and area constraints.
Set up Verilog files and design constraints.
2. Synthesis (Yosys & ABC)
Converts RTL (Verilog) to a gate-level netlist.
Uses ABC (AIG-based logic optimization) for area/power optimization.
3. Floorplanning (OpenROAD)
Defines chip layout, power distribution, and pin locations.
Creates a power grid to manage current flow.
4. Placement & Optimization (RePLace, OpenROAD)
Standard cell placement using RePLace.
Optimizes for density, timing, and congestion.
5. Clock Tree Synthesis (TritonCTS)
Builds a balanced clock distribution network.
Minimizes clock skew and timing violations.
6. Routing (FastRoute, TritonRoute)
Global Routing (FastRoute) – Determines routing paths.
Detailed Routing (TritonRoute) – Assigns metal layers for connections.
7. Signoff Checks (Magic, Netgen, OpenSTA)
Design Rule Check (DRC) – Ensures compliance with foundry rules.
Layout vs. Schematic (LVS) – Verifies layout matches netlist.
Static Timing Analysis (STA) – Ensures setup and hold times are met.
8. GDSII Export
Final chip layout is saved in GDSII format for fabrication.
Why is Open-Source ASIC Design Important?
No licensing fees – Unlike commercial EDA tools (Synopsys, Cadence).
Fully customizable – Allows modification of standard libraries.
Enables innovation – Ideal for startups, universities, and research labs.
Compatible with SkyWater 130nm PDK – A free process design kit (PDK) for real chip manufacturing.

#### Section 1 Tasks

1. Run "picorav32a" synthesis using OpenLane and generat output
2. Calculate flop ration

1. Run "picorav32a" synsthesis using OpenLane and generat output
1. Go to Openlane Directory

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
2. Run the command Docker

```bash
docker
```
3. Go to interactive mode
```tcl
#Use this command to go to interactive mode
./flow.tcl -interactive

#input required packages using this command
package require openlane 0.9


#The OpenLANE flow is now set up to handle any design. Before running a specific design like 'picorv32a', we first need to create important files and directories to prepare the environment using this command

prep -design picorv32a

#Finally run synthesis using this command
run_synthesis

```

Screenshots


![lab 1](https://github.com/user-attachments/assets/c0a3f513-27d5-4f07-979b-7ea50f667e4f)

![lab 2](https://github.com/user-attachments/assets/b2db4aaa-becd-4283-aadc-70797e5872ff)

![lab (3)](https://github.com/user-attachments/assets/d9a18f0b-2541-4c96-8608-c0f3d8ca1ab7)


2. Calculate flop ratio

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
```math
Percentage\ of\ D Flip Flops's = Flop\ Ratio * 100
```

D flip Flop

![Screenshot (73)](https://github.com/user-attachments/assets/1ee559b6-1764-4f0f-aabb-9992b55eaa7a)


Total numbers of cells

![Screenshot (74)](https://github.com/user-attachments/assets/60ccc161-579a-4783-84c1-52024d123e84)

Calculation of Flop Ratio and D Flip Flop's %

```math
Flop\ Ratio = \frac{1613}{14876} = 0.1084296853993009
```
```math
Percentage\ of\ D Flip Flops's = 0.1084296853993009 * 100 = 10.84296853993009\ \%
```

### Section 2 Good floorplan vs bad floorplan and introduction to library cells

#### Brief Overview

Utilization Factor and Aspect Ratio:

Utilization Factor refers to the percentage of the area of a chip or layout that is effectively utilized by the cells (logic, power, etc.). It's a measure of how efficiently the space is being used for the design. A higher utilization factor means more efficient use of the chip's area.
Aspect Ratio is the ratio of the width to the height of the layout. In chip design, a balanced aspect ratio is desirable to avoid issues with routing, power distribution, and heat dissipation. A skewed aspect ratio can lead to longer routing paths and higher power consumption.

Concept of Pre-placed Cells:
Pre-placed cells are components (like standard cells) that are already positioned in the layout before the main floorplanning and placement stages. These cells could be dedicated to specific functions like clock distribution, power grids, or reset logic. The placement is done to optimize performance and reduce the complexity of routing during later stages of design.

De-coupling Capacitors:
De-coupling capacitors are used in chip design to minimize noise and voltage fluctuations in the power supply. These capacitors are placed between the power and ground planes to filter high-frequency noise, stabilize the power supply, and prevent signal integrity issues. They play a crucial role in maintaining stable operation of the IC.

Power Planning:
Power planning involves designing the power distribution network for an IC. It ensures that the correct voltage and current are supplied to each cell in the chip. This process includes designing the power grid, managing voltage drops, and deciding where to place decoupling capacitors. Proper power planning is essential to ensure that the chip operates efficiently and within its power budget.

Pin Placement and Logical Cell Placement Blockage:

Pin Placement refers to the positioning of input/output pins in the chip layout. Proper pin placement is crucial for efficient routing and to meet timing and electrical requirements. The placement should minimize the wire length and reduce congestion.
Logical Cell Placement Blockage refers to regions of the layout where no cells can be placed due to design constraints. These blockages can be caused by pre-placed cells, I/O locations, or regions reserved for specific functions (like clock trees or power grids). Proper management of these blockages is important for efficient chip layout and routing.

Netlist Binding and Initial Place Design:

Netlist Binding: This is the first step in translating a design’s logical description (netlist) into a physical design. It involves assigning specific standard cells (like AND gates, flip-flops, etc.) from a cell library to the elements defined in the netlist. This mapping ensures that each logical function in the netlist is implemented with an appropriate physical cell. The goal is to select cells based on their functionality and constraints (such as timing, power, area) so the design will work as intended.
Initial Place Design: After binding the netlist to specific cells, the next step is the initial placement of these cells on the chip. The placement is typically done in a rough, unoptimized manner to establish a starting point. During this phase, cells are positioned based on their connectivity and the layout's initial area constraints. The main objective is to reduce wire length, minimize congestion, and meet the design's basic performance requirements like timing and power consumption.

Optimize Placement Using Estimated Wire-Length and Capacitance: After the initial placement, the next phase is to optimize the placement of cells to improve the design’s performance. The optimization process is focused on minimizing wire length and capacitance:

Wire Length: Long wires lead to higher resistance and delays, which can degrade performance. Shortening the wire length reduces these delays and contributes to faster signal propagation.
Capacitance: The capacitive coupling between wires impacts both timing (delays) and power consumption (leakage). By minimizing capacitance between cells, the design can achieve faster signal transitions and lower power usage.
By estimating these factors during the optimization, the placement can be adjusted so that the wire length and capacitance are minimized, resulting in better timing, lower power consumption, and improved overall performance.

Final Placement Optimization: Once the initial placement and some optimizations have been done, the next step is final placement optimization. This phase refines the placement of cells with more advanced algorithms and techniques. The goal is to achieve the best balance between timing, power, and area:

Timing: Ensuring that the signals propagate through the chip within the required timing constraints is critical for functionality.
Power: Optimizing the design to consume the least amount of power possible while meeting the performance goals.
Area: Minimizing the area of the layout, which directly impacts the chip’s cost and yield.
Techniques like simulated annealing or gradient-based optimization are often used in this step to iteratively move cells, reducing the overall delays, congestion, and power consumption, while optimizing for the design's area.

Need for Libraries and Characterization:

Libraries: A library in IC design is a collection of pre-designed cells that can be used to implement a wide range of logical functions (such as AND, OR, flip-flops, latches, etc.). These cells are characterized in terms of their timing, power consumption, area, and voltage requirements. Having an extensive library of cells is essential for efficiently implementing complex designs.
Characterization: Cell characterization is the process of measuring and recording the performance characteristics (such as delay, power consumption, and noise behavior) of each cell in the library under various operating conditions (e.g., voltage, temperature, process variations). The characterization data is critical for accurate timing analysis and power estimation, helping designers make informed decisions when selecting cells for their design. Characterization allows for precise modeling of the cells' behavior, leading to better optimization during placement and routing.

Congestion-Aware Placement Using RePlAce: RePlAce is an advanced tool or algorithm used for congestion-aware placement. Congestion refers to regions on the chip where too many cells are packed too closely together, leading to routing difficulties and performance bottlenecks. It occurs when the design's placement density is too high in certain areas, making it difficult to route the wires efficiently.

RePlAce helps manage congestion by adjusting the placement of cells in such a way that areas of high density (congestion) are avoided. By using congestion-aware placement, it ensures that the chip layout is balanced, with enough space between cells to allow for efficient routing and to meet timing and power requirements. RePlAce achieves this by using optimization algorithms that take congestion into account during the placement process, leading to better overall routing and improved chip performance. This step is critical in modern IC design, especially for advanced nodes where congestion can become a major limiting factor.

Inputs for Cell Design Flow:
The cell design flow is a process that involves designing individual components (cells) used in the chip layout, such as logic gates, flip-flops, and buffers. The inputs to this flow include:

Design Specifications: These define the required functionality of the cell, its size, power, and performance (such as delay, drive strength, and power consumption). This can include the required timing, area, and functionality of the cell.
Process Technology: This includes the technology nodes (e.g., 28nm, 7nm) that define the physical characteristics of the cell, such as transistor sizes, interconnect layers, and the manufacturing process (e.g., CMOS).
Electrical Characteristics: These define how the cell should behave electrically, such as voltage levels, current requirements, and timing constraints. These characteristics help in modeling how the cell interacts with other cells in the circuit.
Library Constraints: Constraints regarding the physical and electrical behavior of the cells, ensuring they meet design rules for layout and timing. These constraints can be related to power consumption, area, and performance requirements.

Circuit Design Step:
The circuit design step focuses on defining the logical functionality of the cell. In this stage, the following occurs:

Logic Design: The logical function of the cell is specified, such as implementing AND, OR, XOR gates, flip-flops, multiplexers, etc. The logic is designed to meet the required functionality and ensure it performs the intended operations.
Schematic Design: A schematic of the circuit is created, showing how transistors and other components are connected to achieve the desired functionality. This includes specifying the transistor-level design and their interconnections.
Simulation and Verification: The circuit’s functionality is verified through simulations (e.g., SPICE simulations). These simulations check if the cell operates correctly under various conditions and that it meets the desired specifications for timing, power, and noise margins.
Optimization: The design is optimized for speed, area, and power. Adjustments may be made to the transistor sizing and placement to ensure the cell meets the specifications.

Layout Design Step:
The layout design step is where the cell design is translated into a physical layout. This process includes:

Transistor Layout: The transistors, interconnects, and other components are laid out on the chip in a way that complies with the design rules of the process technology. This includes the placement of gates, source/drain regions, and polysilicon layers, which are used to connect the transistors.
Routing: The interconnections between the cells and components are routed to form the final chip layout. This step involves creating the metal layers that will be used to connect the transistors and ensure that the electrical signals flow correctly between cells.
Design Rule Checking (DRC): After the layout is created, it is checked for design rule violations. These rules ensure that the layout adheres to the manufacturing process’s limitations (e.g., minimum spacing between wires, minimum width of wires) and that the design can be manufactured without issues.
Layout vs. Schematic (LVS): This step ensures that the physical layout matches the intended schematic design. Any discrepancies between the layout and the schematic are flagged and need to be corrected.

Typical Characterization Flow:
Characterization is the process of measuring and recording the performance characteristics of cells under various operating conditions. The typical characterization flow involves the following steps:

Simulation Setup: The first step in characterization is to set up simulations using tools like SPICE. This involves defining the input stimulus, load conditions, and operating voltage for the cell.
Timing Analysis: During characterization, timing analysis is performed to determine the delay through the cell at various operating points. This helps in determining how fast the cell can switch between logic states.
Power Analysis: The power consumption of the cell is also measured under various conditions, including dynamic power (during switching) and static power (when the cell is idle). This helps in estimating how much power the cell will consume in the final design.
Process Variations: The characterization flow includes analyzing the effects of process variations, such as temperature changes, voltage fluctuations, and manufacturing differences, to ensure the cell operates correctly under a wide range of conditions.
Corner Cases: These are extreme operating conditions (e.g., temperature extremes, supply voltage extremes) used to validate the cell’s robustness and ensure that it functions correctly across a broad range of possible real-world conditions.
Characterization Data Generation: After running simulations, the data generated (timing, power, noise, etc.) is stored and used for later steps in the design flow, such as static timing analysis and power estimation.

Timing Threshold Definitions:
Timing thresholds refer to the voltage levels that define when a signal transition (like a rising or falling edge) is considered to occur. These thresholds are critical for determining the timing characteristics of a circuit. Some common timing thresholds include:

Vih (Input High Voltage): The minimum voltage level at which an input is recognized as a logical high (1).
Vil (Input Low Voltage): The maximum voltage level at which an input is recognized as a logical low (0).
Voh (Output High Voltage): The minimum voltage level at which an output is considered a logical high.
Vol (Output Low Voltage): The maximum voltage level at which an output is considered a logical low.
These definitions are crucial in determining the timing margins in a design, ensuring that signals are correctly recognized and there are no errors in logic operations due to unclear voltage levels during signal transitions.

Propagation Delay and Transition Time:

Propagation Delay refers to the time taken for a signal to propagate through a circuit element (such as a gate or flip-flop) from the input to the output. It is a key timing characteristic and determines how quickly a circuit can operate. Propagation delay is usually measured as:
tPLH (Propagation delay, low-to-high output): The delay from the input signal changing from low to high to the output signal changing from low to high.
tPHL (Propagation delay, high-to-low output): The delay from the input signal changing from high to low to the output signal changing from high to low.
Transition Time refers to the time it takes for a signal to change between its logic levels (high and low). It is often defined as the time it takes for a signal to move from 10% to 90% of its final voltage value (or vice versa). Transition time affects the speed at which signals propagate and can influence the overall speed of the circuit. Faster transitions are preferred to reduce the delay and improve the overall performance of the design.

#### Section 2 Tasks

1. Run 'picorv32a' floorplan using OpenLANE flow and get the Output
2. Calculate die area
3. Load floorplan in Magic tool and explore it
4. Run 'picorv32a' design placement using OpenLANE flow and get the output.
5. Load placement in Magic tool and explore it

1. Run 'picorv32a' floorplan using OpenLANE flow and get the Output

1. Go to Openlane Directory

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
2. Run the command Docker

```bash
docker
```
3. Go to interactive mode
```tcl
#Use this command to go to interactive mode
./flow.tcl -interactive

#input required packages using this command
package require openlane 0.9


#The OpenLANE flow is now set up to handle any design. Before running a specific design like 'picorv32a', we first need to create important files and directories to prepare the environment using this command

prep -design picorv32a

#run synthesis using this command
run_synthesis

# Now we can run floorplan
run_floorplan
```

Screenshots of running floorplan

![Screenshot (75)](https://github.com/user-attachments/assets/fdc9d5b6-16d1-4bea-933b-57ced5f91c0d)

![Screenshot (76)](https://github.com/user-attachments/assets/b95558ff-26fe-4f47-927e-a1d4a164ce69)

2. Calculate die area

Screenshot of contents in Floorplan

![Screenshot (77)](https://github.com/user-attachments/assets/43bd6cff-2b57-453d-8476-4286995ec938)

```math
1000\ Unit\ Distance = 1\ Micron
```
```math
Die\ width\ in\ unit\ distance = 660685 - 0 = 660685
```
```math
Die\ height\ in\ unit\ distance = 671405 - 0 = 671405
```
```math
Distance\ in\ microns = \frac{Value\ in\ Unit\ Distance}{1000}
```
```math
Die\ width\ in\ microns = \frac{660685}{1000} = 660.685\ Microns
```
```math
Die\ height\ in\ microns = \frac{671405}{1000} = 671.405\ Microns
```
```math
Area\ of\ die\ in\ microns = 660.685 * 671.405 = 443587.212425\ Square\ Microns
```

3. Load floorplan in Magic tool and explore it

Commands to run floorplan in magic

```bash
# Change directory to floorplan
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/01-02_05-07/results/floorplan/

# Command to run the floorplan in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
FLoorplan in Magic

![Screenshot (78)](https://github.com/user-attachments/assets/259a95f2-1500-48bd-a032-d6494fc4160f)

Port layers

![Screenshot (80)](https://github.com/user-attachments/assets/778a7867-1764-481d-9b42-2056f8e8aa59)
![Screenshot (81)](https://github.com/user-attachments/assets/b8374bf8-886c-4705-a900-2a1d01a09897)
![Screenshot (83)](https://github.com/user-attachments/assets/17ffc04d-6476-4015-9294-d1eda2a0c12d)

Diagonally equal cells

![Screenshot (79)](https://github.com/user-attachments/assets/5512b101-9fc6-4257-8d65-683fd9493bc6)

Unplaced cells

![Screenshot (81)](https://github.com/user-attachments/assets/5a9f55e8-3e60-46df-a0ce-7b5e3ae57044)
![Screenshot (82)](https://github.com/user-attachments/assets/0aea2e0d-df40-4cbb-9b88-92c8af4df95a)

4.Run 'picorv32a' design placement using OpenLANE flow and get the output.

```bash
#So some cells are unplaced in the floorplan and to place them we use this command

run_placement
```

Screenshots of running placement in terminal

![Screenshot (92)](https://github.com/user-attachments/assets/491277fd-31cf-4d78-a140-1f79dad71e42)

![Screenshot (85)](https://github.com/user-attachments/assets/7cf86d5b-3d23-4f7e-bc12-d667a7caad96)

![Screenshot (84)](https://github.com/user-attachments/assets/5f4be562-d801-41b5-9975-7098560b3d53)

Screenshots of floorplan after running placement

```bash
#change the directory to placement
Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/01-02_05-07/results/placement

#Command to Run placement in magic

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

```
![Screenshot (86)](https://github.com/user-attachments/assets/8a57197a-e850-4355-999f-141634b3b1af)
![Screenshot (87)](https://github.com/user-attachments/assets/05b2e1c3-c2a6-463c-b813-64db666090d4)


Screenshot of legally placed cells

![Screenshot (88)](https://github.com/user-attachments/assets/dd4da2a8-3edb-4a18-98a9-ea9dc41a51f6)
![Screenshot (89)](https://github.com/user-attachments/assets/ff32ca39-b2e5-467b-bbe5-800657501b6e)

Screenshots Of exploring floorplan after running placement

![Screenshot (90)](https://github.com/user-attachments/assets/5a7af879-43e3-40b4-9920-012f2a315a11)
![Screenshot (91)](https://github.com/user-attachments/assets/1dd03d68-46cf-40b7-878e-6d142c1a7117)


### Section 3 Design library cell using Magic Layout and ngspice characterization
#### Brief Overview

##### CMOS Inverter and SPICE Simulation:
SPICE Deck Creation for CMOS Inverter:

SPICE (Simulation Program with Integrated Circuit Emphasis) is a widely used tool for simulating electrical circuits, and a SPICE deck refers to the set of input files that define the components and their behavior.
CMOS Inverter: A basic CMOS inverter consists of an NMOS (N-type Metal-Oxide-Semiconductor) and PMOS (P-type Metal-Oxide-Semiconductor) transistor. The SPICE deck for this circuit includes the transistor models, voltage sources, and netlist definitions that describe how the CMOS inverter should behave in a simulation environment.
In this step, you define all the parameters (threshold voltages, channel lengths, etc.) of the NMOS and PMOS transistors and set up the necessary simulation conditions (e.g., input signals and output response).

SPICE Simulation Lab for CMOS Inverter:

This step involves running the SPICE simulation for the CMOS inverter. You simulate how the circuit behaves under different conditions (e.g., input voltages) and observe the output (in terms of voltage).
The goal is to understand the static and dynamic behavior of the inverter, including its switching characteristics, delays, and energy consumption. You may analyze the rise time, fall time, propagation delay, and other performance metrics.

Switching Threshold Vm:

The switching threshold (Vm) refers to the input voltage level at which the output voltage of the inverter transitions from logic 0 to logic 1 (or vice versa).
The inverter switches between high and low output levels depending on the input voltage. Vm is the input voltage at which the inverter output changes states, and it typically lies between the threshold voltages of the NMOS and PMOS transistors.
This voltage is critical for ensuring that the CMOS inverter operates as a proper logic gate, transitioning cleanly between the two states.

Static and Dynamic Simulation of CMOS Inverter:

Static Simulation focuses on the behavior of the CMOS inverter at steady-state conditions, such as the logic 0 and logic 1 states.
Dynamic Simulation simulates the inverter's behavior when switching between these states, typically involving time-dependent analysis to evaluate performance factors like switching time, power consumption, and transition delays.
CMOS Fabrication Process:

Create Active Regions:

The active regions of a CMOS device are the areas where the transistor channels (source, drain, and gate regions) are formed. These regions are where the actual transistor action occurs (i.e., where current flows when the transistor is turned on).
Creating active regions typically involves oxidation and photolithography processes, where regions of the silicon wafer are defined to later form NMOS and PMOS devices.

Formation of N-Well and P-Well:

N-well and P-well are the regions in which the PMOS and NMOS transistors are formed, respectively.
N-well: A region of P-type silicon where NMOS transistors are implanted.
P-well: A region of N-type silicon where PMOS transistors are implanted.
These wells are created by the process of dopant implantation during the fabrication process to ensure that the proper charge carriers are available for each type of transistor.

Formation of Gate Terminal:

The gate terminal is formed by creating a thin layer of polycrystalline silicon (polysilicon) over the active regions. This polysilicon layer will act as the gate electrode that controls the flow of current between the source and drain terminals of the transistor.
The gate is separated from the active region by a thin layer of silicon dioxide (SiO2), which acts as the gate oxide.

Lightly Doped Drain (LDD) Formation:

LDD (Lightly Doped Drain) is a process that helps reduce short-channel effects (where the gate control over the channel is weakened due to small transistor sizes).
LDD involves implanting a light dose of dopants (usually phosphorous or boron) into the source and drain regions, creating a more gradual doping profile near the channel. This reduces the electric field and improves the transistor’s performance, especially for scaled-down technologies.

Source-Drain Formation:

The source and drain are the two terminals of the transistor where the current flows. These regions are highly doped to create N-type or P-type conductivity, depending on whether the transistor is an NMOS or PMOS.
Source-Drain formation is done by implanting the appropriate dopants into the active regions (N-well or P-well) to create the two regions that will allow current to flow when the transistor is turned on.

Local Interconnect Formation:

Local interconnects refer to the metal or polysilicon layers that connect individual components (such as transistors) within the chip. These interconnects form the wiring that connects the different gates and sources/drains.
The interconnect layers are formed after the source-drain and gate regions are created, usually by deposition and etching processes.

Higher Level Metal Formation:

After the local interconnects, higher-level metal layers (M1, M2, M3, etc.) are created to establish long-range connections between different parts of the chip.
These higher-level metal layers are typically formed using copper or aluminum and are essential for creating connections between various blocks of the chip, ensuring that the components can communicate and work together effectively.

Summary:

SPICE Simulation steps help in understanding and evaluating the behavior of the CMOS inverter, including its switching thresholds and performance under various conditions.

The CMOS fabrication process focuses on creating the physical structure of the transistor by forming the active regions, creating the wells, defining the gate, and forming the source-drain terminals. Various process steps like LDD formation, interconnect creation, and higher-level metal layers ensure that the transistor operates efficiently and connects to the rest of the circuit.

#### Section 3 Lab tasks

1.Clone the web URL in vsdstdcelldesign and copy the file to vsdstdcelldesign directory
2. Open the inverter in magic and explore
3. Make a spice file of the inverter 
4. Edit the spice file
5. Run spice file for ngspice simulations
6. fix error in poly.9


```bash
# Change the directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository from this command
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the vsdstdcelldesign directory
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech

# Check if it is there or not
ls
```
Screenshot while copying it

![Screenshot (94)](https://github.com/user-attachments/assets/178e8d73-878d-497d-92c8-3748a24421d4)

Cheking if it is there or not

![Screenshot (93)](https://github.com/user-attachments/assets/a2195d18-6ebf-4d31-9b97-d92e95e450e8)

2. Open the inverter in magic

Command to open the inverter in magic

```bash

# Command to open inverter in magic
magic -T sky130A.tech sky130_inv.mag &

```
 Screenshot of inverter in magic

![Screenshot (96)](https://github.com/user-attachments/assets/c29498d6-5d6b-4426-b3b0-ca00c207caf3)
![Screenshot (95)](https://github.com/user-attachments/assets/d4d14350-0d69-46b1-9980-84277a917993)

NMOS

![Screenshot (97)](https://github.com/user-attachments/assets/3af3b05f-c055-40bb-8515-38a66683c5d3)

PMOS

![Screenshot (98)](https://github.com/user-attachments/assets/9ec3904f-9df7-4d13-ae5b-045991ef2b46)

Y output connected to PMOS and NMOS

![Screenshot (100)](https://github.com/user-attachments/assets/5864ec7c-3a38-48d1-9994-85c4028bca7e)

PMOS connected to VPWR


NMOS connected to VGND 

![Screenshot (105)](https://github.com/user-attachments/assets/2882b3f5-38b7-4d59-b56d-e9b66b37d4d1)

3. Make a spice file of the inverter
```bash
# Check current directory
pwd

# command to extract to .ext file
extract all

# command to set current threshold (cthresh) and resistance threshold (rthresh) to 0, meaning no thresholds are applied in the SPICE simulation, simplifying the model.

ext2spice cthresh 0 rthresh 0

# Convert from .ext to .spice
ext2spice
```
Screenshot of running these commands

![Screenshot (107)](https://github.com/user-attachments/assets/f4ff9434-b928-44bc-bf54-41a7f432482f)


Screenshot of spice file

![Screenshot (108)](https://github.com/user-attachments/assets/2895e4a6-b8ef-4de6-88ad-5f26d5333dc4)


Screenshot of the spice file

![Screenshot (106)](https://github.com/user-attachments/assets/9ba20a33-f1af-4259-aae1-90ba68671780)


Area of a block

![Screenshot (109)](https://github.com/user-attachments/assets/a53b5421-e070-4a9e-adc2-9adfaeae9e3b)

4. Edit the spice file

From this to
![Screenshot (108)](https://github.com/user-attachments/assets/0b0ce338-fc22-4282-a502-1a7f1a7bc70a)

This
![Screenshot (112)](https://github.com/user-attachments/assets/7772755e-9abc-468f-b49c-3b5b7b28d30a)


5. Run Spice file for ngspice simulations

```bash

# Commmand to run ngspice simulations
ngspice sky130_inv.spice

```
Scrrenshot of running ngspice

![Screenshot (113)](https://github.com/user-attachments/assets/921e69fb-d5cd-4477-8361-e709dda1674b)

```bash
# Command to load the plot(graph)
plot y vs time a

```
Plot
![Screenshot (114)](https://github.com/user-attachments/assets/76a9eab3-9235-4d58-919e-5acf597cdc3d)

Calculation for rise time

```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```

20% (660mV)

![Screenshot (116)](https://github.com/user-attachments/assets/c2f55c4a-97dd-499c-bb17-5bf79100223f)
![Screenshot (117)](https://github.com/user-attachments/assets/c620953d-ad82-4f0e-a1d7-21906dc73e0f)

80% (2.64V)

![Screenshot (120)](https://github.com/user-attachments/assets/23172beb-92db-4b31-aba4-cbd1fd0df7cf)
![Screenshot (119)](https://github.com/user-attachments/assets/ef78b270-5ec2-49d2-9695-956a0084c9b8)

```math
Rise\ transition\ time = Time\ taken\ for\ output\ to\ rise\ to\ 80\% - Time\ taken\ for\ output\ to\ rise\ to\ 20\%
```

```math
Rise\ transition\ time = 2.25221 - 1.125 = 1.12721\ ns = 1,127.21\ ps
```

Rise Cell Delay Calculation

```math
50\%\ of\ 3.3\ V = 1.65\ V
```

50% (1.65V)

![Screenshot (122)](https://github.com/user-attachments/assets/39f32a7d-aa78-42e0-89dd-deaba7c82927)
![Screenshot (121)](https://github.com/user-attachments/assets/54dc552b-16dc-4c14-be36-24dad4cd719d)

```math
Rise\ Cell\ Delay = Time\ taken\ for\ output\ to\ rise\ to\ 50\% - Time\ taken\ for\ input\ to\ fall\ to\ 50\%
```

```math
Rise\ Cell\ Delay = 2.21156 - 2.15016 = 0.0614\ ns = 61.4\ ps
```

Cell fall delay calculation

```math
50\%\ of\ 3.3\ V = 1.65\ V
```

50% (1.65V)

![Screenshot (124)](https://github.com/user-attachments/assets/0a5b9946-2120-4c88-b873-24297a21ef3c)
![Screenshot (123)](https://github.com/user-attachments/assets/5fc4c2ad-ac3c-4764-a095-a3e5ea02a212)


```math
Fall\ Cell\ Delay = Time\ taken\ for\ output\ to\ fall\ to\ 50\% - Time\ taken\ for\ input\ to\ rise\ to\ 50\%
```
```math
Fall\ Cell\ Delay = 4.07 - 4.05 = 0.02\ ns = 20\ ps
```

6. Fix error in poly.9

```bash
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool
magic -d XR &
```
Screenshot of running these commands

![Screenshot (125)](https://github.com/user-attachments/assets/7f9ee64d-53d4-4b75-97c3-27acbcfbd7f9)
![Screenshot (126)](https://github.com/user-attachments/assets/c3aa9dc9-59f3-455d-8415-9130dbab4531)

Screenshot of .magicrc file opened in GVim

![Screenshot (127)](https://github.com/user-attachments/assets/f93747c3-5f19-4e46-b26d-5863da35b932)

Fixing error in poly.9

poly rules
![Screenshot (132)](https://github.com/user-attachments/assets/7930262e-e7cb-4c88-abef-dc92de5432d9)

incorrect spacing

![Screenshot (136)](https://github.com/user-attachments/assets/48fe26fc-3f53-4424-801f-a6ad17333e39)


Changes in sky130A.tech file

![Screenshot (133)](https://github.com/user-attachments/assets/2f20feba-70c0-4a6e-af4a-0ef327d96f07)
![Screenshot (134)](https://github.com/user-attachments/assets/935e8c46-57aa-46db-bab8-874219122d9f)

```bash
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

![Screenshot from 2024-03-21 23-13-11](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b18e8e07-ef0f-40fb-9b6d-8aae878a23c6)
![Screenshot from 2024-03-22 00-00-40](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d5afe8d8-691b-485d-a89a-8f901e18b56e)

**Incorrectly implemented difftap.2 simple rule correction**

Screenshot of difftap rules

![Screenshot from 2024-03-22 00-14-47](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/086b7a66-b60a-470a-b5c0-a5ac938ebec3)

Incorrectly implemented difftap.2 rule no drc violation even though spacing < 0.42u

![Screenshot from 2024-03-22 00-14-36](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a2d0d739-2df5-4eb5-ab78-c80d366e24e4)

New commands inserted in sky130A.tech file to update drc

![Screenshot from 2024-03-22 00-26-43](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b5892f9b-9c5d-4b1b-baa2-6fe45f3965b1)

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

![Screenshot from 2024-03-22 00-29-22](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a3f92160-6701-48fb-b6cf-e4c41dc4a531)

**Incorrectly implemented nwell.4 complex rule correction**

Screenshot of nwell rules

![Screenshot from 2024-03-22 00-51-34](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/4ad4901d-0b9a-4339-89e3-7bb3fce2766d)

Incorrectly implemented nwell.4 rule no drc violation even though no tap present in nwell

![Screenshot from 2024-03-22 00-52-51](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/87da8944-0ad8-455d-97ec-3909eac656c3)

New commands inserted in sky130A.tech file to update drc

![Screenshot from 2024-03-22 01-03-42](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/886c6930-6314-4a6f-97d9-6b8423444ac0)
![Screenshot from 2024-03-22 01-04-04](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d9808e9a-42c2-4421-9b82-2ef65a5a1ad7)

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

![Screenshot from 2024-03-22 01-10-25](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/49b1004d-f860-4ca7-86f4-4d79784a01cf)

## Section 4 - Pre-layout timing analysis and importance of good clock tree

### Brief Overview

### Section 4 labs

* Section 4 tasks:-
1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
2. Save the finalized layout with custom name and open it.
3. Generate lef from the layout.
4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
6. Run openlane flow synthesis with newly inserted custom inverter cell.
7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
9. Do Post-Synthesis timing analysis with OpenSTA tool.
10. Make timing ECO fixes to remove all violations.
11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
12. Post-CTS OpenROAD timing analysis.
13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

* Section 4 - Tasks 1 to 4 files, reports and logs can be found in the following folder:

[Section 4 - Tasks 1 to 4 \(vsdstdcelldesign\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign)

* Section 4 - Task 4 files, reports and logs can be found in the following folder:

[Section 4 - Task 4 \(src\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src)

* Section 4 - Task 5 files, reports and logs can be found in the following folder:

[Section 4 - Task 5 \(picorv32a\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a)

* Section 4 - Tasks 6 to 8 & 11 to 13 logs, reports and results can be found in following run folder:

[Section 4 - Tasks 6 to 8 & 11 to 13 Run \(24-03_10-03\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03)

* Section 4 - Tasks 9 to 11 logs, reports and results can be found in following run folder:

[Section 4 - Tasks 9 to 11 Run \(25-03_18-52\)](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52)

#### 1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.

Conditions to be verified before moving forward with custom designed cell layout:
* Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
* Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.
* Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.

Commands to open the custom inverter layout

```bash
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

Screenshot of tracks.info of sky130_fd_sc_hd

![Screenshot from 2024-03-24 13-38-09](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2a35eb22-dd5f-4b67-9712-cbd2a84b526a)

Commands for tkcon window to set grid as tracks of locali layer

```tcl
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```

Screenshot of commands run

![Screenshot from 2024-03-24 13-49-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d0d9c106-4e05-4e73-a7ed-3f718cb69b42)

Condition 1 verified

![Screenshot from 2024-03-24 13-51-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b74b31c8-cdc7-4dcb-9467-5a1787bfa5fe)

Condition 2 verified

```math
Horizontal\ track\ pitch = 0.46\ um
```

![Screenshot from 2024-03-24 13-55-07](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e045e5b6-3592-4242-995d-de2049438ec5)

```math
Width\ of\ standard\ cell = 1.38\ um = 0.46 * 3
```

Condition 3 verified

```math
Vertical\ track\ pitch = 0.34\ um
```

![Screenshot from 2024-03-24 13-58-32](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a471b022-91ac-466a-8dd9-72b90f9c16c1)

```math
Height\ of\ standard\ cell = 2.72\ um = 0.34 * 8
```

#### 2. Save the finalized layout with custom name and open it.

Command for tkcon window to save the layout with custom name

```tcl
# Command to save as
save sky130_vsdinv.mag
```

Command to open the newly saved layout

```bash
# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vsdinv.mag &
```

Screenshot of newly saved layout

![Screenshot from 2024-03-24 14-33-20](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/0beb4300-2ebc-4364-8e3d-37fdb6d52f5b)

#### 3. Generate lef from the layout.

Command for tkcon window to write lef

```tcl
# lef command
lef write
```

Screenshot of command run

![Screenshot from 2024-03-24 14-35-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6928c3dc-e633-414d-9ac1-71349cad4b9b)

Screenshot of newly created lef file

![Screenshot from 2024-03-24 14-37-19](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/15557990-33b4-4402-8c72-39b75da9ed07)

#### 4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

Commands to copy necessary files to 'picorv32a' design 'src' directory

```bash
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Screenshot of commands run

![Screenshot from 2024-03-24 14-55-23](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/78559cee-ad3f-4301-83ae-df99f8417be3)

#### 5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow

```tcl
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory

![Screenshot from 2024-03-24 15-29-56](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7b18f216-1160-4a65-91fd-998495ad3175)

##Thanks I can do it till here only, thankyou for this oportunity I always wanted to know more in field of computer science and this coures made me do it 😊
