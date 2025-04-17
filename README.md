# OZU-RISCV32 Simulator

A RISC-V 32-bit instruction set architecture simulator and disassembler developed for educational purposes. This simulator implements the core RISC-V (RV32I) instruction set with a user-friendly command-line interface.

## Features

- Simulation of RISC-V programs with detailed instruction handling
- Support for R-type, I-type, S-type, SB-type, U-type, and J-type instructions
- In-memory program loading and execution
- Interactive command-line interface for simulation control
- Register state inspection
- Memory content viewing
- Program disassembly in readable RISC-V assembly format
- Step-by-step instruction execution

## Setup and Installation

### Prerequisites

- GCC compiler
- Make (optional, but recommended)
- A terminal or command prompt

### Compilation

1. Navigate to the source directory:
   ```
   cd /path/to/ozu-riscv32-v1/src
   ```

2. Compile using the provided Makefile:
   ```
   make
   ```
   
   Or compile manually:
   ```
   gcc -Wall -g -O2 ozu-riscv32.c -o ozu-riscv32
   ```

## Usage

### Running the Simulator

Execute the simulator with an input program file:

```
./ozu-riscv32 <input_program>
```

The input program should contain RISC-V machine code in hexadecimal format (one instruction per line).

### Simulator Commands

Once the simulator is running, you can use the following commands:

| Command | Description |
|---------|-------------|
| `sim` | Simulate the program to completion |
| `run <n>` | Execute `n` instructions |
| `rdump` | Display all register values |
| `reset` | Clear registers/memory and reload the program |
| `input <reg> <val>` | Set register `reg` to value `val` |
| `mdump <start> <stop>` | Display memory content from address `start` to `stop` |
| `print` | Display the loaded program in assembly format |
| `?` | Show help menu |
| `quit` | Exit the simulator |

## Supported Instructions

The simulator supports the following RISC-V instructions:

### R-Type Instructions
- Arithmetic: `add`, `sub`, `mul`, `div`, `divu`
- Logical: `and`, `or`, `xor`
- Shifts: `sll`, `srl`, `sra`
- Comparisons: `slt`, `sltu`

### I-Type Instructions
- Arithmetic immediate: `addi`
- Logical immediate: `andi`, `ori`, `xori`
- Shifts immediate: `slli`, `srli`, `srai`
- Comparisons immediate: `slti`, `sltiu`
- Loads: `lb`, `lh`, `lw`, `lbu`, `lhu`
- Control transfer: `jalr`

### S-Type Instructions
- Stores: `sb`, `sh`, `sw`

### SB-Type Instructions
- Branches: `beq`, `bne`, `blt`, `bge`, `bltu`, `bgeu`

### U-Type Instructions
- `lui` (Load upper immediate)
- `auipc` (Add upper immediate to PC)

### J-Type Instructions
- `jal` (Jump and link)

### System Instructions
- `ecall` (Environment call)

## Memory Layout

The simulator defines two memory regions:
- Text segment: 0x00010000 - 0x10000000
- Data segment: 0x10000000 - 0xBFFFFFFF

The stack grows downward from 0xBFFFFFFF.

## Example

The repository includes a sample RISC-V assembly program in testAssembly.S that demonstrates loading and storing operations along with basic arithmetic instructions.

## Project Structure

- src: Contains source code files
  - ozu-riscv32.c: Main simulator implementation
  - ozu-riscv32.h: Header file with declarations and memory layout
- whisperSimLab2: Contains sample test programs

## Known Limitations

- Limited support for system calls (only program termination via `ecall`)
- No floating-point instruction support
- No privileged instruction support

## License

This project is provided for educational purposes. Please check with the original authors for licensing information.

## Acknowledgments

- RISC-V Foundation for the open instruction set architecture
- Ozyegin University for supporting the development of this educational tool
- All contributors to the project

---

For more information about RISC-V, visit the [official RISC-V website](https://riscv.org/).