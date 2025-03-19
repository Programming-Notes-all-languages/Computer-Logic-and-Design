<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#for-loops'>For Loops</a>
  </li>
  <li>
    <a href='#while-loops'>While Loops</a>
  </li>
  <li>
    <a href='#do-while-loops'>Do-while Loops</a>
  </li>
</ol>
</details>

## For Loops
In C, an example of a for loop is the following:

```c
for (i = 0; i < size; i = i + 1)
    temp[i] = temp[i] + 128;
```

To implement this for loop in RISC-V, the following can be done:

<pre>
<code class="language-riscv">
add t0, zero, zero
FOR: bge t0, a1, EXIT
#Contents
J FOR
EXIT:
</code>
</pre>

<details>
    <summary>Example problem</summary>

What will be the value of t5?
<pre>
<code class="language-riscv">
.data
.globl main
arr: .space 12

main:
	#initializes the array
 	la a0, arr
 	
 	li t2, 0
 	sw t2, 0(a0)
 	
 	li t3, 1
 	sw t3, 4(a0)
 	
 	li t4, 2
 	sw t4, 8(a0)
 	
 	#initialize the sum to zero
 	li t5, 0
 	
 	#initialize the number of elements in the array
 	li t6, 3
 	
for:
 	lw t1, 0(a0)
 		
 	add t5, t5, t1
 		
 	addi a0, a0, 4
 		
 	addi t6, t6, -1
 		
 	bne t6, zero, for
 		
 	li a7, 10
 	ecall
</pre>
</code>

<ul>  
  <details>
    <summary>Solution</summary>

t5 = 3
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Write the RISC-V instructions to implement a loop where the loop index is stored in t0. Inside the loop, perform the operation <code>arr[i] = arr[i] * 2</code>. The base address of arr is stored in a0
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
<code class="language-riscv">
.globl main

main:
	li a0, 0x10010000
	
	li t0, 1
	sw t0, 0(a0)
	
	li t1, 2
	sw t1, 4(a0)
	
	li t2, 3
	sw t2, 8(a0)
	
	li a1, 3
	
for: 
	lw t3, 0(a0)
	slli t3, t3, 1
	sw t3, 0(a0)
	
	addi a0, a0, 4
	addi a1, a1, -1
	
	bne a1, zero, for
	
	li a7, 10
	ecall
</pre>
</code>
</details>
</ul>  
</details>

## While Loops
In C, an example of a while loop is the following:

```c
i = 0;
while (i < size)
{
    temp[i] = temp[i] * 128;
    i = i + 1;
}
```

To implement this while loop in RISC-V, the following can be done:

<pre>
<code class="language-riscv">
add t0, zero, zero
WHILE: bge t0, a1, EXIT
#Content
J WHILE
EXIT: 
</code>
</pre>

## Do-While Loops
In C, an example of a do-while loop is the following:

```c
i = 0;
do {
    temp[i] = temp[i] * 128;
    i = i + 1;
} while (i < size);
```

To implement this do-while loop in RISC-V, the following can be done:

<pre>
<code class="language-riscv">
add t0, zero, zero
DO: slli t1, t0, 2
#Contents
WHILE: blt t0, a1, DO
EXIT:
</code>
</pre>

<details>
    <summary>Example problem</summary>

What will be the value stored in t<sub>3</sub> after executing the following RISC-V implementation?

<pre>
      addi t0, x0, 0
      addi t1, x0, 1
      addi t2, x0, 5
loop: add t3, t0, t1
      add t0, t1, x0
      add t1, t3, x0
      addi t2, t2, -1
      bne t2, x0, loop
</pre>
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
t0 = 0
t1 = 1
t2 = 5

LOOP ITERATION 1
t3 = 1
t0 = 1
t1 = 1
t2 = 4
4 DNE 0

LOOP ITERATION 2
t3 = 2
t0 = 1
t1 = 2
t2 = 3
3 DNE 0

LOOP ITERATION 3
t3 = 3
t2 = 2
2 DNE 0

LOOP ITERATION 4
t3 = 4
1 DNE 0

LOOP ITERATION 5
t3 = 5
0 = 0
</pre>

t<sub>3</sub> = 5
</details>
</ul>  
</details>
