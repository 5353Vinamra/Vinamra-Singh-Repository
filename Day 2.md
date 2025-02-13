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
