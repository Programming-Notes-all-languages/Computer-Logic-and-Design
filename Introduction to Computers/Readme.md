<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#computer-organization-and architecture overview'>Computer Organization and Architecture Overview</a>
  </li>
  <li>
    <a href='#units-of-measure'>Units of Measure</a>
  </li>
  <li>
    <a href='#computer-level-hierarchy'>Computer Level Hierarchy</a>
  </li>
  <li>
    <a href='#von-neumann-model-and-non-von-neumann-models'>Von Neummann Model and Non-von Neumann Models</a>
  </li>
</ol>
</details>

## Computer Organization and Architecture Overview
### Computer Organization
<ul>
  <li>Encompasses all physical aspects of computer systems</li>
  <li>Circuit design, control signals, and memory types</li>
  <li>Defines how a computer works</li>
</ul>  

### Computer Architecture
<ul>
  <li>Logical and abstract system implementation as seen by the programmer</li>
  <li>Instruction sets, instruction formats, data types, addressing modes, memory access methods, and input/output mechanisms</li>
  <li>How is a computer designed</li>
</ul>  

There is no clear distinction between matters related to computer organization and matters relevant to computer architecture. The <strong>Principle of Equivalence of Hardware and Software</strong> states that any task done by software can also be done using hardware, and any operation performed directly by hardware can be done using software

### Computer Evolution
Electronics technology continues to evolve as with time there is increase capacity and performance, along with reduced cost

### Moore's Law
Moore's Law was founded by Gordon Moore, the founder of Intel

<ul>
  <li>In 1965, the law stated that the density of transistors in an integrated circuit will double every year</li>
  <li>The contemporary version of Moore's Law is that the density of silicon chips doubles every 18 months</li>
</ul>  

### Rock's Law
Rock's Law was founded by Arthur Rock, and Intel financier

<ul>
  <li>The law states that the cost of capital equipment to build semiconductors will double every four years</li>
  <li>For Moore's Law to hold, Rock's Law must fall, or vice versa; however, no one can say which will give out first</li>
</ul>  

### What is a Modern Computer
<ul>
  <li>A modern computer is an electronic, digital, general-purpose computing machine that automatically follows a step-by-step list of instructions to solve a problem</li>
  <li>This step-by-step list of instructions that a computer follows is also called an <strong>algorithm</strong> or a <strong>computer program</strong></li>
</ul>  

### Computer Components
At the most basic level, a computer is a device consisting of three pieces:
<ul>
  <li>A <strong>processor</strong> to interpret and execute programs</li>
  <li>A <strong>memory</strong> to store both data and programs</li>
  <li>A mechanism for <strong>data input and output</strong></li>
</ul>  

## Units of Measure
### Measures of Capacity
<table>
        <thead>
            <tr>
                <th>Decimal Term</th>
                <th>Abbreviation</th>
                <th>Value</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Kilobyte</td>
                <td>KB</td>
                <td>10<sup>3</sup> bytes</td>
            </tr>
            <tr>
                <td>Megabyte</td>
                <td>MB</td>
                <td>10<sup>6</sup> bytes</td>
            </tr>
            <tr>
                <td>Gigabyte</td>
                <td>GB</td>
                <td>10<sup>9</sup> bytes</td>
            </tr>
            <tr>
                <td>Terabyte</td>
                <td>TB</td>
                <td>10<sup>12</sup> bytes</td>
            </tr>
            <tr>
                <td>Petabyte</td>
                <td>PB</td>
                <td>10<sup>15</sup> bytes</td>
            </tr>
            <tr>
                <td>Exabyte</td>
                <td>EB</td>
                <td>10<sup>18</sup> bytes</td>
            </tr>
            <tr>
                <td>Zettabyte</td>
                <td>ZB</td>
                <td>10<sup>21</sup> bytes</td>
            </tr>
            <tr>
                <td>Yottabyte</td>
                <td>YB</td>
                <td>10<sup>24</sup> bytes</td>
            </tr>
        </tbody>
    </table>

<table>
        <thead>
            <tr>
                <th>Binary Term</th>
                <th>Abbreviation</th>
                <th>Value</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Kibibyte</td>
                <td>KiB</td>
                <td>2<sup>10</sup> bytes (1,024 bytes)</td>
            </tr>
            <tr>
                <td>Mebibyte</td>
                <td>MiB</td>
                <td>2<sup>20</sup> bytes (1,048,576 bytes)</td>
            </tr>
            <tr>
                <td>Gibibyte</td>
                <td>GiB</td>
                <td>2<sup>30</sup> bytes (1,073,741,824 bytes)</td>
            </tr>
            <tr>
                <td>Tebibyte</td>
                <td>TiB</td>
                <td>2<sup>40</sup> bytes (1,099,511,627,776 bytes)</td>
            </tr>
            <tr>
                <td>Pebibyte</td>
                <td>PiB</td>
                <td>2<sup>50</sup> bytes (1,125,899,906,842,624 bytes)</td>
            </tr>
            <tr>
                <td>Exbibyte</td>
                <td>EiB</td>
                <td>2<sup>60</sup> bytes (1,152,921,504,606,846,976 bytes)</td>
            </tr>
            <tr>
                <td>Zebibyte</td>
                <td>ZiB</td>
                <td>2<sup>70</sup> bytes (1,180,591,620,717,411,303,424 bytes)</td>
            </tr>
            <tr>
                <td>Yobibyte</td>
                <td>YiB</td>
                <td>2<sup>80</sup> bytes (1,208,925,819,614,629,174,706,176 bytes)</td>
            </tr>
        </tbody>
    </table>

### Measures of Processor Speed
The unit for measuring a processor's speed is hertz. A hertz is the number of clock cycles/second, also known as frequency

<ul>
  <li>Processor speeds are measured in MHz of GHz</li>
  <li>Clock frequency is the reciprocal of cycle time</li>
</ul>  

<table>
        <thead>
            <tr>
                <th>SI Prefix</th>
                <th>Abbreviation</th>
                <th>Value</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Kilo</td>
                <td>k</td>
                <td>10<sup>3</sup></td>
            </tr>
            <tr>
                <td>Mega</td>
                <td>M</td>
                <td>10<sup>6</sup></td>
            </tr>
            <tr>
                <td>Giga</td>
                <td>G</td>
                <td>10<sup>9</sup></td>
            </tr>
            <tr>
                <td>Tera</td>
                <td>T</td>
                <td>10<sup>12</sup></td>
            </tr>
            <tr>
                <td>Peta</td>
                <td>P</td>
                <td>10<sup>15</sup></td>
            </tr>
            <tr>
                <td>Exa</td>
                <td>E</td>
                <td>10<sup>18</sup></td>
            </tr>
            <tr>
                <td>Zetta</td>
                <td>Z</td>
                <td>10<sup>21</sup></td>
            </tr>
            <tr>
                <td>Yotta</td>
                <td>Y</td>
                <td>10<sup>24</sup></td>
            </tr>
        </tbody>
    </table>

<details>
    <summary>Example problem</summary>

If a bus is operating at 133MHz , what is its cycle time in nanoseconds
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
133 <s>M</s> cycles   <s>second</s>   10<sup>6</sup>
------------ X ------ X -- = 133 X 10<sup>-3</sup> cycles/ns
  <s>second</s>       10<sup>9</sup> ns    <s>M</s>
<br />
Cycle time is the reciprocal of clock frequency:
      1 ns
----------------- = 7.52 ns/cycle
133 X 10<sup>-3</sup> cycles
</pre>
</details>
</ul>  
</details>

<table border="1">
  <thead>
    <tr>
      <th>SI Prefix</th>
      <th>Abbreviation</th>
      <th>Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Milli</td>
      <td>m</td>
      <td>10<sup>-3</sup></td>
    </tr>
    <tr>
      <td>Micro</td>
      <td>&#181;</td>
      <td>10<sup>-6</sup></td>
    </tr>
    <tr>
      <td>Nano</td>
      <td>n</td>
      <td>10<sup>-9</sup></td>
    </tr>
    <tr>
      <td>Pico</td>
      <td>p</td>
      <td>10<sup>-12</sup></td>
    </tr>
    <tr>
      <td>Femto</td>
      <td>f</td>
      <td>10<sup>-15</sup></td>
    </tr>
    <tr>
      <td>Atto</td>
      <td>a</td>
      <td>10<sup>-18</sup></td>
    </tr>
    <tr>
      <td>Zeppto</td>
      <td>z</td>
      <td>10<sup>-21</sup></td>
    </tr>
    <tr>
      <td>Yocto</td>
      <td>y</td>
      <td>10<sup>-24</sup></td>
    </tr>
  </tbody>
</table>

<details>
    <summary>Example problem</summary>

How many nanoseconds are in a millisecond
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
        1 <s>s</s>     10<sup>9</sup> ns
1 <s>ms</s> X ------ X ------ = 10<sup>6</sup> ns = 1,000,000 ns
       10<sup>3</sup> <s>ms</s>     1 <s>s</s>
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

How many MiB are in 16 GiB
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
         2<sup>30</sup> <s>B</s>    1 MiB
16 <s>GiB</s> X ----- X ------- = 16,384 MiB
         1 <s>GiB</s>    2<sup>20</sup> <s>B</s>
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

One processor runs at 1.25 GHz. How many nanoseconds is one clock cycle for this processor
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
1.25 G cycles    10<sup>9</sup>     1 s
------------- X ----- X ------ = 1.25 cycles/ns
   seconds        G     10<sup>9</sup> ns
<br />To find how many nanoseconds are in one clock cycle, take the reciprocal of the above result:<br />
   1 ns
---------- = 0.8 ns/cycle
1.25 cycle
</pre>
</details>
</ul>  
</details>

## Computer Level Hierarchy
<ul>
  <li>Each virtual machine layer is an abstraction of the level below it. What this means is that each layer of the computer hierarchy hides the details of the underlying hardware or software components</li>
  <li>The machines at each level execute their own particular instructions, calling upon machines at lower levels to perform tasks as required</li>
  <li>Computer circuits ultimately carry out the work</li>
</ul>  

### Level 6: The User Level
<ul>
  <li>Program execution and user interface level</li>
  <li>The level with which people are most familiar with. It is composed of applications that the user uses, such as Microsoft Word, video games, etc.</li>
  <li>The levels below the user level are nearly invisible to the user</li>
</ul>

### Level 5: High-Level Language Level
<ul>
  <li>The level with which people interact when writing programs in languages such as C and Java</li>
  <li>The compilation of C code produces assembly code which will then be interpreted by Level 4</li>
</ul>  

### Level 4: Assembly Language Level
<ul>
  <li>Acts upon assembly language produced from level t, as well as instructions programmed directly at this level</li>
</ul>

### Level 3: System Software Level
<ul>
  <li>Operating system instructions, which are programs that the central processing unit executes, are dealt with</li>
  <li>Protects system resources</li>
  <li>Assembly language instructions often pass through level 3 without modification</li>
</ul>

### Level 2: Machine Level
<ul>
  <li>Also known as the Instruction Set Architecture (ISA) Level. This is a model that defines how the CPU is controlled by its ISA software. The ISA is the interface between the software that runs the machine and the hardware that executes it</li>
  <li>Consists of instructions that are particular to the architecture of the machine. These instructions are written in machine code which do not further need to be reduced to be understood by the computer's hardware (the computer's organization). Machine code is a low-level programming language comprising bits with values of 0 and 1</li>
  <li>Programs written in machine language need no compilers, interpreters, or assemblers</li>
  <li>This stage represents the point where the system's organization and architecture meet and interact</li>
</ul>  

### Level 1: Control Level
<ul>
  <li>A <strong>control unit</strong> makes sure that the instructions given into the computer are decoded and executed properly</li>
  <li>Control units can be <strong>microprogrammed</strong> or <strong>hardwired</strong>
    <ul>
      <li>Hardwired control units:
        <ul>
          <li>Hardwired control units generate the control signals which go to digital logic components to perform tasks. These control signals are the electricity that travels through a computer</li>
          <li>These are often very fast as they are the actual physical components of the computer; however, they are hard to modify as the structures that generate the control signals, the electricity, are hardwired to the computer</li>
        </ul> 
      </li>   
      <li>Microprogammed control units:
        <ul>
          <li>A microprogram is a program that is written in a low-level language that is implemented by a computer's hardware</li>
          <li>The microprogram control unit is responsible for generating control signals, such as electricity</li>
          <li>Microprograms are popular because of how easily they can be modified; however, there is then an additional layer of code translation which results in slower execution time</li>
        </ul>  
      </li>
    </ul>
  </li>
</ul>      

### Level 0: Digital Logic Level
<ul>
  <li>This level is where we find digital circuits (the chips)</li>
  <li>Digital circuits consist of gates and wires</li>
  <li>These components implement the mathematical logic of all other levels</li>
</ul>  

## Von Neumann Model and Non-von Neumann Models
### The von Neumann Model
John von Neumann wrote a report on the stored program concept, known as the <i>First Draft of a Report on EDVAC</i>

The basic structure proposed in the draft becomes known as the "von Neumann machine"
<ul>
  <li>A <strong>memory</strong> contains instructions and data</li>
  <li>A <strong>processing unit</strong> performs arithmetic and logical operations</li>
  <li>A <strong>control unit</strong> interprets instructions</li>
</ul>  

Today's stored-program machine architecture:
<ul>
  <li>Three hardware systems:
    <ul>
      <li>A <strong>central processing unit (CPU)</strong> with a control unit, an <strong>arithmetic logic unit (ALU)</strong>, <strong>registers</strong> (small storage areas)
        <ul>
          <li>The arithmetic logic unit performs arithmetic operations: addition, subtraction, multiplication, division, and logical operations on binary numbers</li>
          <li>Registers are small storage containers within the CPU that store data and instructions during the execution of processes by the CPU</li>
        </ul>  
      </li>
      <li>A <strong>main memory</strong> system stores data and programs that are being executed by the computer's CPU</li>
      <li>An <strong>input\output system</strong> such as mice, keyboards, monitors, scanners, microphones, webcams, trackpads, and touchscreen.</li>
    </ul>
  </li>
  <li>The capacity to carry out sequential instruction processing</li>
  <li>A single path between the control unit of the CPU and main memory. This single path is known as the <strong>von Neumann bottleneck</strong></li>
</ul>

### Fetch-Decode-Execute Cycle
This process represents how a computer's CPU executes instructions. This cycle is also called the <strong>von Neumann execution cycle</strong>. The following explains how this process works

<ol>
  <li>Fetch:
    <ol>
      <li>The <strong>program counter</strong> is a register that holds the address of the next instruction to be executed. The beginning of this model starts withing the program counter</li>
      <li>The address stored in the program counter is sent:
        <ul>
          <li>First from the program counter register to the ALU, which acts as a highway as no arithmetic operations occur during fetch</li>
          <li>Then to the control unit</li>
        </ul>
      </li>  
      <li>The control unit places the instruction's address on the address bus</li>
      <li>The instructions then come out of the CPU and travel to the main memory</li>
      <li>Within main memory, the computer is going to look for the memory address of the instruction that was stored in the program counter. If the address is found, the information stored in main memory at that address will be pulled out</li>
      <li>The retrieved instruction is then sent back to the CPU
        <ul>
          <li>First to the control unit through the data bus</li>
          <li>Then through the ALU which acts as a highway</li>
          <li>Finally, it is into the instruction register for further processing</li>
        </ul>
      </li>
      <li>The instruction is placed into the instruction register for temporary storage and preparation for decoding</li>
      <li>Once the current instruction is successfully fetched, the program counter is incremented (usually by one) to point to the next instruction in memory</li>
    </ol>
  </li>
  <li>Decoding:
    <ol>
      <li>After the fetch phase is completed, the control unit receives the instruction from the instruction register. 
        <ul>
            <li>The instructions leave the instruction register and first go to the ALU</li>
            <li>From there the instructions then travel to the control unit</li>
        </ul>
      </li>  
      <li>The control unit will interpret the instruction to determine what operation needs to be performed</li>
      <li>The control unit identifies an operation code that specifies the operation to perform. This tells the control unit what kind of operation the ALU must perform</li>
      <li>The control unit identifies any operands needed for the operation, which could be values that need to be processed or addresses where data is located. If the instruction requires additional operands that are not immediately available (they are stored in memory or other registers), the control unit will begin another fetch cycle; however, this will be an operand fetch cycle that does not increment the program counter</li>
      <li>If additional operands for an instruction are needed: 
        <ul>
          <li>The control units sends a memory address using an address bus to fetch the operands from main memory or from a register</li>
          <li>If the operand is in main memory, the address is sent to memory and the corresponding data is fetched</li>
          <li>Once the operand data is located (in memory or a register), it is sent back to the control unit for final instruction processing. The data may travel via the ALU and then to appropriate registers, but not the program counter. The program counter is only updated during the fetch phase to point to the address of the next instruction</li>
        </ul>
      <li>The fetched operand(s) are placed in the appropriate register(s) within the CPU, which could be a general-purpose register or a special register</li>
      <li>Once the control unit has decoded the instruction and fetched any necessary operands, the instruction is not ready for the execute phase</li>
    </ol>
  </li>
  <li>Execute
    <ol>
      <li>The control unit uses the decoded information to generate control signals that orchestrate the execution phase. These signals dictate how the CPU will perform the required operation</li>
      <li>If operands are stored in registers, the control unit directs the ALU to access the appropriate registers. If an operand was fetched during the decode phase, it is already in the CPU's registers</li>
      <li>The ALU then performs the operation and processes operands from registers or memory. If a result is computed, it is stored in a register or written back to memory</li>
    </ol>
  </li>
</ul>      

### System Bus Model
The <strong>von Neumann bottleneck</strong> is a single path between the CPU and main memory
<ul>
  <li>The data bus moves data between the main memory and the CPU registers</li>
  <li>The address bus holds the address of the data that the data bus is currently accessing</li>
  <li>The control bus carries the necessary control signals that specify how the information transfer is to take place</li>
</ul>  

### Non-von Neumann Models
Improvements to the conventional stored-program computers are the addition of specialized buses, floating-point units, and cache memories

Enormous improvements in computational power require departure from the classic von Neumann architecture

<strong>Parallel processing</strong> refers to a collection of different architectures:
<ul>
  <li>Multiple separate computers working together</li>
  <li>Multiple processors sharing system memory</li>
  <li>Multiple cores integrated onto the same chip</li>
</ul>  
