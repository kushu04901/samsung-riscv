# Samsung RISC-V Program
### The program is based on the RISC-V architecture and uses open-source tools to teach people about VLSI chip design and RISC-V. The instructor for this internship is Kunal Ghosh Sir.

# Basic Details

### Name: Kushwanth.S
### College: SRI JAYACHAMRAJENDRA COLLEGE OF ENGINEERING, MYSURU 560076
### Email ID: kushwanthsuresh8@gmail.com
### GitHub Profile: kushu04901
### LinkedIN Profile: [Kushwanth S](https://www.linkedin.com/in/kushwanth-s-profile/)

</details>

# Task-1

<details>
<summary> Task-1: C based lab screenshots </summary>
<br>

![image alt](https://github.com/kushu04901/samsung-riscv/blob/5f199e3496a63c141391b7a4a87c69d9dd1af18b/Task1/sum1toNc.png)

### The above is the lab screenshot of a C code to find the sum of number for 1 to any defined number-N. 

</details>

<details>
<summary> Task-1: RISC-V based lab screenshots </summary>
<br>

![image alt](https://github.com/kushu04901/samsung-riscv/blob/77022a334551089ac438d3ad7f4a9888877389a2/Task1/risc-v%20based%20labvideo2.png)

![image alt](https://github.com/kushu04901/samsung-riscv/blob/a8ed3f7b0d020df80d7c7a8600200b35082f11da/Task1/risc-v%20based%20lab%20video.png)

![image alt](https://github.com/kushu04901/samsung-riscv/blob/4525d6a3dcf9fa58397a36db82487160be741cf7/Task1/risc-v%20based%20labvideo1.png)

The above is the RISC-V based lab screenshots where we first display the entire C code in the terminal using the following command:

```
	cat sum1ton.c
```

Next the given code is compliled in riscv64 gcc compiler using the following command:

```
	riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```

Now a new terminal is opened where the following code is ran:

```
	riscv64-unknown-elf-objdump -d sum1ton.o
```

This will now show the the assembly code and the memory location it is stored in.
Type ```/main``` to locate the main section of our code.
We now use the command:
```
	riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```

This also will show the assembly code and the memory location it is stored in but it is optimized for maximum speed. It enables aggressive optimizations that might trade off correctness in some edge cases to produce faster code.
</details>

-------------------------------------------------

# Task-2

<details>
<summary> Task-2: Screenshot of Area of Rectagle C-code using spike instruction </summary>
<br>
The below programme is the code to calculate area of rectangle.

![image alt](https://github.com/kushu04901/samsung-riscv/blob/e47d6ac239a14b44f4e5ee77f6f8d19860725965/task2/areaofractangle.png)

Now the programme will be run using SPIKE.This command is used to run a riscv target programme.
The command is

```
       spike pk	
```
The below is the given screenshot of the riscv taget of area of the rectangle using spike.

![image alt](https://github.com/kushu04901/samsung-riscv/blob/9cdd6a910b2a5129cb46ab21152f78be1f8232f4/task2/spike1.png)
</details>

<details>
<summary> Task-2: Screenshot of RISC-V object dump optimisation of Area of Rectagle programme </summary>
<br>
The below is the screenshot of the O1 object dump optimisation.

![image alt](https://github.com/kushu04901/samsung-riscv/blob/6dae2189e3e8e7539aa031058ea99e8959b65b57/task2/arearectangleriscv.png)

The below is the screenshot of Ofast object dump optimisation

![image alt](https://github.com/kushu04901/samsung-riscv/blob/756a6df9e80a30bad910115057df032f900206fa/task2/areaofrectangleriscvfast.png)

</details>


# Task-3

<details>
<summary> Task-3: Risc-V R,I,S,B,U and J instruction types</summary>
<br>

In the RISC-V instruction set architecture, the instruction types are categorized based on how they handle operands and the kind of operations they perform. The types you mentioned—R, I, S, B, U, and J—are distinct formats that represent different kinds of instructions. Here's an overview of each:
### 1. **R-type (Register)**

**Format**:
```
       | opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | rs2 (5 bits) | funct7 (7 bits) |
	
```

- **Purpose**: Used for arithmetic and logical instructions where the operands are registers.
- **Examples**:  
  - `ADD`, `SUB`, `AND`, `OR`, `XOR`, `SLL`, `SRL`, `SRA`
- **Explanation**: The operation is performed between the two source registers (`rs1`, `rs2`), and the result is stored in the destination register (`rd`).

---

### 2. **I-type (Immediate)**

**Format**:
```
       | opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

	
```

- **Purpose**: Used for instructions that involve an immediate value (constant) and a register.
- **Examples**:  
  - `ADDI`, `ANDI`, `ORI`, `SLTI`, `LUI`, `JALR`
- **Explanation**: The immediate value (`imm`) is either added, ANDed, or processed with the register (`rs1`), and the result is stored in the destination register (`rd`).

---

### 3. **S-type (Store)**

**Format**:
```
| opcode (7 bits) | imm[4:0] (5 bits) | funct3 (3 bits) | rs1 (5 bits) | rs2 (5 bits) | imm[11:5] (7 bits) |
	
```

- **Purpose**: Used for store instructions, where data is written to memory.
- **Examples**:  
  - `SB`, `SH`, `SW`
- **Explanation**: The value in `rs2` is stored at the memory address computed using the value in `rs1` and the immediate offset (`imm`).
- 
---

### 4. **B-type (Branch)**

**Format**:
```
| opcode (7 bits) | imm[12] (1 bit) | imm[10:5] (6 bits) | funct3 (3 bits) | rs1 (5 bits) | rs2 (5 bits) | imm[4:1] (4 bits) | imm[11] (1 bit) |	
```

- **Purpose**: Used for branch instructions, which alter the control flow based on a condition.
- **Examples**:  
  - `BEQ`, `BNE`, `BLT`, `BGE`, `BLTU`, `BGEU`
- **Explanation**: These instructions compare registers (`rs1`, `rs2`) and, if the condition is true, branch to the target address computed with the immediate (`imm`).

---

### 5. **U-type (Upper Immediate)**

**Format**:
```
| opcode (7 bits) | rd (5 bits) | imm[31:12] (20 bits) |	
```

- **Purpose**: Used for instructions that manipulate upper 20 bits of an immediate value.
- **Examples**:  
  - `LUI` (Load Upper Immediate), `AUIPC` (Add Upper Immediate to PC)
- **Explanation**: These instructions load a 20-bit immediate value into the upper part of a register (`rd`) and perform operations accordingly.

---

### 6. **J-type (Jump)**

**Format**:
```
| opcode (7 bits) | rd (5 bits) | imm[19:1] (20 bits) | imm[11] (1 bit) | imm[10:1] (10 bits) |
	
```

- **Purpose**: Used for jump instructions that alter the control flow.
- **Examples**:  
  - `JAL` (Jump and Link)
- **Explanation**: The `JAL` instruction computes the target address using a 20-bit immediate and saves the return address in the destination register (`rd`).

---
</details>
<details>
<summary> Task-3: 32 bit instruction code of 15 instructions </summary>
<br>
	
![image alt](https://github.com/kushu04901/samsung-riscv/blob/02634267bffaa588bb892ec637e91b3362cabefc/task2/areaofrectangleriscvfast2.png)


### 1.
### Instruction:
```
lui a0, 0x2b
```
- **Operation**: `LUI` (Load Upper Immediate)
 ### Instruction Type:
- **Type**: U-type
  - The `LUI` instruction is a **U-type** instruction, which has a specific format for handling immediate values.
```
| opcode (7 bits) | rd (5 bits) | imm[31:12] (20 bits) |
```

Where:
- **Opcode**: `0110111` for the `LUI` instruction.
- **rd**: Destination register `a0`, which corresponds to `x10` in RISC-V. The binary representation for `x10` is `01010`.
- **Immediate**: The 20-bit immediate value. The immediate value `0x2b` becomes `0x2b00000` when shifted to fill the upper 20 bits of the register.

## Assembling the Instruction

- **Opcode for `LUI`**: `0110111`
- **Destination Register (`a0`)**: `x10` → `01010` in binary.
- **Immediate**: `0x2b` → `0x2b00000` (binary: `00101011000000000000000000000000`).

Thus, the full 32-bit binary encoding for `lui a0, 0x2b` is:
```
 0110111_01010_00000000001010110000

```
### 2.
### Instruction:
```
addi sp,sp,-32

```

- **Operation**: `ADDI` (Add Immediate)
  - Adds the immediate value `-32` to the value in register `sp` (stack pointer).
  
- **Source Register**: `sp` (stack pointer, which is `x2` in RISC-V).
- **Destination Register**: `sp` (the result is stored in the same register, `x2`).
- **Immediate Value**: `-32` (in decimal), which is `0xFFFFFFE0` in hexadecimal.

### Instruction Type:
- **Type**: I-type
  - The `ADDI` instruction is an **I-type** instruction, which is used for operations involving an immediate value and a register.

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

```

Where:
- **Opcode**: `0010011` for the `ADDI` instruction.
- **rd**: Destination register (`sp`), which is `x2` in RISC-V. The binary representation for `x2` is `00010`.
- **funct3**: `000` for the `ADDI` instruction.
- **rs1**: Source register (`sp`), which is `x2`. Its binary representation is `00010`.
- **Immediate**: The 12-bit immediate value, which is `-32` (in 2's complement: `0xFFFFFFE0`).

## Assembling the Instruction

- **Opcode for `ADDI`**: `0010011`
- **Destination Register (`sp`)**: `x2` → `00010` in binary.
- **funct3**: `000` (specific to `ADDI`).
- **Source Register (`sp`)**: `x2` → `00010` in binary.
- **Immediate**: `-32` → `0xFFFFFFE0` (binary: `11111111111111111111111000100000`).

Thus, the full 32-bit binary encoding for `addi sp, sp, -32` is:
```
  0010011_00010_000_00010_111111111110

```
### 3.
### Instruction:
```
addi a0, a0, -736 # 2ad20<__clzdi2+0x40>

```

- **Operation**: `ADDI` (Add Immediate)
  - Adds the immediate value `-736` to the value in register `a0`.
  
- **Source Register**: `a0` (which is register `x10` in RISC-V).
- **Destination Register**: `a0` (the result is stored in the same register, `x10`).
- **Immediate Value**: `-736` (in decimal), which is `0xFFFFF4D0` in hexadecimal.

### Instruction Type:
- **Type**: I-type
  - The `ADDI` instruction is an **I-type** instruction, which is used for operations involving an immediate value and a register.

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

```

Where:
- **Opcode**: `0010011` for the `ADDI` instruction.
- **rd**: Destination register (`a0`), which is `x10` in RISC-V. The binary representation for `x10` is `01010`.
- **funct3**: `000` for the `ADDI` instruction.
- **rs1**: Source register (`a0`), which is `x10`. Its binary representation is `01010`.
- **Immediate**: The 12-bit immediate value, which is `-736` (in 2's complement: `0xFFFFF4D0`).

## Assembling the Instruction

- **Opcode for `ADDI`**: `0010011`
- **Destination Register (`a0`)**: `x10` → `01010` in binary.
- **funct3**: `000` (specific to `ADDI`).
- **Source Register (`a0`)**: `x10` → `01010` in binary.
- **Immediate**: `-736` → `0xFFFFF4D0` (binary: `11111111111111111111010011010000`).

Thus, the full 32-bit binary encoding for `addi a0, a0, -736` is:
```
  0010011_01010_000_01010_111111111101 

```
### 4.
### Instruction:
```
sd ra,24(sp)

```

- **Operation**: `SD` (Store Doubleword)
  - Stores a 64-bit value (doubleword) from the source register (`ra`) to the memory address computed as `sp + 24`.
  
- **Source Register**: `ra` (return address, which is `x1` in RISC-V).
- **Destination Memory Address**: The value in `sp` (stack pointer) plus an immediate offset of `24`.
- **Immediate Value**: `24` (in decimal), which is `0x18` in hexadecimal.

### Instruction Type:
- **Type**: S-type
  - The `SD` instruction is an **S-type** instruction, used for store operations, where data is written to memory.

## Instruction Format

The format for an **S-type** instruction is as follows:
```
| opcode (7 bits) | imm[4:0] (5 bits) | funct3 (3 bits) | rs1 (5 bits) | rs2 (5 bits) | imm[11:5] (7 bits) |

```

Where:
- **Opcode**: `0100011` for the `SD` instruction.
- **funct3**: `011` for `SD` (Store Doubleword).
- **rs1**: Base register (`sp`), which is `x2` in RISC-V. The binary representation for `x2` is `00010`.
- **rs2**: Source register (`ra`), which is `x1`. The binary representation for `x1` is `00001`.
- **Immediate**: The immediate value, which is `24` (in decimal), represented in split 12-bit format for the S-type instruction:
  - `imm[11:5] = 0`
  - `imm[4:0] = 11000` (binary for `24`)

## Assembling the Instruction

- **Opcode for `SD`**: `0100011`
- **funct3**: `011` (specific to `SD`).
- **Base Register (`sp`)**: `x2` → `00010` in binary.
- **Source Register (`ra`)**: `x1` → `00001` in binary.
- **Immediate**: `24` → split into `imm[11:5] = 0` and `imm[4:0] = 11000`.

Thus, the full 32-bit binary encoding for `sd ra, 24(sp)` is:
```
  0100011_11000_011_00010_00001_0000000 

```
### 5.
### Instruction:
```
jal ra,10594 <puts>

```

- **Operation**: `JAL` (Jump and Link)
  - The `JAL` instruction jumps to the target address (in this case, the address of `<puts>`) and stores the return address (the address of the instruction following the jump) in the `ra` (return address) register.
  
- **Destination Register**: `ra` (which is register `x1` in RISC-V).
- **Immediate Value**: The immediate value is `10594` in decimal, which corresponds to the offset from the current instruction to the target address `<puts>`.

### Instruction Type:
- **Type**: J-type
  - The `JAL` instruction is a **J-type** instruction, which handles long-range jumps with a 20-bit signed immediate.

## Instruction Format

The format for a **J-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | imm[19:1] (20 bits) |

```

Where:
- **Opcode**: `1101111` for the `JAL` instruction.
- **rd**: Destination register (`ra`), which is `x1` in RISC-V. The binary representation for `x1` is `00001`.
- **Immediate**: The 20-bit immediate value, which represents the offset to the target address. For `10594`, we need to compute its binary representation and adjust it according to the J-type format.

### Immediate Calculation

1. **Immediate Value**: `10594` (in decimal).
   - Convert `10594` to binary: `10100111010010` (13 bits).
   - The J-type immediate format requires the immediate to be split as:
     - `imm[19:1]`: The 20-bit offset.
     - **imm[19]**: The most significant bit (sign bit) is `0` (positive offset).
     - **imm[10:1]**: Middle bits (from `10594` in binary).
     - **imm[11]**: The 11th bit (set for instruction format).
   - The immediate value `10594` would be encoded in the instruction as `00000000010100111010`.

## Assembling the Instruction

- **Opcode for `JAL`**: `1101111`
- **Destination Register (`ra`)**: `x1` → `00001` in binary.
- **Immediate**: The immediate value `10594` → split and encoded.

Thus, the full 32-bit binary encoding for `jal ra, 10594 <puts>` is:
```
 1101111_00001_00000000010100111010

```
### 6.
### Instruction:
```
lw a1,12(sp)

```

- **Operation**: `LW` (Load Word)
  - Loads a 32-bit word from memory at the address calculated by adding the immediate value `12` to the value in the `sp` (stack pointer) register, and stores it in the `a1` register.
  
- **Source Register**: `sp` (stack pointer, which is `x2` in RISC-V).
- **Destination Register**: `a1` (which is register `x11` in RISC-V).
- **Immediate Value**: `12` (in decimal), which is `0xC` in hexadecimal.

### Instruction Type:
- **Type**: I-type
  - The `LW` instruction is an **I-type** instruction, which is used for load operations involving an immediate value (used as an offset) and a register.

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

```

Where:
- **Opcode**: `0000011` for the `LW` instruction.
- **rd**: Destination register (`a1`), which is `x11` in RISC-V. The binary representation for `x11` is `01011`.
- **funct3**: `010` for `LW` (Load Word).
- **rs1**: Source register (`sp`), which is `x2`. Its binary representation is `00010`.
- **Immediate**: The 12-bit immediate value, which is `12` (in decimal), represented as `000000000011` in binary.

## Assembling the Instruction

- **Opcode for `LW`**: `0000011`
- **Destination Register (`a1`)**: `x11` → `01011` in binary.
- **funct3**: `010` (specific to `LW`).
- **Source Register (`sp`)**: `x2` → `00010` in binary.
- **Immediate**: `12` → `000000000011` (binary).

Thus, the full 32-bit binary encoding for `lw a1, 12(sp)` is:

```
 0000011_01011_010_00010_000000000011 
```
### 7.
### Instruction:
```
sext.w a1,a0

```

- **Operation**: `SEXT.W` (Sign Extension Word)
  - The `SEXT.W` instruction sign-extends the value in the `a0` register from a 32-bit word to a 64-bit value and stores the result in the `a1` register. It essentially copies the value from `a0` to `a1`, extending the sign of the 32-bit value to the full 64-bit value.
  
- **Source Register**: `a0` (which is register `x10` in RISC-V).
- **Destination Register**: `a1` (which is register `x11` in RISC-V).

### Instruction Type:
- **Type**: R-type
  - The `SEXT.W` instruction is an **R-type** instruction, which typically involves operations between two registers or between a register and an immediate value. In this case, it performs the operation between registers.

## Instruction Format

The format for an **R-type** instruction is as follows:

```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | rs2 (5 bits) | funct7 (7 bits) |

```

Where:
- **Opcode**: `0000011` for `SEXT.W` (Sign Extension).
- **funct3**: `001` for `SEXT.W`.
- **rs1**: Source register (`a0`), which is `x10`. Its binary representation is `01010`.
- **rs2**: Not used in `SEXT.W`, so it's set to `00000`.
- **funct7**: `0000000` (indicating it's a standard extension instruction).

## Assembling the Instruction

- **Opcode for `SEXT.W`**: `0000011`
- **Destination Register (`a1`)**: `x11` → `01011` in binary.
- **funct3**: `001` (specific to `SEXT.W`).
- **Source Register (`a0`)**: `x10` → `01010` in binary.
- **funct7**: `0000000` (standard extension).

Thus, the full 32-bit binary encoding for `sext.w a1, a0` is:

```
 0000011_01011_001_01010_00000_0000000

```
### 8.
### Instruction:
```
ld ra,24(sp) 

```

- **Operation**: `LD` (Load Doubleword)
  - Loads a 64-bit doubleword from memory at the address calculated by adding the immediate value `24` to the value in the `sp` (stack pointer) register, and stores it in the `ra` register.
  
- **Source Register**: `sp` (stack pointer, which is `x2` in RISC-V).
- **Destination Register**: `ra` (which is register `x1` in RISC-V).
- **Immediate Value**: `24` (in decimal), which is `0x18` in hexadecimal.

### Instruction Type:
- **Type**: I-type
  - The `LD` instruction is an **I-type** instruction, which is used for load operations involving an immediate value (used as an offset) and a register.

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) | 

```

Where:
- **Opcode**: `0000011` for the `LD` instruction.
- **rd**: Destination register (`ra`), which is `x1` in RISC-V. The binary representation for `x1` is `00001`.
- **funct3**: `011` for `LD` (Load Doubleword).
- **rs1**: Source register (`sp`), which is `x2`. Its binary representation is `00010`.
- **Immediate**: The 12-bit immediate value, which is `24` (in decimal), represented as `00000000011000` in binary.

## Assembling the Instruction

- **Opcode for `LD`**: `0000011`
- **Destination Register (`ra`)**: `x1` → `00001` in binary.
- **funct3**: `011` (specific to `LD`).
- **Source Register (`sp`)**: `x2` → `00010` in binary.
- **Immediate**: `24` → `00000000011000` (binary).

Thus, the full 32-bit binary encoding for `ld ra, 24(sp)` is:
```
 0000011_00001_011_00010_00000000011000 

```
### 9.
### Instruction:
```
li a0,0

```

- **Operation**: `LI` (Load Immediate)
  - The `LI` instruction loads the immediate value `0` into the `a0` register.
  
- **Destination Register**: `a0` (which is register `x10` in RISC-V).
- **Immediate Value**: `0` (in decimal).

### Instruction Type:
- **Type**: I-type
  - The `LI` instruction is often implemented using the `ADDI` instruction in RISC-V. In this case, `li a0, 0` is equivalent to `addi a0, x0, 0`. This means adding the immediate value `0` to the `x0` (zero register), which always contains `0`.

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

```

Where:
- **Opcode**: `0010011` for the `ADDI` instruction (since `li a0, 0` can be implemented using `addi`).
- **rd**: Destination register (`a0`), which is `x10` in RISC-V. The binary representation for `x10` is `01010`.
- **funct3**: `000` for `ADDI` (Add Immediate).
- **rs1**: Source register (`x0`), which is `x0` (the zero register). Its binary representation is `00000`.
- **Immediate**: The 12-bit immediate value, which is `0` (in decimal), represented as `000000000000` in binary.

## Assembling the Instruction

- **Opcode for `ADDI`**: `0010011`
- **Destination Register (`a0`)**: `x10` → `01010` in binary.
- **funct3**: `000` (specific to `ADDI`).
- **Source Register (`x0`)**: `x0` → `00000` in binary.
- **Immediate**: `0` → `000000000000` (binary).

Thus, the full 32-bit binary encoding for `li a0, 0` is:
```
 0010011_01010_000_00000_000000000000

```
### 10.
### Instruction:
```
 jal ra,105a4 <scanf>

```

- **Operation**: `JAL` (Jump and Link)
  - The `JAL` instruction jumps to the target address `<scanf>` (in this case, `105a4` in hexadecimal) and stores the return address (the address of the instruction following the jump) in the `ra` register.
  
- **Destination Register**: `ra` (which is register `x1` in RISC-V).
- **Immediate Value**: The immediate value is `105a4` (in hexadecimal), which represents the offset to the target address `<scanf>` from the current instruction.

### Instruction Type:
- **Type**: J-type
  - The `JAL` instruction is a **J-type** instruction, which is used for jumps with a 20-bit signed immediate.

## Instruction Format

The format for a **J-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | imm[19:1] (20 bits) |

```

Where:
- **Opcode**: `1101111` for the `JAL` instruction.
- **rd**: Destination register (`ra`), which is `x1` in RISC-V. The binary representation for `x1` is `00001`.
- **Immediate**: The 20-bit immediate value, which is the offset to the target address. The immediate value `105a4` (in hexadecimal) needs to be converted to binary and split according to the J-type format.

### Immediate Calculation

1. **Immediate Value**: `105a4` (in hexadecimal).
   - Convert `105a4` to decimal: `67748`.
   - Convert `67748` to binary: `1000010111010100` (17 bits).
   - The J-type instruction requires a 20-bit immediate. This value is split as follows:
     - `imm[19:1]`: `000010111010100` (most significant 19 bits).
     - `imm[11:0]`: `1010100` (least significant bits), which is placed as part of the instruction.

## Assembling the Instruction

- **Opcode for `JAL`**: `1101111`
- **Destination Register (`ra`)**: `x1` → `00001` in binary.
- **Immediate**: `105a4` in hexadecimal → binary representation is split for the J-type format:
  - `imm[19:1]` → `000010111010100`
  - `imm[11:0]` → `1010100`

Thus, the full 32-bit binary encoding for `jal ra, 105a4 <scanf>` is:
```
1101111_00001_000010111010100_1010100

```
### 11.
### Instruction:
```
jal ra,10470 <printf>

```

- **Operation**: `JAL` (Jump and Link)
  - The `JAL` instruction jumps to the target address `<printf>` (in this case, `10470` in hexadecimal) and stores the return address (the address of the instruction following the jump) in the `ra` register.
  
- **Destination Register**: `ra` (which is register `x1` in RISC-V).
- **Immediate Value**: The immediate value is `10470` (in hexadecimal), which represents the offset to the target address `<printf>` from the current instruction.

### Instruction Type:
- **Type**: J-type
  - The `JAL` instruction is a **J-type** instruction, which is used for jumps with a 20-bit signed immediate.

## Instruction Format

The format for a **J-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | imm[19:1] (20 bits) |

```

Where:
- **Opcode**: `1101111` for the `JAL` instruction.
- **rd**: Destination register (`ra`), which is `x1` in RISC-V. The binary representation for `x1` is `00001`.
- **Immediate**: The 20-bit immediate value, which is the offset to the target address. The immediate value `10470` (in hexadecimal) needs to be converted to binary and split according to the J-type format.

### Immediate Calculation

1. **Immediate Value**: `10470` (in hexadecimal).
   - Convert `10470` to decimal: `41744`.
   - Convert `41744` to binary: `1010000011101000` (17 bits).
   - The J-type instruction requires a 20-bit immediate. This value is split as follows:
     - `imm[19:1]`: `0000101000011101` (most significant 19 bits).
     - `imm[11:0]`: `00001000` (least significant bits), which is placed as part of the instruction.

## Assembling the Instruction

- **Opcode for `JAL`**: `1101111`
- **Destination Register (`ra`)**: `x1` → `00001` in binary.
- **Immediate**: `10470` in hexadecimal → binary representation is split for the J-type format:
  - `imm[19:1]` → `0000101000011101`
  - `imm[11:0]` → `00001000`

Thus, the full 32-bit binary encoding for `jal ra, 10470 <printf>` is:
```
1101111_00001_0000101000011101_00001000

```
### 12.
### Instruction:
```
jal ra,101f4 <__muldi3>

```

- **Operation**: `JAL` (Jump and Link)
  - The `JAL` instruction jumps to the target address `<__muldi3>` (in this case, `101f4` in hexadecimal) and stores the return address (the address of the instruction following the jump) in the `ra` register.
  
- **Destination Register**: `ra` (which is register `x1` in RISC-V).
- **Immediate Value**: The immediate value is `101f4` (in hexadecimal), which represents the offset to the target address `<__muldi3>` from the current instruction.

### Instruction Type:
- **Type**: J-type
  - The `JAL` instruction is a **J-type** instruction, which is used for jumps with a 20-bit signed immediate.

## Instruction Format

The format for a **J-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | imm[19:1] (20 bits) |

```

Where:
- **Opcode**: `1101111` for the `JAL` instruction.
- **rd**: Destination register (`ra`), which is `x1` in RISC-V. The binary representation for `x1` is `00001`.
- **Immediate**: The 20-bit immediate value, which is the offset to the target address. The immediate value `101f4` (in hexadecimal) needs to be converted to binary and split according to the J-type format.

### Immediate Calculation

1. **Immediate Value**: `101f4` (in hexadecimal).
   - Convert `101f4` to decimal: `66004`.
   - Convert `66004` to binary: `1000000111110100` (17 bits).
   - The J-type instruction requires a 20-bit immediate. This value is split as follows:
     - `imm[19:1]`: `0000100001111101` (most significant 19 bits).
     - `imm[11:0]`: `1111100` (least significant bits), which is placed as part of the instruction.

## Assembling the Instruction

- **Opcode for `JAL`**: `1101111`
- **Destination Register (`ra`)**: `x1` → `00001` in binary.
- **Immediate**: `101f4` in hexadecimal → binary representation is split for the J-type format:
  - `imm[19:1]` → `0000100001111101`
  - `imm[11:0]` → `1111100`

Thus, the full 32-bit binary encoding for `jal ra, 101f4 <__muldi3>` is:
```
1101111_00001_0000100001111101_1111100

```
### 13.
### Instruction:
```
addi a0,a0,-680 # 2ad58 <__clzdi2+0x78>

```

- **Operation**: `ADDI` (Add Immediate)
  - The `ADDI` instruction adds the immediate value `-680` to the value in the `a0` register and stores the result back in the `a0` register.
  
- **Source Register**: `a0` (which is register `x10` in RISC-V).
- **Destination Register**: `a0` (which is also register `x10` in RISC-V).
- **Immediate Value**: `-680` (in decimal), which is represented as `0xFFFFF9F8` in two's complement (32-bit signed).

### Instruction Type:
- **Type**: I-type
  - The `ADDI` instruction is an **I-type** instruction, which involves an immediate value and a register.

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

```

Where:
- **Opcode**: `0010011` for the `ADDI` instruction.
- **rd**: Destination register (`a0`), which is `x10` in RISC-V. The binary representation for `x10` is `01010`.
- **funct3**: `000` for `ADDI` (Add Immediate).
- **rs1**: Source register (`a0`), which is `x10` in RISC-V. Its binary representation is `01010`.
- **Immediate**: The 12-bit immediate value, which is `-680` (in decimal), represented as `0xFFFFF9F8` in two's complement, which is `1111111111111000` in binary.

### Immediate Calculation

- **Immediate Value**: `-680` (in decimal).
  - Convert `-680` to binary using two's complement (32-bit signed): `1111111111111000` (binary representation of `-680`).
  
## Assembling the Instruction

- **Opcode for `ADDI`**: `0010011`
- **Destination Register (`a0`)**: `x10` → `01010` in binary.
- **funct3**: `000` (specific to `ADDI`).
- **Source Register (`a0`)**: `x10` → `01010` in binary.
- **Immediate**: `-680` → `1111111111111000` (binary).

Thus, the full 32-bit binary encoding for `addi a0, a0, -680` is:
```
0010011_01010_01010_000_1111111111111000

```
### 14.
### Instruction:
```
addi a0,s0,-712

```

- **Operation**: `ADDI` (Add Immediate)
  - The `ADDI` instruction adds the immediate value `-712` to the value in the `s0` register and stores the result back in the `a0` register.
  
- **Source Register**: `s0` (which is register `x8` in RISC-V).
- **Destination Register**: `a0` (which is register `x10` in RISC-V).
- **Immediate Value**: `-712` (in decimal), which is represented as `0xFFFFF3D8` in two's complement (32-bit signed).

### Instruction Type:
- **Type**: I-type
  - The `ADDI` instruction is an **I-type** instruction, which involves an immediate value and a register.

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

```

Where:
- **Opcode**: `0010011` for the `ADDI` instruction.
- **rd**: Destination register (`a0`), which is `x10` in RISC-V. The binary representation for `x10` is `01010`.
- **funct3**: `000` for `ADDI` (Add Immediate).
- **rs1**: Source register (`s0`), which is `x8` in RISC-V. Its binary representation is `01000`.
- **Immediate**: The 12-bit immediate value, which is `-712` (in decimal), represented as `0xFFFFF3D8` in two's complement, which is `1111111111111000` (binary).

### Immediate Calculation

- **Immediate Value**: `-712` (in decimal).
  - Convert `-712` to binary using two's complement (32-bit signed): `1111111111111000` (binary representation of `-712`).
  
## Assembling the Instruction

- **Opcode for `ADDI`**: `0010011`
- **Destination Register (`a0`)**: `x10` → `01010` in binary.
- **funct3**: `000` (specific to `ADDI`).
- **Source Register (`s0`)**: `x8` → `01000` in binary.
- **Immediate**: `-712` → `1111111111111000` (binary).

Thus, the full 32-bit binary encoding for `addi a0, s0, -712` is:
```
0010011_01010_01000_000_1111111111111000

```
### 15.
### Instruction:
```
ld a0,16(sp)

```

- **Operation**: `LD` (Load Doubleword)
  - The `LD` instruction loads a 64-bit doubleword from memory at the address `16(sp)` and stores it in the `a0` register.
  
- **Source Register**: `sp` (which is register `x2` in RISC-V).
- **Destination Register**: `a0` (which is register `x10` in RISC-V).
- **Immediate Value**: `16` (in decimal), which is the offset from the stack pointer `sp`.

### Instruction Type:
- **Type**: I-type
  - The `LD` instruction is an **I-type** instruction, which involves a register (`sp` in this case) and an immediate value (the offset to load from memory).

## Instruction Format

The format for an **I-type** instruction is as follows:
```
| opcode (7 bits) | rd (5 bits) | funct3 (3 bits) | rs1 (5 bits) | imm (12 bits) |

```

Where:
- **Opcode**: `0000011` for the `LD` instruction.
- **rd**: Destination register (`a0`), which is `x10` in RISC-V. The binary representation for `x10` is `01010`.
- **funct3**: `011` for `LD` (Load Doubleword).
- **rs1**: Source register (`sp`), which is `x2` in RISC-V. Its binary representation is `00010`.
- **Immediate**: The 12-bit immediate value, which is `16` (in decimal), represented as `000000001000` in binary.

### Immediate Calculation

- **Immediate Value**: `16` (in decimal).
  - Convert `16` to binary: `000000001000`.

## Assembling the Instruction

- **Opcode for `LD`**: `0000011`
- **Destination Register (`a0`)**: `x10` → `01010` in binary.
- **funct3**: `011` (specific to `LD`).
- **Source Register (`sp`)**: `x2` → `00010` in binary.
- **Immediate**: `16` → `000000001000` (binary).

Thus, the full 32-bit binary encoding for `ld a0, 16(sp)` is:
```
0000011 01010 00010 011 000000001000
```
