<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#unsigned-number-representation'>Unsigned Number Representation</a>
  </li>
  <li>
    <a href='#signed-number-representation'>Signed Number Representation</a>
  </li>
  <li>
    <a href='#computer-level-hierarchy'>Computer Level Hierarchy</a>
  </li>
  <li>
    <a href='#von-neumann-model-and-non-von-neumann-models'>Von Neummann Model and Non-von Neumann Models</a>
  </li>
</ol>
</details>

## Unsigned Number Representation
Every number is a power of some constant value, called a <strong>radix</strong> or the <strong>base</strong>

### Popular Number Systems
<ul>
  <li><strong>Decimal</strong> number system: radix = 10
    <ul>
      <li>Ten digit values: 0, 1, 2 ..., 9</li>
    </ul>
  </li>
  <li><strong>Binary</strong> number system: radix = 2
    <ul>
      <li>Only two digit values: 0 and 1</li>
    </ul>
  </li>
  <li><strong>Octal</strong> number system: radix = 8
    <ul>
      <li>Eighth digit values: 0, 1, 2, ..., 7</li>
    </ul>
  </li>
  <li><strong>Hexadecimal</strong> number system: radix = 16
    <ul>
      <li>0, 1, 2, ...9, A, B, ..., F</li>
    </ul>
  </li>        
</ul>      

### Binary Numbers
Each binary digit is called a <strong>bit</strong> and is either 1 or 0

The <strong>most significant bit</strong> is the left-most bit and the <strong>least significant bit</strong> is the right-most bit

The range for unsigned binary representation that is $n$ bits longs is $0 <= 2$<sup>n - 1</sup>

<details>
    <summary>Example problem</summary>

Convert (10011101)<sub>2</sub> to decimal
<ul>  
  <details>
    <summary>Solution</summary>
(10011101)<sub>2</sub> = 2<sup>7</sup> + 2<sup>4</sup> + 2<sup>3</sup> + 2<sup>2</sup> + 2<sup>0</sup> = 157
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert (.1011)<sub>2</sub> to decimal
<ul>  
  <details>
    <summary>Solution</summary>
(10011101)<sub>2</sub> = 2<sup>-1</sup> + 2<sup>-3</sup> + 2<sup>3-4</sup> = 0.6875
</details>
</ul>  
</details>

### Octal and Hexadecimal Numbers
In octal, only digits 0 to 7 are used. Digits 8 and 9 are not used, meaning that one more digit than 7 is 10

In hexadecimal, there are 16 digits: the first digits ranging from 0 to 9 and the last digits ranging from A to F, where A = 10 and F = 15

<details>
    <summary>Example problem</summary>

Convert (10A4)<sub>16</sub> to binary
<ul>  
  <details>
    <summary>Solution</summary>
(10A4)<sub>2</sub> = (0001 0000 1010 0100)<sub>2</sub>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert (7526)<sub>8</sub> to binary
<ul>  
  <details>
    <summary>Solution</summary>
(7526)<sub>2</sub> = (111 101 010 110)<sub>2</sub>
</details>
</ul>  
</details>

### Number Conversion
<details>
    <summary>Example problem</summary>

Convert (37)<sub>10</sub> to binary
<ul>  
  <details>
    <summary>Solution</summary>
37<sub>10</sub> = (100101)<sub>2</sub>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert (359)<sub>10</sub> to octal
<ul>  
  <details>
    <summary>Solution</summary>
359 / 8 = 44 R 7
44 / 7 = 5 R 4
5 / 8 = 0 R 5<br />
(359)<sub>10</sub> = 547<sub>8</sub>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert (422)<sub>10</sub> to hexadecimal
<ul>  
  <details>
    <summary>Solution</summary>
422 / 16 = 26 R 6
26 / 16 = 1 R 10
1 / 16 = 0 R 1<br />
(422)<sub>10</sub> = 1A6<sub>16</sub>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert (139.6875)<sub>10</sub> to octal
<ul>  
  <details>
    <summary>Solution</summary>
139 / 8 = 17 R 3
17 / 8 = 2 R 1
2 / 8 = 0 R 2<br />
(0.6875)<sub>10</sub> = (.101 100)<sub>2</sub>
(.101 100)<sub>2</sub> = (.54)<sub>8</sub>
(213.54)<sub>8</sub>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert the unsigned hexadecimal fraction ($9CF.2A$)<sub>16</sub> to its decimal equivalent and round to four decimal places
<ul>  
  <details>
    <summary>Solution</summary>
9 x 16<sup>2</sup> + 12 x 16<sup>1</sup> + 15 x 16<sup>0</sup> + 2 x 16<sup>-1</sup> + 10 x 16<sup>-2</sup> = 2511.1641
</details>
</ul>  
</details>

#### Repeated Division Method
Divide the integer by the base of the new representation repeatedly until an integer value of zero is returned. Then, the representation of the new representation of that number is read from bottom to top in the list of remainders

#### Repeated Multiplication Method
Multiply the fractional part of the old representation by two repeatedly. The integer parts, either 0 or 1, are collected at each step. The integer parts are collected from top to bottom to form the binary representation

<details>
    <summary>Example problem</summary>

Convert the decimal fraction 0.3072425 to binary with a maximum of four places to the right of the radix point without rounding by using repeated multiplication method
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
0.3072425 x 2 = 0.614485
 - Integer part: 0     - Fraction part: 0.614485
0.614485 x 2 = 1.22897
 - Integer part: 1    - Fraction part: 0.22897
0.22897 x 2 = 0.45794
 - Integer part: 0    - Fraction part: 0.45794
0.45794 x 2 = 0.91588
 - Integer part: 0    - Fraction part: 0.91588
<br />Answer: 0.0100
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert the decimal integer 659 to binary by using repeated division method
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
659 / 2 = 329 R 1
329 / 2 = 164 R 1
164 / 2 = 82 R 0
82 / 2 = 41 R 0
41 / 2 = 20 R 1
20 / 2 = 10 R 0
10 / 2 = 5 R 0
5 / 2 = 2 R 1
2 / 2 = 1 R 0
1 / 2 = 0 R 1
<br />Answer: 1010010011
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert the binary fraction 11101001.110001 to decimal
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
2<sup>7</sup> + 2<sup>6</sup> + 2<sup>5</sup> + 2<sup>3</sup> + 2<sup>0</sup> + 2<sup>-1</sup> + 2<sup>-2</sup> + 2<sup>-6</sup> = 233.764625
</pre>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert the unsigned (E5DB.A3)<sub>16</sub> to octal
<ul>  
  <details>
    <summary>Solution</summary>

(E5DB.A3)<sub>16</sub> in BCD:
<ul>
  <li>E: (1110)</li>
  <li>5: (0101)</li>
  <li>D: (1101)</li>
  <li>B: (1011)</li>
  <li>A: (1010)</li>
  <li>3: (0011)</li>
</ul>
BCD: (1110 0101 1101 1011 . 1010 0011)<br />
Grouping the above in three-bit sections: (001 110 010 111 011 011 . 101 000 110)<br />
Answer: (162733.506)<sub>8</sub>
</details>
</ul>  
</details>

Convert the unsigned (11001)<sub>2</sub> to hexadecimal
<ul>  
  <details>
    <summary>Solution</summary>

(11001)<sub>2</sub> = (0001 1001)<sub>2</sub>
Answer: (19)<sub>16</sub>
</details>
</ul>  
</details>

## Signed Number Representation
There are several ways to represent a signed number:
<ul>
  <li>Sign-magnitude</li>
  <li>1's complement</li>
  <li>2's complement</li>
</ul>  

### Sign-Magnitude Representation
The leftmost bit is the sign bit: <strong>0 is positive</strong> and <strong>1 is negative</strong>

The largest magnitude bit is represented by the second, leftmost bit

Here is how to represent signed numbers on a four-bit register in signed-magnitude representation:
#### Negative Numbers' Representation on 4-bit Register
$\quad$ -0: (1000)<sub>2</sub><br />
$\quad$ -1: (1001)<sub>2</sub><br />
$\quad$ -2: (1010)<sub>2</sub><br />
$\quad$ -3: (1011)<sub>2</sub><br />
$\quad$ -4: (1100)<sub>2</sub><br />
$\quad$ -5: (1101)<sub>2</sub><br />
$\quad$ -6: (1110)<sub>2</sub><br />
$\quad$ -7: (1111)<sub>2</sub><br />

#### Positive Numbers' Representation on 4-bit Register
$\quad$ 0: (0000)<sub>2</sub><br />
$\quad$ 1: (0001)<sub>2</sub><br />
$\quad$ 2: (0010)<sub>2</sub><br />
$\quad$ 3: (0011)<sub>2</sub><br />
$\quad$ 4: (0100)<sub>2</sub><br />
$\quad$ 5: (0101)<sub>2</sub><br />
$\quad$ 6: (0110)<sub>2</sub><br />
$\quad$ 7: (0111)<sub>2</sub><br />

The  number range for n bits in sign-magnitude representation is $-(2$ <sup>n - 1</sup> $- 1)<= n <= 2$<sup>n - 1</sup> $- 1$</li>

<ul>
  <li>There are two representations for zero: +0 and -0</li>
  <li>There is a symmetric range of represented values from:
  
$-(2$<sup>
$n - 1$</sup> $- 1)<= n <= 2$<sup>
$n - 1$</sup> $- 1$</li>
  <li>It is hard to implement addition and subtraction when doing arithmetic using binary signed-magnitude representations</li>
</ul>  

### 1's Complement Representation
To take the 1's complement of a number in sign-magnitude representation, flip all the bits from 0 to 1 or from 1 to 0 without altering the sign bit

Here is how to represent signed numbers on a four-bit register using one's complement representation:
#### Negative Numbers' Representation on 4-bit Register
$\quad$ -0: (1111)<sub>2</sub><br />
$\quad$ -1: (1110)<sub>2</sub><br />
$\quad$ -2: (1101)<sub>2</sub><br />
$\quad$ -3: (1100)<sub>2</sub><br />
$\quad$ -4: (1011)<sub>2</sub><br />
$\quad$ -5: (1010)<sub>2</sub><br />
$\quad$ -6: (1001)<sub>2</sub><br />
$\quad$ -7: (1000)<sub>2</sub><br />

#### Positive Numbers' Representation on 4-bit Register
$\quad$ 0: (0000)<sub>2</sub><br />
$\quad$ 1: (0001)<sub>2</sub><br />
$\quad$ 2: (0010)<sub>2</sub><br />
$\quad$ 3: (0011)<sub>2</sub><br />
$\quad$ 4: (0100)<sub>2</sub><br />
$\quad$ 5: (0101)<sub>2</sub><br />
$\quad$ 6: (0110)<sub>2</sub><br />
$\quad$ 7: (0111)<sub>2</sub><br />

There is a symmetric range of represented values from:
  
$-(2$<sup>
$n - 1$</sup> $- 1)<= n <= 2$<sup>
$n - 1$</sup> $- 1$</li>

<details>
    <summary>Example problem</summary>

Show how the numbers -14 and +14 are represented in eight-bit registers using sign-magnitude representations and 1's complement representations
<ul>  
  <details>
    <summary>Solution</summary>

Sign-Magnitude Representation for -14: (10001110)<sub>2</sub><br />
Sign-Magnitude Representation for +14: (00001110)<sub>2</sub>

1's Complement Representation for -14: (11110001)<sub>2</sub><br />
1's complement Representation for +14: (00001110)<sub>2</sub>
</details>
</ul>  
</details>

### 2's Complement Representation
To take the 2's complement, the 1's complement of a number represented in sign-magnitude representation. Finally, add a single bit to the 1's complement representation of the number

Here is how to represent signed numbers on a four-bit register using two's complement representation:
#### Negative Numbers' Representation on 4-bit Register
$\quad$ -1: (1111)<sub>2</sub><br />
$\quad$ -2: (1110)<sub>2</sub><br />
$\quad$ -3: (1101)<sub>2</sub><br />
$\quad$ -4: (1100)<sub>2</sub><br />
$\quad$ -5: (1011)<sub>2</sub><br />
$\quad$ -6: (1010)<sub>2</sub><br />
$\quad$ -7: (1001)<sub>2</sub><br />
$\quad$ -8: (1000)<sub>2</sub><br />

#### Positive Numbers' Representation on 4-bit Register
$\quad$ 0: (0000)<sub>2</sub><br />
$\quad$ 1: (0001)<sub>2</sub><br />
$\quad$ 2: (0010)<sub>2</sub><br />
$\quad$ 3: (0011)<sub>2</sub><br />
$\quad$ 4: (0100)<sub>2</sub><br />
$\quad$ 5: (0101)<sub>2</sub><br />
$\quad$ 6: (0110)<sub>2</sub><br />
$\quad$ 7: (0111)<sub>2</sub><br />

There is a symmetric range of represented values from:
  
$-2$<sup>
$n - 1$</sup> $ <= n <= 2$<sup>
$n - 1$</sup> $- 1$</li>

<details>
    <summary>Example problem</summary>

Show how the numbers +53 and -53 are represented in eight-bit registers using sign-magnitude representations, 1's complement representations, and 2's complement representations
<ul>  
  <details>
    <summary>Solution</summary>

Sign-Magnitude Representation for -53: (10110101)<sub>2</sub><br />
Sign-Magnitude Representation for +53: (00110101)<sub>2</sub>

1's Complement Representation for -53: (11001010)<sub>2</sub><br />
1's complement Representation for +53: (00110101)<sub>2</sub>

2's Complement Representation for -53: (11001011)<sub>2</sub><br />
2's Complement Representation for +53: (00110101)<sub>2</sub>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given the 8-bit binary number: 1011 1100. What decimal does this represent if the computer uses:
<ol>
  <li>Sign-magnitude representation</li>
  <li>1's complement representation</li>
  <li>2's complement representation</li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol>
  <li>Sign-magnitude representation: 2<sup>5</sup> + 2<sup>4</sup> + 2<sup>3</sup> + 2<sup>2</sup> = -60</li>
  <li>1's complement representation:
  sign-magnitude representation: (1100 0011)<sub>2</sub> = (-67)<sub>10</sub></li>
  <li>2's complement representation:</li>
  <li>2's complement representation: 
  <pre>
           <s>1</s>1
           11
    1011 1<s>1</s>00
  -         1
  -----------
    1011 1011
  </pre>
  1's complement representation: (1011 1011)<sub>2</sub><br />
  Sign-magnitude representation: (1100 0100)<sub>2</sub> = (-68)<sub>10</sub></li>
</ol>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Represent decimal 155:
<ol type="a">
  <li>Sign-magnitude representation</li>
  <li>1's complement representation</li>
  <li>2's complement representation</li>
  <li>Unsigned 8-bit binary representation</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>Sign-magnitude: 010011011</li>
  <li>1's complement: 010011011</li>
  <li>2's complement: 010011011</li>
  <li>Unsigned 8-bit: 10011011</li>
</ol>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

The sign-extend of 8-bits binary number 0101 1101 to 16 bits is 
<ul>  
  <details>
    <summary>Solution</summary>

0000 0000 0101 1101
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

The sign-extend of 8-bits binary number 1100 1001 to 16 bits is 
<ul>  
  <details>
    <summary>Solution</summary>

1111 1111 1100 1001
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given the 8-bit binary number: 1100 1011<br />
Convert this 8-bit binary number to its decimal equivalent value if this binary number is in unsigned, sign-magnitude, 1's complement, and 2's complement format
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>Unsigned: 203</li>
  <li>Sign-magnitude: -75</li>
  <li>1's complement:<br />
  1100 1011<br />
  Undo 1's complement: 1011 0100 -->52</li>
  <li>2's complement:
<pre>
  11001011
 -       1
 ---------
  11001010
</pre>  
1's complement: 11001010<br />
Undo 1's complement: 1011 0101 --> -53</li>
</ol>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Represent decimal -207 in 8 bits:
<ol type="a">
  <li>Sign-magnitude representation</li>
  <li>1's complement representation</li>
  <li>2's complement representation</li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>Sign-magnitude: 1100 1111</li>
  <li>1's complement: 1011 0000</li>
  <li>2's complement:<br />
<pre>
  10110000
 +       1
 ---------
  10110001
</pre>  
  </li>
</ol>  
</details>
</ul>  
</details>

## Binary Arithmetic Operations
<details>
    <summary>Example problem</summary>

Add $1C37286A$ to $9395E84B$
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
      11 1
   1C37286A
 + 9395E84B
 ----------
   AFCD10B5
</pre>  
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Subtract $1395E84B$ from $9C372865$
<ul>  
  <details>
    <summary>Solution</summary>

<pre>
     +-->16+3
     | +-->16+2
    Bx6x 5x-->16+5
   9<s>C</s><s>3</s><s>7</s><s>2</s>8<s>6</s><s>5</s>
 - 1395E84B
 ----------
   88A1401A<sub>16</sub>
</pre>  
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Represent decimal 115 in sign-magnitude representation, one's complement representation, and two's complement representation, and unsigned 8-bit binary
<ul>  
  <details>
    <summary>Solution</summary>

<ol>
  <li>(0111 0011)<sub>2</sub></li>
  <li>(0111 0011)<sub>2</sub></li>
  <li>(0111 0011)<sub>2</sub></li>
  <li>(0111 0011)<sub>2</sub></li>
</ol>  
</details> 
</ul>  
</details>

### Carry and Overflow
Carry is important when adding and subtracting unsigned integers and indicates that the unsigned sum is out of range

Overflow is important when adding and subtracting signed integers. Indicates that the signed sum is out of range. Overflow occurs when:
<ul>
  <li>Adding two positive numbers and the sum is negative</li>
  <li>Adding two negative numbers and the sum is positive</li>
  <li>Can happen because of the fixed number of sum bits</li>
</ul>  

Overflow occurs when carry in sign does not equal carry out sign:

<details>
    <summary>Example problem</summary>

Add 01001111<sub>2</sub> to 01100011<sub>2</sub> using 8-bit signed-magnitude arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
  1   0 1111
  0   1001111
  0 + 1100011
  -----------
  0   0110010   
  carry in does not equal carry out; therefore, erroneous answer
</pre>
</details> 
</ul>  
</details>

### Sign-Magnitude Arithmetic
When adding or subtracting two binary numbers that are represented in sign-magnitude representation, the sign bit of the resultant matches the sign bit of the number which is larger in magnitude. If adding -2 and 1, the sign bit of the result is 1 since the magnitude of 2 is greater than the magnitude of 1

If the signs are the same for both numbers in signed-magnitude representations, then add their magnitudes and use that same sign bit value for the sign bit of the result

If the signs differ, then one must determine which representation's magnitude is greater. The sign bit of the result is the same as the sign of the operator with the larger magnitude. The magnitude must be obtained by subtracting the smaller from the larger one

<details>
    <summary>Example problem</summary>

Add 01001111<sub>2</sub> to 01100011<sub>2</sub> using 8-bit sign-magnitude arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
  1   0 1111
  0   1001111
  0 + 1100011
  -----------
  1   0110010   
</pre>
There is overflow since the carry in bit does not equal the carry out bit. The summation of two positive integers should not result in a negative integer; therefore, the result is erroneous
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add -57<sub>10</sub> to 38<sub>10</sub> using 8-bit sign-magnitude arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
-57 in signed-magnitude representation is: (1011 1001)<sub>2</sub><br /><br />
38 in signed-magnitude representation is: (0010 0110)<sub>2</sub>
<pre>
          <s>1</s>1
          11
  1   011<s>1</s>001
  0 - 0100110
  -----------
  1   0010011
</pre>
The answer is -19<sub>10</sub> which is valid
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Subtract 10011000<sub>2</sub> from 10101011<sub>2</sub> using 8-bit sign-magnitude arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
<pre>
       1
       1
    10<s>1</s>01011
  - 10011000
  -----------
     0010011 
</pre>
We know that the answer must be negative since subtracting -23 from -43 is the same as -43 being added to 23, which is negative; therefore, the sign bit should be 1: 10010011<sub>2</sub>
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add 103<sub>10</sub> to -87<sub>10</sub> using 8-bit sign-magnitude arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
107<sub>10</sub> = (0110 1011)<sub>2</sub> in signed-magnitude representation<br /><br />
87<sub>10</sub> = (0101 0111)<sub>2</sub> in signed-magnitude representation
<pre>
       1 1
       1 1
  0  1<s>1</s>0<s>1</s>011
  0 -1010111
  ----------
  0  0010100 
</pre>
The answer is 00010100<sub>2</sub> which is 20<sub>10</sub> and is valid
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add -127<sub>10</sub> to 50<sub>10</sub> using 8-bit sign-magnitude arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
-127<sub>10</sub> = (1111 1111)<sub>2</sub> in signed-magnitude representation<br /><br />
50<sub>10</sub> = (0011 0010)<sub>2</sub> in signed-magnitude representation
<pre>
  1  1111111
  0 -0110010
  ----------
  1  1001101 
</pre>
The answer is 11001101<sub>2</sub> which is -77<sub>10</sub> and is valid
</details> 
</ul>  
</details>

### One's Complement Arithmetic
Unlike in signed magnitude, in one's complement addition there is no need to maintain the sign bit separate from the other bits. The sign takes care of itself

Using 1's complement arithmetic, a <strong>end-around carry</strong> bit can be generated. If a carry is generated at the most significant end of the two numbers, then this carry must be added to the digit at the least significant end of the result

<details>
    <summary>Example problem</summary>

Add these two numbers in sign-magnitude representation, 23<sub>10</sub> and -9<sub>10</sub>, using 8-bit one's complement arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
23<sub>10</sub> = 0001 0111<sub>2</sub> in one's complement
-9<sub>10</sub> = 1000 1001<sub>2</sub> = 1111 0110 in one's complement
<pre>
  1 111 11
    00010111
  + 11110110
  -----------
    00001101 
  +        1
  ----------
    00001110         
</pre>
The answer is 14<sub>10</sub> and the answer is valid
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add these two numbers in sign-magnitude representation, -117<sub>10</sub> and 51<sub>10</sub>, using 8-bit one's complement arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
-117<sub>10</sub> = 1111 0101<sub>2</sub> = 1000 1010<sub>2</sub> in one's complement
51<sub>10</sub> = 0011 0011<sub>2</sub> in one's complement
<pre>
         1
    10001010
  + 00110011
  -----------
    10111101   
</pre>
The answer is -66<sub>10</sub> and the answer is valid
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add these two numbers in sign-magnitude representation, 11010101<sub>2</sub> and 01101101<sub>2</sub>, using 8-bit one's complement arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
11010101<sub>2</sub> = -85<sub>10</sub>. In one's complement representation, this is 10101010<sub>2</sub>
01101101<sub>2</sub> = 109<sub>10</sub>
<pre>
  1 11 1
    10101010
  + 01101101
  -----------
    00010111
  +        1
  ----------
    00011000
</pre>
The answer is 24<sub>10</sub> and the answer is valid
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add these two numbers in sign-magnitude representation, 10111001<sub>2</sub> and 10010110<sub>2</sub>, using 8-bit one's complement arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
10111001<sub>2</sub> = -57<sub>10</sub>. In one's complement representation, this is 11000110<sub>2</sub>
10010110<sub>2</sub> = -22<sub>10</sub>. In one's complement representation, this is 11101001<sub>2</sub>
<pre>
  1 1
    11000110
  + 11101001
  -----------
    10101111
  +        1
  ----------
    10110000
</pre>
The answer is 11001111<sub>2</sub> and in decimal the answer is -79<sub>10</sub>. The answer is valid
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add these two numbers in sign-magnitude representation, 11011001<sub>2</sub> and 11011001<sub>2</sub>, using 8-bit one's complement arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
11011001<sub>2</sub> = -89<sub>10</sub>. In one's complement representation, this is 10100110<sub>2</sub>
11011001<sub>2</sub> = -89<sub>10</sub>. In one's complement representation, this is 10100110<sub>2</sub>
<pre> 
  1  1  11
    10100110
  + 10100110
  -----------
    01001100
  +        1
  ----------
    01001101
</pre>
The answer is 01001101<sub>2</sub> and in decimal the answer is 77<sub>10</sub>. The answer is erroneous because the sum of two negative numbers cannot be positive. Overflow occurred because the sum of -89 and -89 cannot accurately be represented in an 8-bit register.
</details> 
</ul>  
</details>

### Two's Complement Arithmetic
Unlike with one's complement arithmetic, the carry out is discarded rather than adding the carry out bit to the least significant bit

<details>
    <summary>Example problem</summary>

Add these two numbers in decimal, -44<sub>10</sub> to -99<sub>10</sub>, using 8-bit two's complement arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
-99<sub>10</sub> = (1110 0011)<sub>2</sub> in signed-magnitude representation<br />
(1110 0011)<sub>2</sub> is equal to (1001 1100)<sub>2</sub> in one's complement representation and is equal to (1001 1101)<sub>2</sub> in two's complement representation<br /><br />
-40<sub>10</sub> = (1010 1000)<sub>2</sub> in signed-magnitude representation<br />
(1010 1000)<sub>2</sub> is equal to (1101 0111)<sub>2</sub> in one's complement representation and is equal to (1101 1000)<sub>2</sub> in two's complement representation
<pre> 
 1 0 11
   10011101
 + 11011000
 ----------
   01110101<sub>2</sub>
</pre>
Overflow occurs since the carry in bit is 0 and the carry out bit is 1. Since they are different, the answer is therefore erroneous
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Add these two numbers in decimal, -120<sub>10</sub> and 50<sub>10</sub>, using 8-bit two's complement arithmetic
<ul>  
  <details>
    <summary>Solution</summary>
-120<sub>10</sub> = (1111 1000)<sub>2</sub> in signed-magnitude representation<br />
(1111 1000)<sub>2</sub> in one's complement representation is (1000 0111)<sub>2</sub> which is equal to (1000 1000)<sub>2</sub> in two's complement representation<br /><br />
50<sub>10</sub> = (0011 0010)<sub>2</sub> in two's complement representation
<pre> 
 0 0
   10001000
 + 00110010
 ----------
   10111010<sub>2</sub>
</pre>
(1011 1010)<sub>2</sub> in one's complement representation is (1011 1001)<sub>2</sub> which in signed-magnitude representation is (1100 0110)<sub>2</sub>. This in decimal is -70<sub>10</sub>. There is no overflow since the carry in bit equals the carry out bit; therefore, the answer is valid
</details> 
</ul>  
</details>

### Binary Multiplication and Division
Binary multiplication and division by two can be done easily using an arithmetic shift operation

A <strong>left arithmetic shift</strong> inserts a 0 in for the rightmost bit and shifts everything else left one bit; in effect, it multiplies the number by two

A <strong>right arithmetic shift</strong> shifts everything one bit to the right, but copies the sign bit; in effect, it divides the number by two

<details>
    <summary>Example problem</summary>

Multiply the value 11 expressed using 8-bit signed 2's complement representation by two
<ul>  
  <details>
    <summary>Solution</summary>

Sign-magnitude representation: (0000 1011)<sub>2</sub><br />
1's complement representation: (0000 1011)<sub>2</sub><br />
2's complement representation: (0000 1011)<sub>2</sub><br />
Answer: (0001 0110)<sub>2</sub><br />
The sign bit has not changed; therefore, overflow has not occurred, so the result is value
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Multiply the value 66 expressed using 8-bit signed 2's complement representation by two
<ul>  
  <details>
    <summary>Solution</summary>

Sign-magnitude representation: (0100 0010)<sub>2</sub><br />
1's complement representation: (0100 0010)<sub>2</sub><br />
2's complement representation: (0100 0010)<sub>2</sub><br />
Answer: (1000 0100)<sub>2</sub><br />
The sign bit has changed; therefore, overflow has not occurred, so the result is value
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Divide the value 12 expressed using 8-bit signed 2's complement representation by two
<ul>  
  <details>
    <summary>Solution</summary>

Sign-magnitude representation: (0000 1100)<sub>2</sub><br />
1's complement representation: (0000 1100)<sub>2</sub><br />
2's complement representation: (0000 1100)<sub>2</sub><br />
Answer: (0000 0110)<sub>2</sub><br />
The sign bit has changed; therefore, overflow has not occurred, so the result is value
</details> 
</ul>  
</details>

## Character Codes
### Binary Coded Decimal (BCD)
Binary coded decimal encodes each digit of a decimal number into a 4-bit binary form. For example, the decimal digits of 146 are encoded to 0001, 0100, and 0110 respectively

<details>
    <summary>Example problem</summary>

Convert (95)<sub>10</sub> into its binary equivalent value and give its binary coded decimal value as well
<ul>  
  <details>
    <summary>Solution</summary>

Binary value: (0101 1111)<sub>2</sub>
Binary coded decimal value: (1001 0101) 
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Convert the binary coded decimal value 1001 0100 0111 0000 to decimal
<ul>  
  <details>
    <summary>Solution</summary>

Decimal value: (9470)<sub>10</sub>
</details> 
</ul>  
</details>

### Extended Binary-Coded Decimal Interchange Code (EBCDIC)
In recent years, BCD was extended to an 8-bit code, called EBCDIC, which was one of the first widely-used computer codes that support upper and lowercase alphabetic characters, in addition to special characters

### ASCII
ASCII is the dominant character code in the United States

The first bit in an ASCII code is the high-order bit for parity and then the rest of the seven bits are for character codes

The parity bit is either turned "on" or "off" depending on whether the sum of the other bits in the byte is even or odd
<ul>
  <li>"A": lower 7 bits is 1000001. The parity bit is 0: 01000001</li>
  <li>"C": lower 7 bits is 1000011. The parity bit is 1: 11000011</li>
</ul>

### Unicode
Both EBDIC and ASCII were built around the Latin alphabet and cannot provide data representation for the non-Latin alphabets

Many of today's systems embrace Unicode, a 16-bit system that can encode the characters of every language in the world

### Parity Bit & Error Detection Codes
The <strong>parity bit</strong> is used to make the number of 1's odd or even

<strong>Even parity</strong> is where the number of 1's in the transmitted data is even

<strong>Odd parity</strong> is where number of 1's in the transmitted data is odd

<details>
    <summary>Example problem</summary>

Assign the proper even parity bit to the binary code 101101011111
<ul>  
  <details>
    <summary>Solution</summary>

1101101011111
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

An odd parity system receives the following groups: 10110, 11010, 110011, 110101110100, and 1100010101010. Determine which groups, if any, are in error
<ul>  
  <details>
    <summary>Solution</summary>

110011 and 1100010101010 because there is an even number of 1's in each of these code groups
</details> 
</ul>  
</details>
