<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#arrays'>Arrays</a>
  </li>
  <li>
    <a href='#function-call-and-return'>Function Call and Return</a>
  </li>
  <li>
    <a href='#the-stack'>The Stack</a>
  </li>
</ol>
</details>

## Arrays
Here is how arrays are created in RISC-V:

<pre>
<code class="language-riscv">
.text
.globl main

main:
	#initializes the array
 	la a0, arr
 	
 	li t2, 0
 	sw t2, 0(a0)
 	
 	li t3, 1
 	sw t3, 4(a0)
 	
 	li t4, 2
 	sw t4, 8(a0)
</code>
</pre>

## Function Call and Return
<ol>
  <li>Function parameters are placed in eight registers: a0 - a7 also known as x10 - x17</li>
  <li>To transfer control to the procedure and save return address, use the following jump-and-link instruction: <code>jal ra, calleFunction</code></li>
  <li>Perform the desired task</li>
  <li>Put results in a place where the calling procedure can access. There are two value registers to return results: a0 and a1</li>
  <li>Return to calling procedure: jr ra</li>
</ol>  

<details>
    <summary>Example problem</summary>

Write a function that takes two integers as arguments and returns their sum. Assume the arguments are passed in a0 and a1, and the return value should be stored in a0
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
<code class="language-riscv">
main:
	addi a0, x0, 5
	addi a1, x0, 9

	jal Sum

Sum:
	add a0, a0, a1
	jr ra
</code>
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Find the maximum value in an array that you create using functions
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
<code class="language-riscv">
.globl main

main:
	#initializes the array
 	li a0, 0x10010000
 	
 	li t0, 55
 	sw t0, 0(a0)
 	
 	li t1, 1
 	sw t1, 4(a0)
 	
 	li t2, 99
 	sw t2, 8(a0)
 	
 	li t3, 44
 	sw t3, 12(a0)
 	
 	#initalize parameter max value to first element of array
 	add a1, t0, zero
 	
 	#initialize parameter number of elements within array
 	addi, a2, zero, 4
 	
 	jal Maximum
 	
 	li a7, 10
 	ecall
 	
 Maximum:
 	jal ra, for
 	jr ra
 	
 for:
 	lw t5, 0(a0)
 	
 	addi a0, a0, 4
 	addi a2, a2, -1
 	
 	bgt t5, a1, updateMax
 	
 	bne a2, zero, for
 	
 	jr ra
 
 updateMax:
        sub a1, a1, zero
 	add, a1, t5, zero
 	
 	jr ra
</code>
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Find the number of even and odd numbers in an array
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
<code class="language-riscv">
.globl main

main:
	#initialize the array
	li a0, 0x10010000
	
	#initialize the count of even numbers
	li t1, 0
	
	#initialize the count of odd numbers
	li t2, 0
	
	li t0, 2
	sw t0, 0(a0)
	
	li t3, 7
	sw t3, 4(a0)
	
	li t4, 8
	sw t4, 8(a0)
	
	li t5, 9
	sw t5, 12(a0)
	
	li t6, 10
	sw t6, 16(a0)
	
	li t0, 13
	sw t0, 20(a0)
	
	li t0, 15
	sw t0, 24(a0)
	
	li t0, 18
	sw t0, 28(a0)
	
	#number of elements in array
	li a1, 8
	
	jal findCounts
	
	li a7, 10
	ecall
	
findCounts:
	jal for
	jr ra
	
for:
	lw t0, 0(a0)
	
	addi a0, a0, 4
	
	andi t0, t0, 1
	
	bne t0, zero, addOdd
	j addEven
	
addOdd:
	addi t2, t2, 1
	j loopContinue
	
addEven:
	addi t1, t1, 1	
	j loopContinue
	
loopContinue:
	addi a1, a1, -1
	
	bne a1, zero, for
	
	jr ra
</code>
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Write a RISC-V instruction to call a function LINEAR_SEARCH located at a different address
<ul>  
  <details>
    <summary>Solution</summary>

jalr, ra, 0(t0) 
</details>
</ul>  
</details>

## The Stack
The stack is memory used to temporarily save variables

The stack uses the last-in-first-out queue, meaning that the information stored last is on the top of the stack

The stack pointer, also known as sp and x2, points to the top of the stack

<details>
    <summary>Example problem</summary>

Write a RISC-V instructions to allocate stack space and backup the original values of registers s0 and ra
<ul>  
  <details>
    <summary>Solution</summary>

addi sp, sp, -8
sw s0, 8(sp)
sw ra, 4(sp)
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Write a RISC-V instructions to restore the original values of registers s0 and ra
<ul>  
  <details>
    <summary>Solution</summary>

lw s0, 8(sp)
lw ra, 4(sp)
addi sp, sp, 8
</details>
</ul>  
</details>

# Homework 1
.globl main

main:
	lui a0, 0x10010
	
	addi t0, zero, 0
	sw t0, 0(a0)
	
	addi t0, t0, 1
	sw t0, 4(a0)
	
	addi t0, t0, 1
	sw t0, 8(a0)
	
	addi t0, t0, 1
	sw t0, 12(a0)
	
	#number of array elements
	addi a2, zero, 4
	
	#number we are searching for in array
	addi a1, zero, 3
	
	#initializing i
	addi t3, zero, 0
	
	addi t4, zero, 4
	
	jal, ra, linear_search
	
linear_search:
	j for

for:
	ble a2, zero, NotFound

	lw t2, 0(a0)
	
	addi a0, a0, 4
	
	addi a2, a2, -1
	
	beq t2, a1, Found
	
	addi t3, t3, 1
	
	j for

NotFound:
	sub a0, a0, zero
	addi a0, a0, -1
	
	j Exit

Found:
	sub a0, a0, zero
	add a0, a0, t3

Exit:
	
