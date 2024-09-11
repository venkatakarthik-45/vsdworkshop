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
## L1,L2,L3 - OpenLANE Directory structure in detail

-  Before going into the Openlane Directory structure, lets know about the basic commands which we use in this tool.
-  cd : Change directory
-  ls -ltr : List everything in chronological order
-  ls -help : list all the commands and its meaning
-  clear : clearning everything.

-  Coming to the OpenLane Directory, 
>  Open the terminal window and first we need to change our current directory to openlane directory which is shown in below.
  `cd Desktop/work/tools/openlane_working_dir/openlane` 
>  Next we need to type docker
  `docker`
>  Now we are in OpenLane flow with the docker sub-system. we need to Call on interactive mode using the below command
  `./flow.tcl -interactive`
> Now in this mode, we need to add our package for our design using OpenLane flow using the following command
  `package require openlane 0.9`
>  Right now, our package is created and openlane is ready to design, but to design it and generate reports and results we need to          create one folder which is **picorv32a**
  `prep -design picorv32a`  
> Here after doing the above step you will get the output as **Preparation successful**. After getting that you need to proceed with the   below command. Finally, we need to run synthesis for our design using the following command. The output for this command shows that      **Synthesis successful**
  `run_synthesis`

-  I have shared every screenshot below for the above process. Make sure While executing those commands you need to get the exact output    that is shown in screenshots

![ol4](https://github.com/user-attachments/assets/7b523e8a-9d2a-4882-9be3-7c896c058a2b)
![ol5](https://github.com/user-attachments/assets/2453c524-b2b3-47ba-b70c-a57f13420ac1)
![ol7](https://github.com/user-attachments/assets/26f49f56-3251-4297-b4fb-4477cce95df6)

-  After completing the synthesis step, we need to calculate the flop ratio which is shown below,

![image](https://github.com/user-attachments/assets/6966c58e-e726-47c5-80e9-314d764ea07b)

![image](https://github.com/user-attachments/assets/b81497fa-fa59-4241-a2f2-0f827bb46848)



   



     



