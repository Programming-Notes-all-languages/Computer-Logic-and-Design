<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#positional-number-system'>Positional Number System</a>
  </li>
  <li>
    <a href='#converting-between-bases'>Converting Between Bases</a>
  </li>
  <li>
    <a href='#representing-signed-numbers-in-binary'>Representing Signed Numbers in Binary</a>
  </li>  
  <li>
    <a href='#arithmetic-in-positional-number-systems'>Arithmetic in Positional Number Systems</a>
  </li>  
</ol>
</details>

## Positional Number System
<ul>
  <li>
    <a>A <em>positional number system</em>, also known as a <em>weighted number system</em>, is where the weight of a digit depends on the digit's location within the number</a>
  </li>
  <li>
    <a>The <em>radix point</em> is used to differentiate the values that represent integers and values that represent fractions</a>
  </li> 
  <li>
    <a>The <em>radix</em> is the base of the number system</a> 
  </li>
  <li>
    <a>Number (with n integer digits and m fractional digits) = (digit<sub>n-1</sub> * radix<sup>n-1</sup>) + (DIGIT<sub>n-2</sub> * radix<sup>n-2</sup>) + ... + (DIGIT<sub>1</sub> * radix) + (DIGIT<sub>0</sub> * radix<sup>0</sup>) + (DIGIT<sub>-1</sub> * radix<sup>-1</sup>) + ... + (DIGIT<sub>-m</sub> * radix<sup>-m</sup>)</a>
  </li>  
  <li>
    <a>The set of allowed digits for a number system can be found with the following where r represents the system's radix: {0, 1, ..., r-1}</a>
  </li>
  <li>
    <a>The most significant digit is the leftmost digit with the highest weight</a>
  </li>
  <li>
    <a>The least significant digit is the rightmost digit with the lowest weight</a>
  </li>  
  <li>    
    <a>There are four very popular positional number systems:</a>
    <ul>
      <li>
        <a>Decimal number system</a>
        <ul>
          <li>
            <a>The radix for decimal numbers: r = 10</a>
          </li> 
          <li>
            <a>Ten possible digits for decimal numbers: zero, one, two, three, four, five, six, seven, eight, and nine</a>
          </li>
          <li>
            <a>The weight of position i: w<sub>i</sub> = 10<sup>i</sup></a>
          </li>    
        </ul>   
      </li>  
      <li>
        <a>Binary number system</a>
        <ul>
          <li>
            <a>Each binary digit is called a bit which can store two values: either 0 or 1</a>
          </li>
          <li>
            <a>The largest number of bits that a number system with n digits can have is 2<sup>n</sup> - 1</a>
          </li>  
          <li>
            <a>The least significant bit is the rightmost bit of the binary number</a>
          </li>  
          <li>
            <a>The most significant bit is the leftmost bit. In an eight-bit number, the bit representing 2<sup>7</sup> is the most significant bit. This bit may store 0 or 1; if the bit stores 0, then 0 is the most significant bit</a>
          </li>  
        </ul>  
      </li>  
      <li>
        <a>Octal number system</a>
        <ul>
          <li>
            <a>The radix for decimal numbers: r = 8</a>
          </li> 
          <li>
            <a>Ten possible digits for decimal numbers: zero, one, two, three, four, five, six, and seven</a>
          </li>
          <li>
            <a>The weight of position i: w<sub>i</sub> = 8<sup>i</sup></a>
          </li>    
        </ul>   
      </li>  
      <li>
        <a>Hexadecimal number system</a>
        <ul>
          <li>
            <a>The radix for decimal numbers: r = 16</a>
          </li> 
          <li>
            <a>Ten possible digits for decimal numbers: zero, one, two, three, four, five, six, seven, eight, nine, A, B, C, D, E, and F</a>
          </li>
          <li>
            <a>The weight of position i: w<sub>i</sub> = 16<sup>i</sup></a>
          </li>    
        </ul>   
      </li> 
    </ul>
  </li>     
</ul>    

## Converting Between Bases
<ul>
  <li>
    <a>Converting hexadecimal numbers to decimal numbers:</a>
    <details>
    <summary>Convert (D5)<sub>16</sub> to base 10</summary>
      <pre>
        <code>
          (D)<sub>16</sub> = (1101)<sub>2</sub><br />
          (5)<sub>5</sub> = (0101)<sub>2</sub><br />
          (D5)<sub>16</sub> = (11010101)<sub>2</sub><br />
          (11010101)<sub>2</sub> = 2<sup>7</sup> + 2<sup>6</sup> + 2<sup>4</sup> + 2<sup>2</sup> + 2<sup>0</sup> = (213)<sub>10</sub>
        </code>
      </pre>   
    </details>
    <details>
    <summary>Convert (AA)<sub>16</sub> to base 10</summary>
      <pre>
        <code>
          (A)<sub>16</sub> = (1010)<sub>2</sub><br />
          (AA)<sub>16</sub> = (10101010)<sub>2</sub><br />
          (10101010)<sub>2</sub> = 2<sup>7</sup> + 2<sup>5</sup> + 2<sup>3</sup> + 2<sup>1</sup> = (170)<sub>10</sub>
        </code>
      </pre>   
    </details>
  </li> 
  <li>
    <a>Converting decimal numbers to binary numbers (unsigned)</a>
    <details>
    <summary>Convert (76)<sub>10</sub> to base 2</summary>
      <pre>
        <code>
          (76)<sub>10</sub> = 2<sup>6</sup> + 2<sup>3</sup> + 2<sup>2</sup> = (1001100)<sub>2</sub>
        </code>
      </pre>   
    </details>   
  </li>    
  <li>
    <a>Converting octal numbers to decimal numbers (unsigned)</a>  
    <details>
    <summary>Convert (23)<sub>8</sub> to base 10</summary>
      <pre>
        <code>
          (2 * 8<sup>1</sup>) + (3 * 8<sup>0</sup>) = (19)<sub>10</sub>
        </code>
      </pre>   
    </details>
    <details>
    <summary>Convert (57)<sub>8</sub> to base 10</summary>
      <pre>
        <code>
          (5 * 8<sup>1</sup>) + (7 * 8<sup>0</sup>) = (47)<sub>10</sub>
        </code>
      </pre>   
    </details>
  </li>     
  <li>
    <a>Converting binary numbers to hexadecimal numbers (unsigned)</a>
    <details>
    <summary>Convert (10110)<sub>2</sub> to base 16</summary>
      <pre>
        <code>
          First 4 bits: (0001)<sub>2</sub> = (1)<sub>16</sub><br />
          Second 4 bits: (0110)<sub>2</sub> = (6)<sub>16</sub><br />
          (10110)<sub>2</sub> = (16)<sub>16</sub>
        </code>
      </pre>   
    </details>
  </li> 
  <li>
    <a>Converting binary numbers to decimal numbers(unsigned)</a>
    <details>
    <summary>Convert (10011101)<sub>2</sub> to base 10</summary>
      <pre>
        <code>
          2<sup>7</sup> + 2<sup>4</sup> + 2<sup>3</sup> + 2<sup>2</sup> + 2<sup>0</sup> = (157)<sub>10</sub>
        </code>
      </pre>   
    </details>
    <details>
    <summary>Convert (0.1011)<sub>2</sub> to base 10</summary>
      <pre>
        <code>
          2<sup>-1</sup> + 2<sup>-3</sup> + 2<sup>-4</sup> = (0.6875)<sub<10>10</sub>
        </code>
      </pre>   
    </details>
  </li>          
</ul>

## Representing Signed Numbers in Binary
<ul>
  <li>
    <a>There are several ways to represent a signed number in binary. Positive numbers are typically stored as their binary representation without much modification</a>
    <ul>
      <li>
        <a>Sign-magnitude</a>
        <ul>
          <li>
            <a>For signed-magnitude, the leftmost is the bit the denotes the sign of the number. If the leftmost bit is 0, then the number represented in binary is positive. If the leftmost bit is 1, then the number represented in binary is negative. All of the bits to the right of the highest order bit represent the number's magnitude</a>
          </li> 
          <details>
          <summary>Show how the numbers -45 and +45 are represented in eight-bit registers using signed-magnitude representation</summary>
            <pre>
              <code>
                (45)<sub>10</sub> = 2<sup>5</sup> + 2<sup<3></sup> + 2<sup>2</sup> + 2<sup>0</sup><br />
                Sign-magnitude representations for -45 and 45:<br />
                (-45)<sub>10</sub> = (10101101)<sub>2</sub><br />
                (45)<sub>10</sub> = (00101101)<sub>2</sub>
              </code>
            </pre>   
          </details> 
          <li>
            <a>There are two representations for zero in a four-bit register when using signed-magnitude representation: +0, (0000)<sub>2</sub>, and -0, (1000)<sub>2</sub></a> 
          </li>  
          <li>
            <a>For a n-bit register, the range of integers is the following: [-(2<sup>n-1</sup> - 1), +(2<sup>n-1</sup> - 1)]</a>
          </li>  
          <li>
            <a>It is difficult to implement addition and subtraction using signed-magnitude properties</a>
          </li> 
        </ul>    
      </li>
      <li>
        <a>1's complement</a>
        <ul>
          <li>
            <a>To do the 1's complement flip all of the bits in the binary number. Make every 0 a 1 and make every 1 a zero. This method is done because the complement of a number is simply the number's inverse. Do NOT change the sign bit when flipping each of the bits representing the magnitude of the number</a>
          </li>
          <details>
          <summary>Show how the numbers -14 and +14 are represented in eight-bit registers using signed-magnitude representation</summary>
            <pre>
              <code>
                (14)<sub>10</sub> = 2<sup>3</sup> + 2<sup>2</sup> + 2<sup>1</sup><br />
                Sign-magnitude representations for -14 and +14:<br />
                (14)<sub>10</sub> = (00001110)<sub>2</sub><br />
                (-14)<sub>10</sub> = (10001110)<sub>2</sub><br />
                1's complement representations for -14 and +14:<br />
                (14)<sub>10</sub> = (00001110)<sub>2</sub><br />
                (-14)<sub>10</sub> = (11110001)<sub>2</sub><br />
              </code>
            </pre>   
          </details> 
          <li>
            <a>There are two representations for zero in a four-bit register when using 1's complement representation: +0, (0000)<sub>2</sub>, and -0, (1111)<sub>2</sub></a> 
          </li>  
          <li>
            <a>For a n-bit register, the range of integers is the following: [-(2<sup>n-1</sup> - 1), +(2<sup>n-1</sup> - 1)]</a>
          </li> 
        </ul>    
      </li>
      <li>
        <a>2's complement</a>
        <ul>
          <li>
            <a>This representation is the most widely used as it has many advantages over signed-magnitude representation and the 1's complement representation</a>
          </li>
          <li>
            <a>To find the 2's complement, the number must be represented in binary. Then, we must find the 1's complement of that number without changing the sign bit. Lastly, one bit must be added to the right most bit</a>
          </li>
          <details>
          <summary>Show how the numbers -12 and 12 are represented in eight-bit registers using signed-magnitude, 1's complement, and 2's complement representations</summary>
            <pre>
              <code>
                (12)<sub>10</sub> = 2<sup>3</sup> + 2<sup>2</sup><br />
                Sign-magnitude representations for -12 and 12:<br />
                (-12)<sub>10</sub> = (10001100)<sub>2</sub><br />
                (12)<sub>10</sub> = (00001100)<sub>2</sub><br />
                1's complement representations for -12 and 12:<br />
                (-12)<sub>10</sub> = (11110011)<sub>2</sub><br />
                (12)<sub>10</sub> = (00001100)<sub>2</sub><br />
                2's complement representations for -12 and 12:<br />
                (-12)<sub>10</sub> = (11110100)<sub>2</sub><br />
                (12)<sub>10</sub> = (00001100)<sub>2</sub>
              </code>
            </pre>   
          </details>
          <details>
          <summary>Show how the numbers -53 and 53 are represented in eight-bit registers using signed-magnitude, 1's complement, and 2's complement representations</summary>
            <pre>
              <code>
                (53)<sub>10</sub> = 2<sup>5</sup> + 2<sup>4</sup> + 2<sup>2</sup> + 2<sup>0</sup><br />
                Sign-magnitude representations for 53 and -53:<br />
                (53)<sub>10</sub> = (00110101)<sub>2</sub></br />
                (-53)<sub>10</sub> = (10110101)<sub>2</sub></br />
                1's complement representations  for 53 and -53:<br />
                (53)<sub>10</sub> = (00110101)<sub>2</sub></br />
                (-53)<sub>10</sub> = (11001010)<sub>2</sub></br />
                2's complement representations for 53 and -53:<br />
                (53)<sub>10</sub> = (00110101)<sub>2</sub></br />
                (-53)<sub>10</sub> = (11001011)<sub>2</sub></br />
              </code>
            </pre>   
          </details>
          <li>
            <a>Since the 2's complement adds a single bit to the 1's complement, there is only one representation for zero, which is positive zero (0000)<sub>2</sub>. Instead, there is a representation for negative eight in a four-bit register
          <li>
            <a>There is only one representation for 0, which is +0 (0000)<sub>2</sub></a> 
          </li>
          <details>
          <summary>Given the eight-bit binary number, (10011101)<sub>2</sub>, what decimal number does this represent if the computer uses (a) signed-magnitude representation, (b) 1's complement representation, and (c) 2's complement representation</summary>
            <pre>
              <code>
                a) signed-magnitude representation of x is (10011101)<sub>2</sub><br />
                x = 2<sup>4</sup> + 2<sup>3</sup> + 2<sup>2</sup> + 2<sup>0</sup> = (-29)<sub>10</sub><br />
                b) 1's complement of x is (10011101)<sub>2</sub>:<br />
                taking complement of (10011101)<sub>2</sub> gives (11100010)<sub>2</sub> where sign bit is leftmost bit with the value of 1 (x is negative)<br />
                x = (11100010)<sub>2</sub> = (-1) * 2<sup>6</sup> + 2<sup>5</sup> + 2<sup>1</sup> = (-98)<sub>10</sub><br />
                c) 2's complement of x is (10011101)<sub>2</sub>:<br />
                (10011101)<sub>2</sub> minus one bit is (10011100)<sub>2</sub>. Then, taking the complement of (10011100)<sub>2</sub> gives (11100011)<sub>2</sub><br />
                x = (11100011)<sub>2</sub> = (-1) * 2<sup>6</sup> + 2<sup>5</sup> + 2<sup>1</sup> + 2<sup>0</sup> = (-99)<sub>10</sub><br /> 
              </code>
            </pre>   
          </details>   
        </ul>    
      </li>    
    </ul>    
  </li>
</ul>    

## Arithmetic in Positional Number Systems
<ul>
  <li>
    <a>Binary addition (unsigned):</a>
    <ul>
      <li>
        <a>Start with least significant bit (the rightmost bit)</a>
      </li>
      <li>
        <a>Add each pair of bits</a>
      </li>
      <li>
        <a>Include the carry in the addition, if present</a>
      </li> 
      <li>
        <a>With addition, there is a sum value and carry out value. The sum value is what goes under the equals line and the carry is if the summation of two digits results in overflow. The carry value is then written on top one digit to the left of where the sum was written</a>
      </li>
      <details>
      <summary>Add the unsigned binary numbers (00110110)<sub>2</sub> and (00011101)<sub>2</sub></summary>
        <pre>
          <code>

| | | | | | | | | | 
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| carry | | 1 | 1 | 1 | 1 |  |  |  |
| | 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 |
| + | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 |
| result: | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 

</code>
        </pre>   
      </details>
    </ul>  
  </li>
  <li>  
    <a>Binary subtraction (unsigned):</a>
    <ul>
      <li>
        <a>Start with least significant bit (rightmost bit)</a>
      </li>
      <li>
        <a>Subtract each pair of bits</a>
      </li>
      <li> 
        <a>Include the borrow in the subtraction, if present</a>
      </li>   
      <details>
      <summary>Subtract the unsigned binary numbers (00110110)<sub>2</sub> and (00011101)<sub>2</sub></summary>
        <pre>
          <code>

| | | | | | | | | | 
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| borrow | | | ~~0~~ | 10 ~~0~~ | 10 | | 0 | 10 |
| | 0 | 0 | ~~1~~ | ~~1~~ | ~~0~~ | 1 | ~~1~~ | 0 |
| - | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 |
| result: | 0** | 0 | 0 | 1 | 1 | 0 | 0 | 1 |

</code>
        </pre>   
      </details>
    </ul>  
  <li>
    <a>Hexadecimal Addition:</a>
    <ul>
      <li>
        <a>Start with least significant hexadecimal digits</a>
      </li>
      <li>
        <a>If summation of two hex digits is greater than or equal to 16, then sum is equal to sum minus 16 and carry is equal to one</a>
      </li>
      <details>
      <summary>Add (1C37286A)<sub>16</sub> and (9395E84B)<sub>16</sub></summary>
        <pre>
          <code>     

| | | | | | | | | | 
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| carry | | | | 1 | 1 | | 1 | |
| | 1 | C | 3 | 7 | 2 | 8 | 6 | A |
| + | 9 | 3 | 9 | 5 | E | 8 | 4 | B |
| result: | A | F | C | D | 1 | 0 | B | 5 |

</code>
        </pre>
      </details>
    </ul>    
  <li>
    <a>Hexadecimal Subtraction:</a> 
    <ul>
      <li>
        <a>Start with the least significant hexadecimal digit</a>
      </li>
      <li>
        <a>If difference between two hex digits is less than zero, then difference is equal to 16 plus the magnitude of the difference and one digit needs to be borrowed from digit one to the left of one currently being worked on</a>
      </li>
      <details>
      <summary>Subtract (1395E84B)<sub>16</sub> from (9C372865)<sub>16</sub></summary>
        <pre>
          <code>      

| | | | | | | | | | 
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| borrow | | B | 10 | 6 | 10 | | 5 | 10 |
| | 9 | ~~C~~ | 3 | ~~7~~ | 2 | 8 | ~~6~~ | 5 |
| - | 1 | 3 | 9 | 5 | E | 8 | 4 | B |
| result: | 8 | 8 | A | 1 | 4 | 0 | 1 | A |

</code>
        </pre>
      </details>  
    </ul>
  </li>
  </li>     
  <li>
    <a>Addition and subtraction using signed-magnitude arithmetic:</a>   
    <ul>
      <li>
        <a>Addition rules for adding signed-magnitude representations of integers:</a> 
        <ul>
          <li>
            <a>If the signs are the same for both representations, then add their magnitudes and use that same sign bit value for the sign bit of the result</a>
          </li>
          <li>
            <a>If the signs differ, then one must determine which representation's magnitude is greater. The sign bit of the result is the same as the sign of the operator with the larger magnitude. The magnitude must be obtained by subtracting the smaller one from the larger one</a>
          </li> 
          <details>
          <summary>Add (01001111)<sub>2</sub> to (00100011)<sub>2</sub> using signed-magnitude arithmetic</summary>
            <pre>
              <code>        

| | | | | | | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | sign bit | | | | 1 | 1 | 1 | 1 |  | |
| (79) | 0 |   | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| +(35) | 0 | + | 0 | 1 | 0 | 0 | 0 | 1 | 1 |
| (144) | 0 | | 1 | 1 | 1 | 0 | 0 | 1 | 0 |
(01110010)<sub>2</sub>

</code>
            </pre>
          </details> 
          <li>
            <a>If there is a carry on the seventh bit from the right in an eight-bit register, then there is an overflow condition and the carry is discarded. This then results in an incorrect sum</a>
          </li>  
          <li>
            <a>The sign bits are segregated in the addition because they are only relevant after the addition is performed</a>
          </li> 
          <details>
          <summary>Add (01001111)<sub>2</sub> to (01100011)<sub>2</sub> using signed-magnitude arithmetic</summary>
            <pre>
              <code>        

| | | | | | | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | sign bit 1 | | | | 1 | 1 | 1 | 1 | | |
| (79) | 0 |   | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| +(99) | 0 | + | 1 | 1 | 0 | 0 | 0 | 1 | 1 |
| (50) | 0 | | 0 | 1 | 1 | 0 | 0 | 1 | 0 |
(00110010)<sub>2</sub>

</code>
            </pre>
          </details>
          <details>
          <summary>Subtract (01001111)<sub>2</sub> to (01100011)<sub>2</sub> using signed-magnitude arithmetic</summary>
            <pre>
              <code>        

| | | | | | | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | sign bit | | | 0 | 1 ~~10~~ | 1 ~~10~~ | 10 | | | |
| (99) | 0 |   | 1 | ~~1~~ | 0 | 0 | 0 | 1 | 1 |
| -(79) | 0 | - | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| (20) | 0 | | 0 | 0 | 1 | 0 | 1 | 0 | 0 |
(00010100)<sub>2</sub>

</code>
            </pre>
          </details> 
          <details>
          <summary>Subtract (01100011)<sub>2</sub> from (01001111)<sub>2</sub>using signed-magnitude arithmetic</summary>
            <pre>
              <code>        

| | | | | | | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | sign bit | | | 0 | 1 ~~10~~ | 1 ~~10~~ | 10 | | | |
| (99) | 0 |   | 1 | ~~1~~ | 0 | 0 | 0 | 1 | 1 |
| -(79) | 0 | - | 1 | 0 | 0 | 1 | 1 | 1 | 1 |
| (-20) | 0 | | 0 | 0 | 1 | 0 | 1 | 0 | 0 |
Sign must be negative as 79 - 99 is less than zero<br />
(10010100)<sub>2</sub>

</code>
            </pre>
          </details>
          <details>
          <summary>Subtract (10011000)<sub>2</sub> from (10101011)<sub>2</sub>using signed-magnitude arithmetic</summary>
            <pre>
              <code>        

| | | | | | | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | sign bit | | | 0 | 10 | | | | |
| (43) | 0 | | 0 | ~~1~~ | 0 | 1 | 0 | 1 | 1 |
| -(24) | 0 | - | 0 | 0 | 1 | 1 | 0 | 0 | 0 |
| (-19) | 0 | | 0 | 0 | 1 | 0 | 0 | 1 | 1 |
Sign must be negative as 79 - 99 is less than zero<br />
(10010011)<sub>2</sub>

</code>
            </pre>
          </details>
          <details>
          <summary>Add (10010011)<sub>2</sub> to (00001101)<sub>2</sub>using signed-magnitude arithmetic</summary>
            <pre>
              <code>        

| | | | | | | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | sign bit | | | 0 | 1 ~~10~~ | 1 ~~10~~ | 10 | | |
| (-19) | 1 | | 0 | 0 | 1 | 0 | 0 | 1 | 1 |
| +(13) | 0 | + | 0 | 0 | 0 | 1 | 1 | 0 | 1 |
| (7) | 1 | | 0 | 0 | 0 | 0 | 1 | 1 | 1 |

</code>
            </pre>
          </details>
        </ul>  
      </li>
    </ul>     
  </li>  
</ul>   
