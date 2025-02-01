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
After running Synthesis, now it's time to run the Floorplan. To run floorplan in openLANE flow:
```
run_floorplan
```
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_run.png)
<br/><br/>When navigating though results/floorplan/ directory, we get a 'def' file, which includes many informations such as die area.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_diearea.png)
<br/><br/>To visualize the floorplan design using a GUI, we use MAGIC tool.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/fp_dir.png)
<br/><br/>The picorv32a floorplan layout in Magic:
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/magic_fp.png)
Magic tool Guidelines:<br/>
Centering the Design:
- Press ```S``` to select the entire design.
- Press ```V``` to align it to the center of the screen.
<br/>To zoom a Specific Area:
- Left-click and drag to highlight the desired region.
- Right-click to open the context.
- Press ```Z``` to zoom in on the selected section.
<br/>Viewing Cell Details:
- Hover over the cell you want to inspect.
- Press ```S``` to select the cell.
- In the 'tkcon' window, type ```what``` to display detailed information about the cell.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/tkcon_fp.png)
