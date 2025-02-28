<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#boolean-function-representation'>Boolean Function Representation</a>
  </li>
  <li>
    <a href='#logic-gates-and-digital-components'>Logic Gates and Digital Components</a>
  </li>
  <li>
    <a href='#combinational-circuits'>Combinational Circuits</a>
  </li>
  <li>
    <a href='#sequential-circuits'>Sequential Circuits</a>
  </li>
</ol>
</details>

## Boolean Function Representation
There are many ways to represent a given boolean function
<ul>
  <li>Truth table</li>
  <li>Boolean expressions
    <ul>
      <li>The <strong>sum-of-products form</strong> is where ANDed variables are ORed together, e.g., $F(x, y, z) = xy + yz + xz$</li>
      <li>The <strong>sum-of-products form</strong> is where ORed variables are ANDed together: $F(x, y, z) = (x + y)(y + z)(x + z)</li>
    </ul>
  </li>
  <li>Two boolean expression that can be represented by the same truth table are considered <strong>logically equivalent</strong></li>
</ul>

<h2 style="text-align:center;">Boolean Algebra Laws</h2>
<table>
        <tr>
            <th>#</th>
            <th>Law Name</th>
            <th>Expression</th>
        </tr>
        <tr>
            <td>1</td>
            <td>Identity Law</td>
            <td>A + 0 = A, A · 1 = A</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Null (Domination) Law</td>
            <td>A + 1 = 1, A · 0 = 0</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Idempotent Law</td>
            <td>A + A = A, A · A = A</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Complement Law</td>
            <td>A + A' = 1, A · A' = 0</td>
        </tr>
        <tr>
            <td>5</td>
            <td>Double Negation</td>
            <td>(A')' = A</td>
        </tr>
        <tr>
            <td>6</td>
            <td>Commutative Law</td>
            <td>A + B = B + A, A · B = B · A</td>
        </tr>
        <tr>
            <td>7</td>
            <td>Associative Law</td>
            <td>(A + B) + C = A + (B + C), (A · B) · C = A · (B · C)</td>
        </tr>
        <tr>
            <td>8</td>
            <td>Distributive Law</td>
            <td>A · (B + C) = A · B + A · C</td>
        </tr>
        <tr>
            <td>9</td>
            <td>Absorption Law</td>
            <td>A + (A · B) = A, A · (A + B) = A</td>
        </tr>
        <tr>
            <td>10</td>
            <td>De Morgan's Theorems</td>
            <td>(A · B)' = A' + B', (A + B)' = A' · B'</td>
        </tr>
        <tr>
            <td>11</td>
            <td>Redundancy (Consensus) Law</td>
            <td>A · B + A' · C + B · C = A · B + A' · C</td>
        </tr>
        <tr>
            <td>12</td>
            <td>Absorption (Simplified)</td>
            <td>A + A · B = A</td>
        </tr>
    </table>

<details>
    <summary>Example problem</summary>

Simplify $B1 + (((AD)' + D'C)A)'$
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 11A.png" alt="Problem 11A">
</details> 
</ul>  
</details>

In order to eliminate confusion, designers express boolean functions in <strong>canonical</strong> form:
<ul>
  <li><strong>Canonical sum-of-product form</strong> is the sum of minterms $(\sum m)$</li>
  <li><strong>Canonical product-of-sum form</strong> is the produce of maxterms $(\Pi m)$</li>
</ul>

<details>
    <summary>Example problem</summary>

Write the boolean expression in canonical sum-of-product form and canonical product-of-sum form for the following boolean functions by not creating truth tables:
<ol>
  <li>
  
  $f(a, b, c, d) = ab' + bc'd + acd$</li>
  <li>

  $f(a, b, c, d) = (a' + b)(b + c' + d)(a + d')$</li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol>

  <li>
  
  $f(a, b, c, d) = ab' + bc'd + acd$<br />
  
  Sum-of-product form: <br />
  $f(a, b, c, d) = ab'(c + c')(d + d') + bc'd(a + a') + acd(b + b')$<br />

  $f(a, b, c, d) = ab'cd + ab'cd' + ab'c'd + ab'c'd' + abc'd + a'bc'd + abcd$<br />

  $\sum m(5, 8, 9, 10, 11, 13, 15)$<br />
  <br />Product-of-sum form:<br />
  
  $\Pi M(0, 1, 2, 3, 4, 6, 7, 12, 14)$<br />
  $f(a, b, c, d) = (a + b + c + d)(a + b + c + d')(a + b + c' + d)(a + b + c' + d')(a + b' + c + d)(a + b' + c' + d)(a + b' + c' + d')(a' + b' + c + d)(a' + b' + c' + d)$</li>
  <li>

  $f(a, b, c, d) = (a' + b)(b + c' + d)(a + d')$<br />

  Sum-of-product form:<br />

  $f(a, b, c, d) = a'bc'd' + a'bcd' + a'b'c'd' + abc'd' + abc'd + abcd' + abcd$<br />

  $\sum m(0, 4, 6, 12, 13, 14, 15)$<br />

  Product-of-sum form:<br />

  $f(a, b, c, d) = (a' + b + c' + d')(a' + b + c' + d)(a' + b + c + d')(a' + b + c + d)(a + b + c' + d)(a + b' + c' + d')(a + b' + c + d')(a + b + c' + d')(a + b + c + d')$<br />

  $\Pi M(1, 2, 3, 5, 7, 8, 9, 10, 11)$</li>

  <img src="Images/Example Problems/Problem 10A.png" alt="Problem 10A">
</ol>   
</details> 
</ul>  
</details>

<strong>Minterm</strong> is a logical product of all the literals, each literal may be or without the bar. The output result of the minterm function is 1

<strong>Maxterm</strong> is a logical sum of all the literals, each literal may be with or without the bar. The output result of maxterm function is 0

<details>
    <summary>Example problem</summary>

Write the minterm and maxterm for a function $F(x, y, z)$ when $x = 0, y = 1,$ and $z = 0$
<ul>  
  <details>
    <summary>Solution</summary>

Minterm: $x'yz'$<br />
Maxterm: $x + y' + z$
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Write the boolean expression in canonical sum-of-product form and canonical product-of-sum form for the following:
$\sum m(1, 2, 5, 6)$
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 9A.png" alt="Problem 9A">
</details> 
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Simplify the following function and show its truth table values:

<div align="center">

$F$ $($ $x$ $,$ $y$ $,$ $z$ $)$ $=$ $x$ $'$ $y$ $z$ $'$ $+$ $x$ $'$ $y$ $z$ $+$ $x$ $y$ $'$ $z$ $'$ $+$ $x$ $y$ $z$ $'$ $+$ $x$ $y$ $z$ $=$ $\sum$ $m$ $($ $2$ $,$ $3$ $,$ $4$ $,$ $6$ $,$ $7$ $)$</div>
<ul>  
  <details>
    <summary>Solution</summary>

$F(x, y, z) = x'y(z' + z) + x(y'z' + yz' + yz)$<br />
$F(x, y, z) = x'y + x(z'(y' + y) + yz)$<br />
$F(x, y, z) = x'y + x(z' + yz)$<br />
$F(x, y, z) = x'y + xz' + xyz$<br />
$F(x, y, z) = y(x' + xz) + xz'$<br />
$F(x, y, z) = y(x' + z) + xz'$<br />
$F(x, y, z) = x'y + yz + xz'$<br /><br />

<table border="1">
  <tr>
    <th>$x$</th>
    <th>$y$</th>
    <th>$z$</th>
    <th>$F(x, y, z) = x'y + yz + xz'$</th>
  </tr>
  <tr>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td>1</td>
    <td>0</td>
    <td>1</td>
  </tr>
  <tr>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
  </tr>
  <tr>
    <td>1</td>
    <td>0</td>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>1</td>
  </tr>
  <tr>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
  </tr>
</table>
The maxterm representation of the function is the following: $F(x, y, z) = (x + y + z)(x + y + z')(x' + y + z') = \Pi(0, 1, 5)$
</details> 
</ul>  
</details>

## Logic Gates and Digital Components
A logic gate implements a simple boolean operation where a collection of gates form an integrated circuit

<table>
    <thead>
        <tr>
            <th>Gate</th>
            <th>Symbol</th>
            <th>Truth Table</th>
        </tr>
    </thead>
    <tbody>
        <!-- AND Gate -->
        <tr>
            <td>AND</td>
            <td><img src="Images/Logic Gates/AND.png" alt="AND Gate Symbol" width="120" height="60"></td>
            <td>
                <table>
                    <tr><td>0</td><td>0</td><td>0</td></tr>
                    <tr><td>0</td><td>1</td><td>0</td></tr>
                    <tr><td>1</td><td>0</td><td>0</td></tr>
                    <tr><td>1</td><td>1</td><td>1</td></tr>
                </table>
            </td>
        </tr>
        <!-- OR Gate -->
        <tr>
            <td>OR</td>
            <td><img src="Images/Logic Gates/OR.png" alt="OR Gate Symbol" width="120" height="60"></td>
            <td>
                <table>
                    <tr><td>0</td><td>0</td><td>0</td></tr>
                    <tr><td>0</td><td>1</td><td>1</td></tr>
                    <tr><td>1</td><td>0</td><td>1</td></tr>
                    <tr><td>1</td><td>1</td><td>1</td></tr>
                </table>
            </td>
        </tr>
        <!-- NOT Gate -->
        <tr>
            <td>NOT</td>
            <td><img src="Images/Logic Gates/NOT.png" alt="NOT Gate Symbol" width="120" height="60"></td>
            <td>
                <table>
                    <tr><td>0</td><td>1</td></tr>
                    <tr><td>1</td><td>0</td></tr>
                </table>
            </td>
        </tr>
        <!-- NAND Gate -->
        <tr>
            <td>NAND</td>
            <td><img src="Images/Logic Gates/NAND.png" alt="NAND Gate Symbol" width="120" height="60"></td>
            <td>
                <table>
                    <tr><td>0</td><td>0</td><td>1</td></tr>
                    <tr><td>0</td><td>1</td><td>1</td></tr>
                    <tr><td>1</td><td>0</td><td>1</td></tr>
                    <tr><td>1</td><td>1</td><td>0</td></tr>
                </table>
            </td>
        </tr>
        <!-- NOR Gate -->
        <tr>
            <td>NOR</td>
            <td><img src="Images/Logic Gates/NOR.png" alt="NOR Gate Symbol" width="120" height="60"></td>
            <td>
                <table>
                    <tr><td>0</td><td>0</td><td>1</td></tr>
                    <tr><td>0</td><td>1</td><td>0</td></tr>
                    <tr><td>1</td><td>0</td><td>0</td></tr>
                    <tr><td>1</td><td>1</td><td>0</td></tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>XOR</td>
            <td><img src="Images/Logic Gates/XOR.png" alt="XOR Gate Symbol" width="120" height="60"></td>
            <td>
                <table>
                    <tr><td>0</td><td>0</td><td>0</td></tr>
                    <tr><td>0</td><td>1</td><td>1</td></tr>
                    <tr><td>1</td><td>0</td><td>1</td></tr>
                    <tr><td>1</td><td>1</td><td>0</td></tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>XOR</td>
            <td><img src="Images/Logic Gates/XNOR.png" alt="XNOR Gate Symbol" width="120" height="60"></td>
            <td>
                <table>
                    <tr><td>0</td><td>0</td><td>1</td></tr>
                    <tr><td>0</td><td>1</td><td>0</td></tr>
                    <tr><td>1</td><td>0</td><td>0</td></tr>
                    <tr><td>1</td><td>1</td><td>1</td></tr>
                </table>
            </td>
        </tr>
    </tbody>
</table>

Here are two more equivalences involving XOR:<br />
$x \oplus 1 = x'$<br />
$x \oplus 0 = x$

<details>
    <summary>Example problem</summary>

Indicate the output of the circuits shown below for the given input signals
<img src="Images/Example Problems/Problem 1.png" alt="Problem 1">
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>R = 1</li>
  <li>S = 0</li>
</ol>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Construct the input/output table for the following circuit
<img src="Images/Example Problems/Problem 2.png" alt="Problem 2">
<ul>  
  <details>
    <summary>Solution</summary>

<table>
    <thead>
        <tr>
            <th>$P$</th>
            <th>$Q$</th>
            <th>$R$</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>1</td>
            <td>1</td>
        </tr>
        <tr>
            <td>1</td>
            <td>0</td>
            <td>1</td>
        </tr>
        <tr>
            <td>0</td>
            <td>1</td>
            <td>0</td>
        </tr>
        <tr>
            <td>0</td>
            <td>0</td>
            <td>1</td>
        </tr>
    </tbody>
</table>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Indicate the output of the circuits shown below for the given input signals
<img src="Images/Example Problems/Problem 3.png" alt="Problem 3">
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>$(P \vee Q) \land \neg(P \land Q)$</li>
  <li>$(P \land Q) \land \neg R$</li>
</ol>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Construct circuits for the following Boolean expressions:
<ol type="a">
  <li>$(\neg P \land Q) \vee \neg Q$</li>
  <li>$((P \land Q) \land (R \land S)) \land T$</li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol>
  <li><img src="Images/Example Problems/Problem 4a.png" alt="Problem 4a"></li>
  <li><img src="Images/Example Problems/Problem 4b.png" alt="Problem 4b"></li>
</ol>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Design a circuit for the following input/output table:
<table>
    <thead>
        <tr>
            <th>$P$</th>
            <th>$Q$</th>
            <th>$R$</th>
            <th>$S$</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>1</td>
            <td>1</td>
            <td>1</td>
        </tr>
        <tr>
            <td>1</td>
            <td>1</td>
            <td>0</td>
            <td>0</td>
        </tr>
        <tr>
            <td>1</td>
            <td>0</td>
            <td>1</td>
            <td>1</td>
        </tr>
        <tr>
            <td>1</td>
            <td>0</td>
            <td>0</td>
            <td>1</td>
        </tr>
        <tr>
            <td>0</td>
            <td>1</td>
            <td>1</td>
            <td>0</td>
        </tr>
        <tr>
            <td>0</td>
            <td>1</td>
            <td>0</td>
            <td>0</td>
        </tr>
        <tr>
            <td>0</td>
            <td>0</td>
            <td>1</td>
            <td>0</td>
        </tr>
        <tr>
            <td>0</td>
            <td>0</td>
            <td>0</td>
            <td>0</td>
        </tr>
    </tbody>
</table>
<ul>  
  <details>
    <summary>Solution</summary>

$(P \land Q \land R) \vee (P \land \neg Q \land R) \vee (P \land \neg Q \land \neg R)$
</details>
</ul>  
</details>

Two digital logic circuits are <strong>equivalent</strong> if, and only if, their input/output tables are identical

<details>
    <summary>Example problem</summary>

Show that $((P \land \neg Q) \vee (P \land Q)) \land Q$ and $P \land Q$ are logically equivalent using boolean algebra
<ul>  
  <details>
    <summary>Solution</summary>

$\equiv ((P \land \neg Q) \vee (P \land Q)) \land Q$

$\equiv (P \land (Q \vee \neg Q)) \land Q \quad$ Distributive Property 

$\equiv (P \land t) \land Q \quad$ Negation Law

$\equiv P \land Q \quad$ Identity Law
</details>
</ul>  
</details>

### Universal Gates
NAND and NOR are known as <strong>universal gates</strong> as any boolean function can be constructed using only NAND or only NOR gates

## Combinational Circuits
Digital logic circuits can be categorized as:
<ul>
  <li>Combinational circuits</li>
  <li>Sequential circuits</li>
</ul>

Combinational logic is used to build circuits that contain basic boolean operators, inputs, and outputs. An output in a combinational circuit is always based entirely on the given inputs

### Half-Adder
A half-adder is a typical combinational circuit that is used to add two binary digits together

The truth table reveals that:
<ul>
  <li>The sum is actually an XOR gate</li>
  <li>The carry is equivalent to an AND gate</li>
</ul>  

<img src="Images/Logic Gates/HALF ADDER.png" alt="Half Adder" width="300" height="150">

The sum of the half-adder is equal to $A \oplus B$

The $C$ is $A \land B$

### Full-Adder
A full-adder allows for three inputs, $x$, $y$, and carry-in, and two outputs, sum and carry-out

<img src="Images/Logic Gates/FULL ADDER.png" alt="Full Adder" width="300" height="150">

The sum of a full-adder is equal to $(A \oplus B) \oplus C$<sub>in</sub>

The $C$<sub>out</sub> is $((A \oplus B) * C$<sub>in</sub>$) + A * B$

### Ripple-Carry Adder
One limitation of a full-adder is that it can add only three bits. Full adders can be connected ins series to add binary numbers. This type of circuit is called a <strong>ripple-carry adder</strong> because of the sequential generation of carries that ripple through the adder stages

<img src="Images/Logic Gates/RIPPLE CARRY ADDER.png" alt="Ripple Carry Adder" width="300" height="150">

### Decoders
Decoders are used to decode binary information from a set of $n$ inputs to a maximum of $2$<sup>n</sup> outputs

#### 3-8 Decoder Truth Table
<table>
        <tr>
            <th>x</th>
            <th>y</th>
            <th>z</th>
            <th>D0</th>
            <th>D1</th>
            <th>D2</th>
            <th>D3</th>
            <th>D4</th>
            <th>D5</th>
            <th>D6</th>
            <th>D7</th>
        </tr>
        <tr><td>0</td><td>0</td><td>0</td><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr>
        <tr><td>0</td><td>0</td><td>1</td><td>0</td><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr>
        <tr><td>0</td><td>1</td><td>0</td><td>0</td><td>0</td><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr>
        <tr><td>0</td><td>1</td><td>1</td><td>0</td><td>0</td><td>0</td><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td></tr>
        <tr><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>1</td><td>0</td><td>0</td><td>0</td></tr>
        <tr><td>1</td><td>0</td><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>1</td><td>0</td><td>0</td></tr>
        <tr><td>1</td><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>1</td><td>0</td></tr>
        <tr><td>1</td><td>1</td><td>1</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>1</td></tr>
    </table>

<details>
    <summary>Example problem</summary>

Draw the decoder $\Pi m(0, 3, 7)$
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 1.png" alt="Problem 1">
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Draw the decoder $\sum m(2, 4, 6)$
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 1.png" alt="Problem 1">
</details>
</ul>  
</details>

### Multiplexers
A multiplexer (MUX) is a digital logic circuit that selects one of the several input signals and forwards the selected input to a single output line

<img src="Images/Logic Gates/MULTIPLEXER.png" alt="Multiplexer" width="300" height="150">

<details>
    <summary>Example problem</summary>

Find the boolean expression F<br />
<img src="Images/Example Problems/Problem 7.png" alt="Problem 7">
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 7A.png" alt="Problem 7A">
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Design a 2 x 1 MUX for $F(a, b) = a'b + ab$
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 8A.png" alt="Problem 8A">
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

<ol>
  <li>
  
  Write the CSOP of $Z$<sub>2</sub> expressed with $\sum$ in variables $A, B, C$</li>
  <li>
  
  Write the CSOP of $f(A, B, C, D)$ expressed with $\sum$</li>
</ol>  
<img src="Images/Example Problems/Problem 11.png" alt="Problem 9">
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 11A.png" alt="Problem 9A">
</details>
</ul>  
</details>

## Sequential Circuits
### Clocks
Sequential circuits are updated with a clock which can be rising or falling edge triggered

<img src="Images/Logic Gates/CLOCKS.png" alt="Clocks" width="300" height="150">

### SR Flip-FLops
SR flip-flops are the most basic sequential logic components. The S and the R stand for set and reset

The flip-flop can hold the value of one or zero, until the clock changes.

The SR flip-flop has three inputs: S, R, and its current output Q(t)

<img src="Images/Logic Gates/SR FlIP-FLOP.png" alt="SR Flip-FLop" width="300" height="150">

### JK Flip-Flops
The SR flip-flop can be modified to provide a stable state when S and R inputs are both 1; this modified flip-flop is called a JK flip-flop

<img src="Images/Logic Gates/JK FlIP-FLOP.png" alt="JK Flip-FLop" width="300" height="150">

### D Flip-Flops
The D flip-flop is another variant of the SR flip-flop

<img src="Images/Logic Gates/D FlIP-FLOP.png" alt="JK Flip-FLop" width="300" height="150">

<details>
    <summary>Example problem</summary>

<ol type="a">
  <li>
  
  Write out the truth table for the future control signal of Q<sub>A</sub>(t + 1) and Q<sub>B</sub>(t + 1) for a given A, B, and X<br />
  <img src="Images/Logic Gates/Problem 12.png" alt="Problem 12"></li>
  <li>
  
  Write out the truth table for the future control signal of Q<sub>A</sub>(t + 1) and Q<sub>B</sub>(t + 1) for a given A, B, and X<br />
  <img src="Images/Logic Gates/Problem 13.png" alt="Problem 13"></li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li><img src="Images/Logic Gates/Problem 12A.png" alt="Problem 12A"></li>
  <li><img src="Images/Logic Gates/Problem 13A.png" alt="Problem 13A"></li>
</details>
</ul>  
</details>
