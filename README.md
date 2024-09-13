![VSD-Logo](https://github.com/user-attachments/assets/c5fed76c-83e9-4839-810f-16963bd59484)

# **NASSCOM VSD DIGITAL VLSI SOC Design and Planning**

- This workshop, organized by **VLSI SYSTEM DESIGN (VSD) in collaboration with NASSCOM, focuses on Digital VLSI SoC (System on Chip) design and planning**.

- This workshop focuses on SoC design and planning, specifically using the Google-SkyWater 130nm open-source process and the OpenLANE flow. It guides us through the Physical Design (PnR) process, transforming an RTL netlist into a finalized chip design, covering the challenges of each stage. The workshop aims to empower participants to explore ASIC design flow and create their own chips, leveraging this innovative, open-source technology for accessible and automated chip design.


# DAY-1 

# Sky130 - Inception of open-source EDA, OpenLANE and Sky130 PDK
# Section-1 : How to talk to computers
## L1 - Introduction to QFN-48 Package, chip, pads, core, die, and IPs

- A **PACKAGE** refers to the physical enclosure that surrounds an integrated circuit (IC) or electronic component. It provides both mechanical protection and electrical connections between the component (like a chip or IC) and the circuit board (PCB). The package type is important as it impacts the size, assembly method, and performance of the electronic circuit. So here in our workshop, we use **QFN-48 (Quad Flat No-lead) package**,  It is a type of surface-mount integrated circuit package. The number "48" refers to the number of pins or connections it has, meaning it has 48 leads. These leads are usually exposed on the bottom of the package instead of extending out like traditional leads in other IC packages.
- A package is the outer shell or enclosure that surrounds the chip (also known as the die) inside. The chip is the actual semiconductor component where all the electronic circuits and functions are embedded, while the package provides the necessary protection and external connections for the chip to communicate with other components on a circuit board. which is shown in the below figure,

![vg](https://github.com/user-attachments/assets/09c2db49-e366-43fd-8938-bd9f3e1794ab)

- Inside the package, **wire bonds** are tiny wires (usually made of gold, aluminum, or copper) that connect the internal chip to the external leads or pads on the package. These wire bonds allow electrical signals, power, and data to flow between the chip and the circuit board, enabling the chip to function in electronic devices.
- The QFN-48 PACKAGE with size 7nm x 7nm is shown below.

![Screenshot (509)](https://github.com/user-attachments/assets/53d8b313-47a6-4261-904c-bcd2b7764f9d)

![Screenshot (507)](https://github.com/user-attachments/assets/1d330338-f6a4-42ba-9ece-012f640e2784)

- In the above figure, the chip which is originated in the middle shares the signals to the external world using **PADS**.

### **PADS** :
  - Pads are critical for making electrical connections between components and the different parts of a package.
  
### **DIE** :
  - The die is the size of the actual chip within an integrated circuit (IC). It contains the transistors and other electronic components.
  
### **CORE** :
  - A core refers to the main processing unit of a chip. Like all the digital logic takes place. It is a section of the die that performs 
    computing tasks by executing instructions. Modern processors often have multiple cores (e.g., quad-core, octa-core), allowing them to 
    perform multiple tasks simultaneously (multithreading/multiprocessing).

  ![JNSKJDS](https://github.com/user-attachments/assets/839d3067-abb9-4deb-bd4f-2d1d1726d91d) 

- A typical chip consists of a SOC, SRAM, ADC, DAC, PLL, and other components. The PLL, ADC, DAC, and SRAM are actually Foundry IPs.
  
### **Foundry** :
  - A foundry is a company that manufactures semiconductor chips for other companies. The foundry doesn't design the chips; it only 
    handles the fabrication process.These companies, like TSMC (Taiwan Semiconductor Manufacturing Company) and GlobalFoundries, 
    specialize in the production of semiconductor chips but do not design their own.

### **Foundry IPs (Intellectual Property)** :
  - IPs require significant expertise and intelligence to build particular Blocks. It actually refers to pre-designed and verified 
    building blocks 
    (often called IP blocks) that a foundry offers to chip designers. These IPs help designers accelerate the development of their chips 
    without having to design everything from scratch.

   ![Screenshot (513)](https://github.com/user-attachments/assets/f93cb0a9-f43a-4a57-93e2-4f6445072982)

## L2 :  Introduction to RISC-V

### **ISA (Instruction Set Architecture)**
 - In general terms, an Instruction Set Architecture (ISA) is the set of instructions that a computer's processor (CPU) can execute. It 
   defines the interface between software and hardware, specifying how software controls the hardware. Like it's nothing but a language 
   of a computer.
 - You can think of an Instruction Set Architecture (ISA) as the "language" of a computer's processor. Just like a human language has 
   grammar and vocabulary that define how words and sentences are constructed and understood, an ISA defines how instructions are 
   formatted, what operations the CPU can perform, and how it interacts with memory and other components.
   * *1) Instructions:* * The "words" in this language are the instructions that the CPU can execute, such as arithmetic operations, 
      data transfers, and control instructions.
   * *2) Syntax and Semantics:* * The ISA specifies the syntax (format) and semantics (meaning) of each instruction, dictating how 
      instructions should be written and what they do.
   * *3) Communication:* * Just as languages facilitate communication between people, an ISA facilitates communication between software 
      and hardware, enabling programs to control the CPU and perform tasks.

 ## L3 : From Software Applications to Hardware

 - When you use an app on your computer, it sends commands to the system software (like the operating system), which acts as a translator 
   between your app and the hardware. The system software converts these commands into binary code (the language of the hardware), which 
   the CPU and other components then execute. The results are then sent back through the system software to the app, allowing you to see 
   the outcome of your actions.
 - So the Application software enters the block called System software and then the application program converts into the binary language 
   which is understandable for the hardware.
 - Application Software is like MS Office, Firefox, Acrobat Reader DC, etc.
 - For System Software the major components are OS, Compiler, and Assembler.

![Screenshot (516)](https://github.com/user-attachments/assets/33456517-57ec-43fe-8961-346de33150eb)


### Operating System (OS) :
 - The operating system (OS) is responsible for handling input/output operations, allocating memory, and managing low-level system 
   functions. Its main role is to translate a specific application into its respective assembly language program and ultimately into 
   binary language, making it understandable by the hardware. This is the primary function of the OS.
   
### Compiler :
 - The compiler is used to convert the respective program or any standard format to its respective language based on the hardware we are 
   using. The Output of the Compiler i.e. the syntax of `.exe file` depends on the hardware we are using.
 - The `.exe file` consist of instructions that has been implemented by the particular hardware. The hardware here is RISC V.

### Assembler :
 - Once we receive instructions from the compiler, the assembler will take each instruction and convert it into its respective binary 
   numbers, also known as a machine language program. Finally, the binary language is sent to the hardware. When the hardware receives a 
   specific pattern or information, it performs a task and generates the output accordingly.

- The instructions we receive from the compiler serve as the interface between the C language and the hardware. These instructions are 
  known as the ISA or computer architecture. The interface is referred to as the abstract interface.

![Screenshot (520)](https://github.com/user-attachments/assets/df4c46ad-9378-4833-80d2-e613e3a51cde)
![Screenshot (521)](https://github.com/user-attachments/assets/126624e4-a859-4654-bb45-3b4ffead7dc3)
 

- If we delve deeper, there is another interface that plays a major role in reaching the hardware: Hardware Description Language (HDL).
- First, we need to write the HDL for the instruction. Then we synthesize it into the Gate Level Netlist, followed by converting the 
  Gate Level Netlist into its respective Layout based on the general RTL2GDS Flow.
   
![Screenshot (522)](https://github.com/user-attachments/assets/f362374f-6045-4fe8-a49f-971d54dd2e2d)

# Section-2 : SoC design and OpenLANE
## L1 - Introduction to all components of open-source digital ASIC design

![Screenshot (524)](https://github.com/user-attachments/assets/7b638600-88ba-45ea-afbd-382ef803b7d7)

- The components of open-source digital ASIC design involve as follows,
### RTL Design: 
  - Register-Transfer Level (RTL) is a critical design abstraction that models the flow of digital signals between hardware 
    registers in a synchronous digital circuit. The logical operations performed on these signals are also part of this model. A variety 
    of open-source platforms are available for RTL design, including Librecores, Opencores, and repositories on GitHub. These resources 
    have been instrumental in accelerating my understanding of RTL design.
### EDA Tools: 
- Electronic Design Automation (EDA) refers to the suite of tools used to design and verify integrated circuits (ICs), printed circuit 
  boards (PCBs), and other electronic systems. Several open-source EDA tools, like Qflow, OpenROAD, and OpenLANE, are available. Today, 
  I focused on OpenLANE, which is particularly effective for open-source digital ASIC design. These tools are central to automating and 
  verifying the design process.
### PDK Data: 
- The Process Design Kit (PDK) is an essential interface between the fabrication process (FAB) and the design stage. The PDK includes 
  collections of files such as process design rules (DRC, LVS, REX), digital standard cell libraries, and I/O libraries, which are used 
  by EDA tools to model and simulate IC fabrication.

![Screenshot (525)](https://github.com/user-attachments/assets/bde588ef-09f4-40c4-8177-2251a6506409)

- An example of an open-source PDK is the SkyWater 130nm process, released in collaboration with Google in 2020. Though newer 
  fabrication technologies, like the cutting-edge 5nm process, are available, the 130nm process remains relevant for many applications 
  due to its lower cost and sufficient processing speed for most use cases. For example, Intel’s P4EE @ 3.46 GHz (released in Q4 '04) 
  and Sky130_OSU (a single-cycle RV32i CPU) pipeline can achieve over 1 GHz clock speeds using this technology.

![Screenshot (526)](https://github.com/user-attachments/assets/99d28ef2-8db9-4ce4-bfa8-40fa8e3126c8)

## L2 - Simplified RTL2GDS flow 
- The  simplifying RTL to GDSII flow, breaking it down step by step to streamline the understanding of this complex process. Below is an 
  Outline the major phases involved in this flow.

![Screenshot (529)](https://github.com/user-attachments/assets/c0f09633-6584-420a-9bcf-d10ce48342ed)

### Synthesis: 
- The synthesis phase converts the RTL design into a circuit, leveraging the standard cell library (SCL). The end result is a gate-level 
  netlist that represents the same functionality as the RTL but at a lower abstraction level. This netlist, described in hardware 
  description languages (HDL) like Verilog or VHDL, connects standard cells, which have regular layouts akin to electrical components, 
  such as HDL, SPICE models, etc.

![Screenshot (530)](https://github.com/user-attachments/assets/4498f11e-325a-4a74-8562-f0deaf55b986)  ![Screenshot (531)](https://github.com/user-attachments/assets/8651bc6c-556e-4b98-919d-31d39cac7745)

### Floor/Power Planning:
- In this stage, The planning of the silicon area and distributing power across the entire circuit takes place. At the chip level floor 
  planning involves dividing the chip die into different blocks and positioning the I/O pads. In micro-level floor planning involves 
  dimensions, pin locations, and rows are defined. Power planning is also crucial here, where the power distribution network is 
  constructed, typically using multiple VDD and GND lines. Metal strips are laid horizontally and vertically in parallel to minimize 
  resistance, with upper metal layers (which are thicker and more resistant to electromigration) being preferred for power distribution.

![Screenshot (534)](https://github.com/user-attachments/assets/fa4299ae-c50e-42b6-9762-ff79c4c4880d)
![Screenshot (533)](https://github.com/user-attachments/assets/a7fc7e24-c2ba-4425-a4d4-56fde156182a)
![Screenshot (535)](https://github.com/user-attachments/assets/50091cd1-5e13-4045-9267-cd79ca639231)

### Placement: 
- The next step is to place the gate-level netlist onto the floor-planned rows, aligning them with the available sites. Cells should be 
  placed as closely as possible to minimize interconnect delays. Placement is typically divided into two stages:

![Screenshot (536)](https://github.com/user-attachments/assets/5eb04d3f-8f95-492b-a15a-8a1a5ac9bcfa)

   1) **Global Placement:** In this initial stage, cells are roughly positioned within the core area, balancing timing and congestion 
           constraints. It provides a broad view of the netlist but may not strictly adhere to all placement rules.
   2) **Detailed Placement:** Here, the exact routes and layers for each netlist are determined, ensuring valid routing while 
           optimizing for area and timing constraints. Minimizing vias and power consumption are also key objectives in this stage.

![Screenshot (538)](https://github.com/user-attachments/assets/2ba3d11a-e854-4032-bc13-1de6e3ed9065)

### Clock Tree Synthesis (CTS): 
- Before signal routing, the clock must be routed. Clock tree synthesis ensures that the clock is distributed to all sequential 
  elements, such as flip-flops and registers. The clock network resembles a tree, with the clock source at the root and the sequential 
  elements at the leaves. The goal of CTS is to minimize clock skew while ensuring the clock network maintains good shape and 
  performance. Typically, H-trees or X-trees are used to reduce skew, with some devices offering specialized global routing resources to 
  further optimize clock signal distribution.
  
    **Clock Skew & Clock Jitter :** Clock skew is two different flip flops receive the clock signal at slightly different times due to 
      differences in clock net length but clock jitter is on the same flip flop but the position of the clock edge moves edge to edge 
      due to some noise in oscillator. 

![Screenshot (539)](https://github.com/user-attachments/assets/19b6e017-d831-4220-a491-8fed042befff)

### Routing: 
- Once the clock is routed, the signal routing begins. This involves making physical connections between signal pins using metal layers. 
  Signal routing is divided into two parts:

  1) **Global Routing:** This step generates guides for routing the signals.

  2) **Detailed Routing:** The actual physical connections (wires) are implemented using these guides. Special attention is given 
       to the clock and power/ground nets. The Sky130 PDK defines six routing layers, with the lowest being the local interconnect 
       layer made of titanium nitride, and the remaining five layers being aluminum.

![Screenshot (541)](https://github.com/user-attachments/assets/12ce3eed-42f4-47ad-bea3-013b2505f423)

- As the Routing grid is huge,  A divide-and-conquer approach is used to handle the large routing grids effectively. first global 
  routing is performed then detail routing uses the fine grids and the routing guides to implement the actual wiring.

![Screenshot (543)](https://github.com/user-attachments/assets/92e56365-c494-4b69-a698-453fa4789d8d)


### Sign-Off: 
- After routing, the final layout is constructed, and the design enters the verification phase. There are two key types of verification:

   1) **Physical Verification:** This checks the design for adherence to fabrication rules through Design Rule Checking (DRC) and 
        Layout vs. Schematic (LVS) verification.

   2) **Timing Verification:** Static Timing Analysis (STA) ensures that the design meets timing constraints across all operating 
        conditions.

![Screenshot (542)](https://github.com/user-attachments/assets/c49d4e33-1907-4195-b0f9-d9478a065d86)


## L3 & L4 - Introduction to OpenLANE detailed ASIC design flow and Strive chipsets

OpenLANE is an advanced, open-source framework designed for automating the ASIC (Application-Specific Integrated Circuit) design process. It leverages several key open-source tools to guide a design from RTL (Register Transfer Level) to a finalized GDSII layout. Here is a detailed breakdown of the OpenLANE design flow and its tools:

![Screenshot (545)](https://github.com/user-attachments/assets/dc957a22-2262-4499-855d-a0147e9b3488)

### Key Open-Source Tools:
-  Yosys: RTL-to-Gates synthesis tool.
-  ABC: Logic synthesis and optimization tool.
-  OpenROAD: Complete toolchain for physical design automation, including floorplanning, placement, clock tree synthesis, and routing.
-  MAGIC: VLSI layout tool used for Design Rule Checking (DRC) and Layout vs. Schematic (LVS) checks.
-  Netgen: Tool for LVS, comparing SPICE extracted from layout with Verilog netlist.
-  OpenSTA: Static Timing Analysis (STA) tool.
-  KLayout: Layout viewer and editor.
-  Fault: Tool for Design for Test (DFT) tasks, including scan insertion and ATPG (Automatic Test Pattern Generation).
-  Qflow: Toolchain for digital synthesis and placement/routing


### 1. RTL to Logic Circuit Conversion:
-  Tool: Yosys
-  Process: The design starts with RTL code, which is processed by Yosys. Yosys translates the RTL description into a logic circuit         representation using various digital components.
-  Optimization and Mapping: This logic circuit is then optimized and mapped into standard cells from a synthesis library using ABC. ABC    requires guidance via an ABC Script, which defines synthesis strategies aimed at either minimizing area or optimizing timing. The        selection of strategies depends on design objectives.
  
### 2. Synthesis Exploration:
-  Purpose: To evaluate different synthesis strategies and their impact on design delay and area.
-  Utility: The Synthesis Exploration Utility generates reports that compare the effects of various strategies. These reports help          identify the most effective strategy for the design.
  
### 3. Design Exploration and Regression Testing:
-  Tool: Design Exploration Utility
-  Process: This utility performs design configuration sweeps to identify optimal settings. It produces reports showing the design          matrix and layout violations. This exploration is crucial for finding the best configurations and is also used for regression testing    by comparing results from approximately 70 designs against established benchmarks.
  
### 4. Design for Test (DFT):
-  Tool: Fault
-  Purpose: To prepare the design for testing post-fabrication. This optional step includes:
   -  Scan Insertion: Incorporates scan chains to facilitate testing.
   -  Automatic Test Pattern Generation (ATPG): Creates test patterns for the design.
   -  Test Pattern Compaction: Reduces the number of test patterns needed.
   -  Fault Coverage and Simulation: Ensures comprehensive fault coverage and simulates test patterns to verify design functionality.

![Screenshot (546)](https://github.com/user-attachments/assets/52bb1616-3b20-44c7-a58f-41ceadc41181)
     
### 5. Physical Implementation (Place and Route - PnR):
-  Tool: OpenROAD
-  Steps:
    -  Floor/Power Planning: Defines the chip layout and plans power distribution across the design.
    -  End Decoupling Capacitors and Tap Cells Insertion: Adds capacitors and tap cells to enhance performance and reliability.
-  Placement:
    -  Global Placement: Initial placement of cells to address congestion and timing.
    -  Detailed Placement: Fine-tunes cell positions to meet precise timing and routing constraints.
    -  Post Placement Optimization: Further optimization after initial placement to improve performance.
-  Clock Tree Synthesis (CTS): Distributes the clock signal to all sequential elements like flip-flops and registers.
-  Routing:
    -  Global Routing: Establishes general routing paths for connections.
    -  Detailed Routing: Finalizes metal tracks to connect standard cells, macros, and I/O pins.
      
### 6. Logic Equivalence Checking (LEC):
-  Tool: Yosys
-  Purpose: To ensure that the netlist resulting from physical implementation is functionally equivalent to the original gate-level         netlist from synthesis. This is crucial as the netlist may be modified during various stages of physical implementation.
  
### 7. Antenna Rule Violation Handling:
-  Process: Metal wires can act as antennas, accumulating charges that can damage transistor gates during fabrication.
-  Preventive Approach: Fake Antenna Diode Insertion Script adds fake antenna diodes next to each cell input after placement. An antenna    checker (MAGIC) runs on the routed layout. If violations are found, fake diodes are replaced with real ones.

![Screenshot (548)](https://github.com/user-attachments/assets/fe9f7243-6110-4fed-a4cd-1692d8331f17)
![Screenshot (550)](https://github.com/user-attachments/assets/bfdf111f-471d-4e78-ab21-5a3766c289dc)

  
### 8. Final Verification:
-  Timing Verification:
  -  Static Timing Analysis (STA)
      -  Tool: OpenSTA (OpenROAD)
      -  Process: Involves extracting interconnect RC parameters and performing timing analysis to identify any timing violations.                Timing reports are generated to ensure the design meets performance requirements.

![Screenshot (551)](https://github.com/user-attachments/assets/0f7ede8e-29a2-4d9d-aa23-c12ab14f0993)

  -  Physical Verification:
      -  Design Rule Checking (DRC): Conducted using MAGIC to ensure the layout adheres to design rules.
      -  Layout vs. Schematic (LVS): MAGIC and Netgen are used to compare the extracted SPICE model from the layout with the Verilog              netlist. This comparison ensures that the layout matches the intended schematic.
    
-  One of the most exciting aspects of OpenLANE is its integration with **StriVe**, a family of fully open-source System-on-Chips (SoCs)    that utilizes open-source PDKs, EDA tools, and RTL designs. StriVe exemplifies the power of open collaboration, where every layer        of the SoC, from design to fabrication, is accessible to the public.

![Screenshot (544)](https://github.com/user-attachments/assets/02bd6182-67e5-42af-9c24-8de1ca1090a5)
  
-  The ultimate goal of OpenLANE is to generate a clean GDSII file, which is the final representation of the chip design, free from any     issues or violations. When we say “clean,” it means:
    -  No LVS (Layout vs. Schematic) violations: Ensures the layout corresponds correctly to the design schematic.
    -  No DRC (Design Rule Check) violations: Ensures the design complies with the fabrication process rules.
    -  No timing violations: Guarantees that the design meets all timing constraints, which is crucial for the correct operation of             high-speed circuits.
-  By integrating these tools and processes, OpenLANE provides a robust, automated flow for ASIC design, ensuring accuracy and              efficiency from initial RTL code to final layout.

# Section - 3 Get familiar with open-source EDA tools
## OpenLANE Directory structure in detail, Design Preparation Step and Review files after design prep and run synthesis

-  Before going into the Openlane Directory structure, lets know about the basic commands which we use in this tool.
```
-  cd : Change directory
-  ls -ltr : List everything in chronological order
-  ls -help : list all the commands and its meaning
-  clear : clearning everything.
```
-  Coming to the OpenLane Directory,
  
-    Open the terminal window and first, we need to change our current directory to openlane directory which is shown below.
     `cd Desktop/work/tools/openlane_working_dir/openlane` 
-    Next we need to type docker 
    `docker`
-    Now we are in OpenLane flow with the docker sub-system. we need to Call on interactive mode using the below command
    `./flow.tcl -interactive`
-    Now in this mode, we need to add our package for our design using OpenLane flow using the following command
     `package require openlane 0.9`
-    Right now, our package is created and openlane is ready to design, but to design it and generate reports and results we need to          create one folder which is **picorv32a**
     `prep -design picorv32a`  
-    After doing the above step you will get the output as **Preparation successful**. After getting that you need to proceed with            the below command. Finally, we need to run synthesis for our design using the following command. The output for this command             shows that **Synthesis successful**
     `run_synthesis` 
  

-  I have shared every screenshot below for the above process. Make sure While executing those commands you need to get the exact output    that is shown in screenshots

![ol4](https://github.com/user-attachments/assets/7b523e8a-9d2a-4882-9be3-7c896c058a2b)
![ol5](https://github.com/user-attachments/assets/2453c524-b2b3-47ba-b70c-a57f13420ac1)
![ol7](https://github.com/user-attachments/assets/26f49f56-3251-4297-b4fb-4477cce95df6)

-  After completing the synthesis step, we need to calculate the flop ratio which is shown below,
-  To check the values, you just need to scroll up after your successful synthesis run. As shown in the above 3rd snapshot, there is a      line highlighted which is **Chip area for module `\picorv32a`: 147712.918400**. Above that you can see the Highlighted values shown      in the figure.  

![ol8](https://github.com/user-attachments/assets/b7062491-2095-41d6-9ea3-2e6ece7b7caa)

![image](https://github.com/user-attachments/assets/6966c58e-e726-47c5-80e9-314d764ea07b)

![image](https://github.com/user-attachments/assets/b81497fa-fa59-4241-a2f2-0f827bb46848)

## Steps to characterize synthesis results

-  How to check the timing report shown in below screenshots

![To check the timing report](https://github.com/user-attachments/assets/e97b137c-c64d-487f-af48-30ebfdbd4fce)

![Timing_report](https://github.com/user-attachments/assets/f889a42f-6847-4d15-853c-b0e002ff1939)


# Day-2 Good floorplan vs bad floorplan and introduction to library cells
# L1 - Chip Floor planning considerations
## Utilization factor and aspect ratio

-  A detailed comparison of optimal and suboptimal floorplans, focusing on design efficiency and scalability.

![Screenshot (553)](https://github.com/user-attachments/assets/fed5af38-6716-4b1d-a600-17d28337b9bf)

-  In the physical design flow, the initial steps are crucial for defining the core and die dimensions.
  
-  Die: The die refers to the actual size of the chip within an integrated circuit (IC), housing transistors and I/O components.
-  Core: The core is the processing unit of the chip, where all digital logic occurs. It is a section of the die that handles the           execution of tasks and logic operations. Modern processors often have multiple cores (e.g., quad-core, octa-core), enabling              multitasking and increased processing efficiency.

![Screenshot (558)](https://github.com/user-attachments/assets/f99d7653-b59d-4e2d-b465-13b6b92a68ff)
  
-  The dimensions of the core (height and width) are determined by the design’s netlist, which dictates the number of components            required to execute the logic. Consequently, the die’s dimensions are directly influenced by the core’s size.
-  Before going into the dimensions of the core, let us know about Netlist.
-  What is Netlist? : A netlist represents the connections between all the components within the design, and it plays a fundamental         role in determining the layout and structure of the chip
-  Let’s consider a netlist that contains two logic gates and two flip-flops, where each element occupies an area of 1 square unit.         In this case, the total number of components in the netlist is 4. So Area occupied by the netlist is 4 square units. Therefore, the      minimum total area required for the core will be:

                                    Core Area = 2 (logic gates) + 2 (flip-flops) = 4 square units
   
-  Below screenshots shows step by step explanation of How we are defining the width and height of Core and Die.

![Screenshot (554)](https://github.com/user-attachments/assets/78a811a2-d5d9-47cd-b172-a82452769703)

![Screenshot (555)](https://github.com/user-attachments/assets/bef94ed6-7f7d-4427-885e-83f4f4080c69)

![Screenshot (556)](https://github.com/user-attachments/assets/868fc622-948c-4fe6-95d7-b56a18802415)

![Screenshot (557)](https://github.com/user-attachments/assets/34e57d4d-47d3-426b-bf73-2c1c789ee467)

-  Till now we are done with initializing the values of Width and height and here are the two critical metrics that influence               floorplanning decisions:
  -  ### Utilization Factor: Defined as the ratio of the area occupied by the netlist to the total core area. A utilization factor of 1           indicates 100% usage, often signaling a poorly optimized floor plan with no room for future expansion.
   
                                  Utilization Factor (UF): 𝑈𝐹 = Area occupied by netlist / Total core area

![Screenshot (560)](https://github.com/user-attachments/assets/b9217712-844f-4e5a-ab0f-683c3ebdf7d0)
![Screenshot (561)](https://github.com/user-attachments/assets/aba4a5e2-2d25-4215-ae58-48df273e5a94)

  - Let us calculate the Utilization factor, which is Utilization factor = (4 square units)/(4 square units) = 1 (100% Utilization)

![Screenshot (563)](https://github.com/user-attachments/assets/f801a55a-382a-433a-b41b-d608ec7592d1)

  -  ### Aspect Ratio (AR): The ratio of core height to core width. An AR of 1 indicates a square-shaped core, while deviations from 1            represent a rectangular shape.

                                  Aspect Ratio (AR): 𝐴𝑅 = Height of the core / Width of the core
     
​  -  Let us calculate the Aspect Ratio, which is Aspect Ratio = (2 units)/(2 units) = 1 (Which is square in shape)

![Screenshot (565)](https://github.com/user-attachments/assets/116d15a1-a796-4b98-9ef1-77344590037d)
![Screenshot (566)](https://github.com/user-attachments/assets/43268db3-b47d-45b6-ba6e-f4ad75805e4c)

-  The below screenshots are the other examples for better understanding.

![Screenshot (567)](https://github.com/user-attachments/assets/c9e6f580-5bcd-43bc-8693-18480ad20e4f)
![Screenshot (568)](https://github.com/user-attachments/assets/021c4946-eecd-415a-a071-b723f4e446b7)
![Screenshot (569)](https://github.com/user-attachments/assets/1a507a1a-0d25-4e1d-a60c-dbda2451903b)
![Screenshot (570)](https://github.com/user-attachments/assets/87e63807-6150-416a-95c9-ddb1f088c7cf)
![Screenshot (571)](https://github.com/user-attachments/assets/c071dcd2-178d-4ea2-94b5-1f4ba219522b)


-  For the above scenario, the Aspect ratio is, Aspect Ratio = (2 units)/(4 units) = 0.5 (The core is Rectangle in shape)

## Concept of pre-placed cells

- Here we define the locations of preplaced cells.
- Before that, let us understand what are preplaced cells.

### Preplaced cells
-  The cells that are already implemented once and used multiple times are called pre-placed cells. Like Implement once and use it          multiple times.
-  We have to define or arrange the location of cells before the placement and routing step. Those locations are fixed after arranging.
-  These cells are but Macor's or IP's whih is a peace of complex logic that has been re-used multiple times.
-  Pre-placed cells must be placed in the design area based on the design scenario or design background. So that those locations of         cells are very well defined.
-  Below are the step-by-step screenshots of how to define the locations of pre-placed cells.

![Screenshot (573)](https://github.com/user-attachments/assets/dd74f6da-e991-4b29-b51b-cb9a8f725d02)
![Screenshot (574)](https://github.com/user-attachments/assets/10ef7ce3-7676-4a6f-a81f-fcf51a9db98f)
![Screenshot (575)](https://github.com/user-attachments/assets/0491afb1-6c68-4bb9-acb0-7ee1ff4b8cb1)
![Screenshot (576)](https://github.com/user-attachments/assets/ef185e72-5edd-4327-95ba-a903289d625c)
![Screenshot (577)](https://github.com/user-attachments/assets/8e1cbf0f-7ae9-4cae-a62c-657df1c3ed58)
![Screenshot (578)](https://github.com/user-attachments/assets/1da374d3-ba11-4c95-a4cc-12126d5a5ed2)
  

## Decoupling Capacitors

-  Decoupling Capacitors are used in integrated circuit (IC) design to stabilize the power supply and filter out noise. They play a         crucial role in maintaining the performance and reliability of the chip by ensuring that the power supply remains stable and free        from fluctuations.

![Screenshot (581)](https://github.com/user-attachments/assets/d780a2a5-14a6-40da-bf46-ad4ab86006cd)
![Screenshot (582)](https://github.com/user-attachments/assets/057626f1-7e16-4a59-9632-cd84db0d6032)


-  Decoupling capacitors is vital for ensuring reliable and stable operation of integrated circuits by filtering noise and stabilizing      the power supply. Proper selection and placement of these capacitors are key to optimizing the performance of your chip design.

![Screenshot (584)](https://github.com/user-attachments/assets/ce2ae36a-8a72-4478-b810-2922aa49a178)


-  Noise Filtering: When digital circuits switch states, they draw varying amounts of current, which can cause fluctuations in the power    supply. Decoupling capacitors help to smooth out these fluctuations by providing a local reservoir of charge that can quickly respond    to changes in current demand.

![Screenshot (583)](https://github.com/user-attachments/assets/f478d63d-016e-4eac-acc1-919561c6a73e)


-  Stabilizing Power Supply: By placing decoupling capacitors close to the power pins of ICs, they help to reduce the impact of high-       frequency noise and prevent potential interference from affecting the circuit’s operation.

![Screenshot (585)](https://github.com/user-attachments/assets/f341519e-fd01-498b-9d33-66a59e739989)

## Power planning

-  Power planning is a critical aspect of integrated circuit (IC) design, ensuring that the chip receives stable and reliable power         across all its components. Effective power planning involves both local and global strategies to manage power distribution and noise     reduction.
-  As previously discussed, decoupling capacitors are used locally to filter high-frequency noise and stabilize the power supply close      to the power pins of individual ICs. This local strategy helps in mitigating noise generated by switching transients and ensuring        smooth operation of each cell or component.

![Screenshot (586)](https://github.com/user-attachments/assets/5f6a8ed5-0f44-4c33-b6fc-531496509410)
![Screenshot (587)](https://github.com/user-attachments/assets/f2885a18-315f-4a8d-ad7f-fd5850085a3a)
![Screenshot (588)](https://github.com/user-attachments/assets/125678a1-e8e2-40d9-851a-83eac97310b0)

-  For global power management, the focus shifts to the overall power distribution network within the chip. This involves several key       strategies:

    -  ### Power Distribution Network (PDN):
      
      -  Power and Ground Planes: Utilize dedicated power and ground planes in the chip layout to provide a low-resistance path for               power distribution. These planes help to reduce voltage drops and ensure that power is uniformly distributed across the chip.

      -  Power Grids: Implement power grids or mesh structures to connect the power and ground planes to various parts of the chip.               These grids ensure that power is consistently delivered to different sections of the chip and reduce the risk of localized               power shortages.
        
    -  ### Global Decoupling Capacitors:

      -  Capacitor Arrays: In addition to local decoupling capacitors, global decoupling capacitors are placed at strategic locations             across the chip. These capacitors help to filter low-frequency noise and provide additional charge storage to handle variations          in current demand across larger areas.

      -  Placement Strategy: Position global decoupling capacitors in areas where high current fluctuations are expected or where                 critical components are located. The goal is to minimize the distance between the capacitors and the components they support. 

-  Let us consider a scenario, Consider a local circuitry designed as a black box, which can be replicated multiple times. This             circuitry has logic at the boundaries and manages current demand with decoupling capacitors. A signal is transmitted from a              driver to a load, switching from logic 0 to logic 1. Maintaining a consistent signal on this line is crucial for ensuring the            load receives the correct data.

![Screenshot (589)](https://github.com/user-attachments/assets/7ea0cbd0-b174-4820-9ec5-b7d753d94bf0)

-  Challenge with a 16-Bit Bus:

![Screenshot (590)](https://github.com/user-attachments/assets/fadac7c3-5b77-45ed-80ae-ab3b0c99ef0c)

1)  Power Supply Distance: Assume a 16-bit bus needs to retain the signal consistently from the driver to the load. Since the power          supply is located far from the bus, there will be unavoidable voltage drops along the line. Decoupling capacitors cannot be placed       at every point due to physical constraints.

2)  Signal Behavior: When a particular line on the 16-bit bus is at logic 1, the capacitors are charged to 𝑉𝑑𝑑. When the line is at          logic 0, the capacitors discharge to the ground. This charging and discharging cycle occurs because the bus is connected to an           inverter, causing all capacitors to either charge or discharge.

-  Ground Bounce and Voltage Drop:

![Screenshot (591)](https://github.com/user-attachments/assets/20dedad2-34a3-4d97-9fda-e9017565808e)
![Screenshot (592)](https://github.com/user-attachments/assets/aa18778b-dfca-482b-96eb-c383a207d6e5)
  
1)  Ground Bounce: All capacitors connected to a single ground can cause a ground bounce during the discharging phase. This bounce           results in a temporary increase in ground voltage, which can exceed the noise margin level. If the voltage bump is large enough, it      can cause the signal to enter an undefined state, resulting in unpredictable behavior, either logic 1 or logic 0.

2)  Voltage Drop: When capacitors initially at 0 volts charge to 𝑉𝑑𝑑 through a single 𝑉𝑑𝑑 tap point, it can cause a voltage drop at         this tap point. As long as the voltage drop remains within the noise margin level, the system functions correctly. However, if the       voltage drop exceeds this margin, the signal becomes unpredictable.

-  Solution - Mesh Power Distribution:

![Screenshot (594)](https://github.com/user-attachments/assets/cc99657a-28c8-4def-ab47-6d7a8298ce0a)
  
-  Mesh Power Distribution: To address the issues of ground bounce and voltage drop, a mesh power distribution system can be                implemented. This involves using multiple power supply points throughout the design. Each block of the circuitry draws power from the    nearest supply and returns the charge to the nearest ground point. This approach minimizes voltage drops and reduces ground bounce,      leading to more stable and reliable operation.

## Pin Placement and logical cell placement blockage 

### Pin Placement

-  Pin placement refers to the strategic positioning of input/output (I/O) pins on a chip's physical layout.
-  Proper pin placement is critical for optimizing signal integrity, reducing wire lengths, and minimizing congestion in routing paths.
-  It has a significant impact on the chip's performance, power consumption, and manufacturability.
-  The front-end Team defines the netlist, which outlines the logical connections between different components and determines the data      flow.
-  While the Back-End Team takes the netlist and physically places the pins on the chip, ensuring that the pin locations align with         physical design constraints.

-  Let’s consider a design where we have two circuits operating on separate clocks. The first circuit is driven by clk1 and the second      by clk2, with each circuit receiving distinct inputs: Din1 for the first and Din2 for the second. The outputs of these circuits are      Dout1 and Dout2, respectively. Additionally, there are pre-placed cells within the design: Block A, which takes inputs from both Din1    and Din2, and Block B, which receives inputs from both clk1 and clk2, generating a clock output ClkOut.

![Screenshot (596)](https://github.com/user-attachments/assets/c918993e-fb1d-4b0e-94ec-f7ca6d450c86)
![Screenshot (597)](https://github.com/user-attachments/assets/52788037-f8ed-4e9c-8e90-10a425db23af)

-  In this design, we have four input ports (Din1, Din2, clk1, clk2) and three output ports (Dout1, ClkOut, Dout2).

-  Now, consider another design to be implemented. This new configuration, which involves a total of six input ports and five output        ports, is particularly useful for understanding timing analysis between different clocks. The connections between the various gates      are described in a netlist, coded in VHDL or Verilog, which defines the relationship between all the components.

![Screenshot (598)](https://github.com/user-attachments/assets/8b320ba0-fd61-429c-bc12-9bfcb7e89909)
![Screenshot (599)](https://github.com/user-attachments/assets/6a400dda-e07f-4002-8a28-38c40f92a041)

-  Once we’ve generated the netlist, we can integrate it into the previously designed core and focus on the layout. The space between       the core and die will be used for pin placement. In this phase, the front-end team defines the connectivity of the netlist, including    inputs and outputs, while the back-end team is responsible for determining the optimal pin placements. Based on these placements,        pre-placed blocks should be positioned close to their corresponding input sources to minimize routing complexity and improve             performance.

![Screenshot (600)](https://github.com/user-attachments/assets/14d0fd8e-272a-4341-908c-89c56a7ea517)

-  The clock ports appear bigger in size compared to the I/O ports because the clock is continuously driven by the cells. It                continuously sends signals to the flops, effectively driving the entire chip. Therefore, we need a path with the least resistance for    clock pins. The larger the size, the lower the resistance.

### Logical cell placement blockage

-  We have finished pin placement and now we need to ensure that none of the automated placement and routing tools place any cells in a     specific area. This area should be blocked by the routing tool. 
-  Up to this point, we have implemented blockage for logical cell placement to prevent any cells from being placed in this area. This      ensures that the automated placement and routing tool does not place any cells in the reserved pin locations.

![Screenshot (602)](https://github.com/user-attachments/assets/9d9643d0-a53a-4e9a-aa77-0239b6995fb9)


## Steps to Run Floor plan using OpenLANE

-  Before we proceed with the actual floor plan, we need to set up the switches required for this floor plan.
-  In the floorplanning stage, designers need to carefully configure certain parameters, commonly referred to as switches, which            directly impact the layout and functionality of the chip. These switches control various aspects of the design and can significantly     alter the floorplan when adjusted. Two key parameters that are often considered as switches are the Utilization Factor and Aspect        Ratio.
-  Before beginning the floorplanning process, designers must cross-check all switches to ensure they are correctly configured and          aligned with the project specifications. Misconfigured switches can lead to inefficient use of space, poor routing, or failure to        meet timing and power goals.
-  Command to run Floor plan

          run_floorplan

![floorplan success](https://github.com/user-attachments/assets/7688151b-7f2f-44ca-9000-94d09e14ded9)
![global variables](https://github.com/user-attachments/assets/1cfa9592-8d8c-4f2d-9000-3ba399abe9d6)

-  Once the floorplan is successful, we need to check the actual layout which is by using a tool called MAGIC.
-  Before that, we need to check the die area in microns from the values in floorplan.

![die_area](https://github.com/user-attachments/assets/1245aa50-a62b-46e0-846e-753952e9d6fb)

-  Below are the following steps to how to access the tool from the terminal and actual layouts as well.
-  First, you need to change the directory to which your generated floorplan exists.

        cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-09_12-31/results/floorplan/
        
-  After that you need to enter one command which is to generate our floorplan using the MAGIC tool

        magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
   
-  The Screenshots of our floorplan

![ol9](https://github.com/user-attachments/assets/bb33d799-62ed-4325-b85b-a969b394b324)

-  After this, you will able to see a layout. To place the layout in the centre of your screen first you need to place your cursor on the layout and 

        press - s to select (Here your entire layout gets highlighted
        press - v to set the layout to the centre of your screen
   
-  If you want to zoom in to a specific portion of the layout, first left-click on your mouse and then adjust the area you want to zoom     in on. Next, right-click on your mouse. Finally, press "z" to zoom in until you see the standard cell diagram.

![zoom_in_layout](https://github.com/user-attachments/assets/29a818e5-b1d7-4f04-84a4-559fff25cbd6)
![zoom_in_layout_1](https://github.com/user-attachments/assets/206e9128-52a7-470b-abeb-5aed9a1088a0)
![zoom_in_layout_2](https://github.com/user-attachments/assets/39aab64c-0838-4e85-9f6e-af4858cf3b40)


## L2 - Library Binding & Placement

## Netlist binding and initial place design

-  In a real-time scenario, if we take a circuit and check the shape of any gate in that circuit, we can easily identify its functionality. In real life, the shape will typically look like a box.

![Screenshot (604)](https://github.com/user-attachments/assets/1bfc7ab6-3bf1-469a-bb76-65be41983fb0)

-  For the circuit example below, we have provided the real-time view of the particular circuit and given physical dimensions (width and height) because that's what we actually deal with in practice.

![Screenshot (605)](https://github.com/user-attachments/assets/e3e12e8c-59ec-4985-bc17-b22082658f73)
![Screenshot (606)](https://github.com/user-attachments/assets/db66e2ff-37b5-4b60-a66a-6f4394c0764f)


- Each element of the netlist now has proper dimensions with height and width. Blocks already have precise dimensions. We will only consider the blocks and remove wires.

![Screenshot (607)](https://github.com/user-attachments/assets/db29efba-4ccb-4419-8dd0-f59361da2cd3)

-  Lets combine all the blocks into one side and call it a Library.
-  Before proceeding further, first, we need to know about what is library.

### Library
-  The contains everything like cells, shapes and size of cells, Various flavours of the same cells, Timing information and the delay information.
-  Here the size is referred to as the drive strengths.
-  Also it has different functionality and different threshold voltages as shown in the below screenshots.

![Screenshot (608)](https://github.com/user-attachments/assets/b8237a3a-3a8a-4743-bd0c-355e7f9ff993)

-  Once we determine the proper sizes and shapes of each gate, the next step is to place those particular shapes and sizes into a floorplan.

![Screenshot (609)](https://github.com/user-attachments/assets/5229ec0d-cfa6-41e9-b136-79130f583034)

-  We need to take the physical view of the netlist and should place over the floorplan

![Screenshot (610)](https://github.com/user-attachments/assets/85ae01a7-95e6-47ea-bde6-b97ccd71e9a6)

- The FF1 is positioned close to Din1, and FF2 is positioned near Din2, with combinational circuits placed between FF1 and FF2 as per the Netlist diagram.

![Screenshot (611)](https://github.com/user-attachments/assets/db35deff-71f4-47a8-b7b1-70b33dd5e7b7)

-  why we are placing that because to avoid delay and other conditions.
-  If you look at the below image, you'll see that FF2 is positioned near Dout2. A noteworthy point here is that we have combined the combinational cells. As a result, the delay between FF1 and 1 is minimal.

![Screenshot (612)](https://github.com/user-attachments/assets/1f60b297-7df3-4a1f-9656-8e638ff56796)

- The remaining flops are also placed as shown in the below images,

![Screenshot (613)](https://github.com/user-attachments/assets/ba4c3248-8629-43a1-896c-2cf3125dcacd)
![Screenshot (614)](https://github.com/user-attachments/assets/90364e2b-3804-493d-bf96-469039557c22)

## Final placement optimization using estimated wire-length and capacitance

-  When we closely examine the images above, we notice a significant distance between some flops and combinational circuits. This could potentially cause delays and become a major issue for us. To address this, we employ a solution known as Optimized Placement.

-  We also utilize the concept of Signal Integrity to ensure the integrity of the signal. To maintain this integrity, we use Repeaters. At this stage, we estimate wire length and capacitance in order to insert repeaters. Repeaters act as buffers that recondition the original signal, create a new signal replicating the original, and then share it further.

-  The process of signal integrity relies on wire length estimation and calculation. We estimate the wire length and calculate capacitance to create a waveform, ensuring that the transition of the waveform is within the permissible range. This process is also referred to as slew analysis.
  
-  So based on the above explanation, you can see how we are placing buffers in each stage.

![Screenshot (615)](https://github.com/user-attachments/assets/e2f52470-b1d4-48db-b0e9-65b558378be6)
![Screenshot (617)](https://github.com/user-attachments/assets/d2ca9872-0f56-4d2a-9c88-9ccd731f450e)
![Screenshot (619)](https://github.com/user-attachments/assets/0912c57a-e7b9-4352-9e74-71892a557002)
![Screenshot (620)](https://github.com/user-attachments/assets/7ccc0f2e-cf0e-4d3d-9e22-1973e26030b2)
![ndfjs](https://github.com/user-attachments/assets/98d72354-e745-47a3-b436-11451f26cd0a)


## Need for Libraries and Characteristics

-  Every typical IC Design has a proper flow which is shown below.

### Step-1 Logic Synthesis:
-  For instance, if we have functionality coded in the form of RTL, the next step is to convert the logical functionality into hardware, a process referred to as logic synthesis.
-  The output of logic synthesis is nothing but an arrangement of gates that will represent the original functionality that we actually described using RTL.

### Step-2 Floor planning: 
-  In this step, we import the output of logic synthesis or the Netlist from the logic synthesis and decide on the core and die. The dimensions of the core and die completely depend on the number of gates, their shapes, and the sizes present in the output of the logic synthesis.
   
### Step-3 Placement:
At this stage, we take the specific logic cells from the netlist and position them on the chip to ensure the initial timing requirements are met.

### Step-4 Clock Tree Synthesis (CTS): 
-  For example, if we want to minimize skew or ensure that the clock is evenly distributed across all logic cells, CTS ensures that the clock signal reaches each clock endpoint and that the buffer cells maintain equal rise and fall times for the clock signal.

### Stage-5 Routing: 
-  For example, if we want to route between 2 points there are certain properties of the cells that have to be taken care of while routing, and also it depends on the characteristics of the 2 points.

### Stage-6 Static Timing Analysis:
- This stage involves checking the setup time, hold time, and maximum achievable frequency for the circuit, which is the final stage in the IC Design flow and is also known as Sign-off STA.

-  Below are screenshots of the Typical IC Design Flow

![Screenshot (621)](https://github.com/user-attachments/assets/6826ad20-c012-486b-8bca-3be0e95b9e21)
![Screenshot (622)](https://github.com/user-attachments/assets/5707ed30-900c-4623-b25e-8357b981d561)

## Congestion-aware placement using RePlAce

-  Placement is a key step in the VLSI design process, where the physical locations of standard cells or logic elements are determined within a chip. This phase is crucial as it sets the foundation for effective routing and overall chip performance. Placement can be divided into two main stages:

  1. Global Placement:
  -  The main objective is to reduce the wire length. In OpenLANE we use the concept of HPWL (Half-parameter wire length)
  -  In this initial phase, cells are assigned approximate locations on the chip.
  -  Some overlap between cells is tolerated at this stage.
  -  The focus is on achieving a broad layout that adheres to area constraints, providing a rough framework for the design.
    
  2. Detailed Placement:
  -  After global placement, detailed placement fine-tunes the locations of cells.
  -  It eliminates overlaps and ensures that all cells are placed in valid, predefined locations on the grid.
  -  A well-executed detailed placement phase is essential for optimizing the routing process and improving the overall efficiency of the design.

-  Finally, the main motto is to decrease the OVFL (Overflow) value. If it decreases it means the placement is going perfect.
-  To run placement

                                          run_synthesis
-  Screenshots for reference,

![placement_1](https://github.com/user-attachments/assets/1d3d4fbf-967c-48db-a1ff-f3637495a464)
![placement_2](https://github.com/user-attachments/assets/ca54d8d7-12c0-4084-865a-14435d880cd2)

-  After we complete the placement, we need to check out the layout. The process is shown below.
-  First, you need to change the directory to openlane results

             cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-09_12-31/results/placement/  

-  After this, you need to run the below command to check the placement using the MAGIC tool

             magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

-  Screenshots for your reference,

![placement_3](https://github.com/user-attachments/assets/a76e59c9-8a5f-4b9d-95da-63103f0aed67)
![placement_4](https://github.com/user-attachments/assets/80380f75-8525-448a-95cb-ff1a1a06a396)

-  The key point here is that in the flow, the PDN is created after floorplanning. However, in the OpenLANE flow, the order is slightly different. We create the PDN just before the routing, after the post-floorplan and post-CTS stages.


## L3 - Cell design and Characterization flows







