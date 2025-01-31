# Vinamra-Singh-Repository
## Brief Overview
### Section 1
#### Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs
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
#### Introduction to RISCV-V
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

### Introduction to All Components of Open-Source Digital ASIC Design
#### What is Digital ASIC Design?
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

### Simplified RTL-to-GDSII Flow
The RTL-to-GDSII flow is the complete ASIC design process, from writing RTL code to generating a GDSII file for fabrication.

#### Simplified RTL2GDS Flow:
RTL Design – Write the hardware logic in Verilog.
Logic Synthesis (Yosys) – Convert RTL to a gate-level netlist.
Floorplanning (OpenROAD) – Define chip layout constraints.
Placement (RePLace) – Arrange standard cells.
Clock Tree Synthesis (TritonCTS) – Balance clock distribution.
Routing (TritonRoute) – Connect logic components using metal layers.
DRC & LVS Checks (Magic, Netgen) – Ensure manufacturability.
GDSII Generation – Export the final layout for fabrication.
Each step uses open-source tools, eliminating the need for proprietary software.

### Introduction to OpenLANE and Strive Chipsets
#### What is OpenLANE?
OpenLANE is an open-source ASIC design flow developed by efabless, built on tools like:

Yosys – Logic synthesis.
OpenROAD – Placement, CTS, routing.
Magic & KLayout – Layout visualization and DRC checks.
Netgen – LVS verification.
Fault – DRC rule checking.
Strive Chipsets
Strive chipsets are RISC-V based open-source designs developed using OpenLANE, demonstrating a fully open-source ASIC implementation.

### Introduction to OpenLANE Detailed ASIC Design Flow
#### In-Depth OpenLANE Flow
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

## Section 1 Labs

### Run "picorav32a" synthesis using OpenLane and generat output

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











