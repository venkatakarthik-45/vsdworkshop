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








     



