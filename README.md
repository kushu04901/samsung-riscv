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
![image alt]()


### Instruction:
```
1.lui a0, 0x2b
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
| 0110111 | 01010 | 00000000001010110000 |

```
