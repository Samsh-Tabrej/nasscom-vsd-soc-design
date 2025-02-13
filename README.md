# Digital VLSI SoC Design and Planning
Welcome to the OpenLANE workshop organized by VSD in collaboration with NASSCOM! In this session, we will explore the complete process of designing an Application-Specific Integrated Circuit (ASIC) using the OpenLane ASIC flow. Starting from the Register Transfer Level (RTL) design, we will progress through various key stages to ultimately generate a Graphical Data System (GDS) file.

# Curriculum
- Introduction to open-source EDA tools and 130nm PDKs <br/>
- Floorplanning and standard cell design <br/>
- Designing and characterizing a library cell <br/>
- Pre-layout timing analysis and clock tree synthesis <br/>
- The final Leap: From RTL2GDS

# Breakdown of QFN-48 Chip, Pads, Core, Die, Macros & IPs
- QFN-48 Package<br/>
The QFN-48 (Quad Flat No-lead, 48-pin) package is a compact, surface-mount IC package designed for high-performance applications with efficient thermal dissipation and low parasitic effects. It features 48 connection pads around its edges and a central exposed pad for improved heat dissipation, making it ideal for space-constrained designs.<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/arduino%20chip.png) ![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/package.png)
- Core <br/>
The core is the central region of the chip where the main logic components are placed. It houses combinational circuits, standard cells, hard and soft IPs, and interconnections that define the chip’s functionality.
- Die <br/>
The die is the physical silicon area that contains both the core and the I/O pads. Multiple dies are fabricated on a single wafer, which is later cut into individual chips for packaging.
- Pads <br/>
I/O pads serve as the interface between the core and external connections, enabling communication with other components. These pads include input, output, and power pads, and are typically surrounded by pad cells that facilitate external bonding.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/core%2C%20pads%2C%20die.png)
- Macros and Foundry Ips <br/>
Macros are pre-designed functional blocks used within an integrated circuit (IC) to optimize design efficiency. They can be hard macros (pre-placed and routed, such as memory blocks or analog components) or soft macros (synthesizable and flexible, like digital logic modules). Foundry IPs (Intellectual Properties) are pre-verified circuit designs provided by semiconductor foundries to assist in chip design. These can include standard cells, memory compilers, I/O libraries, PLLs, ADCs, DACs, and high-speed interfaces.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/macros%2C%20ips.png)

# Overview of RISC-V ISA
The Instruction Set Architecture (ISA) defines how software communicates with hardware, acting as the intermediary between the code we write and the machine's operations. While high-level programming languages like C and Java are used to develop applications, machines can't understand them directly. Instead, ISA enables the translation of programs from assembly language to machine code that the hardware can execute. The RISC-V ISA is the latest open-source architecture designed for this purpose, providing a simple, efficient, and flexible instruction set that allows for customization and optimization in processor design.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/RISC-V%20ISA.png)

# From Software to Hardware 
In everyday use, we interact with application software (like apps) to perform tasks, but there’s a process happening behind the scenes to bridge the gap between the software and the hardware. This bridge is provided by system software, which sits between the applications and the hardware, translating software instructions into a format that the hardware can process—binary code.

System software involves:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/sw%20to%20hw.png)
- Operating System (OS): <br/> The OS manages core functions like input/output, memory management, and system-level tasks. It translates application requests into higher-level code, often in languages like C, C++, or Java, that the system can handle.
- Compiler: <br/> The compiler takes this code and converts it into machine-readable instructions, often creating executable files (e.g., .exe), which are tailored for the specific hardware.
- Assembler: <br/> The assembler further processes these instructions, turning them into binary code, the only language that the hardware can directly understand and execute to perform the necessary operations.

# ASIC design flow
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/asicflow.png)
ASIC design is a complex process that involves a series of steps to transform a design from Register Transfer Level (RTL) into the final GDSII layout file. The design flow integrates various tools and methodologies to ensure the final chip meets performance, area, and power requirements.
- Synthesis:<br/> The process where RTL code is converted into a gate-level netlist using a set of Standard Cell Libraries (SCLs), which defines the logic gates and their interconnections.
- Floorplanning:<br/> This step involves the arrangement of large functional blocks or macros on the chip layout and planning the power distribution network, which ensures efficient power delivery throughout the chip.
- Placement:<br/> In this phase, the individual cells and macros are positioned on the chip, both globally and with detailed adjustments, optimizing for area and performance.
- Clock Tree Synthesis (CTS):<br/> CTS aims to balance clock signal arrival times across the entire chip, minimizing clock skew and ensuring synchronous operation of all parts of the chip.
- Routing:<br/> The routing process connects the placed cells and macros using metal layers (e.g., SkyWater PDK uses up to 6 metal layers) to form the necessary interconnections between the logic blocks.
- Sign-Off Checks:<br/>
Design Rule Checking (DRC): Verifies that the physical design adheres to the foundry’s manufacturing rules, ensuring manufacturability.<br/>
Layout vs. Schematic (LVS): Compares the layout with the gate-level netlist to ensure there are no discrepancies.<br/>
Static Timing Analysis (STA): Analyzes the timing of signals across the design to ensure the chip meets the required timing constraints and operates reliably at high speeds.<br/> <br/>

To successfully design an open-source digital ASIC, a few fundamental elements are essential:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/asic1.png)
- RTL Designs<br>
Register-Transfer Level (RTL) design is a foundational stage in the VLSI design process, where the functionality of digital circuits is described in terms of data flow between registers and the logical operations performed on that data. It serves as the blueprint for the digital behavior of the ASIC, specifying how data is transferred and manipulated within the circuit.
- EDA Tools<br/>
Electronic Design Automation (EDA) tools are specialized software used to design, simulate, and verify integrated circuits (ICs). These tools help engineers test the functionality, timing, and performance of an IC, ensuring the design meets all required specifications, including power, area, and speed.
- PDK Data<br/>
A Process Design Kit (PDK) provides the necessary files and data to model the manufacturing process used in IC design. It includes:<br/>
Design Rules for fabrication, which help ensure the layout complies with manufacturing limitations (e.g., DRC, LVS, etc).<br/>
Device Models to simulate the behavior of various components.<br/>
Digital Standard Cell Libraries for logic functions, and I/O Libraries for interfacing with external systems. These elements guide the design and ensure that the resulting ASIC can be manufactured reliably.<br/>

# Introduction to OpenlANE and StriVe chipsets
OpenLANE is an open-source ASIC design flow that provides a comprehensive toolchain for digital design, from RTL to GDSII, supporting custom chip development. It integrates several EDA tools for synthesis, placement, routing, and verification. It is a tape-out-hardened flow that addresses two main use cases: hardening a macro and integrating a System-on-a-Chip (SoC). It was used successfully to tape out a family of RISC-V based SoCs known as “striVe”.<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/striVe.png)
StriVe chipsets are customizable, energy-efficient processors designed for specialized applications, focusing on low-power and high-performance computing. They leverage open-source frameworks like OpenLane to enable rapid prototyping and development of ASICs.

# Inception of open-source EDA, OpenLANE and Sky130 PDK
# DAY-1 LAB
# The openlane directory structure
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/openlane_dir.png)
We have to run the picorv32a design synthesis using openLANE flow and generate design statistics and synthesis reports.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/picorv32a_dir.png)
<br/>
To invoke openLANE flow and perform the synthesis we use the following commands inside openlane folder in terminal:<br/>
To invoke openLANE flow
```
docker
```
To run the flow in interactive (step-by-step) mode
```
./flow.tcl -interactive
```
Import required packages
```
% package require openlane 0.9
```
To prepare the picorv32a design and setup necessary folders and files for synthesis
```
% prep -design picorv32a
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/openlane_docker.png)
After running the preparation step, a new directory with modified date as name is created inside 'runs' directory. This directory contains all the necessary files and subdirectories required for storing the synthesis reports and outputs.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/design_prep_runs.png)
<br/>
Ater this, to run the synthesis:
```
run_synthesis
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/synthesis_run.png)
Type ```exit``` to exit from the openLANE flow.<br/><br/>
After this, we can check the synthesis results and statistics & timing reports from the previously created directory itself.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/syn_report.png)
<br/>Inside 1-yosys_4.stat.rpt, the synthesis statistics report is stored.<br/>
From this we can calculate the flop ratio:<br/>
Flop ratio = (Total no. of D-FFs)/(Total no. of cells)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/dff_ratio.png)
From the statistics report we get flop ratio as: 1613/14876 = 0.108429685<br/>
Hence, the percentage of D-FFs are 10.84%<br/>

# Good floorplan vs bad floorplan and introduction to library cells
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/w_h_core.png)
Utilization Factor and Aspect Ratio:<br/>
To determine the Utilization Factor and Aspect Ratio, it is essential to first define the height and width of both the core and die areas.<br/>
The core area refers to the region within a chip that accommodates all the logic cells and circuit components. This is where the primary logic operations take place.<br/>
The die area, on the other hand, encompasses the core and serves as the space for placing I/O components and connections.<br/>
The dimensions of the core area are determined by the netlist of the design, which specifies the number of components required to implement the logic. Consequently, the height and width of the die area are dictated by the dimensions of the core area.<br/><br/>
For instance, consider a netlist consisting of two logic gates and two flip-flops, each occupying an area of 1 square unit. Since the netlist includes a total of four elements, the minimum core area required to accommodate these components would be 4 square units.<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/eg_netlist.png) ![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/w_h_netlist.png)
Utilization Factor: <br/>
The Utilization Factor is the ratio of the area occupied by the netlist to the total available core area. For an optimized FloorPlan, the Utilization Factor should be less than 1. If it reaches 1, there won’t be any extra space for adding additional logic, making the FloorPlan 100% utilized. <br/>
Utilization Factor = Area occupied by netlist / Total core area <br/>

Aspect Ratio: <br/>
The Aspect Ratio represents the proportion between the height and width of the core. A core with an aspect ratio of 1 forms a square, whereas any other value results in a rectangular shape.<br/>
Aspect Ratio = Height of the core / Width of the core<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/min_area_netlist.png)

In this case,<br/>
Utilization Factor = (4 x 1 sq. unit)/(2 unit x 2 unit) = 1<br/>
Hence, the core area is 100% utilized by the netlist.<br/>
Aspect Rtio = (2 unit)/(2 unit) = 1<br/>
Hence, the core has a square shape.<br/>
​
<br/>Now, after adding pre-placed cells, decoupling capacitors, power planning and pin placement the corresponding floorplan will look like:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_concepts.png)

# Running Floorplan using OpenLANE
# DAY-2 LAB
After running Synthesis, now it's time to run the Floorplan. To run floorplan in openLANE flow:
```
run_floorplan
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_run.png)
<br/><br/>When navigating though results/floorplan/ directory, we get a 'def' file, which includes many informations such as die area.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_diearea.png)
<br/><br/>To visualize the floorplan design using a GUI, we use MAGIC tool.<br/>
```magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_dir.png)
<br/><br/>The picorv32a floorplan layout in Magic:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/magic_fp.png)
Magic tool Guidelines:<br/>
> Centering the Design:
- Press ```S``` to select the entire design.
- Press ```V``` to align it to the center of the screen.<br/>
> To zoom a Specific Area:
- Left-click and drag to highlight the desired region.
- Right-click to open the context.
- Press ```Z``` to zoom in on the selected section.<br/>
> Viewing Cell Details:
- Hover over the cell you want to inspect.
- Press ```S``` to select the cell.
- In the 'tkcon' window, type ```what``` to display detailed information about the cell.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/tkcon_fp.png)

# Running Placement using OpenLANE
Placement in VLSI (Very Large Scale Integration) refers to the process of assigning the physical locations of standard cells, macros, and IP blocks within a chip’s layout while optimizing for performance, power, and area (PPA). It occurs after logic synthesis and before routing in the backend design flow. 
<br/>Placement can be categorized into global placement, which provides an initial distribution of cells to minimize wirelength and congestion, and detailed placement, which fine-tunes cell positions while adhering to design rules, avoiding overlaps, and optimizing timing. Advanced techniques like analytical, partitioning-based, and simulated annealing methods are used to enhance placement efficiency in modern chip designs.<br/><br/>
After doing floorplan of desired utilization factor and aspect ratio, now its time to place the specific netlist on the core of the chip. This must be done by keeping mind, the IO pins, the interconnects, and keeping the standard cells as close as possible to reduce the timimg delays due to larger wire lengths. At places where distance between two standard cells or a standard cell and IO pin is relatively larger, we have to add buffers to minimize the wire length.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/wiring_plcmt.png)
<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/detailed_plcmt.png)
<br/>
To run the placement in OpenLANE flow:
```
run_placement
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/plcmt_run.png)
<br/>
To visualize the placement in Magic tool: ```magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/magic_plcmt.png) ![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/zoomed_plcmt.png)
<br/>
In the placement process, each sigle cell (eg. Inverter) from the library has specific design flow that are classified into three different parts:<br/>
> Inputs
- PDKs
- DRC and LVS rules
- SPICE models
- Library & User-defined specs
> Design Steps
- Circuit design
- Layout Design
- Characterization using GUNA
> Outputs
- CDL (Circuit Description Language)
- GDSII
- LEF (Library Exchange Format)
- SPICE extracted netlist
- Timing, Noise, and Power Libraries

<br/>Typical Characterization flow for a CMOS inverter circuit:
1. Reading model files (eg. PMOS or NMOS models).
2. Read extracted SPICE netlist.
3. Recognize the behaviour of the buffer.
4. Read sub-circuits of the inverter.
5. Attach necessary power sources.
6. Apply the stimulus to the characterization setup.
7. Provide necessary output load capacitance.
8. Provide necessary simulation command (eg., .tran or .dc).
9. Feed in the configuration file to GUNA software which will generate the timing, noise, power, .libs, etc models.

<br/>Timing Characterization in VLSI Design:<br/>
Timing characterization in VLSI design refers to the process of analyzing and modeling the behavior of a standard cell or a circuit concerning signal propagation delays, transition times (slew), and setup/hold constraints. It helps in generating timing libraries (e.g., Liberty .lib files) used for Static Timing Analysis (STA).

<br/>Key Timing Parameters:<br/>
- Timing Threshold: These are predefined voltage levels (expressed as a percentage of supply voltage, VDD) used to measure delays and transitions in a digital circuit.
- Propagation Delay: The time it takes for a signal transition to travel from the input to the output of a gate. It is measured between the same voltage thresholds on input and output, typically from 50% of input swing to 50% of output swing.
- Slew Rate (Transition Time): The time taken for a signal to transition between two voltage thresholds.
- Slew Low Rise Threshold (slew_low_rise_thr): The lower voltage threshold used to measure the rise transition time (e.g., 20% of VDD).
- Slew High Rise Threshold (slew_high_rise_thr): The upper voltage threshold for rise time measurement (e.g., 80% of VDD).
- Slew Low Fall Threshold (slew_low_fall_thr): The lower voltage threshold for fall time measurement (e.g., 20% of VDD).
- Slew High Fall Threshold (slew_high_fall_thr): The upper voltage threshold for fall time measurement (e.g., 80% of VDD).
- Input Rise Threshold (in_rise_thr): The voltage threshold used to measure rising transitions at the input.
- Input Low Threshold (in_low_thr): The voltage threshold used to measure falling transitions at the input.
- Output Rise Threshold (out_rise_thr): The voltage threshold used to measure rising transitions at the output.
- Output Low Threshold (out_low_thr): The voltage threshold used to measure falling transitions at the output.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/timing_slew.png)

# Design library cell using Magic Layout and ngspice characterization
# DAY-3 LAB
Let us clone a custom inverter standard cell from a github repository and explore its layout in Magic.<br/><br/>
#clone the repo inside openlane directory ```git clone https://github.com/nickson-jose/vsdstdcelldesign```<br/><br/>
#copy the path of sky130.tech file into the vsdstdcelldesign directory ```cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign```<br/><br/>
#Open the layout in Magic ```magic -T sky130A.tech sky130_inv.mag &```<br/><br/>
Screenshot of above commands in terminal.
![Screenshot of above commands in terminal](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/inv_git_clone.png)
<br/>Layout of custom CMOS inverter in Magic.
![Layout of custom CMOS inverter in Magic](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/magic_inv.png)

<br/>Extraction of the Spice file of inverter from Magic:<br/><br/>
In the tkcon window type ```pwd``` to print working directory.<br/><br/>
To extract into .ext format: ```extract all```<br/><br/>
Before converting ext to spice, enable the parasitic extraction: ```ext2spice cthresh 0 rthresh 0```<br/><br/>
Converting the .ext to .spice: ```ext2spice```<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/tkcon_extract.png)
<br/>Modify the spice model file for analysis, according to the libs file present.<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/inv_spice.png)
<br/><br/>Run the extracted spice model: ```ngspice sky130_inv.spice```<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/spice_run.png)
<br/><br/>To plot the characteristics of output and input waveforms with respect to time: ```plot y vs time a```<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/y_vs_a_plot.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/time_n_delay.png)
<br/><br/>From this plot we can calculate various parameters related to timings and delays of the CMOS inverter characteristics.<br/><br/>
Characterizing the parameters:<br/><br/>
Rise Time: The time taken for the output waveform to transition from 20% to 80% of its maximum value.<br/>
Using data points:<br/>
x0 = 2.18257e-09, y0 = 0.66<br/>
x1 = 2.24684e-09, y1 = 2.64<br/>
Rise time = x1 - x0 = 0.06427 ns<br/><br/>
Fall Time: The time taken for the output waveform to transition from 80% to 20% of its maximum value.<br/>
Using data points:<br/>
x0 = 4.07995e-09, y0 = 2.64<br/>
x1 = 4.09524e-09, y1 = 0.66<br/>
Fall time = x1 - x0 = 0.01529 ns<br/><br/>
Propagation Delay: The time taken for a 50% transition at the output(low to high) corresponding to a 50% transition at the input(high to low).<br/>
Using data points:<br/>
x0 = 2.21153e-09, y0 = 1.65018<br/>
x1 = 2.14988e-09, y1 = 1.65018<br/>
Propagation delay = x1 - x0 = 0.06165 ns<br/><br/>
Cell Fall Delay: The time taken for a 50% transition at the output(high to low) corresponding to a 50% transition at the input(low to high).<br/>
Using data points:<br/>
x0 = 4.078e-09, y0 = 1.65007<br/>
x1 = 4.05e-09, y1 = 1.65007<br/>
Cell fall delay = x1 - x0 = 0.028 ns<br/>

# Fixing DRC errors in the Layout geometries
<br/>Commands to download and view the magic tech file and associated files to perform DRC corrections:<br/><br/>
Move to home directory: ```cd```<br/><br/>
Download the lab files: ```wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz```<br/><br/>
Extract the compressed file: ```tar xfz drc_tests.tgz```<br/><br/>
List all the files and directories in it: ```ls -al```<br/><br/>
Open the .magicrc file in vim: ```vi .magicrc```<br/><br/>
Command to open magic tool in better graphics: ```magic -d XR```<br/><br/>

![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/runn_magic.png)
<br/>Screenshot of .magicrc file:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/magicrc_file.png)
<br/><br/>Opening metal-3 mag file to view the drc errors:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/m3_mag_file.png)
<br/><br/>Import poly .mag file to check drc errors and fix them:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/poly_mag.png)
<br/><br/>As zooming into the poly.9 and creating a box, we can see the errors and edit the sky130A.tech file to fix it. 
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/poly_box.png)
<br/><br/>By adding allpolynonres into the specified locations in the sky130A tech file, we can fix it.<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/poly_vim_1.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/poly_vim_2.png)

Run these commands in the tkcon window:<br/>
Loading updated tech file: ```tech load sky130A.tech```<br/>
Re-running DRC check to see updated DRC errors: ```drc check```<br/>
Select the space, and getting the error messages ```drc why```<br/>
<br/><br/>Checking the poly mag file:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/poly_check.png)
<br/><br/>Incorrectly implemented 'difftap.2' rule, no drc violation even though spacing < 0.42u:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/diff_2.png)
<br/><br/>The periphery rules for poly.9 as mentioned by sky130PDK:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/rules_poly.png)

<br/><br/>Fixing incorrectly implemented nwell.4 rule(no tapp present in nwell, i.e., untapped):<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/nwell_mag.png)
<br/><br/>Adding untapped nwell, subtracting other tapped nwell and setting all variants to 'full' in the sky130A.tech file:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/nwell_vi_1.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/nwell_vi_2.png)
<br/><br/>The periphery rules for nwell.4 as mentioned by sky130PDK:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/nwell.4_rules.png)
<br/><br/>Run these commands in the tkcon window:<br/>
Loading updated tech file: ```tech load sky130A.tech```<br/>
Re-running DRC check to see updated DRC errors: ```drc check```<br/>
Select the space, and getting the error messages ```drc why```<br/>
<br/>Checking the nwell mag file:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/nwell_check.png)

# Pre-layout timing analysis and importance of good clock tree
Introduction to Delay Tables:<br/>
Delay tables play a critical role in timing analysis by providing a detailed representation of how signals propagate through various circuit components. These tables contain information about the delay characteristics of standard cells, interconnects, and macros, helping designers predict signal arrival times accurately.

<br/>Purpose of Delay Tables:<br/>
In modern VLSI design, achieving precise timing closure is crucial to ensure the circuit operates correctly at the desired clock frequency. Delay tables contribute to this by:<br/>
- Modeling propagation delays through logic gates and interconnects.
- Assisting timing analysis tools in evaluating signal transitions.
- Enabling optimization of placement and routing based on real-time delay estimations.

<br/>During physical design, delay tables serve multiple functions:<br/>
- Cell Characterization: Standard cells (such as NAND, NOR, and flip-flops) are characterized using delay tables based on factors like input transition time and output load capacitance.
- Interconnect Modeling: Delays due to routing and parasitics are estimated using lookup tables derived from extracted parasitic data.
- Static Timing Analysis (STA): Timing verification tools use delay tables to compute worst-case and best-case timing scenarios, ensuring that setup and hold requirements are met.

<br/>Types of Delay Representation:<br/>
- Library Characterization Data (Lib Files) – These include lookup tables (LUTs) that provide delays based on input slew and output capacitance.
- Parasitic Delay Models (SPEF, RSPF) – Account for wire delays and coupling effects.
- Propagation Delay Tables – Define delays for individual gates under different operating conditions.

# DAY-4 LAB
Commands to open the custom inverter layout.<br/>
Change directory to vsdstdcelldesign: ```cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign```
<br/>Command to open custom inverter layout in magic: ```magic -T sky130A.tech sky130_inv.mag &```
<br/>Screenshot of tracks.info of sky130_fd_sc_hd:<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/tracks_info.png)
<br/>Commands for tkcon window to set grid as tracks of locali layer
<br/>Get syntax for grid command ```help grid```
<br/>Set grid values accordingly ```grid 0.46um 0.34um 0.23um 0.17um```

<br/>Once the three conditions are verified, i.e.,
<br/>Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
<br/>Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.
<br/>Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.
<br/>Save the custom inverter layout: ```save sky130_vsdinv.mag```<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/grid_save_magic.png)
<br/>Command to open the newly saved custom inverter layout in magic: ```magic -T sky130A.tech sky130_vsdinv.mag &```<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/magic_new_inv.png)
<br/>Now generate the lef file from Layout.
<br/>Command for tkcon window to write lef: ```lef write```<br/><br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/write_lef.png)
<br/><br/>The screenshot of the generated lef file is shown below:<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/lef_inv.png)

<br/>Now, Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
<br/>Commands to copy necessary files to 'picorv32a' design 'src' directory
<br/>Copy lef file: ```cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/```
<br/>Copy lib files: ```cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/```<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/copy_files.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/picorv_src_new.png)

<br/>Now, modify the config.tcl file as below, adding the fast, slow and typical libraries:
```
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib" 
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```
<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_config.png)

<br/>Run openlane flow synthesis with newly inserted custom inverter cell.
<br/>inside openlane 0.9: ```%prep -design picorv32a -tag 31-01_17-10 -overwrite```
<br/>Additional commands to include newly added lef to openlane flow:
<br/>```set lefs [glob $::env(DESIGN_DIR)/src/*.lef]```
<br/>```add_lefs -src $lefs```<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_docker.png)
<br/><br/>Now the design is ready for synthesis: ```run_synthesis```<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_syn_run.png)
<br/><br/>Commands to view and change parameters to improve timing and run synthesis:
```
# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) 1

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```
<br/>Now, run the floorplan ```run_floorplan```<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_failed.png)
<br/><br/>As in above case the floorplan is failed to execute, run the following command to succesfully run floorplan:
```
init_floorplan
place_io
tap_decap_or
```
<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_fp.png)
<br/><br/>Now we'll run placement: ```run_placement```<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/plcmt_new.png)
<br/><br/>To view placement in Magic tool:
<br/>Change directory to path containing generated placement def:
```cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-01_17-10/results/placement/```
<br/>Command to load the placement def in magic tool:
```magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &```
<br/><br/>Screenshot of the placement implementation in Magic:<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/magic_plcmt_NEW.png)
<br/><br/>Screenshot of the custom inverter successfully inserted in the placement<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/inv_in_plcmt.png)
<br/><br/>To view the internal connections:<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/expand_inv_plcmt.png)<br/>

# Post-synthesis timing analysis with OpenSTA tool
Newly created pre_sta.conf for STA analysis in openlane directory<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pre_sta_conf.png)
<br/><br/>Newly created my_base.sdc for STA analysis in picorv32a/src directory based on the file openlane/scripts/base.sdc<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/my_base_sdc.png)
<br/><br/>The modified values like capacitance is taken from the libs file:<br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/libs_inv_8.png)
<br/>
To run the Static Timing Analysis(STA) in other terminal:<br/>
```
\# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

\# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/sta1.png)
We get a wns and slack violated value of -36.62 and tns value of -3854.15, which is very high.<br/><br/>
Now, running the synthesis for minimized slack violation:<br/>
```
# prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Additional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Command to set reduce MAX_FANOUT to 4
echo $::env(SYNTH_MAX_FANOUT) 4

# Now that the design is prepped and ready, we can run synthesis
run_synthesis
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/re_synth.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/syn_results.png)
<br/>Now the tns and wns value is minimized to 0.00.

<br/>Again running STA to reduce slack violations by manually reducing delays:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/sta_2.png)
<br/><br/>Here we got the max delay as 0.81 (of '_02560_' net)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/max_delay_net.png)
<br/><br/>To reduce this delay we have to replace the cell under driver pins of desired net:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/config_delays_sta.png)
<br/><br/>Again running the STA and checking wether the maximum delay and slack is reduced:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/sta_3.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/max_delay_reduced.png)
<br/><br/>As we can clearly see, the delay and slack is reduced by a significant factor.
<br/>To do basic timing ECO: ```report_checks -from _35312_ -to _35239_ -through _32503_```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/timing_ECO.png)

<br/>Now, replace some more cells to increase the ports and reduce the salck:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/replace_cell1.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_slack_dec.png)
<br/><br/> Initially the wns & slack violation was -36.62 and tns was -3854.15, but now wns & slack violation is -3.82(~89.5% reduction) and tns is -326.38(~91.5% reduction).
<br/><be/>Now, overwrite this verilog file on the previous picorv32a verilog file that we got by synthesis: 
```write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-01_17-10/results/synthesis/picorv32a.synthesis.v```
<br/>Exit from OpenSTA: ```exit```
Let's check whether our verilog file is being overwritten:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_syn_verilog.png)
<br/><br/>Checking cell 22390 that we changed recently, and got that it is being changed. Hence the verilog file is overwritten successfully.
<br/>Now run floorplan```run_floorplan```, placement```run_placement``` and cts(clock tree synthesis) ```run_cts```.
<br/><br/>Let's check some parameters like clock buffer list, root buffer, capacitance, etc based on the cts.tcl file:
<br/><br/>Screenshot of cts.tcl file:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/cts_tcl.png)
<br/><br/>Screenshot of displaying parameters and invoking openROAD ```openroad```.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/openroad.png)

# Post-CTS OpenROAD timing analysis
The commands required to succesfully implement OpenROAD:
```
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/31-01_17-10/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/31-01_17-10/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/31-01_17-10/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all clocks as propagated clocks
set_propagated_clock \[all_clocks\]

# Check syntax of \'report_checks\' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/openroad_cmds.png)
<br/><br/>This will generate a hold and a setup report:
<br/>Screenshot of Hold report:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/hold_report.png)
<br/><br/>Screenshuot of Setup report
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/setup_report.png)
<br/><br/>Inboth the cases the timing slack is 'MET' and not violated.
<br/>But we can improve the slack even more, even though it has negative effect like increase in area. We can reduce the slack by removing the 'clkbuf_1' from the buffer list.
```
# Checking current value of \'CTS_CLK_BUFFER_LIST\'
echo \$::env(CTS_CLK_BUFFER_LIST)

# Removing \'sky130_fd_sc_hd\_\_clkbuf_1\' from the list
set ::env(CTS_CLK_BUFFER_LIST) \[lreplace \$::env(CTS_CLK_BUFFER_LIST) 0 0\]

# Checking current value of \'CTS_CLK_BUFFER_LIST\'
echo \$::env(CTS_CLK_BUFFER_LIST)

# Checking current value of \'CURRENT_DEF\'
echo \$::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF)/openLANE_flow/designs/picorv32a/runs/17-01_14-04/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of \'CTS_CLK_BUFFER_LIST\'
echo \$::env(CTS_CLK_BUFFER_LIST)
```
<br/><br/>Screenshot of code implementation:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/run_new_cts.png)
```
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/17-01_14-04/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/17-01_14-04/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/17-01_14-04/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty \$::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit
```
<br/><br/>Screenshot of code implementation:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_openroad.png)

<br/><br/>New setup and hold reports:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_hold.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/new_setup.png)

<br/><br/>It can be clearly noted that the setup has improved by 5.9ps and the hold has improved by 738.2ps which is quite significant.

<br/><br/>We can reinsert the clkbuf_1 into the buffer list after the openroad implementation:
```
# Checking current value of \'CTS_CLK_BUFFER_LIST\'
echo \$::env(CTS_CLK_BUFFER_LIST)

# Inserting \'sky130_fd_sc_hd\_\_clkbuf_1\' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) \[linsert \$::env(CTS_CLK_BUFFER_LIST) 0
sky130_fd_sc_hd\_\_clkbuf_1\]

# Checking current value of \'CTS_CLK_BUFFER_LIST\'
echo \$::env(CTS_CLK_BUFFER_LIST)
```
<br/><br/>Screenshot of code implementation:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/reinsert_clk_buf_1.png)

# Final steps for RTL2GDS using tritonRoute and openSTA
# DAY-5 LAB
Generation of Power Distribution Network(PDN) and exploring the layout in Magic:
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# Since we have aliased the long command to \'docker\' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using
the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now we have to prep the design  
prep -design picorv32a -tag 31-01_17-10

# Check current def
echo  $::env(CURRENT_DEF)

# Now that CTS is done we can do power distribution network
gen_pdn
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pdn_docker.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pdn_info.png)
<br/><br/>After running pdn, if we check CURRENT_DEF: ```echo  $::env(CURRENT_DEF)```, it is now changed from 'picorv32a.cts.def' to '17-pdn.def'<br/><br/>
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pdn_end_def.png)

<br/><br/>Now run routing: ```run_routing```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/0_violn_rout.png)
i.e., zero violations while running the routing process.

<br/><br/>Now to load the PDN DEF in Magic:
```
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-01_17_10/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 17-pdn.def &
```
<br/><br/>Screenshots of final PDN layout in Magic:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pnr1.png)
<br/><br/>Zoomed_in:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pnr2.png)
<br/><br/>Exploring the Layout and getting idea of design:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pnr3.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pnr4.png)
<br/><br/>PDN def image:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/pico_def.png)
<br/><br/>Post-routing setup and hold STA report:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/hold_fnl.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/setup_fnl.png)

<br/><br/>
# Acknowledgements
- Kunal Ghosh, Co-founder, VLSI System Design.<br/>
- Nickson P Jose, Technical Lead, HCLTech.<br/>
- R. Timothy Edwards, Senior Vice President of Analog and Design, Efabless Corporation.<br/>
