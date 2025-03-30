<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#comments'>Comments</a>
  </li>
  <li>
    <a href='#registers'>Registers</a>
  </li>
  <li>
    <a href='#r-type-instructions'>R-type Instructions</a>
  </li>
  <li>
    <a href='#i-type-instructions'>I-type Instructions</a>
  </li>
  <li>
    <a href='#s-type-instructions'>S-type Instructions</a>
  </li>
</ol>
</details>

## Comments
RISC-V assembly programs may contain a single line or multi-line comments
<ul>
  <li>The pound character, #, is used for single line comments</li>
</ul>  

## Registers
RISC-V has a 32 x 32-bit register file which are used frequently to access data

The 32 general purpose registers range from x0 to x31

x0: the constant value 0
x1: return address
x2: stack pointer
x3: global pointer
x4: thread pointer
x5 - x7, x28 - x31: temporaries
x8: saved register/frame pointer
x9, x18 - x27: saved registers
x10 - x11: function arguments/results
x12 - x17: function arguments

## R-Type Instructions
### R-type Instructions: Arithmetic
The typical arithmetic operations include addition (ADD), subtraction (SUB), and comparisons (set less than SLT and set les than unsigned SLTU)

#### ADD
Format: add rd, rs1, rs2<br />
Description: adds the registers rs1 and rs2 and stores the result in rd. Arithmetic overflow is ignored<br />
Implementation: x[rd] = x[rs1] + x[rs2]

#### SUB
Format: sub rd, rs1, rs2<br />
Description: subtracts the registers rs2 from rs1 and stores the result in rd. Arithmetic overflow is ignored<br />
Implementation: x[rd] = x[rs1] - x[rs2]<br />

#### SLT
Format: slt rd, rs1, rs2<br />
Description: place the value 1 in register rd if rs1 is less than register rs2 when both are treated as signed 2's complement; otherwise, 0 is written to rd<br />
x[rd] = x[rs1] &lt;s x[rs2]<br />

#### SLTU
Format: sltu rd, rs1, rs2<br />
Description: place the value 1 in register rd if register rs1 is less than register rs2 when both are treated as unsigned numbers; otherwise, 0 is written to rd<br />
x[rd] = x[rs1] &lt;u x[rs2]<br />

<details>
    <summary>Example problem</summary>

Assume t0 and t1 store 0x00000015 and 0xFFFFFFF9

<ol type="a">
  <li>ADD      t2, t0, t1</li>
  <li>SUB      t3, t0, t1</li>
  <li>SLT      t4, t0, t1</li>
  <li>SLTU     t5, t0, t1</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
<pre>
 11111 11
  0000 0015
+ FFFF FFF9
-----------
  0000 000E = 0x0E
</pre>
  </li>
  <li>
<pre>
-FFFF FFF9 = 0000 0007<br />
  0000 0015
+ 0000 0007
-----------
  0000 001C
</pre>
  </li>
  <li>0x0</li>
  <li>0x1</li>  
</ol>
</details>
</ul>  
</details>

### Pseudo Instructions
Pseudo-instructions help improve code clarity and make writing assembly code faster, but are not directly executable by the processor; the assembler will convert them into one or more real instructions when assembling the programs

Some examples of pseudo-instructions are: li and mv

### R-type Instructions: Logical
#### AND
Format: and rd, rs1, rs2<br />
Description: performs bitwise AND on registers rs1 and rs2 and places the result in rd<br />
Implementation: x[rd] = x[rs1] & x[rs2]<br />

#### OR
Format: or rd, rs1, rs2<br />
Description: performs bitwise OR on registers rs1 and rs2 and places the result in rd. Not compatible with negative numbers<br />
Implementation: x[rd] = x[rs1] | x[rs2]<br />

#### XOR
Format: xor rd, rs1, rs2<br />
Description: performs bitwise XOR on registers rs1 and rs2 and places the result in rd<br />
Implementation: x[rd] = x[rs1] $\oplus$ x[rs2]<br />

<details>
    <summary>Example problem</summary>

Assume t0 and t1 store 0x00000015 and 0xFFFFFFF9

<ol type="a">
  <li>AND      t2, t0, t1</li>
  <li>OR       t3, t0, t1</li>
  <li>XOR      t4, t0, t1</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
<pre>
0000 0015 =<br />
0000 ... 0001 0101<br />
FFFF FFF9 =<br />
1111 ... 1111 1001<br />
AND on last two hex digits: 0001 0001
AND on first six hex digits: 0000 00
Converted back to hex, AND = 0x00000011
</pre>
  </li>
  <li>
<pre>
0000 0015 =<br />
0000 ... 0001 0101<br />
FFFF FFF9 =<br />
1111 ... 1111 1001<br />
OR on last two hex digits: 1111 1101
OR on first six hex digits: 1111 11
Converted back to hex, AND = 0x111111FD
</pre>
  </li>
  <li>
<pre>
0000 0015 =<br />
0000 ... 0001 0101<br />
FFFF FFF9 =<br />
1111 ... 1111 1001<br />
OR on last two hex digits: 1110 1100
OR on first six hex digits: 1111 11
Converted back to hex, AND = 0x111111EC
</pre>
  </li>
</ol>
</details>
</ul>  
</details>

### R-type Instructions: Shifting
#### SLL
Format: sll rd, rs1, rs2<br />
Description: inserts 0 to the least significant bit and shifts out the most significant bit on the value in register rs1 by the shift amount in register rs2<br />
Implementation: x[rd] = x[rs1] << x[rs2]<br />

#### SRL
Format: srl rd, rs1, rs2<br />
Description: insets 0 to the most significant bit and shifts our the least significant bit on the value in register rs1 by the shift amount in register rs2<br />
Implementation: x[rd] = x[rs1] >>u x[rs2]<br />

#### SRA
Format: sra rd, rs1, rs2<br />
Description: inserts sign bit to the most significant bit and shifts out the least significant bit p on the value in register rs1 by the shift amount in register rs2<br />
Implementation: x[rd] = x[rs1] >>s x[rs2]<br />

<details>
    <summary>Example problem</summary>

Assume t0, t1, and t2 store 0x15, 0x3, and 0xFFFFFF15

<ol type="a">
  <li>SLL      t3, t0, t1</li>
  <li>SRL      t4, t0, t1</li>
  <li>SRA      t5, t0, t1</li>
  <li>SRA      t6, t2, t1</li>  
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
<pre>
0x15 = 0000 ... 0001 0101
0x15 shifted by 0x3: 0000 ... 1010 1000
t3 = 0x000000A8
</pre>
  </li>
  <li>
<pre>
0x15 = 0000 ... 0001 0101
0x15 shifted by 0x3: 0000 ... 0000 0010
t4 = 0x00000002
</pre>
  </li>
  <li>
<pre>
0x15 = 0000 ... 0001 0101
0x15 shifted by 0x3: 0000 ... 0000 0010
t5 = 0x00000002
</pre>
  </li>
  <li>
<pre>
0xFFFFFF15 = 1111 ... 0001 0101
0xFFFFFF15 shifted by 0x3: 1111 ... 1110 0010
t6 = 0xFFFFFFE2
</pre>
  </li>
</ol>
</details>
</ul>  
</details>

## I-type Instructions
An I-type instruction contains a 12-bit constant Imm

### ALU Arithmetic and Logic
Use rs1 as the first data operand and Imm as the second data operand<br />
The ALU performs arithmetical, logical or shifting operations on rs1 and Imm<br />
The ALU output is stored to rd

#### ADDI
Format: addi rd, rs1, Imm<br />
Description: adds the sign-extended 12-bit immediate to register rs1. Arithmetic overflow is ignored<br />
Implementation: x[rd] = x[rs1] + sign_ext(Imm)

#### ANDI
Format: andi rd, rs1, Imm<br />
Description: performs bitwise AND on register rs1 and the sign-extended 12-bit immediate and place the result in rd<br />
Implementation: x[rd] = x[rs1] & sign_ext(Imm)

#### ORI
Format: ori rd, rs1, Imm<br />
Description: performs bitwise OR on register rs1 and the sign-extended 12-bit immediate and place the result in rd. Not compatible with negative numbers<br />
Implementation: x[rd] = x[rs1] | sign_ext(Imm)

#### XORI
Format: xori rd, rs1, Imm<br />
Description: performs bitwise XOR on register rs1 and the sign-extended 12-bit immediate and place the result in rd<br />
Implementation: x[rd] = x[rs1] ^ sign_ext(Imm)

#### SLTI
Format: slti rd, rs1, Imm<br />
Description: place the value 1 in register rd if register rs1 is less than the sign-extended immediate when both are treated as signed numbers; otherwise, 0 is written to rd<br />
Implementation: x[rd] = x[rsi] &lt;s sign-ext(Imm)

#### SLTIU
Format: sltiu rd, rs1, shift_amount<br />
Description: place the value 1 in register rd if register rs1 is less than the immediate when both are treated as unsigned numbers; otherwise, 0 is written to rd<br />
Implementation: x[rd] = x[rs1] &lt;u sign-ext(Imm)

#### SLLI
Format: slli rd, rs1, shift_amount<br />
Description: inserts 0 to the least significant bit and shifts out the most significant bit on the value in register rs1 by the shift amount in the immediate<br />
Implementation: x[rd] = x[rs1] << shift_amount

#### SRLI
Format: srli rd, rs1, shift_amount<br />
Description: inserts 0 to the most significant bit and shifts our the least significant bit on the value in register rs1 by the shift amount in the immediate<br />
Implementation: x[rd] = x[rs1] >>u shift_amount

#### SRAI
Format: sra rd, rs1, shift_amount<br />
Description: inserts sign bit to the most significant bit and shifts out the least significant bit on the value in register rs1 by the shift amount in the immediate<br />
Implementation: x[rd] = x[rs1] >>s shift_amount

#### LI
Format: li rd, Imm<br />
Description: loads an immediate (constant) value into a register. The number must be 12-bits or between -2048 to 2047<br />
Implementation: x[rd] = Imm

#### LUI
Format: lui rd, Imm<br />
Description: loads a value that gets shifted by 12 bits to the left. In other words, the number is multiplied by 4096. Lui does handle the sign because it sign-extends the 20-bit immediate when storing it in the register<br />
Implementation: x[rd] = Imm

<details>
    <summary>Example problem</summary>

Select all of the following RISC-V assembly code snippets that correctly initialize t0 to $DDCB9A82$<sub>16</sub> without using pseudo instructions
<ol type="a">
  <li>lui t1, 0xDDCB9<br />
ori t1, t1, 0xA82</li>
  <li>lui t1, 0xDDCBA<br />
addi t1, t1, 0xA82</li>
  <li>lui t1, 0xDDCBA<br />
ori t1, t1, 0xA82</li>
  <li>lui t1, 0xDDCB9<br />
addi t1, t1, 0xA82</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
t1 = 0xDDCB9000
0xDDCB9000 ADDI 0xFFFFFA82
 
  1111 
  DDCBA000
+ FFFFFA82 
----------
  DDCB9A82

So the required steps are: lui t1, 0xDDCBA and addi t1, t1, 0xA82
</pre>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Which of the following RISC-V instructions correctly computes t1 = t0 % 256 for non-negative values of t0
<ol type="a">
  <li>xori t1, t0, 256</li>
  <li>andi t1, t 256</li>
  <li>slli t1, t0, 8<br />
  srli t1, t1, 8</li>
  <li>andi t1, t0, 255</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

Assume t0 = 1 and t1 = 1<br />
t1 = t0 % 256<br />
t1 = 1 % 256 = 1<br />
<ol type="a">
  <li>
  <pre>
  t0 = 0000 0001
  255 = 1111 1111

  0000 0001 XOR 1111 1111 = 1111 1110 = 254

  Incorrect
  </pre>
  </li>
  <li>
  <pre>
  t0 = 0 0000 0001
  256 = 1 0000 0000

  0 0000 0001 XOR 1 0000 0000 is 1 0000 0001

  Incorrect
  </pre>
  </li>
  <li>
  <pre>
  slli t1, t0, 8
  t1 is equal to t0 shifted 8 bits to the left
  t0 = 0000 ... 0001 which shifted 8 bits to the left is: 0000 ... 0001 0000 0000

  srli t1, t1, 8
  t1 is equal to t1 shifted 8 bits to the right
  t1 = 0001 0000 0000 which shifted 8 bits to the right is: 0000 ... 0001

  Correct for these values of t1 and t0

  Now, if t0 = 3 and t1 = 3

  slli t1, t0, 8
  t1 is equal to t0 shifted 8 bits to the left
  t0 = 0000 ... 0011 which shifted 8 bits to the left is: 0000 ... 0011 0000 0000

  srli t1, t1, 8
  t1 is equal to t1 shifted 8 bits to the right
  t1 = 0000 ... 0011 which shifted 8 bits to the right is: 0000 ... 0000

  Incorrect

  </pre>
  </li>
  <li>
  <pre>
  andi t1, t0, 255
  t0 = 0000 0001
  255 = 1111 1111

  0000 0001 AND 1111 1111 is 0000 0001

  Correct
  </pre>
  </li>
</ol>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Select all of the following RISC-V assembly code snippets correctly initializes t1 to (A123C5BD)<sub>16</sub> without using pseudo-instructions?
<ol type="a">
  <li>lui t1, 0xA123C<br />addi t1, t1, 0x5BD</li>
  <li>lui t1, 0xA123D<br />ori t1, t1, 0x5BD</li>
  <li>lui t1, 0xA123C<br />ori t1, t1, 0x5BD</li>
  <li>lui t1, 0xA123D<br />addi t1, t1, 0x5BD</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
  <pre>
t1 = 0xA123C000
t1 = 0xA123C000 + 0x000005BD = 0xA123C5BD

Correct
  </pre>
  </li>
  <li>
  <pre>
t1 = 0xA123D000
t1 = 0xA123D000 OR 0x000005BD = 0xA123D5BD

Incorrect
  </pre>
  </li>
  <li>
  <pre>
t1 = 0xA123C000
t1 = 0xA123C000 OR 0x000005BD = 0xA123C5BD

Correct
  </pre>
  </li>
  <li>
  <pre>
t1 = 0xA123D000
t1 = 0xA123D000 + 0x000005BD = 0xA123D5BD

Incorrect
  </pre>
  </li>
</ol>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Which of the following RISC-V assembly code snippet correctly implements t1 = t0 * 10.25 without using multiplication and division instructions
<ol type="a">
  <li>slli t1, t0, 3<br />
slli t2, t0, 1<br />
srli t3, t0, 2<br />
add t1, t1, t2<br />
add t1, t1, t3</li>
  <li>slli t1, t0, 3<br />
slli t2, t0, 1<br />
srli t3, t0, 2<br />
sub t1, t1, t2<br />
add t1, t1, t3</li>
  <li> slli t1, t0, 2 <br />
slli t2, t0, 1<br />
srli t3, t0, 2<br />
add t1, t1, t2<br />
sub t1, t1, t3</li>
  <li>slli t1, t0, 4 <br />
slli t2, t0, 2<br />
srli t3, t0, 2<br />
add t1, t1, t2<br />
add t1, t1, t3</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

Assume t0 = 1 and t1 = 2
<ol type="a">
  <li>
  <pre>
slli t1, t0, 3
t0 = 1 = 0000 ... 0001
This shifted by 3 to the left is: t0 = 0000 ... 1000
t1 = 8<br />

slli t2, t0, 1
t0 = 1 = 0000 ... 0001
This shifted by 1 to the left is: t0 = 0000 ... 0010
t2 = 2<br />

srli t3, t0, 2
t0 = 1 = 0000 ... 0001
This shifted by 2 to the right is: t0 = 0000 ... 0000
t3 = 0<br />

add t1, t1, t2
t1 = 8 + 2 = 10
t1 = 10<br />

add t1, t1, t3
t1 = 10 + 0 = 10
t1 = 10

Correct as 10.25 truncated is 10
  </pre>
  </li>
  <li>
  <pre>
slli t1, t0, 3
t0 = 1 = 0000 ... 0001
This shifted by 3 to the left is: t0 = 0000 ... 1000
t1 = 8<br />  

slli t2, t0, 1
t0 = 1 = 0000 ... 0001
This shifted by 1 to the left is: t0 = 0000 ... 0010
t2 = 2<br />

srli t3, t0, 2
t0 = 1 = 0000 ... 0001
This shifted by 2 to the right is: t0 = 0000 ... 0000
t3 = 0<br />

sub t1, t1, t2
t1 = t2 - t1 = 2 - 8 = -6
t1 = -6<br />

add t1, t1, t3
t1 = t1 + t3 = -6 + 0 = -6
t1 = -6

Incorrect as -6 does not equal 10
  </pre>
  </li>
  <li>
  <pre>
slli t1, t0, 2
t0 = 1 = 0000 ... 0001
This shifted by 2 to the left is: t0 = 0000 ... 0100
t1 = 4<br />  

slli t2, t0, 1
t0 = 1 = 0000 ... 0001
This shifted by 1 to the left is: t0 = 0000 ... 0010
t2 = 2<br />

srli t3, t0, 2
t0 = 1 = 0000 ... 0001
This shifted by 2 to the right is: t0 = 0000 ... 0000
t3 = 0<br />

add t1, t1, t2
t1 = t1 + t2 = 4 + 2 = 6
t1 = 6<br />

sub t1, t1, t3
t1 = t3 - t1 = 0 - 6 = -6
t1 = -6

Incorrect as -6 does not equal 10
  </pre>
  </li>
  <li>
  <pre>
slli t1, t0. 4
t1 = 1 = 0000 ... 0001
This shifted by 4 to the left is: t0 = 0000 ... 0001 0000
t1 = 16<br />

slli t2, t0, 2
t0 = 1 = 0000 ... 0001
This shifted by 2 to the left is: t0 = 0000 ... 0010
t2 = 2<br />

srli t3, t0, 2
t0 = 1 = 0000 ... 0001
This shifted by 2 to the right is: t0 = 0000 ... 0000
t3 = 0<br />

add t1, t1, t2
t1 = t1 + t2 = 16 + 2 = 18
t1 = 18<br />

add t1, t1, t3
t1 = t1 + t3 = 18 + 0 = 18
t1 = 18

Incorrect as 18 does not equal 10
  </pre>
  </li>  
</ol>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Which of the following RISC-V assembly code snippet correctly implements t1 = 0 without using multiplication and division instructions
<ol type="a">
  <li>xor t1, t1, t1</li>
  <li>mv t1, x0</li>
  <li>addi t1, zero, 0</li>
  <li>sub t1, t1, t1</li>
  <li>addi, t1, x0, 0</li>
  <li>addi t1, x0, x0</li>
  <li>add t1, zero, zero</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

The answers are: A, C, D, E, F, G
</details>
</ul>  
</details>

#### MV
Format: mv rd, rs1<br />
Description: moves data from one register to another. It is essentially a shorthand for the addi instruction with an immediate value of 0<br />
Implementation: x[rd] = x[rs1]

<details>
    <summary>Example problem</summary>

Select all of the following RISC-V assembly instructions that correctly initialize t<sub>1</sub> to 25 without using pseudo-instructions?
<ol type="a">
  <li>addi t1, x0, 25</li>
  <li>ori t1, x0, 25</li>
  <li>li t1, 25</li>
  <li>lui t1, 25</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

The answers a and b
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Which of the following RISC-V instructions correctly computes t1 = t0 % 256 for non-negative values of t0?
<ol type="a">
  <li>addi t1, x0, 256</li>
  <li>xori t1, x0, 256</li>
  <li>slli t1, t0, 8<br />srli t1, t1, 8</li>
  <li>andi t1, t0, 255</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

The correct answer is d
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Assume registers t<sub>0</sub> and t<sub>1</sub> store the hexadecimal values 0xE6ABC9D5 and 0xF27831BD, respectively. What is the hexadecimal value stored in register 5<sub>2</sub> after executing the following RISC-V assembly code snippets?<br />
XOR t2, t0, t1<br />         
XORI t2, t2, -1
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
t0 = 1110 0110 1010 1011 1100 1001 1101 0101
t1 = 1111 0010 0111 1000 0011 0001 1011 1101
t2 = 0001 0100 1101 0011 1111 1000 0110 1000
t2 = 0x14D3F868

t2 = t2 XOR 0xFFFFFFFF
t2 = 0001 0100 1101 0011 1111 1000 0110 1000
0xF= 1111 1111 1111 1111 1111 1111 1111 1111
t2 = 1110 1011 0010 1100 0000 0111 1001 0111
t2 = 0xEB2C0797
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Select all of the following RISC-V assembly code snippets that correctly implement t2 = t0 NAND t1
<ol type="a">
  <li>nand t2, t0, t1</li>
  <li>and t2, t0, t1<br />xori t2, t2, -1</li>
  <li>and t2, t0, t1<br />ori t2, t2, -1</li>
  <li>and t2, t0, t1<br />addi t3, x0, -1<br />xor t2, t2, t3</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

The correct answers are b and d
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Which of the following RISC-V instructions correctly computes t1 = t0 % 16 for non-negative values of t0?
<ol type="a">
  <li>andi t1, t0, 15</li>
  <li>andi t1, t0, 16</li>
  <li>srai t1, t0, 4<br />slli t1, t1, 4</li>
  <li>slli t1, t0, 4<br />srli t1, t1, 4</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

The correct answer is a
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Select all of the following RISC-V assembly code snippets correctly implements t2 = t0 NOR t1 without using pseudo-instructions?
<ol type="a">
  <li>nor t2, t0, t1</li>
  <li>or t2, t0, t1<br />xori t2, t2, -1</li>
  <li>or t2, t0, t1<br />li t3, -1<br />xor t2, t2, t3</li>
  <li>or t2, t0, t1<br />addi t3, x0, -1<br />xor t2, t2, t3</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

The correct answer is b and d
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Which of the following RISC-V assembly instruction correctly initializes t1 to -59 without using pseudo-instructions?
<ol type="a">
  <li>lui t1, -59</li>
  <li>li t1, -59</li>
  <li>addi t1, x0, -59</li>
  <li>ori t1, x0, -59</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

The correct answer is c
</details>
</ul>  
</details>

### Memory Read
Note that RISC-V is a little-endian system, meaning that the least significant byte of a multi-byte data type is stored first at the smallest memory address, followed by the more significant bytes in order
#### LB
Format: lb rd, Imm(rs1)<br />
Description: loads an 8-bit value from memory and sign-extends this before storing it in register rd<br />
Implementation: x[rd] = sign_ext(x[rs1])

#### LH
Format: lh rd, Imm(rs1)<br />
Description: loads two bytes, a 16-bit value from memory and sign-extends this before storing it in register rd<br />
Implementation: x[rd] = sign_ext(x[rs1])

#### LW
Format: lw rd, Imm(rs1)<br />
Description: loads a 32-bit value from memory and sign-extends this before storing it in register rd<br />
Implementation: x[rd] = sign_ext(x[rs1])

#### LBU
Format: lbu rd, Imm(rs1)<br />
Description: loads an 8-bit value from memory and zero-extends this before storing it in register rd<br />
Implementation: x[rd] = zero_ext(x[rs1])

#### LHU
Format: lhu rd, Imm(rs1)<br />
Description: loads a 16-bit value from memory and zero-extends this before storing it in register rd<br />
Implementation: x[rd] = zero_ext(x[rs1])

<details>
    <summary>Example problem</summary>

Assume register t0 has the value of 0x100100C1 and the memory status is shown below<br />
Address $\quad \quad \quad$ Data<br />
0x100100C0 $\quad$ 0x36<br />
0x100100C1 $\quad$ 0x7B<br />
0x100100C2 $\quad$ 0x9D<br />
0x100100C3 $\quad$ 0xA5<br />

<ol type="a">
  <li>Write out the 32-bit hex values in t1 after the following instruction is executed: LBU t1, 0(t0)</li>
  <li>Write out the 32-bit hex values in t2 after the following instruction is executed: LH t2, 1(t0)</li>
  <li>Write out the 32-bit hex values in t2 after the following instruction is executed: LW t3, -1(t0)</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
  <pre>
The memory address is 0(t0) which is t0 + 0 = 0x100100C1
The data at this address is 0x7B which in binary is 0111 1010
Since we are loading 32 bits unsigned, we load 0 for the sign bit and the answer is 0x0000007B
  </pre>
  </li>
  <li>
  <pre>
The memory address is 1(t0) which is t0 + 1 = 0x100100C2
Now, since we are loading two bytes of data and since RISC-V is little-endian, the memory addresses are 0x100100C2 and 0x100100C3
Since we are loading 32 bits signed, we must determine the sign bit
A59D = 1010 0101 1001 1101 and the sign bit is 1 which means the data is negative
0xFFFFA59D
  </pre>
  </li>
  <li>
  <pre>
The memory address is -1(t0) which is t0 - 1 = 0x100100C0
Now, since we are loading four bytes of data and since RISC-V is little-endian, the memory addresses are 0x100100C0 - 0x100100C3
No sign-extension is needed because there are 32 bits of data stored in memory
0xA59D7B36
  </pre>
  </li>
</ol>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Which of the following sequences correctly implements reading Fibonacci values from memory before computing F[i] = F[i-1] + F[i-2]? Assume the address of F[i] is stored in register t0

<ol type="a">
  <li>lw t1, 0(t0)<br />lw t2, 4(t0)<br />add t3, t1, t2</li>
  <li>lw t1, 4(t0)<br />lw t2, 8(t0)<br />sub t3, t1, t2</li>
  <li>sw t1, 0(t0)<br />sw t1, 4(t0)<br />lw t3, 8(t0)</li>
  <li>lw t1, -4(t0)<br />lw t2, -8(t0)<br />add t3, t1, t2</li>
</ol>             
<ul>  
  <details>
    <summary>Solution</summary>

The correct answer is d
</details>
</ul>  
</details>

## S-type Instructions
#### SB
Format: sb rs2, Imm(rs1)<br />
Description: store 8-bit, values from the low bits of register rs2 to memory<br />
Implementation: x[rs2] [7:0] = x[rs1]

#### SH
Format: sh rs2, Imm(rs1)<br />
Description: store 16-bit values from the low bits of register rs2 to memory<br />
Implementation: x[rs2] [15:0] = x[rs1]

#### SW
Format: sh rs2, Imm(rs1)<br />
Description: store 32-bit values from the low bits of register rs2 to memory<br />
Implementation: x[rs2] [31:0] = x[rs1]

<details>
    <summary>Example problem</summary>

Consider the instruction sequence below:<br />
<pre>
lui a1, 0x10010
addi t0, zero, -364
sw t0, 12(a1)
lb t1, 13(a1)
</pre>
What is the final value of register t1 after execution?            
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
a1 = 0x10010000
t0 = -364 = 0001 0110 1100 in unsigned
1's: 1110 1001 0011
2's: 1110 1001 0100
t0 = 0xFFFFFE94

The address where t0 is stored is at = a1 + 0xC = 0x1001000C. So, 0x94 is stored at 0x1001000C and 0xFE is stored at 0x1001000D. 0xFF is stored at 0x1001000F and 0xFF is stored at 0x10010010
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given a positive integer x stored in register s0, write a single RISC-V instruction to calculate x % 32 and store the result in register s1        
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
andi s1, s0, 31
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given a positive integer x stored in register s0, write a single RISC-V instruction to calculate x * 64 and store the result in register s1        
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
slli s1, s0, 6
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given a positive integer x stored in register s0, write a single RISC-V instruction to calculate x / 128 and store the result in register s1        
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
srai s1, s0, 7
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Write the RISC-V instructions to initialize register s0 to 0xDEADBEEF  
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
    1111
    DEADC000 
  + FFFFFEEF
  ----------
    DEADBEEF

lui s0, 0xDEADC
addi s0, s0, 0xEEF
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Write the RISC-V instructions to compute t2 = t0 AND t1 using a minimum number of instructions 
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
and t2, t0, t1
</pre>
</details>
</ul>  
</details>
