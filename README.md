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
  </li>
  <li>
    <a><em>Computer architecture</em> consists of the logical implementations of the computer's design, known as the computer's software</a>
  </li>
  <li>
    <a><em>Principle of Equivalence of Hardware and Software</em>: defines that any task that can be accomplished by software can be done using only hardware and vice versa</a>
  </li>
  <li>
    <a>The necessary components to build a computer system consist of the following components:</a>
    <ul>
      <li>
        <a>A <em>processor</em>, known as the central processing unit, is needed to understand and run programs</a>
      </li>
      <li>
        <a>A <em>memory</em> stores programs and information within the computer</a>
      </li>
      <li>
        <a>Mechanisms for <em>data input and output</em> which transfers information from the user, to the computer, and then to the user again</a>
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
    <a>For Moore's Law to hold, Rock's Law must no longer persist or vic versa</a>
  </li>  
</ul>  

## The Computer Level Hierarchy
![Untitled-Diagram95](https://github.com/Programming-Notes-all-languages/Computer-Organization/assets/154717520/72e6eade-2bbe-4098-85b7-21dd9e3b5279)
<ul>
  <li>
    <a>Level 6: The User Level</a>
    <ul>
      <li>
        <a>This level is composed of the applications that the user uses, such as Microsoft Word, video games, etc.</a>
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
        <a>This is the level that consists of high-level languages like C, C++, Python, etc</a>
      </li>
      <li>
        <a>These languages must then be translated into a language that the computer can understand. High-level languages are translated into assembly languages which makes machine code</a>
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
        <a>At this level, all high-level languages are translated into assembly languages</a>
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
        <a>This level also translates assembly languages into machine language</a>
      </li>
    </ul>
  </li>
  <li>
    <a>Level 2: Machine Level</a>
    <ul>
      <li>
        <a>This level is also known as the Instruction Set Architecture (ISA) Level</a>
      </li>
      <li>
        <a>This stage consists of the instructions that are particular to the computer's architecture. This means that these instructions are understandable to the computer's hardware</a>
      </li>
      <li>
        <a>These instructions are written in machine code which do not further need to be reduced to be understood by the computer's architecture</a>
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
        <a>This level contains the <em>control unit</em> which makes sure that the instructions given to the computer are executed properly and that data is moved to the correct places</a>
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
              <a>A microprogram is a program that is written in a low-level language that is executed by a computer's architecture</a>
            </li>
            <li>
              <a>The machine code that was translated in level two is fed into the microprogram</a>
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
        <a>This level consists of the gates and wires of the computer</a>
      </li>
    </ul>
  </li>                          
</ul>  

## Measures of Capacity and Processor Speed
<ul>
  <li>
    <a>Measures of capacity in decimal terms:</a>
    <ul>
      <li>
        <a>Kilobyte (KB): 10<sup>3</sup> bytes</a>
      </li>
      <li>
        <a>Megabyte (MB): 10<sup>6</sup> bytes<a>
      </li>
      <li>
        <a>Gigabyte (GB): 10<sup>9</sup> bytes</a>
      </li>  
      <li>
        <a>Terabyte (KB): 10<sup>12</sup> bytes</a>
      </li>
    </ul>
  </li>
  <li>
    <a>Measures of capacity in binary terms:</a>
    <ul>
      <li>
        <a>Kibibyte (KiB): 2<sup>10</sup> bytes</a>
      </li>
      <li>
        <a>Kibibyte (KiB): 2<sup>20</sup> bytes</a>
      </li>
      <li>
        <a>Gibibyte (GiB): 2<sup>30</sup> bytes</a>
      </li>
      <li>
        <a>Tebibyte (TiB): 2<sup>40</sup> bytes</a>
      </li>
    </ul>
  </li>
  <li>
    <a>Measures of processor speed:</a>
    <ul>
      <li>
        <a>Hertz = (clock cycles) / second --> this is also known as frequency</a>
      </li>
    </ul>
  </li>      
</ul>  

## The von Nuemann Model
<ul>
  <li>
    <a>The stored-program concept outlines that all stored-program computers have all of the following characteristics:</a>
    <ul>
      <li>
        <a>Consists of the three architecture systems:</a>
        <ul>
          <li>
            <a>A <em>central processing unit</em> containing a control unit, <em>arithmetic logic unit (ALU)</em>, and <em>registers</em></a>
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
        <a>There is lastly a single path between the control unit of the CPU and the main memory. This single path is called the <em>von Neumann bottleneck</em></a>
      </li>    
    </ul>
  </li>
  ![IMG_0710](https://github.com/Programming-Notes-all-languages/Computer-Organization/assets/154717520/b78893b2-73c5-4cf0-8756-41598f54318e)
  <li>
    <a>The process that represents how a computer's CPU executes instructions is defined as the <em>fetch-decode-execute cycle</em>. The following will explain how this process works</a>
    <ul>
      <li>
        <a>The beginning of this model is within the registers, specifically the program counter. The program counter is a special register that holds the data is the computer's next instruction</a>
      </li>
      <li>
        <a>The other registers may be holding values, such as int x or even float y</a>
      </li>
      <li>
        <a>The fetching happens when the computer takes the address of the next instruction and passes it through the arithmetic-logic unit. From there, the instruction is then sent to the control unit. The control unit then comes out of the CPU and then goes to the main memory. Within main memory, the computer is going to look for that address and if it is found, the information stored at that memory address will be pulled out. That information is then sent back to the control unit</a>
      </li>    
      <li>
        <a>The decoding then takes place after the fetching is complete. What information is now in the control unit is just a series of ones and zeros. The control unit will make sense of the instructions that it receives from the main memory. Afterward, this information is sent to the ALU</a>
      </li>
      <li>
        <a>Execute then takes place after the information is sent to the ALU. For example, if the information represented in bits really means to add two variables together, then the ALU will perform that summation. Afterward, the information can be passed to the input/output system if told so by the computer. Additionally, the new information could be sent back to the registers where some number of the registers are now updated with new information. Another possibility is that the information is sent back to the control unit where it gets sent to memory and the main memory is updated with the new information</a>
      </li>  
    </ul>  
  </li>  
  <li>
    <a>The von Neumann bottleneck occurs at each arrow within the model above--except for the bidirectional arrow connecting the ALU and the input/output system. The path from the ALU to the to the registers, the path from the registers to the ALU, the bidirectional path between the ALU and control unit, and lastly the bidirectional path between the control unit and the main memory are all subject to the bottleneck</a>
  </li>  
  <li>
    <a>System Bus Model</a>
  </li>
  <ul>
    <li>
      <a>There are three busses associated with the bus model:</a>
      <ul>
        <li>
          <a>Data bus: moves data between components on the motherboard. This bus is bidirectional with respect to the CPU, main memory, and input/output system</a>
        </li>
        <li>
          <a>Address bus: holds specific addresses from the main memory location and transports those addresses. It sends these addresses from the CPU to the memory and to the input/output system. The address bus is single-directional for the CPU, main memory, and input/output system</a>
        </li>
        <li>
          <a>Control bus: carries the necessary control signals, e.g. electricity, pulses, frequencies, etc., between the CPU, main memory, and input/output system. The control bus is bidirectional for the CPU, main memory, and input/output system</a>
        </li>    
      </ul>    
    </li>
  </ul>      
</ul>    

## Non-von Nuemann Model
<ul>
  <li>
    <a>Improvements in computation power require some deviation from the conventional von Nuemann model. These improvements primarily take place in the form of <em>parallel processing</em> which refers to a vast collection of different computer architectures such as the following:</a>
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
