# Vinamra-Singh-Repository
## Advanced Physical Design Using OpenLane/Sky130
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

#### Section 1 Lab Tasks

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

Screenshots of every Lab activities


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

#### Section 2 Lab Tasks

1. Run 'picorv32a' floorplan using OpenLANE flow and get the Output
2.

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
























