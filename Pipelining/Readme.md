<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#pipeline-performance'>Pipeline Performance</a>
  </li>
  <li>
    <a href='#instruction-pipelining'>Instruction Pipelining</a>
  </li>
  <li>
    <a href='#hazards'>Hazards</a>
  </li>
</ol>
</details>

## Pipeline Performance
Pipelining is used to overlap the execution of a program to make it run more efficiently and faster

A pipeline can process $n$ tasks in $k + n - 1$ cycles
<ul>
  <li>

  $k$ cycles are needed to complete the first task</li>
  <li>

  $n - 1$ cycles are needed to complete the remaining $n - 1$ tasks</li>
</ul>

$S$ <sub>k</sub> = serial execution in cycles / pipelined execution in cycles = $nk$ / $k + n - 1$

## Instruction Pipelining
Some CPUs divide the fetch-decode-execute cycle into smaller steps. These smaller steps can often be executed in parallel to increase throughput

Such parallel execution is called <strong>instruction pipelining</strong>. Instruction pipelining provides for <strong>instruction level parallelism</strong>

There are five stages to the RISC-V processor pipeline:
<ul>
  <li><strong>Instruction fetch</strong> from instruction memory</li>
  <li><strong>Instruction decode</strong> and register read</li>
  <li><strong>Execute</strong> operation or calculate load/store address</li>
  <li><strong>Memory access</strong> for load and store</li>
  <li><strong>Write back</strong> result to register</li>
</ul>

<details>
    <summary>Example problem</summary>

A nonpipelined system takes 200ns to process a task. The same task can be processed in a 5-segment pipeline with a clock cycle of 40ns

<ol>
  <li>Determine the speedup ration of the pipeline for 200 tasks</li>
  <li>What is the maximum speedup that could be achieved with the pipeline unit over the nonpipelined unit?</li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol>
 <li>

 $S$ <sup>k</sup> = $n * k * t$ / $t * (n + k - 1)$ = (200 * 200) / ((200 + 5 - 1) * 40) = 4.9019</li>
 <li>

 Speedup<sub>max</sub> = $k$ = 5</li>
</ol>
</details>
</ul>  
</details>

### Speedup Formula for Pipelining
<div align="center">
Speedup = Execution time of non-pipeline processor / Execution time of pipelined processor
</div>

Since execution time is proportional to the number of cycles, speedup can be written as:

<div align="center">
Speedup = Total cycles (non-pipelined) / Total cycles (pipelined)
</div>

Where total cycles (non-pipelined) is equal to the number of instructions times the number of clock cycles and where the total cycles (pipelined) is equal to the pipeline depth + (number of total instructions - 1)

<details>
    <summary>Example problem</summary>

A non-pipelined processor executes an instruction in 5 clock cycles, whereas a pipelined processor has a 5-stage pipeline with a clock cycle time equal to the longest stage. If there are 100 instructions to execute and no stalls, what is the speedup achieved by pipelining?
  <details>
    <summary>Solution</summary>

Total clock cycles (non-pipelined) = # of clock cycles * # of instructions = 5 * 100 = 500<br />

Total clock cycles (pipelined) = pipeline depth + (instructions - 1) * total cycles = 5 + (100 - 1) * 1 = 104<br />

Speedup = 500 / 104 = 4.81
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A 6-stage pipeline processor operates with a clock cycle time of 200ps and executes 500 instructions. Due to data hazards, the processor incurs 2 stall cycles per instruction on average. Assuming a non-pipelined processor takes 6 * 200 ps per instruction, what is the effective speedup of the pipelined  processor?
  <details>
    <summary>Solution</summary>

Total clock cycles (non-pipelined) = # of clock cycles * # of instructions = (6 * 500) * 200ps = 600000ps<br />

Total clock cycles (pipelined) = pipeline depth + (instructions - 1) * total cycles = (6 + (500 - 1) * 3) * 200ps = 300600ps<br />

Speedup = 600000ps / 300600ps = 1.996
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A processor has two implementations:

A 4-stage pipeline with a clock cycle of 150ps
An 8-stage pipeline with a clock cycle of 90ps

Assume 500 instructions are executed and ignore hazards. What is the speedup of the 8-stage pipeline compared to the 4-stage pipeline?
  <details>
    <summary>Solution</summary>
4-stage:

Total clock cycles (pipelined) = pipeline depth + (instructions - 1) * total cycles = (4 + (500 - 1)) * 150ps = 75450ps<br />

8-stage:

Total clock cycles (pipelined) = pipeline depth + (instructions - 1) * total cycles = (8 + (500 - 1)) * 90ps = 45630ps<br />

Speedup of 8-stage versus 4-stage = 75450 / 45630 = 1.654
</details>
</ul>  
</details>

## Hazards
<strong>Hazards</strong> are situations that cause incorrect execution 

A <strong>bubble</strong> or <strong>pipeline stall</strong> is a delay in execution of an instruction in an instruction pipeline in order to resolve a hazard

<ul>
  <li><strong>Structure hazards</strong> means a required resource is busy</li>
  <li><strong>Data hazard</strong> means need to wait for previous instruction to complete its data read/write</li>
  <li><strong>Control hazard</strong> means deciding on control action depends on previous instruction</li>
</ul>

### Structure Hazards
An example of a structure hazard is the following: one instruction is storing a value to memory while another is being fetched from memory, both need access to memory

The best way to eliminate a structure hazard is to implement separate instruction and data memory

<details>
    <summary>Example problem</summary>

A pipelined processor is designed with a single-port memory, which means that both instruction fetch (IF) and memory access (MEM) stages must share the same memory unit. What kind of hazard does this architecture suffer from, and what is the best solution to minimize its impact?

<ul>  
  <details>
    <summary>Solution</summary>

Structural hazard. The fix is to implement separate instruction and data memory
</details>
</ul>  
</details>

### Data Hazards
The synonymous for this type of hazard is a <strong>read after write hazard (RAW hazard)</strong>

An example of a data hazard is the following: given two instructions $I$ and $J$, where $I$ comes before $J$. Instruction $J$ should read an operand after it is written by $I$. Hazard occurs when $J$ reads the operand before $I$ writes it

### Control Hazards 
A control hazard occurs in a pipelined processor when the CPU does not know which instruction to fetch due to a change in the control flow, such as a branch or jump
