# RISC-V Single-Cycle Processor with CSR Support

This project presents a **basic RISC-V single-cycle CPU design** that includes support for **Control and Status Registers (CSRs)**. It is intended as an **educational reference** for understanding how RISC-V instructions are executed, how privileged CSRs work, and how exceptions are handled in a simple processor.

The design prioritizes **clarity and learning** over performance or optimization.


## Key Characteristics

* Implements the **RV32I base integer instruction set**
* Uses a **single-cycle datapath** (each instruction completes in one clock cycle)
* Includes **machine-mode CSR functionality**
* Supports basic **exception and interrupt handling**
* Simple register file and memory models
* Written in **Verilog or VHDL** (depending on implementation choice)
* Well-suited for students studying computer architecture or RISC-V internals


## CSR Support

The processor includes a dedicated CSR unit with support for common machine-mode registers:

* `mstatus` – Machine status register
* `mtvec` – Trap vector base address
* `mepc` – Exception program counter
* `mcause` – Exception cause register

Supported CSR features:

* CSR read, write, and modify instructions
* Automatic CSR updates during exceptions
* Control flow redirection to exception handlers


## Processor Architecture

This is a **single-cycle architecture**, meaning all stages of instruction execution occur within one clock cycle.

### Main Components

* **Program Counter (PC)**
  Tracks the address of the current instruction.

* **Instruction Memory**
  Stores the program instructions.

* **Register File**
  Contains 32 general-purpose registers (`x0–x31`).

* **ALU**
  Executes arithmetic, logical, and comparison operations.

* **Data Memory**
  Used for load and store instructions.

* **Control Unit**
  Generates control signals based on instruction fields (`opcode`, `funct3`, `funct7`).

* **CSR Unit**
  Manages privileged registers and system instructions.

* **Exception Logic**
  Handles illegal instructions, system calls, and traps.

## Datapath Operation

The instruction flow in the single-cycle datapath is as follows:

1. Instruction is fetched using the PC
2. Instruction fields are decoded (`opcode`, `rs1`, `rs2`, `rd`, immediate)
3. ALU or CSR operation is performed
4. Data memory is accessed if required
5. Results are written back to the register file
6. PC is updated (normal execution or exception redirection)

Since all of this happens in one cycle, the design is easy to analyze but not optimized for speed.

## Supported Instructions

### Integer (R-Type)

* `ADD`, `SUB`, `AND`, `OR`, `XOR`
* `SLL`, `SRL`, `SRA`
* `SLT`, `SLTU`

### Immediate (I-Type)

* `ADDI`, `ANDI`, `ORI`, `XORI`
* `SLTI`, `SLTIU`
* `SLLI`, `SRLI`, `SRAI`

### Load and Store

* Loads: `LB`, `LH`, `LW`, `LBU`, `LHU`
* Stores: `SB`, `SH`, `SW`

### Branch

* `BEQ`, `BNE`
* `BLT`, `BGE`
* `BLTU`, `BGEU`

### Jump

* `JAL`, `JALR`

### CSR Instructions

* `CSRRW`, `CSRRS`, `CSRRC`
* `CSRRWI`, `CSRRSI`, `CSRRCI`

---

## Exception and Trap Handling

The processor supports **machine-mode exceptions**, including:

* Illegal instruction exceptions
* Misaligned memory accesses
* `ecall` and `ebreak`

During an exception:

* `mepc` stores the faulting instruction address
* `mcause` records the reason for the exception
* `mtvec` provides the address of the exception handler
* Control flow is redirected to the handler automatically

---

## How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/Moizadlh/RISC-V_SingleCycleWithCSR.git

### 2. Open the Project

* Open the folder in **Visual Studio Code**
* Install a **SystemVerilog extension** for better readability and navigation

### 3. Compile the Design

Use any HDL simulator such as:

* ModelSim
* Vivado
* QuestaSim
* Other compatible simulators

Compile all source files before running the testbench.


### 4. Run Simulation

* Execute the provided testbench
* Observe instruction execution, CSR behavior, and exception handling


### 5. View Waveforms

* Open waveform output files in **GTKWave**
* Inspect signals such as:

  * PC updates
  * Register writes
  * CSR accesses
  * Exception transitions

## Suggested Experiments

You can modify the testbench to explore:

* Arithmetic and logical operations
* Load and store execution
* Branch and jump behavior
* CSR read/write instructions
* Exception and trap handling mechanisms


## Educational Goal

This project is meant to serve as a **learning tool**, helping users:

* Understand single-cycle CPU design
* Learn how CSRs work in RISC-V
* Study exception and trap handling
* Build a foundation for pipelined and multi-cycle processors



Just tell me 👍
