<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#b-type-instructions'>B-type Instructions</a>
  </li>
  <li>
    <a href='#i-type-instructions'>I-type Instructions</a>
  </li>
  <li>
    <a href='#s-type-instructions'>S-type Instructions</a>
  </li>
</ol>
</details>

Branches are conditional jumps that alter the flow of execution based on register values. RISC-V uses B-type instructions for branching

## B-type Instructions
<ul>
  <li>Compare the values stored in rs1 and rs2</li>
  <li>Update the program counter (PC) with the branch destination address if the branch condition is valid</li>
  <li>Otherwise, update the PC with PC + 4, which is the address of the next instruction</li>
  <li>The branch range of B-type instructions is &plusmn;4 KiB</li>
</ul>

#### BEQ
Format: beq rs1, rs2, Imm<br />
Description: take the branch if registers rs1 and rs2 are equal<br />
Implementation: if (x[rs1] == x[rs2])

#### BNE
Format: bne rs1, rs2, Imm<br />
Description: take the branch if registers rs1 and rs2 are not equal<br />
Implementation: if (x[rs1] != x[rs2])

#### BLT
Format: blt rs1, rs2, Imm<br />
Description: take the branch if registers rs1 is less than rs2, using signed comparison<br />
Implementation: if (x[rs1] &lt;s x[rs2])

#### BGE
Format: bge rs1, rs2, Imm<br />
Description: take the branch if registers rs1 is greater than or equal to rs2, using signed comparison<br />
Implementation: if (x[rs1] &gt;=s x[rs2])

#### BLTU
Format: bltu rs1, rs2, Imm<br />
Description: take the branch if registers rs1 is less than rs2, using unsigned comparison<br />
Implementation: if (x[rs1] &lt;u x[rs2])

#### BGEU
Format: bgeu rs1, rs2, Imm<br />
Description: take the branch if registers rs1 is greater than or equal to rs2, using unsigned comparison<br />
Implementation: if (x[rs1] &gt;=u x[rs2])

#### General Rule of Thumb
<ul>
  <li>With if-else, branch on the opposite condition to skip the if block and jump to else</li>
  <li>With if only, branch normally to execute the if block when true</li>
</ul>  

<details>
    <summary>Example problem</summary>

Assume integer variables $a$, $b$, $x$, and $y$ are stored in register $t$<sub>0</sub>, $t$<sub>1</sub>, $t$<sub>2</sub>, and $t$<sub>3</sub>, respectively. Consider the high-level code snippet below:<br />

```c
if (a > b)
    x = y + 5;
else
    x = y - 5;    
```

To correctly implement the above high-level code in RISC-V assembly, which actual RISC-V branch instruction should be used to replace BRANCH_INSTRUCTION

<pre>
<code class="language-riscv">
IF:           BRANCH_INSTRUCTION
THEN:         addi t2, t3, 5
              J        ENDIF
ELSE:         addi t2, t3, -5
ENDIF:
</code>
</pre>
<ul>  
  <details>
    <summary>Solution</summary>

ble t0, t1, ELSE
</details>
</ul>  
</details>

### Using Branches
#### Using Branches in if Statements

In C, this is how selection statements work:
```c
if (a > b)
    x = y + 5;
```

Here in RISC-V, this is how branch statements work:
<pre>
<code class="language-riscv">
bgt t0, t1, IF_BODY
IF_BODY:
    addi t2, t3, 5

#In the code above, the branch statement identifies whether t0 is greater than t1. If so, control jumps to the IF_BODY section and t2 is equal to t3 summed with 5
</code>
</pre>

#### Using Branches in if-else Statements
In C, this is how selection statements work:
```c
if (a > b)
    x = y + 5;
else
    x = y - 5;
```

Here in RISC-V, this is how branch statements work:
<pre>
<code class="language-riscv">
ble t0, t1, ELSE
THEN:
    addi t2, t3, 5
J ENDIF
ELSE:
    addi t2, t3, 4
ENDIF:

#In the code above, the branch statement identifies whether t0 is greater than t1. If so, control jumps to the IF_BODY section and t2 is equal to t3 summed with 5; otherwise, control jumps to the SKIP_IF section and t2 is equal to t3 summed with 4
</code>
</pre>

<details>
    <summary>Example problem</summary>

Write RISC-V instructions to implement a conditional branching structure (IF-ELSE-ENDIF) that checks if the value in t0 is greater than t1. If true, add t0 and t1 adn store the result in t0. If false, subtract t1 from t0 and store the result in t0

<pre>
<code class="language-riscv">
.globl main

main:
	li t0, 3
	li t1, 4
	
	ble t0, t1, ELSE
	add t0, t0, t1
	J ENDIF
ELSE:
	sub t0, t0, t1
ENDIF:
</code>
</pre>
<ul>  
  <details>
    <summary>Solution</summary>

ble t0, t1, ELSE
</details>
</ul>  
</details>

### J-type Instructions
<ol>
  <li>J-type instructions are mainly used as unconditional branch instructions</li>
  <li>One typical J-type instruction is JAL which stores the return address to register: rd: x[rd] = pc + 4</li>
  <li>Branch range of J-type instructions: &plusmn;1 MiB</li>
  <li>The default rd register is x1</li>
  <li>The default function call instruction is JAL RA, LABEL</li>>
</ol>  

#### JAL
Format: jal rd, Imm<br />
Description: jump to address and place return address in rd<br />
Implementation: x[rd] = pc + 4;

#### JALR
Format: jalr rd rs1, Imm<br />
Description: jump to address and place return address in rd<br />
Implementation: x[rd] = pc + 4;

<ul>
  <li>JAL and JALR can form a pair of instructions to complete the function call and return</li>
  <li>In the caller function, JAL ra, Callee_Func is used to call a function labelled by Callee_Func. This JAL instruction saves the return address (the instruction following the JAL instruction) to register ra, and then jumps to the beginning of the callee function, which is identified by Callee_Func</li>
  <li>In the callee function, JR RA is used to return to the caller function following the JAL instruction, the caller function therefore is executed continuously</li>
</ul>

If you need to call a function located at a different address, that means that the function you want to call is not within the current jump range that jal can handle. So you might need to use alternative methods like loading the address into a register and jumping with jalr

JAL is good for jumping to a fixed program counter relative address like a function name or loop name whereas JALR is used to jump to a location stored in a register. Use JAL if the function's address is known at compile time

<details>
    <summary>Example problem</summary>

Write RISC-V instructions to implement a conditional check: if t0 % 4 == 3, then jump to the assembly directive labeled ENDIF
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
<code class="language-riscv">
andi t1, t0, 3
addi t2, zero, 3
bne t1, t2, ENDIF
</code>
</pre>
</details>
</ul>  
</details>
