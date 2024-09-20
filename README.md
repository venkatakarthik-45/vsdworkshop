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

### Cell Design:
-  This flow consists of 3 parts
    1. Inputs
    2. Design Steps
    3. Outputs
-  let us know everything briefly.
  1. Inputs:
     -  If you want to design cells, we require few inputs they are,
       -  PDK's: Process design kits, These kits come from foundries. Those kits consist of
           -  DRC, LVS Rules
           -  SPICE Models
           -  Library and User-define specs.

 ### DRC and LVS Rules:
-  Design Rule Checking (DRC) ensures that the physical layout of an integrated circuit (IC) adheres to specific manufacturing requirements set by the semiconductor foundry.DRC rules enforce constraints on geometry, such as minimum spacing between components, metal layer width, and via dimensions, to ensure that the chip can be reliably fabricated.
-  These rules help avoid errors like short circuits, open circuits, or electrical failures that could arise during manufacturing.
-  The Tech files contain the design rules and process parameters necessary for fabricating the chip. we have few rules like Polywidth, extension over active and poly to active spacing. which is clearly shown in the below image
-  Layout vs Schematic (LVS) is a verification process that checks whether the physical layout matches the original schematic design.
-  It compares the netlist generated from the layout to the netlist derived from the circuit's logical design.
-  Screenshots shown for your reference,

![Screenshot (628)](https://github.com/user-attachments/assets/44dcebfa-df40-4d58-ad0e-a64cd91e338d)
![Screenshot (629)](https://github.com/user-attachments/assets/b0e28c17-1f67-4cef-949f-c2c0e58b50d2)

### SPICE (Simulation Program with Integrated Circuit Emphasis) Models:
-  SPICE models are detailed mathematical models used to simulate the electrical behavior of individual components in a circuit (e.g., transistors, diodes, resistors, capacitors).
-  These models represent the electrical characteristics of components such as voltage, current, capacitance, and resistance under various operating conditions
-  Screenshots shown for your reference,

![Screenshot (630)](https://github.com/user-attachments/assets/b55e9ed1-e19d-4d8b-b8fb-035433d489d8)
![Screenshot (631)](https://github.com/user-attachments/assets/64d09785-8fb0-4a26-b5f2-322e83ae1490)

### Library and User-Defined Specifications:

### Standard Cells:
-  A standard cell library contains a collection of predefined and pre-characterized logic gates, flip-flops, and other digital components used to build ICs.
-  These libraries come with detailed specifications, such as timing, power consumption, and area, for different operating conditions.
-  The library also includes information about physical layout, cell dimensions, pin positions, and connectivity, allowing designers to use these cells in their designs without manually designing each component.
-  These cells are being placed in a section called Library. Where we also keep all the Decap cells, Macro, IPs, etc.
-  The screenshots provided below contain information about standard cells.

![Screenshot (625)](https://github.com/user-attachments/assets/ae2397f3-d760-4776-a31f-31ac7913010e)
![Screenshot (626)](https://github.com/user-attachments/assets/bf11f910-ccc4-4d0f-b6e4-3ba0b8f2c0c3)
![Screenshot (627)](https://github.com/user-attachments/assets/5f129817-3b1b-4979-89bb-98a8a787532e)

### User-defined Specification:
-  User-defined specs are constraints or requirements set by the design team for specific components or subsystems that go beyond what is provided in the standard library.
-  Let us consider a few examples, Cell Height is defined as the separation between the power rail and the ground rail, it is the responsibility of the library developer to maintain.
-  cell width can influence timing in VLSI design. The width of a standard cell, which determines the number of transistors and their arrangement in a cell, directly affects factors like drive strength, capacitance, and delay, all of which contribute to the overall timing of the circuit. It is also the responsibility of the library developer to maintain the drive strength as per the requirement.
-  The lower the drive strength of a cell, the harder it is for the cell to drive its connected load.
-  Few more example shown in below screenshots for your reference

![Screenshot (634)](https://github.com/user-attachments/assets/93f3784f-f7c6-4477-96b1-27bccd0c09d7)
![Screenshot (633)](https://github.com/user-attachments/assets/2e79107e-e2a8-4a7c-9d27-99e7dfaff88e)
![Screenshot (636)](https://github.com/user-attachments/assets/b4a2cbe9-4f48-4aef-bb03-7c9819120dde)
![Screenshot (635)](https://github.com/user-attachments/assets/b7d0945d-5d6d-4ea5-996e-6b00ecc5e2fe)

## Design steps

-  In this stage, we have 3 steps
    1. Circuit Design
    2. Layout Design
    3. Characterization

1. Circuit design:
  -  Develop the logical representation of your circuit using schematic design tools.
  -  Define the functionality and interconnections of standard cells to achieve the desired logic.
  -  Specify the functionality of each cell and its connections within the circuit.
  -  Ensure that all logical operations and connections are accurately represented in the schematic.
  -  Once you know about the values of PMOS and NMOS, the Next step is to implement those values in Layout design.
  -  After everything, the typical output that we get after circuit design is "Circuit description language(CDL)" `.CDL FILE`

![Screenshot (637)](https://github.com/user-attachments/assets/48199567-9a27-46c8-bc4b-1e9b0a405793)
![Screenshot (638)](https://github.com/user-attachments/assets/da618fb0-d49b-46db-90e3-814274d02581)
![Screenshot (639)](https://github.com/user-attachments/assets/3ee62a49-b336-4780-ae3a-4ca54f22e871)

2. Layout Design:
  -  Utilize layout design tools MAGIC to translate the logical schematic into a physical layout.
  -  Design the placement of standard cells and the routing of interconnects.
  -  Here we have 2 steps, step 1, is to get the function implementation through an MOS Transistor (Set of PMOS and NMOS)
  -  Step 2 is to get the PMOS and NMOS network graph out of the design that we have implemented.
  -  The Output of layout design is a GDSII (Graphic Data System II) File which is  used to describe the physical layout of an integrated circuit, a LEF (Library Exchange Format) File which describes the physical and electrical properties of standard cells and other components used in the design and Extracted SPICE Netlist, A detailed description of resistance, capacitance of the each and every element of the circuit of the layout. `.cir file` 

![Screenshot (640)](https://github.com/user-attachments/assets/1d1d24c7-62cf-4fe1-afda-dfb59f52543c)
![Screenshot (641)](https://github.com/user-attachments/assets/8eda8fea-cf5a-4e94-a1ab-2d892ab6fa14)
![Screenshot (642)](https://github.com/user-attachments/assets/38f05d55-cbf8-41b0-8a97-f479d1b2bc1a)
![Screenshot (643)](https://github.com/user-attachments/assets/d208ab2b-d243-4d64-a2a9-cb9274d3bafd)

3. Characterization:
  -  Analyze the circuit for timing performance, power consumption, and noise levels.
  -  Use tools like GUNA for comprehensive characterization to ensure the design meets performance and power specifications.

![Screenshot (649)](https://github.com/user-attachments/assets/b9731c7b-2b89-4d84-b87a-c0b10b92168d)
![Screenshot (650)](https://github.com/user-attachments/assets/2cacf374-0540-4e0f-bbe6-4dc9c0c41ff0)
![Screenshot (651)](https://github.com/user-attachments/assets/86d8577f-eb32-45ff-be63-d7d2c58f2d33)


## L4 - General timing characterization parameters

-  Timing threshold definitions are crucial for understanding the behavior of waveforms in circuit design.
-  Key parameters include:
  -  Slew Thresholds (e.g., Slew_low_rise-thr): Represents the point at which the signal transition is considered complete. Typically, this is set at about 20% or 30% of the signal swing.
  -  Delay Thresholds (e.g., in_rise_thr): Defines the points for measuring rise and fall times in the waveform. These thresholds are usually around 50% of the signal swing, indicating when the signal has transitioned through half of its final value.

![Screenshot (652)](https://github.com/user-attachments/assets/2ce086de-765b-4715-9faa-f6130369c721)
![Screenshot (653)](https://github.com/user-attachments/assets/9fd77274-5efa-406e-8f10-8aa437c8aa42)
![Screenshot (654)](https://github.com/user-attachments/assets/3681b2d5-3e0c-4567-b450-e8b1dbb10300)

### Propagation Delay and Transition Time

1. Propagation Delay:
-  It Measures the time difference between when the input reaches a threshold (e.g., 50%) and when the output reaches the same threshold.

                        Propagation Delay = Time (out_rise_thr) − Time (in_rise_thr)

-  Negative delays indicate poor threshold point choices or issues with the waveform. Correct threshold selection is crucial to avoid inaccuracies

![Screenshot (655)](https://github.com/user-attachments/assets/e23b15ff-5683-48ca-a243-79632499bb2b)
![Screenshot (656)](https://github.com/user-attachments/assets/6bbf9b64-e5d6-4af0-a9d1-f7e3c9cfe643)
![Screenshot (657)](https://github.com/user-attachments/assets/d98909ec-219c-456a-9257-f94889f1fa57)
![Screenshot (658)](https://github.com/user-attachments/assets/a20c2af2-09f1-45bd-b216-6b1b4e811ccc)
![Screenshot (659)](https://github.com/user-attachments/assets/5a3afc55-e668-407d-8f2b-d31ddbb919b3)

2. Transition Time:
-  It  Measures the time taken for the signal to transition between two points on the waveform, often defined by high and low thresholds.

  Transition Time = 
    -  for rise waveform, Time(slew_high_rise) − Time(slew_low_rise)
    -  for fall waveform, Time(slew_high_fall) − Time(slew_low_fall)
  
![Screenshot (660)](https://github.com/user-attachments/assets/d16a7b97-4370-4e4a-a4dc-546cd9531d88)
![Screenshot (661)](https://github.com/user-attachments/assets/92d1bd07-59d8-41d0-81fb-7ec81fb09a69)


# Day 3 
# SKY130 - Design library cell using Magic Layout and NGSPICE characterization
## L1 - Labs for CMOS inverter ngspice simulations
### IO placer revision
-  IO placer is one of the open-source EDA tools used to place the Input and Output around the core.
-  Below one is the pre IO Placer Image

![ol10](https://github.com/user-attachments/assets/22673f48-bb3b-49f2-adf6-4edf78c3c358)

-  Now, first, we need to check the switches in the configuration. Then, we have to find the syntax "env(FP_IO_MODE) 1" and change it to "env(FP_IO_MODE) 2". After that, we need to run the floor planning again.
-  Below are the images,

![Set_fp_to 2](https://github.com/user-attachments/assets/09eaedf0-5e0b-4857-811d-e2f03d40082e)
![Set_fp_to_2](https://github.com/user-attachments/assets/752b6643-1986-41a8-b4c7-882ef750d78e)

-  After changing it, finally, we need to check our Placement post IOPlacer step. below is the image for that

![IO Final](https://github.com/user-attachments/assets/16dd77f5-ed71-4822-987f-3656c608e616)

## SPICE DECK creation for CMOS

-  For SPICE deck creation for a CMOS inverter, you're essentially generating a netlist that outlines the connectivity of the circuit. It includes details of the components (like MOSFETs) and their connections.

-  The Voltage Transfer Characteristic (VTC) SPICE simulation involves running this netlist through a simulator, providing input signals, and capturing the output response. This helps in analyzing the behavior of the inverter, specifically how input voltages map to output voltages, giving insight into its switching characteristics.

-  This process comprises of 4 steps,
### step-1 Component connectivity :
-  First we need to create spice deck. It is nothing but the connectivity info about Netlist. It has everythng like Input that should provide to the simulation and TAC points which will take the output.
-  M1 -> PMOS , M2 -> NMOS . We need to define the connectivity of the substrate terminal. The substrate terminal is a potential component or pins on your NMOS and PMOS.
-  The source of PMOS is connected to Vdd, NMOS is connected to Vss and we also have an output load capacitor.

![Screenshot (662)](https://github.com/user-attachments/assets/98fe21ea-0714-4d04-b831-8109c90bed34)

### Step-2 Component Values:
-  In this step, we mainly focus on the values for PMOS and NMOS.
-  The PMOS is given the values of width/Length as 0.375u/0.25u. It says our channel length is 250nm or 0.25u(micron) and the channel width is 375nm or 0.375u.
-  The same values we are assuming for M2 which is our NMOS.
-  There is a scenario where the PMOS should be wider than the NMOS.
-  Ideally, our PMOS should be twice or thrice bigger than our NMOS.
-  We assume the output load is 10fF(Femto-Farads). This output comes after lots of calculations like output capacitance and etc.
-  The Input gate voltage we assume it as 2.5v and we assume the drain voltage or main supply voltage as 2.5v

![Screenshot (663)](https://github.com/user-attachments/assets/59d20e1a-087e-4233-adb8-2aae3f4908a0)
![Screenshot (664)](https://github.com/user-attachments/assets/25fa62fb-53f2-4120-a561-be41183b9e1b)
![Screenshot (665)](https://github.com/user-attachments/assets/f4da63d9-e353-4808-982e-3442e36c77f5)


### Step-3 Identify nodes"
-  Nodes here mean the points between two components.
-  The node names here as per the circuit are, In, Vdd, Out, and Vss or 0.
-  If you want to define load capacitor, we will say that load capacitor lies between "Out" & "0". Same for Vdd as well.

![Screenshot (666)](https://github.com/user-attachments/assets/c008aa5c-874f-480b-9789-18cd367a35ce)
![Screenshot (667)](https://github.com/user-attachments/assets/2af0c38e-6dc5-40ec-9a49-70295bdc2285)


### Step-4 Let's write SPICE Deck:
-  The below image is a SPICE Deck which is written as per the circuit.

![Screenshot (672)](https://github.com/user-attachments/assets/de3c4281-6e4a-49d7-9ea7-958858ad6304)

-  So now, let's get some idea about each line of SPICE Deck
-  The first line which is

                              M1 out in vdd vdd pmos W=0.375u L=0.25u

![Screenshot (668)](https://github.com/user-attachments/assets/9f27e098-2eae-489f-b9dc-a47cdbec1328)
   
-  This line completely describes the PMOS transistor. which is defined by the name "M1".
-  There is a trick which is to understand which is drain, which is source and gate in the given syntax.
-  Trick, After M1, consider the four terms in the form of "D G S S" (Drain, Gate, Source and Substrate). The connectivity explanation in the syntax is written in the form of a given definition which is "D G S S". 
-  "M1 out in vdd vdd" describes, for M1 MOSFET, the drain is connected to the "Out" node. The Gate is connected to the "In" Node. The substrate is connected to the "Vdd" Node and The source is connected to the "Vdd" Node. PMOS which us M1 is of type PMOS.

                              M2 out in 0 0 nmos W=0.75u L=0.25u

![Screenshot (669)](https://github.com/user-attachments/assets/2aac8071-e6be-49d6-a102-bc1f99969398)
   
-  Same for the above line as well, for M2 MOSFET, the drain is connected to the "Out" node. The gate is connected to the "In" Node and the source is connected to the "0" Node The substrate is connected to the "0" Node.
-  Let's describe the connectivity information for other components and also for our circuit.

                              cload out 0 10f
                              Vdd vdd 0 2.5
                              Vin in 0 2.5

![Screenshot (670)](https://github.com/user-attachments/assets/48d797a9-8b85-4325-8903-69c6cfa05656)
   
-  The above line describes about load capacitor, which is connected between "Out" Node and "" Node. Its value is of 10fF. Same for Vdd and Vin.
-  Let's see about Simulation commands

                              .op
                              .dc Vin 0 2.5 0.05

![Screenshot (671)](https://github.com/user-attachments/assets/efd0a5e2-84f3-41fb-b4ef-45270a38a7b3)

   
-  These 2 lines describe, we will be sweeping the gate voltage (Input voltage) of the NMMOS from 0 to 2.5 at steps of 0.05. The reason here is we need to calculate the voltage at Output (out) while we sweep the input voltage because of the Voltage Transfer Characteristics (VTS) - Output voltage vs Input Voltage.

  ### Step-5 Describing Model File:
  -  This is where we get the complete description of PMOS and NMOS trasistors and All parameters which is related to 250nm technology node and all will be described in the model file which is in ` .mod file` extension.

                                .LIB "tsmc 0.25um_model.mod" CMOS MODELS
                                .end
![Screenshot (672)](https://github.com/user-attachments/assets/1528bc1a-502e-471e-b6b5-d949a56b9b3d)


## SPICE SIMULATION
-  Now we will be doing the SPICE SIMULATIONS for the below-provided specifications.

![Screenshot (674)](https://github.com/user-attachments/assets/000ca040-3926-471f-9586-4c8720dbd9b7)
  
-  Steps to run : path -> Source of ckt file (.cir) -> To Execute that ,the command is run -> Next "Setplot" -> dc1 -> display -> plot out vs in.
-  Below are the screenshots for your reference.

![Screenshot (675)](https://github.com/user-attachments/assets/aa4aacbc-7460-45b9-bf38-9599f2f2c456)
![Screenshot (676)](https://github.com/user-attachments/assets/9b8fcb0f-004d-4c95-8496-b03c07ee9169)
![Screenshot (677)](https://github.com/user-attachments/assets/1fccc10a-4235-4288-961e-a92b8ba05b1a)
![Screenshot (678)](https://github.com/user-attachments/assets/93465797-8172-4e12-979a-9a41cf3432cd)
![Screenshot (679)](https://github.com/user-attachments/assets/34deddc6-432b-47f4-993b-4dbcb2c7dbc2)
![Screenshot (680)](https://github.com/user-attachments/assets/d08d9006-cc44-4259-8848-53e9d0518602)
![Screenshot (681)](https://github.com/user-attachments/assets/e0a8729f-81f5-46a0-a6c9-3f3fb042818c)
![Screenshot (682)](https://github.com/user-attachments/assets/1a93d876-e116-4142-8892-f7344a65fe74)
![Screenshot (683)](https://github.com/user-attachments/assets/70a893fc-3b7f-4eae-a442-8af3d3becf1f)
![Screenshot (684)](https://github.com/user-attachments/assets/b05f9362-3e3f-4169-bb51-f5a8de73b399)
![Screenshot (685)](https://github.com/user-attachments/assets/b9d8af67-d229-4a08-9518-f741dabe2894)

-  lets analyze the waveforms of the above-implemented simulation.

![Screenshot (686)](https://github.com/user-attachments/assets/a9262cca-c806-4096-abf5-396ecc4bc57b)
![Screenshot (687)](https://github.com/user-attachments/assets/c39c8cdd-fea0-4df7-897b-7d69ff44e542)

-  Now let's change the values of Wp which is the width of the PMOS which is shifted 2.5 times of our NMOS channel width (0.375 * 2.5 = 0.9375)

![Screenshot (690)](https://github.com/user-attachments/assets/202ef39b-696b-4aef-ab5c-5e270465376f)

-  We have increased the width of the PMOS Transistor.
-  Lets analyze the waveforms.

![Screenshot (691)](https://github.com/user-attachments/assets/5f58d15c-227f-4256-8305-122979f1b491)

-  Now let's compare the two waveform specifications which we implemented.

![Screenshot (692)](https://github.com/user-attachments/assets/76637351-c3e3-4a75-ab7f-aa6deed5cfdb)

Here is the first characteristic that we got after analyzing is 

### The switching threshold (Vm): 
-  In a CMOS inverter is the input voltage at which the output voltage equals the input voltage, meaning 𝑉𝑖𝑛=𝑉𝑜𝑢𝑡. This parameter is key to defining the robustness of the inverter circuit. Regardless of the NMOS or PMOS sizes, the behavior remains consistent: when 
𝑉𝑖𝑛 is low, 𝑉𝑜𝑢𝑡​ is high, and vice versa. This characteristic, maintained across different transistor sizes, contributes to the reliability and widespread use of CMOS logic in gate designs.
-  Switching Threshold means the point at which the device switches. As per the waveforms, Irrespective of voltage levels both the shapes are the same. As shown below,

![Screenshot (693)](https://github.com/user-attachments/assets/be480c44-6e86-458f-be0f-eba4c243880d)
![Screenshot (694)](https://github.com/user-attachments/assets/69e4d21f-7572-4e6a-b91f-04c36bf05c80)

 
### Static Characteristics :
-  Static characteristics of a CMOS inverter refer to the steady-state behavior of the circuit, which describes how the output voltage changes in response to different input voltages. These characteristics are captured in the Voltage Transfer Characteristic (VTC) curve.
-  Vm is the point where Vin = Vout, Vgs = Vds and Idsp = - Idsn.


![Screenshot (695)](https://github.com/user-attachments/assets/8fcafefc-f7cd-4498-bdf5-107c1644e9fe)
![Screenshot (696)](https://github.com/user-attachments/assets/a2746e6e-1407-4fc0-9ad5-3602cd0d3361)
![image](https://github.com/user-attachments/assets/fd0d572a-bdb8-4ffb-bfa7-0e35601307a8)


### Static and Dynamic Simulations of CMOS Inverter
-  Now let's do the dynamic simulations, where we identify what is the value of rise and fall delay and how it varies by varying switching thresholds.
-  Let's introduce one more spice deck with Transient analysis as an add-on. Everything else remains same and also the input we provide will be a pulse and the Simulation command will be transient analysis

                                        .tram 10p 4n 

![Screenshot (698)](https://github.com/user-attachments/assets/94369aef-777c-4519-8174-1a9bb5e7e34d)

-  Here the pulse we provide is

                              Vin in 0 0 pulse 0 2.5 0 10p 10p 1n 2n


-  The pulse Starting from 0v and ends at 2.5v. The shift is 0 and it says that the pulse is starting at exactly time unit 0. If it is 50ps, then the pulse would have started after 50ps.
-  In the above syntax the 1n and 2n are defined as the pulse width because it is 50% duty cycle and the Complete cycle is 2n.
-  The Rise time and fall time are 10ps and 10 ps. Now this particular pulse is fed as in input to our CMOS and does transient analysis.
-  The same steps that we need to follow for this as we implemented earlier. The only difference here we see is an extra command which is "setplot" . It defines the transient analysis.
-  Below are the screenshots of particular implementations.

![Screenshot (698)](https://github.com/user-attachments/assets/8ff37684-d06c-49b5-8328-6b094870dd33)
![Screenshot (699)](https://github.com/user-attachments/assets/beab81e8-d081-434d-a46f-4e21a37da835)
![Screenshot (700)](https://github.com/user-attachments/assets/c032278b-4e44-4a4d-b1ed-1f63cada2f31)
![Screenshot (701)](https://github.com/user-attachments/assets/60c0df07-f401-4537-841b-a8eeba13d163)
![Screenshot (702)](https://github.com/user-attachments/assets/5cb8f855-d19d-4598-8bce-5ccf1e213daa)
![Screenshot (703)](https://github.com/user-attachments/assets/2f8b510a-820f-428a-9627-1ba53011c188)
![Screenshot (704)](https://github.com/user-attachments/assets/1b07893a-adfe-47d8-bb43-49c1f7f6a9fc)
![Screenshot (705)](https://github.com/user-attachments/assets/72840f36-9df7-45a9-9558-d54922d182a3)
![Screenshot (706)](https://github.com/user-attachments/assets/6f497ea9-4625-4cd2-adac-4cd5dc00240a)
![Screenshot (707)](https://github.com/user-attachments/assets/2acf75d8-925f-4289-87fd-679ca212c73a)
![Screenshot (708)](https://github.com/user-attachments/assets/0271ca4c-767b-4880-8619-6b1e395e736a)

-  Finally, we get the waveforms of Time vs voltage and by that we can calculate the rise and fall delay.

![Screenshot (709)](https://github.com/user-attachments/assets/fcc741c7-9733-4930-a59e-b03fb883c426)
![Screenshot (710)](https://github.com/user-attachments/assets/6b34bb80-7315-49dd-8555-e53042a1c4d9)
![Screenshot (711)](https://github.com/user-attachments/assets/05fdb410-3c10-41eb-a578-828e644ca355)
![Screenshot (712)](https://github.com/user-attachments/assets/4ed466b4-88dc-41dc-a7e4-d172688fc4da)
![Screenshot (713)](https://github.com/user-attachments/assets/6d370eb8-cc44-42be-8e91-7ec0c4730d48)
![Screenshot (714)](https://github.com/user-attachments/assets/eab99f0d-925c-490d-979a-b476cefd40bc)
![Screenshot (715)](https://github.com/user-attachments/assets/bc28599b-4a0f-4225-a994-cd92a706e616)
![Screenshot (716)](https://github.com/user-attachments/assets/186ae5ee-97bd-40b5-a0eb-8194a28c19aa)
![Screenshot (717)](https://github.com/user-attachments/assets/e65710f1-cebf-4ef6-91da-b1dc490364a2)
![Screenshot (718)](https://github.com/user-attachments/assets/8adb250c-3fab-441a-ae9a-94616450e119)
![Screenshot (719)](https://github.com/user-attachments/assets/efde8218-75f3-4cfd-a58a-2687b2bfca4d)
![Screenshot (720)](https://github.com/user-attachments/assets/e9ffff00-6b71-4601-8ffd-2b4680a637f4)
![Screenshot (721)](https://github.com/user-attachments/assets/054cd031-3dc3-4a98-94bf-188b71469b6e)
![Screenshot (722)](https://github.com/user-attachments/assets/bf4f537f-b46b-4c03-a537-f30fb1bc2a4c)


## LAB STEPS TO GIT-CLONE

The following images and information show the git clone options,

          cd Desktop/work/tools/openlane_working_dir/openlane

          git clone https://github.com/nickson-jose/vsdstdcelldesign
   
          cd vsdstdcelldesign
    
          cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech

          magic -T sky130A.tech sky130_inv.mag &

![gitclone](https://github.com/user-attachments/assets/32642e94-c085-4f3f-8315-dd2a49892f5e)
![gitclone_2](https://github.com/user-attachments/assets/072b894f-86e5-45a7-b374-4f40990945b1)
![copying_sky130A](https://github.com/user-attachments/assets/445ba7ef-53d0-4f1a-9ccc-eb3a44537eb8)
![Aftercopying_sky130A](https://github.com/user-attachments/assets/5d50db21-bd2f-41e1-b370-c655d8f103ea)

## ThEORY - INCEPTION OF LAYOUT & CMOS FABRICATIONS

-  The process of CMOS fabrication involves various stages, including substrate selection, isolation, well formation, gate terminal creation, and interconnect formation.

### 1. Substrate Selection:
-  Starting Material: The process begins with a p-type silicon wafer, usually oriented along the (100) crystallographic plane, which has a resistivity of 5-50 ohms to allow high-performance transistors.
-  Importance: The substrate acts as the foundation for all subsequent fabrication steps. A well-doped substrate helps control parasitic capacitances and ensures optimal electrical properties.

 ![Screenshot (725)](https://github.com/user-attachments/assets/2aabe35c-1f2a-418a-a47d-991a37e0b207)  

### 2. Active Region Formation:
-  Defining the Regions: The p-type silicon substrate is etched to create isolated pockets, where individual NMOS and PMOS transistors will be formed.
-  Isolation Process:
    -  A thin layer (~40 nm) of silicon dioxide (SiO₂) is deposited for electrical isolation.
    -  Over the SiO₂, a thicker (~80 nm) silicon nitride (Si₃N₄) layer is deposited, which will serve as a hard mask during subsequent etching steps.
-  Photolithography and Etching:
    -  A photoresist layer (~1 µm) is deposited over the Si₃N₄ layer, and Mask 1 is applied using UV light to expose unwanted regions.
    -  The exposed Si₃N₄ is etched away, exposing the SiO₂ underneath.
    -  The photoresist is then removed, and the wafer undergoes a Local Oxidation of Silicon (LOCOS) process to grow thick SiO₂ in the exposed areas, creating an insulating layer. This prevents interference between transistors (known as bird’s beak formation during oxide growth).
-   Final Cleaning: Si₃N₄ is removed using hot phosphoric acid to complete the isolation of transistor regions.

![Screenshot (726)](https://github.com/user-attachments/assets/7b176bcc-16d1-44bf-a081-a46cc9a02864)
![Screenshot (727)](https://github.com/user-attachments/assets/8a5ac75a-f5cd-4a98-9593-8acb7f7cf98a)
![Screenshot (728)](https://github.com/user-attachments/assets/bff6bd4a-4411-4112-8927-16c5e56ae26e)
![Screenshot (729)](https://github.com/user-attachments/assets/32fb8cba-b181-4078-a3fe-20d6e2514c15)
![Screenshot (730)](https://github.com/user-attachments/assets/ce02c1ee-0ef5-4205-8885-560f5fae6430)
![Screenshot (731)](https://github.com/user-attachments/assets/f7529b24-b23c-4fdf-9286-f1e66b1f5cd7)
![Screenshot (732)](https://github.com/user-attachments/assets/b835fa9b-fd64-4d2c-afe4-e6e9c8a70c84)
![Screenshot (733)](https://github.com/user-attachments/assets/babcf489-6b04-4234-847a-90a7bd6cdba2)


### 3. N-Well and P-Well Formation:
-  Well Definition: The NMOS transistors require a P-well, and the PMOS transistors need an N-well. These wells are not formed simultaneously.
-  Photolithography (Mask 2 & Mask 3):
First, the P-well region is protected with photoresist, and Mask 2 is used for patterning. Boron ions (~200 keV) are implanted into the exposed area, creating a P-type region. Similarly, Mask 3 is applied to form the N-well using Phosphorus ions.
-  Drive-In Diffusion: After implantation, the wafer is placed in a high-temperature furnace to diffuse the dopants deeper into the substrate, forming the final well structures.

![Screenshot (735)](https://github.com/user-attachments/assets/cc40d361-3a5a-45af-88de-850082583a37)
![Screenshot (736)](https://github.com/user-attachments/assets/7e5ef27e-c5cd-40fe-b818-dc966d5dda96)
![Screenshot (737)](https://github.com/user-attachments/assets/ac6a3177-5550-46c0-abbb-2f0f970d32b9)
![Screenshot (738)](https://github.com/user-attachments/assets/64add539-2502-47fc-8268-1d55aeede095)
![Screenshot (739)](https://github.com/user-attachments/assets/691651b6-3ca4-4c6e-a32b-695add94feca)
![Screenshot (740)](https://github.com/user-attachments/assets/0593c23d-b07a-4128-997f-81e82d855755)
![Screenshot (741)](https://github.com/user-attachments/assets/4c3ee6ae-b0d9-45fb-9785-0c56f0d41ab1)
![Screenshot (742)](https://github.com/user-attachments/assets/98be5a03-e64f-4399-b572-709e453f8d37)
![Screenshot (743)](https://github.com/user-attachments/assets/e5d95097-edab-492f-a37b-58b0b283c353)
![Screenshot (744)](https://github.com/user-attachments/assets/8bc8e2ab-babf-4807-af1e-f97064f5f847)
![Screenshot (745)](https://github.com/user-attachments/assets/53ea2107-0d4b-4264-a970-d1e1c10904bd)
![Screenshot (746)](https://github.com/user-attachments/assets/73f8ccc5-91fe-4c66-8f3f-8c5ed9616b5f)
![Screenshot (747)](https://github.com/user-attachments/assets/6fe7f6f3-e569-4dad-9e9a-f00b3535f3bb)

 
### 4. Gate Formation:
-  Gate Oxide: The gate is a crucial terminal controlling the transistor's switching behavior. To start, the damaged oxide layer from previous steps is removed using hydrofluoric acid (HF).
-  New Oxide Growth: High-quality oxide (~10-20 nm) is regrown to provide a gate dielectric layer that controls the transistor's threshold voltage.
-  Polysilicon Deposition: A polysilicon layer (doped to reduce resistance) is deposited over the oxide. The polysilicon serves as the gate terminal in both NMOS and PMOS transistors.
-  Etching: Mask 6 is used to etch away the unnecessary polysilicon, defining the gate regions.


![Screenshot (748)](https://github.com/user-attachments/assets/fb14d665-b29e-47f2-83cb-9a6b1b4709fa)
![Screenshot (749)](https://github.com/user-attachments/assets/79928416-b1b1-43a7-a4dd-8310ab786bbb)
![Screenshot (750)](https://github.com/user-attachments/assets/9ff40abb-8b06-47a6-885d-adac97ab7438)
![Screenshot (751)](https://github.com/user-attachments/assets/880ffb6f-57c4-47b6-992a-0951e79db748)
![Screenshot (752)](https://github.com/user-attachments/assets/d13ea3b4-9eeb-450d-a0c3-6fd295d1b098)
![Screenshot (753)](https://github.com/user-attachments/assets/d7c14f20-e172-4c85-8c9b-b7ca624490d6)
![Screenshot (754)](https://github.com/user-attachments/assets/fbe5e787-c011-4a96-b3cf-f2c2e0d99207)
![Screenshot (755)](https://github.com/user-attachments/assets/7e69f95f-2158-434a-a9f2-a8a9de13ae98)
![Screenshot (756)](https://github.com/user-attachments/assets/0d7a1620-245f-46c1-a61a-60e18252ae47)
![Screenshot (757)](https://github.com/user-attachments/assets/b8e05a91-3033-4a12-95f6-8c1962381a80)
![Screenshot (758)](https://github.com/user-attachments/assets/3c248b1c-64d2-46f5-8c78-88c29c8c6fa3)
![Screenshot (759)](https://github.com/user-attachments/assets/c6ecda21-80e8-4370-9593-43a69e5eb0df)


### 5. Lightly Doped Drain (LDD) Formation:
-  Mitigating Short-Channel Effects: The LDD structure helps minimize hot electron effects and short-channel issues by using gradual doping.
-  Process:
    -  For NMOS, phosphorus ions are implanted using Mask 7 to create lightly doped N regions (N-).
    -  For PMOS, boron ions are implanted using Mask 8, forming lightly doped P regions (P-).
-  Spacer Formation: Thick layers of SiO₂ or Si₃N₄ are deposited, and anisotropic etching is performed to create spacers on the sides of the gate. These spacers protect the light doping regions during subsequent high-energy doping.

![Screenshot (760)](https://github.com/user-attachments/assets/21883e2f-1fc2-477b-9ac9-b22b792f5eaf)


### 6. Source/Drain Formation:
-  Screen Oxide Layer: A thin screen oxide layer is deposited to prevent channeling during ion implantation.
-  Ion Implantation:
    -  In the P-well (NMOS region), arsenic ions are implanted (~75 keV) using Mask 9 to create heavily doped N+ regions, which will form the source and drain.
    -  In the N-well (PMOS region), boron ions (~50 keV) are implanted using Mask 10 to form the P+ source and drain regions.
Annealing: A high-temperature annealing step (~1000°C) activates the dopants and repairs any crystal damage from implantation.

![Screenshot (761)](https://github.com/user-attachments/assets/7e53cf4f-90df-40f2-ae44-a57ef320bd9b)
![Screenshot (762)](https://github.com/user-attachments/assets/87801937-c4ee-49a7-8e20-07d6474f8536)
![Screenshot (763)](https://github.com/user-attachments/assets/58335c51-9a9e-4de5-aaca-3be598fa5735)
![Screenshot (764)](https://github.com/user-attachments/assets/b4d3e3bc-ebbb-4d3c-a3f8-6011b151446b)
![Screenshot (765)](https://github.com/user-attachments/assets/5f569d69-4314-494d-9566-366b18344f97)
![Screenshot (766)](https://github.com/user-attachments/assets/d75a73fd-e2ff-4bee-8461-64acfba10a22)
![Screenshot (767)](https://github.com/user-attachments/assets/4ce53669-f324-4fe5-9cf6-be43c83a7f3d)



### 7. Local Interconnect Formation:
-  Etching and Metal Deposition: The thin screen oxide layer is removed, and a layer of titanium (Ti) is sputtered over the wafer. Ti has low resistivity and excellent adhesion properties.
-  Reaction and Silicide Formation:
  -  The wafer is heated to around 650-700°C in a nitrogen (N₂) atmosphere for a short time (~60 seconds). Titanium reacts with the silicon in the source, gate, and drain regions, forming titanium silicide (TiSi₂).
  -  Another reaction between Ti and nitrogen forms titanium nitride (TiN), which serves as a barrier and contact material for local interconnects.
-  Etching TiN: Using Mask 11 and photolithography, TiN is etched away from undesired areas.

![Screenshot (768)](https://github.com/user-attachments/assets/522fce9e-eec1-46ac-bb9d-350bfbd19075)
![Screenshot (769)](https://github.com/user-attachments/assets/a1057413-e9f7-4a61-ac0b-c8b90e574ec3)
![Screenshot (770)](https://github.com/user-attachments/assets/21e72195-3c1a-4956-8cef-f0a7321eea43)
![Screenshot (771)](https://github.com/user-attachments/assets/281d5bcf-c560-43b9-ab4e-eb46641af3b9)
![Screenshot (772)](https://github.com/user-attachments/assets/54ce70eb-d649-4331-8246-d3c8e502f4f0)
![Screenshot (773)](https://github.com/user-attachments/assets/4091da1c-a402-4ace-afcc-78821af78a81)
![Screenshot (774)](https://github.com/user-attachments/assets/20330939-dd99-4954-aede-730bf7749156)
![Screenshot (775)](https://github.com/user-attachments/assets/c920aa83-d979-461c-b9ca-b11bdcc3f852)
![Screenshot (776)](https://github.com/user-attachments/assets/52a0b9fc-c7ec-42bc-b678-6d5265188841)
![Screenshot (777)](https://github.com/user-attachments/assets/47338d5c-c12c-4a92-ace2-c047643cae8e)


### 8. Higher-Level Metal Formation:
-  Surface Planarization: A thick SiO₂ layer with impurities is deposited over the wafer to create a planar surface, crucial for reliable metal interconnect formation. The surface is then polished using Chemical Mechanical Polishing (CMP) to ensure smoothness. Higher metal layers facilitate complex routing between multiple components on the chip.
-  Metal Thickness: The thickness of metal layers must be carefully controlled to ensure adequate conductivity and to prevent issues such as electromigration.
-  Design Rules: Design rules for spacing, width, and alignment of metal lines must be strictly followed to prevent short circuits, signal degradation, and manufacturing defects.
-  Interconnect Performance: The design of higher-level metal layers impacts the performance of the chip, including signal speed and power consumption.

![Screenshot (778)](https://github.com/user-attachments/assets/64dd4ace-063c-48a1-830b-acdd04bbe019)
![Screenshot (779)](https://github.com/user-attachments/assets/2b72c3d7-dff0-4ac1-adf3-685173de9140)
![Screenshot (780)](https://github.com/user-attachments/assets/8f47d4cf-37aa-4046-8969-a5f0e0ba0292)
![Screenshot (781)](https://github.com/user-attachments/assets/97191d80-44ae-49f4-aee0-a60014c8637f)
![Screenshot (782)](https://github.com/user-attachments/assets/4504e280-5059-4a48-b1ae-5189ea71747e)
![Screenshot (783)](https://github.com/user-attachments/assets/efb7c085-4a8f-45db-b3e2-044ef61b4684)
![Screenshot (784)](https://github.com/user-attachments/assets/89e542f9-8bf3-427b-93f2-e44566586741)
![Screenshot (785)](https://github.com/user-attachments/assets/0073d7b7-8433-4dce-8804-21302443ec11)
![Screenshot (786)](https://github.com/user-attachments/assets/42c13927-280d-4f70-8ca2-35e4d23a696e)
![Screenshot (787)](https://github.com/user-attachments/assets/b755b16d-9f60-4893-8c9d-0a7d7e6b775a)
![Screenshot (788)](https://github.com/user-attachments/assets/99653100-a0d4-43bc-b1bc-183e5364ecc2)
![Screenshot (789)](https://github.com/user-attachments/assets/6258d59e-7094-44ab-8741-f00ad8b3806c)


After all the fabrication steps in which our chip gets involved, the final look is shown below,

![Screenshot (790)](https://github.com/user-attachments/assets/827962ea-61c3-4d48-9f11-ee7a71198efc)


## INTRODUCTION TO SKY 130 BASE LAYERS LAYOUT AND LEF USING INVERTERS

-  Now you need to load the custom inverter layout in Magic.
-  The commands for those to clone the inverter from the git hub shown above earlier. Below is the process for your reference.

![Opeining_Inverter_using_magic](https://github.com/user-attachments/assets/6c8884a3-5f70-4535-b94a-68a395bf9cbb)

-  The Layout screenshot below is for you to look over.

![Inverter_magic](https://github.com/user-attachments/assets/d897b0ad-957e-4b43-8bd0-74f39311d600)

-  Now you need to identify the NMOS and PMOS

![Pmos selected](https://github.com/user-attachments/assets/6cc937ff-04e9-4a6d-a61b-5ce3eaa86151)
![nmos selected](https://github.com/user-attachments/assets/b7eaefc5-81a1-484b-a151-13f32374af12)

-  Now we need to check the output terminal, P and also Nmos. for that, you need to press s once to select and press s again to select the entire thing.

![selecting y](https://github.com/user-attachments/assets/7e9c3b84-9f1f-462c-ab38-39b13ea61e0d)
![selecting p](https://github.com/user-attachments/assets/3e24a228-f96a-48b0-b318-93126eaf2dcc)
![selecting nmos](https://github.com/user-attachments/assets/21993456-2e20-454e-8bcd-5af55e80bb59)

-  Now we need to extract our Inverter in magic tkcon window using the following steps

        pwd
        extract all
        ext2spice cthresh 0 rthresh 0 (This command is for parasitic extraction)
        ext2spice

-  Below are the screenshots for your reference

