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
