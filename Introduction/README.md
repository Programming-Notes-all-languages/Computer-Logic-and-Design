<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#the-main-components-of-a-computer'>The Main Components of a Computer</a>
  </li>
  <li>
    <a href='#moores-law-and-rocks-law'>Moore's Law and Rock's Law</a>
  </li>
  <li>
    <a href='#the-computer-level-hierarchy'>The Computer Level Hierarchy</a>
  </li>
  <li>
    <a href='#measures-of-capacity-and-processor-speed'>Measures of Capacity and Processor Speed</a>
  </li>
  <li>
    <a href='#the-von-nuemann-model'>The von Nuemman Model</a>
  </li>  
  <li>
    <a href='#non-von-nuemann-model'>Non-von Nuemann Model</a>
  </li>
</ol>
</details>


## The Main Components of a Computer
<ul>
  <li>
    <a><em>Computer organization</em> consists of the physical components of a computer, such as the computer's hardware. It is concerned with the way the computer's hardware is connected to make a computer</a>
    <ul>
      <li>
        <a>Examples include the computer's circuit design, control signals, and memory types</a>
      </li>
      <li>
        <a>Computer organization is concerned with how the computer works</a>
      </li>  
    </ul>    
  </li>
  <li>
    <a><em>Computer architecture</em> consists of the logical implementations of the computer's design as seen by the coder, known as the computer's software</a>
    <ul>
      <li>
        <a>Computer architecture is concerned with how the computer is designed</a>
      </li>
    </ul>    
  </li>
  <li>
    <a>There is no clear distinction between processes related to computer architecture and computer organization. Computer scientists and computer engineers hold differing views as to what is computer architecture and what is computer organization. Computer architecture cannot exist without computer organization and vice versa</a>
  </li>  
  <li>
    <a><em>Principle of Equivalence of Hardware and Software</em>: defines that any task that can be accomplished by software can be done using only hardware and vice versa</a>
  </li>
  <li>
    <a>The necessary components to build a computer system consist of the following components:</a>
    <ul>
      <li>
        <a>A <em>processor</em>, known as the central processing unit, is needed to understand, interpret, and execute, programs</a>
      </li>
      <li>
        <a>A <em>memory</em> stores programs and information within the computer</a>
      </li>
      <li>
        <a>Mechanisms for <em>data input and output</em> which transfers information from the user, to the computer, and then to the user again</a>
      </li>
      <li>
        <a>Computers follow step by step instructions which are called <em>algorithms</em></a>
      </li>
    </ul>
  </li>      
</ul>


## Moore's Law and Rock's Law
<ul>
  <li>
    <a>The founder of Moore's Law is Gordon Moore, who is the founder of Intel</a>
  </li>
  <li>
    <a><em>Moore's Law</em></a>: states that "the density of transistors in an integrated circuit will double every year"</a>
  </li>
  <ul>
    <li>
        <a>The current version of this law is that "the density of silicon chips doubles every 18 months"</a>
    </li>  
    <li>
        <a>Moore's Law cannot hold forever since transistors are already the size of an atom, meaning that they physically cannot become any smaller. There are financial limitations too</a>
    </li>  
  </ul>  
  <li>
    <a>Rock's Law was created by Author Rock, an Intel financier and investor</a>
    <ul>  
      <li>
        <a><em>Rock's Law</em>: states that "the cost of capital equipment to build semiconductors will double every four years"</a>
      </li>
      <li>
        <a>Rock's Law cannot hold forever as well since the money to produce these chips will be astronomical</a>
      </li>
    </ul>  
  </li>
  <li>
    <a>For Moore's Law to hold, Rock's Law must no longer persist or vice versa</a>
  </li>  
</ul>  


## The Computer Level Hierarchy
![Untitled-Diagram95](https://github.com/Programming-Notes-all-languages/Computer-Organization/assets/154717520/72e6eade-2bbe-4098-85b7-21dd9e3b5279)
<ul>
  <li>
    <a>Level 6: The User Level</a>
    <ul>
      <li>
        <a>This level is composed of the applications that the user uses, such as Microsoft Word, video games, etc. The user here executes the programs and this stage is known as the user interface level</a>
      <li>
        <a>This is the level that humans are most familiar with</a>
      </li>
      <li>
        <a>The levels below the user level are nearly invisible to the user</a>  
      </li>
    </ul>    
  </li>
  <li>
    <a>Level 5: High-Level Language Level</a>
    <ul>
      <li>
        <a>This is the level that consists of high-level languages like C, C++, Python, etc. The user interacts with this level when coding in high-level languages like the ones listed above</a>
      </li>
      <li>
        <a>The compilation of C code, running the gcc command, produces assembly code which will then be interpreted by level four</a>
      </li>
      <li>
        <a>The user at the higher level sees very little of all levels below itself</a>
      </li>    
    </ul>
  </li>
  <li>
    <a>Level 4: Assembly Language Level</a>
    <ul>
      <li>
        <a>At this level, the computer acts upon the assembly language that the high-level language produced during the code's compilation</a>
      </li>
    </ul>
  </li>
  <li>
    <a>Level 3: System Software Level</a>
    <ul>
      <li>
        <a>At this level, operating system instructions, which are programs that the central processing unit executes, are dealt with</a>
      </li>
      <li>
        <a>Assembly language code often passes through this stage without any modification</a>
      </li>
      <li>
        <a>This stage manages system resources</a>
      </li>  
    </ul>
  </li>
  <li>
    <a>Level 2: Machine Level</a>
    <ul>
      <li>
        <a>This level is also known as the Instruction Set Architecture (ISA) Level. This ISA is a model that defines how the CPU is controlled by its ISA software. The ISA is the interface between the software that runs the machine and the hardware that executes it</a>
      </li>
      <li>
        <a>This stage consists of the instructions that are particular to the computer's architecture. These instructions are written in machine code which do not further need to be reduced to be understood by the computer's architecture. In other words, the computer's hardware will understand these instructions as they are written in machine code</a>
      </li>
      <li>
        <a>Machine code is a low-level programming language comprising of bits with values of 0 and 1</a>
      </li>  
      <li>
        <a>This stage represents the point where the system's organization and architecture meet and interact</a>
      </li>    
    </ul>
  </li>  
  <li>
    <a>Level 1: Control Level</a>
    <ul>
      <li>
        <a>This level contains the <em>control unit</em> which makes sure that the instructions given to the computer are decoded and executed properly</a>
      <li>
        <a>Control units can be either <em>hardwired</em> or they can be microprogrammed</em></a>
      </li>
      <ul>
        <li>
          <a>Hardwired control units:</a>
        </li>  
        <ul>
          <li>
            <a>Hardwired control units generate the control signals which go to digital logic components to perform tasks. These control signals are the electricity that travels through a computer</a>
          </li>
          <li>
            <a>These are often very fast as they are the actual physical components of the computer; however, they are hard to modify as the structures that generate the control signals, the electricity, are hardwired to the computer</a>
          </li>
        </ul>
        <li>
          <a>Microprogrammed control units:</a>
          <ul>
            <li>
              <a>A microprogram is a program that is written in a low-level language that is implemented by a computer's hardware</a>
            </li>
            <li>
              <a>The microprogram control unit is responsible for generating control signals, such as electricity</a>
            </li>  
            <li>
              <a>Microprograms are popular because of how easily they can be modified; however, there is then an additional layer of code translation which results in slower execution times</a>
            </li>    
          </ul>
        </li>      
      </ul>
    </ul>  
  </li>
  <li>
    <a>Level 0: Digital Logic Level</a>
    <ul>
      <li>
        <a>This level consists of the digital circuits inside of the computer, also known as the computer's chips. These chips consist of gates and wires</a>
      </li>
      <li>
        <a>The chips implement mathematical logic</a>
      </li>  
    </ul>
  </li>                          
</ul>  


## Measures of Capacity and Processor Speed
| | Measures of Capacity | |
| :---: | :---: | :---: |
| **Decimal term** | **Abbreviation** | **Value (bytes)** |
| kilobyte | KB | 10<sup>3</sup> |
| megabyte | MG | 10<sup>6</sup> |
| gigabyte | GB | 10<sup>9</sup> |
| terabyte | TB | 10<sup>12</sup> |
| petabyte | PB | 10<sup>15</sup> |
| exabyte | EB | 10<sup>18</sup> |
| zettabyte | ZB | 10<sup>21</sup> |
| yottabyte | YB | 10<sup>24</sup> |


| | Measures of Capacity | |
| :---: | :---: | :---: |
| **Binary term** | **Abbreviation** | **Value (bytes)** |
| kibibyte | KB | 2<sup>10</sup> |
| mebibyte | MiG | 2<sup>20</sup> |
| gibibyte | GiB | 2<sup>30</sup> |
| tebibyte | TiB | 2<sup>40</sup> |
| pebibyte | PiB | 2<sup>50</sup> |
| exbibyte | EiB | 2<sup>60</sup> |
| zebibyte | ZiB | 2<sup>70</sup> |
| yobibyte | YiB | 2<sup>80</sup>> |  


| | Measures of Processor | |
| :---: | :---: | :---: |
| **Term** | **Abbreviation** | **Value (Hz)** |
| kilohertz | KHz | 10<sup>3</sup> |
| megahertz | MHz | 10<sup>6</sup> |
| gigahertz | GHz | 10<sup>9</sup> |
| terahertz | THz | 10<sup>12</sup> |
| petahertz | PHz | 10<sup>15</sup> |
| exahertz | EHz | 10<sup>18</sup> |
| zettahertz | ZHz | 10<sup>21</sup> |
| yottahertz | YHz | 10<sup>24</sup> |


<ul>
  <li>
    <a>Hertz is a measure of cycles per second. The number of cycles per second is also known as frequency</a>
  </li>
  <li>
    <a>Processor speeds are measured in MHz, but currently, processors are now measured in GHz</a>
  </li>  
</ul>


| | Measures of Time/Space | |
| :---: | :---: | :---: |
| **Prefix** | **Abbreviation** | **Value** |
| milli | m | 10<sup>-3</sup> |
| micro | &mu; | 10<sup>-6</sup> |
| nano | n | 10<sup>-9</sup> |
| pico | p | 10<sup>-12</sup> |
| femto | f | 10<sup>-15</sup> |
| atto | a | 10<sup>-18</sup> |
| zepto | z | 10<sup>-21</sup> |
| yocto | y | 10<sup>-24</sup> |


## The von Nuemann Model
<ul>
  <li>
    <a>The stored-program concept outlines that all stored-program computers have all of the following characteristics:</a>
    <ul>
      <li>
        <a>Consists of all three of following hardware systems:</a>
        <ul>
          <li>
            <a>A <em>central processing unit</em> containing a control unit, <em>arithmetic logic unit (ALU)</em>, and <em>registers</em></a>
            <ul>
              <li>
                <a>The arithmetic logic unit performs arithmetic operations, addition, subtraction, multiplication, and division, and logical operations on binary numbers</a>
              </li>  
              <li>
                <a>Registers are small storage containers within the CPU that store data and instructions during the execution of processes by the CPU</a>
              </li>
            </ul>  
          </li>
          <li>
            <a>A <em>main memory system</em> stores data and programs that are being executed by the computer's CPU</a>
          </li>
          <li>
            <a>An <em>I/O system</em> such as mice, keyboards, monitors, etc</a>  
          </li>  
        </ul>    
      </li>
      <li>
        <a>Ability to process instructions in a sequential manner</a>
      </li>
      <li>
        <a>There is lastly a single path between the control unit of the CPU and the main memory. This single path is called the <em>von Neumann bottleneck</em>. This path is a bidirectional path between the CPU's control unit and the system's main memory</a>
      </li>    
    </ul>
  </li>


![IMG_0710](https://github.com/Programming-Notes-all-languages/Computer-Organization/assets/154717520/b78893b2-73c5-4cf0-8756-41598f54318e)
  <li>
    <a>The process that represents how a computer's CPU executes instructions is defined as the <em>fetch-decode-execute cycle</em>. This cycle is also called the <em>von Neumann execution cycle</em>. The following will explain how this process works</a>
    <ul>
      <li>
        <a>Fetch: the beginning of this model is within the registers, specifically the program counter. The program counter is a special register that holds the data is the computer's next instruction. The other registers may be holding values, such as int x or even float y. The fetching happens when the CPU retrieves instructions from the main memory. The instruction is typically stored within a register in the CPU that is called the program counter. The instruction address travels from the program counter to the ALU, to then the control unit. The instructions then come out of the CPU and then go to the main memory. Within main memory, the computer is going to look for that address and if it is found, the information stored at that memory address will be pulled out. That information is then sent back to the control unit</a>
      </li>    
      <li>
        <a>Decoding: takes place after the fetching is complete. The control unit will make sense of the instructions that it receives from the main memory. In other words, the control unit will decode the information. This process involves identifying what operations need to be performed. This step also identifies any additional operands that are needed to execute the instruction. If additional operands for an instruction are needed, then a fetch operand cycle occurs. Here, the control unit sends a bus to get the address of the additional instruction from the main memory. Once the address is found, the address is sent to the control unit, then the ALU, then to the additional registers in the CPU--not the program counter register</a>
      </li>
      <li>
        <a>Execute: takes place after the information is sent to the ALU. If any data is needed from the registers to complete that instruction, then the ALU will fetch that data and execute the instruction using that data. For example, if the information represented in bits really means to add two variables together, then the ALU will perform that summation. Afterward, the new information could be sent back to the registers where some number of the registers are now updated with new information or main memory. The ALU essentially executes the instructions which were made legible to the ALU by the control unit during decoding</a>
      </li>  
    </ul>  
  </li>  
  <li>
    <a>System Bus Model</a>
  </li>
  <ul>
    <li>
      <a>There are three busses associated with the bus model:</a>
      <ul>
        <li>
          <a>Data bus: moves data between main memory and registers. This bus is bidirectional with respect to the CPU and main memory</a>
        </li>
        <li>
          <a>Address bus: holds the addresses of the data that the data bus is currently processing. The address bus is single-directional for the CPU and for the main memory. The address bus passes addresses one way only: from the CPU to main memory</a>
        </li>
        <li>
          <a>Control bus: carries the necessary control signals, e.g. electricity, pulses, frequencies, etc., which are needed for the CPU to communicate with hardware components of the computer. The control bus is bidirectional for the CPU and main memory</a>
        </li>    
      </ul>    
    </li>
  </ul>      
</ul>    


## Non-von Nuemann Model
<ul>
  <li>
    <a>Improvements in computation power require some deviation from the conventional von Neumann model. These improvements primarily take place in the form of <em>parallel processing</em> which refers to a vast collection of different computer architectures such as the following:</a>
    <ul>
      <li>
        <a>Multiple computers working together on a task</a>
      </li>
      <li>
        <a>Multiple CPUs which share a single system memory</a>
      </li>
      <li>
        <a>Multiple cores on the same CPU</a>
      </li>
    </ul>        
  </li>
</ul>    
