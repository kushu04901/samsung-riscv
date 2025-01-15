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

<details>
<summary> Task-2: Screenshot of RISC-V object dump optimisation of Area of Rectagle programme </summary>
<br>
The below is the screenshot of the O1 object dump optimisation.

![image alt](https://github.com/kushu04901/samsung-riscv/blob/9cdd6a910b2a5129cb46ab21152f78be1f8232f4/task2/spike1.png)
