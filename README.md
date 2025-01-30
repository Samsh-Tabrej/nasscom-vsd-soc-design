# Digital VLSI SoC Design and Planning
Welcome to the OpenLane workshop organized by VSD in collaboration with NASSCOM! In this session, we will explore the complete process of designing an Application-Specific Integrated Circuit (ASIC) using the OpenLane ASIC flow. Starting from the Register Transfer Level (RTL) design, we will progress through various key stages to ultimately generate a Graphical Data System (GDS) file.

# Curriculum
- Introduction to open-source EDA tools and 130nm PDKs <br/>
- Floorplanning and standard cell design <br/>
- Designing and characterizing a library cell <br/>
- Pre-layout timing analysis and clock tree synthesis <br/>
- The final Leap: From RTL2GDS

# Breakdown of QFN-48 Chip, Pads, Core, Die, Macros & IPs
- QFN-48 Package<br/>
The QFN-48 (Quad Flat No-lead, 48-pin) package is a compact, surface-mount IC package designed for high-performance applications with efficient thermal dissipation and low parasitic effects. It features 48 connection pads around its edges and a central exposed pad for improved heat dissipation, making it ideal for space-constrained designs.
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/arduino%20chip.png)
![](https://github.com/Samsh-Tabrej/nasscom-vsd-soc-design/blob/main/media/package.png)
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

# Introduction to Openlane and StriVe chipsets
OpenLANE is an open-source ASIC design flow that provides a comprehensive toolchain for digital design, from RTL to GDSII, supporting custom chip development. It integrates several EDA tools for synthesis, placement, routing, and verification. It is a tape-out-hardened flow that addresses two main use cases: hardening a macro and integrating a System-on-a-Chip (SoC). It was used successfully to tape out a family of RISC-V based SoCs known as “striVe”.<br/>
StriVe chipsets are customizable, energy-efficient processors designed for specialized applications, focusing on low-power and high-performance computing. They leverage open-source frameworks like OpenLane to enable rapid prototyping and development of ASICs.
