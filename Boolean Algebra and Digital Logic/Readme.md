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
    <a href='#karnaugh-maps'>Karnaugh Maps</a>
  </li>
  <li>
    <a href='#quine-mccluskey-method'>Quine McCluskey Method</a>
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
            <td>XNOR</td>
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

<details>
    <summary>Example problem</summary>

Using NAND gates, implement the BOolean function F(A, B, C) = AB + BC
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 16A.png" alt="Problem 16A">
</details>
</ul>  
</details>

## Karnaugh Maps
The Karnaugh map is actually nothing more than an extension of the concepts of truth tables, Venn diagrams, and minterms

Steps:
<ol>
  <li>Set up the K-map. Choose the right K-map size, where two variables is a 2x2 grid, three variables is a 3x3 grid, and four variables is a 4x4 grid. For a 5 variable function, create two 4x4 grids with the first variable equal to zero for one grid and the first variable equal to one for the other grid. Then label the columns with gray cord order: 00, 01, 11, 10. Fill in the K-map with 1s for the minterms where the function is true and Xs for the don't care values</li>
  <li>Group the 1s. Make groups of 1, 2, 4, 8, ... (always power of 2) where the groups can wrap around the edges of the map. Always try to make the largest possible groups for the most simplified result</li>
  <li>Extract the simplified terms. Inside of each group, find the variables that stay the same across all cells. These variables form the product term and the variables that change inside the group are eliminated</li>
  <li>Write the simplified expression. Each group gives one product term and combine all the product terms with or</li>
</ol>

<details>
    <summary>Example problem</summary>

<ol type="a">
  <li>
  
  Simplify the Boolean function using a 3-variable K-map:<br>
  
  <strong>Function:</strong><br>
  $F(A,B,C) = \Sigma m(0,1,2,5,7)$</li>
  <li>
  Simplify the Boolean function using a 3-variable K-map:<br>
  
  <strong>Function:</strong><br>
  $F(A,B,C) = \Sigma m(0,2,3,5,6)$</li>
  <li>
  Simplify the Boolean function using a 3-variable K-map:<br>
  
  <strong>Function:</strong><br>
  $F(A,B,C) = \Sigma m(1,2,4,5,6,7)$</li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
  
<table>
  <tr>
    <th>AB \ C</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <th>00</th>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <th>01</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>11</th>
    <td>0</td>
    <td>1</td>
  </tr>
  <tr>
    <th>10</th>
    <td>0</td>
    <td>1</td>
  </tr>
</table>

$F(A,B,C) = A'B' + A'C' + AC$</li>
  <li>
  
<table>
  <tr>
    <th>AB \ C</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <th>00</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>01</th>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <th>11</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>10</th>
    <td>0</td>
    <td>1</td>
  </tr>
</table>

$F(A,B,C) = A'B + BC' + BC' + AB'C$</li>
  <li>
  
<table>
  <tr>
    <th>AB \ C</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <th>00</th>
    <td>0</td>
    <td>1</td>
  </tr>
  <tr>
    <th>01</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>11</th>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <th>10</th>
    <td>1</td>
    <td>1</td>
  </tr>
</table>

$F(A,B,C) = BC' + B'C + A$</li>
</ol>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

<ol type="a">
  <li>
  
  Simplify the Boolean function using a 4-variable K-map:<br>
  
  <strong>Function:</strong><br>
  $F(A,B,C,D) = \Sigma m(0,1,2,5,7,8,9,10,14)$<br />
  <strong>Don’t cares:</strong><br>
  $d = \Sigma m(11,15)$
  <br /></li>
  <li>
  Simplify the Boolean function using a 5-variable K-map:<br>
  
  <strong>Function:</strong><br>
  $F(A,B,C,D,E) = \Sigma m(0,1,2,3,8,9,10,11,16,17,18,19,24,25,26,27)$<br />
  
  <strong>Don’t cares:</strong><br>
  $d = \Sigma m(5,7,13,29)$
  <br />
</li>

</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li><img src="Images/Example Problems/Problem 17A.png" alt="Problem 17A"></li>
  <li><img src="Images/Example Problems/Problem 18A.png" alt="Problem 18A"></li>
</ol>
</details>
</ul>  
</details>

### Prime Implicants
<em>Prime implicants</em> are the product terms (AND of variables_ obtained from grouping 1s in a Karnaugh map. It represents the largest possible group, meaning it cannot be combined with other adjacent 1s to make it bigger

### Essential Prime Implicants
An <em>essential prime implicant</em> is a prime implicant that covers at least one minterm that is not covered by any other prime implicant. These are mandatory to include in the minimized operation

All essential prime implicants are prime implicants; however, not a prime implicants are essential prime implicants

<details>
    <summary>Example problem</summary>

<ol type="a">
  <li>
  
  Simplify the Boolean function using a 3-variable K-map:<br>
  
  <strong>Function:</strong><br>
  $F(A,B,C) = \Sigma m(0,1,2,5,7)$</li>
  <li>
  Simplify the Boolean function using a 3-variable K-map:<br>
  
  <strong>Function:</strong><br>
  $F(A,B,C) = \Sigma m(0,2,3,5,6)$</li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
  
<table>
  <tr>
    <th>AB \ C</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <th>00</th>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <th>01</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>11</th>
    <td>0</td>
    <td>1</td>
  </tr>
  <tr>
    <th>10</th>
    <td>0</td>
    <td>1</td>
  </tr>
</table>

Prime implicants: A'B', AC, A'C", B'C<br />
Essential prime implicants: AC + A'C'<br />
$F(A,B,C) = A'B' + AC + A'C'$<br /></li>
  <li>
  
<table>
  <tr>
    <th>AB \ C</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <th>00</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>01</th>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <th>11</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>10</th>
    <td>0</td>
    <td>1</td>
  </tr>
</table>

Prime Implicants: A'C', AB'C, BC', A'B<br />
Essential Prime Implicants: A'C', AB'C, BC', A'B<br /> 
$F(A,B,C) = A'B + BC' + BC' + AB'C$</li>
</ol>
</details>
</ul>  
</details>

## Quine McCluskey Method
The purpose of the <em>Quine McCluskey Method</em> is for minimizing boolean expressions using a tabular method. This method works similar to the Karnaugh maps, but scales better for more than four variables. This method also guarantees finding the minimal sum-of-products form

Steps:
<ol>
  <li>Write the Boolean function as a sum of minterms where each minterm is a binary combination</li>
  <li>Group the minterms by the total number of ones. Example: minterm <code>0101</code> (two 1s) goes into group two</li>
  <li>Compare the terms from adjacent groups between group N and group N + 1. If the terms differ in exactly one bit, combine them and replace the differing bit with a dash (-). Example: <code>0101</code> and <code>0111</code> -> <code>01-1</code></li>
  <li>Repeat combining until no further reductions are possible. The unused terms are the <em>prime implicants</em></li>
</ol>

<details>
    <summary>Example problem</summary>

Minimize the following function using the Quine McCluskey Method: $F(A, B, C) = \sum m(1, 3, 5, 7)$
<ul>  
  <details>
    <summary>Solution</summary>

Minterms:<br />
$m1$ = <code>001</code><br />
$m3$ = <code>011</code><br />
$m5$ = <code>101</code><br />
$m7$ = <code>111</code><br />

Group A1:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>001</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A2:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3</td>
      <td>011</td>
      <td>→</td>
    </tr>
    <tr>
      <td>5</td>
      <td>101</td>
      <td>→</td>
    </tr>
  </tbody>
</table> 

Group A3:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>7</td>
      <td>111</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B1 (A1-A2):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1, 3</td>
      <td>0-1</td>
      <td>→</td>
    </tr>
    <tr>
      <td>1, 5</td>
      <td>-01</td>
      <td>→</td>
    </tr>
  </tbody>
</table> 

Group B2 (A2-A3):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3, 7</td>
      <td>-11</td>
      <td>→</td>
    </tr>
    <tr>
      <td>5, 7</td>
      <td>1-1</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group C1(B1-B2):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1, 3, 5, 7</td>
      <td>--1</td>
      <td>✓</td>
    </tr>
  </tbody>
</table>

Prime implicant: <code>--1</code>

$F(A, B, C) = C$
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Minimize the following function using the Quine McCluskey Method: $F(A, B, C, D) = \sum m(0, 1, 2, 5, 6, 7, 8, 9 ,10, 14)$
<ul>  
  <details>
    <summary>Solution</summary>

Minterms:<br />
$m0$ = <code>0000</code><br />
$m1$ = <code>0001</code><br />
$m2$ = <code>0010</code><br />
$m5$ = <code>0101</code><br />
$m6$ = <code>0110</code><br />
$m7$ = <code>0111</code><br />
$m8$ = <code>1000</code><br />
$m9$ = <code>1001</code><br />
$m10$ = <code>1010</code><br />
$m14$ = <code>1110</code><br />

Group A1:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0000</td>
      <td>→</td>
    </tr>
    <tr>
      <td>1</td>
      <td>0001</td>
      <td>→</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0010</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A2:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2</td>
      <td>0010</td>
      <td>→</td>
    </tr>
    <tr>
      <td>8</td>
      <td>1001</td>
      <td>→</td>
    </tr>
  </tbody>
</table>
Group A3:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>5</td>
      <td>0101</td>
      <td>→</td>
    </tr>
    <tr>
      <td>6</td>
      <td>0110</td>
      <td>→</td>
    </tr>
    <tr>
      <td>9</td>
      <td>1001</td>
      <td>→</td>
    </tr>
    <tr>
      <td>10</td>
      <td>1010</td>
      <td>→</td>
    </tr>
  </tbody>
</table>
Group A4:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>7</td>
      <td>0111</td>
      <td>→</td>
    </tr>
    <tr>
      <td>14</td>
      <td>1110</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B1 (A1, A2): 
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0, 1</td>
      <td>000-</td>
      <td>→</td>
    </tr>
    <tr>
      <td>0, 2</td>
      <td>00-0</td>
      <td>→</td>
    </tr>
    <tr>
      <td>0, 8</td>
      <td>-000</td>
      <td>→</td>
    </tr>
  </tbody>
</table>
Group B2 (A2, A3):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1, 5</td>
      <td>0-01</td>
      <td>✓</td>
    </tr>
    <tr>
      <td>1, 9</td>
      <td>-001</td>
      <td>→</td>
    </tr>
    <tr>
      <td>2, 6</td>
      <td>0-01</td>
      <td>→</td>
    </tr>
    <tr>
      <td>2, 10</td>
      <td>-010</td>
      <td>→</td>
    </tr>
    <tr>
      <td>8, 9</td>
      <td>100-</td>
      <td>→</td>
    </tr>
    <tr>
      <td>8, 10</td>
      <td>10-0</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B3 (A3, A4):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>5, 7</td>
      <td>01-1</td>
      <td>✓</td>
    </tr>
    <tr>
      <td>6, 7</td>
      <td>011-</td>
      <td>✓</td>
    </tr>
    <tr>
      <td>6, 14</td>
      <td>-110</td>
      <td>→</td>
    </tr>
    <tr>
      <td>10, 14</td>
      <td>1-10</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group C1 (B1, B2):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0, 1, 8, 9</td>
      <td>-00-</td>
      <td>✓</td>
    </tr>
    <tr>
      <td>0, 2, 8, 10</td>
      <td>-0-0</td>
      <td>✓</td>
    </tr>
  </tbody>
</table>
Group C2 (B2, B3):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2, 6, 10, 14</td>
      <td>--10</td>
      <td>✓</td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>Prime Implicant</th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>10</th>
      <th>14</th>
      <th>Variables</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1,5</td>
      <td></td>
      <td>X</td>
      <td></td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>0-01</td>
    </tr>
    <tr>
      <td>5,7</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>01-1</td>
    </tr>
    <tr>
      <td>6,7</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>011-</td>
    </tr>
    <tr>
      <td>0,1,8,9</td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td>-00-</td>
    </tr>
    <tr>
      <td>0,2,8,10</td>
      <td>X</td>
      <td></td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td></td>
      <td>X</td>
      <td></td>
      <td>-0-0</td>
    </tr>
    <tr>
      <td>2,6,10,14</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td>--10</td>
    </tr>
  </tbody>
</table>

Column 9 has only a single X, so it is an essential prime implicant (0, 1, 8, 9) with the value <code>-00-</code>. Now remove this prime implicant row and corresponding minterm column 0, 1, 8, 9

<table>
  <thead>
    <tr>
      <th>Prime Implicant</th>
      <th>2</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>10</th>
      <th>14</th>
      <th>Variables</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1,5</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>0-01</td>
    </tr>
    <tr>
      <td>5,7</td>
      <td></td>
      <td>X</td>
      <td></td>
      <td>X</td>
      <td></td>
      <td></td>
      <td>01-1</td>
    </tr>
    <tr>
      <td>6,7</td>
      <td></td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td>011-</td>
    </tr>
    <tr>
      <td>0,2,8,10</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td></td>
      <td>-0-0</td>
    </tr>
    <tr>
      <td>2,6,10,14</td>
      <td>X</td>
      <td></td>
      <td>X</td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td>--10</td>
    </tr>
  </tbody>
</table>

Column 14 has only one single X, so it is an essential prime implicant (2, 6, 10, 14) with the value <code>--10</code>. Now remove this prime implicant row and corresponding minterm column 2, 6, 10, 14

<table>
  <thead>
    <tr>
      <th>Prime Implicant</th>
      <th>5</th>
      <th>7</th>
      <th>Variables</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1,5</td>
      <td>X</td>
      <td></td>
      <td>0-01</td>
    </tr>
    <tr>
      <td>5,7</td>
      <td>X</td>
      <td>X</td>
      <td>01-1</td>
    </tr>
    <tr>
      <td>6,7</td>
      <td></td>
      <td>X</td>
      <td>011-</td>
    </tr>
    <tr>
      <td>0,2,8,10</td>
      <td></td>
      <td></td>
      <td>-0-0</td>
    </tr>
  </tbody>
</table>

The second row prime implicant (5, 7) has a larger number of Xs than any other row, so it is an essential prime implicant (5, 7) with the value <code>01-1</code>. Removing columns 5 and 7 leaves the table with no columns, so all the essential prime implicants have been found

All extracted essential prime implicants: <code>-00-</code>, <code>--10</code>, <code>01-1</code>

Minimal Quine-McCluskey Expression: $F(A, B, C, D) = B'C' + CD' + A'BD$
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Minimize the following function using the Quine McCluskey Method: $F(A, B, C, D) = \sum m(0, 1, 2, 4, 6, 8, 9 ,11, 13, 15)$
<ul>  
  <details>
    <summary>Solution</summary>

Minterms:<br />
$m0$ = <code>0000</code><br />
$m1$ = <code>0001</code><br />
$m2$ = <code>0010</code><br />
$m4$ = <code>0100</code><br />
$m6$ = <code>0110</code><br />
$m8$ = <code>1000</code><br />
$m9$ = <code>1001</code><br />
$m11$ = <code>1011</code><br />
$m13$ = <code>1101</code><br />
$m15$ = <code>1111</code><br />

Group A1:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0000</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A2:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>0001</td>
      <td>→</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0010</td>
      <td>→</td>
    </tr>
    <tr>
      <td>4</td>
      <td>0100</td>
      <td>→</td>
    </tr>
    <tr>
      <td>8</td>
      <td>1000</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A3:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>6</td>
      <td>0110</td>
      <td>→</td>
    </tr>
    <tr>
      <td>9</td>
      <td>1001</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A4:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>11</td>
      <td>1011</td>
      <td>→</td>
    </tr>
    <tr>
      <td>13</td>
      <td>1101</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A5:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>15</td>
      <td>1111</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B1 (A1, A2): 
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0, 1</td>
      <td>000-</td>
      <td>→</td>
    </tr>
    <tr>
      <td>0, 2</td>
      <td>00-0</td>
      <td>→</td>
    </tr>
    <tr>
      <td>0, 4</td>
      <td>0-00</td>
      <td>→</td>
    </tr>
    <tr>
      <td>0, 8</td>
      <td>-000</td>
      <td>→</td>
    </tr>
  </tbody>
</table>
Group B2 (A2, A3):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1, 9</td>
      <td>-001</td>
      <td>→</td>
    </tr>
    <tr>
      <td>2, 6</td>
      <td>0-10</td>
      <td>→</td>
    </tr>
    <tr>
      <td>4, 6</td>
      <td>01-0</td>
      <td>→</td>
    </tr>
    <tr>
      <td>8, 9</td>
      <td>100-</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B3 (A3, A4):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>9, 11</td>
      <td>10-1</td>
      <td>→</td>
    </tr>
    <tr>
      <td>9, 13</td>
      <td>1-01</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B4 (A4, A5):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>11, 15</td>
      <td>1-11</td>
      <td>→</td>
    </tr>
    <tr>
      <td>13, 15</td>
      <td>11-1</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group C1 (B1, B2):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0, 2, 4, 6</td>
      <td>0--0</td>
      <td>✓</td>
    </tr>
    <tr>
      <td>0, 1, 8, 9</td>
      <td>-00-</td>
      <td>✓</td>
    </tr>
  </tbody>
</table>

Group C2 (B2, B3):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2, 6, 9, 13</td>
      <td>--01</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group C3 (B3, B4):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>9, 11, 13, 15</td>
      <td>1--1</td>
      <td>✓</td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>Prime Implicant</th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>4</th>
      <th>6</th>
      <th>8</th>
      <th>9</th>
      <th>11</th>
      <th>13</th>
      <th>15</th>
      <th>Variables</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0, 1, 8, 9</td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td>-00-</td>
    </tr>
    <tr>
      <td>0, 2, 4, 6</td>
      <td>X</td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>0--0</td>
    </tr>
    <tr>
      <td>9, 11, 13, 15</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td>X</td>
      <td>X</td>
      <td>1--1</td>
    </tr>
  
  </tbody>
</table>

Columns 1, 2, 4, 6, 8, 11, 13, and 15 have only a single X, so the essential prime implicants are (0, 1, 8, 9), (0, 2, 4, 6), and (9, 11, 13, 15). Now remove the prime implicant rows corresponding to minterm column 1, 2, 4, 6, 8, 11, 13, and 15

Doing that leaves no more prime implicants; therefore, the prime implicants above are essential prime implicants

All extracted essential prime implicants: <code>-00-</code>, <code>0--0</code>, <code>1--1</code>

Minimal Quine-McCluskey Expression: $F(A, B, C, D) = B'C' + A'D' + AD$
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Minimize the following function using the Quine McCluskey Method: $F(A, B, C) = \sum m(1, 3, 7, 11, 15)$ with $d = \sum m(0, 2)$
<ul>  
  <details>
    <summary>Solution</summary>

Minterms:<br />
$m0$ = <code>0000</code><br />
$m1$ = <code>0001</code><br />
$m2$ = <code>0010</code><br />
$m3$ = <code>0011</code><br />
$m7$ = <code>0111</code><br />
$m11$ = <code>1011</code><br />
$m15$ = <code>1111</code><br />

Group A1:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0000</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A2:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>0001</td>
      <td>→</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0010</td>
      <td>→</td>
    </tr>
  </tbody>
</table> 

Group A3:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3</td>
      <td>0011</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A4:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>7</td>
      <td>0111</td>
      <td>→</td>
    </tr>
    <tr>
      <td>11</td>
      <td>1011</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group A5:
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>15</td>
      <td>1111</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B1 (A1-A2):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0, 1</td>
      <td>000-</td>
      <td>→</td>
    </tr>
    <tr>
      <td>0, 2</td>
      <td>-00-0</td>
      <td>→</td>
    </tr>
  </tbody>
</table> 

Group B2 (A2-A3):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1, 3</td>
      <td>00-1</td>
      <td>→</td>
    </tr>
    <tr>
      <td>2, 3</td>
      <td>001-</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B3 (A3-A4):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3, 7</td>
      <td>0-11</td>
      <td>→</td>
    </tr>
    <tr>
      <td>3, 11</td>
      <td>-011</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group B4 (A4-A5):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>7, 15</td>
      <td>-111</td>
      <td>→</td>
    </tr>
    <tr>
      <td>11, 15</td>
      <td>1-11</td>
      <td>→</td>
    </tr>
  </tbody>
</table>

Group C1 (B1-B2):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0, 1, 2, 3</td>
      <td>00--</td>
      <td>✓</td>
    </tr>
  </tbody>
</table>

Group C2 (B3-B4):
<table>
  <thead>
    <tr>
      <th>Pair (Decimal)</th>
      <th>Binary</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3, 7, 11, 15</td>
      <td>--11</td>
      <td>✓</td>
    </tr>
  </tbody>
</table>

Prime Implicant Chart Excluding Don't Cares
<table>
  <thead>
    <tr>
      <th>Prime Implicant</th>
      <th>1</th>
      <th>3</th>
      <th>7</th>
      <th>11</th>
      <th>15</th>
      <th>Variables</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0,1,2,3</td>
      <td>X</td>
      <td>X</td>
      <td></td>
      <td></td>
      <td></td>
      <td>00--</td>
    </tr>
    <tr>
      <td>3,7,11,15</td>
      <td></td>
      <td>X</td>
      <td>X</td>
      <td>X</td>
      <td>X</td>
      <td>--11</td>
    </tr>
  </tbody>
</table>

Column 1 has one single X, so essential prime implicant (0, 1, 2, 3) has a value of <code>00--</code>. Now remove the columns associated with this prime implicant: columns 1 and 3. Column 7, 11, and 15 have one single X, so essential prime implicant (3, 7, 11, 15) has a value of <code>--11</code>. Now remove the columns associated with the prime implicant: columns: 3, 7, 11, and 15. This leaves no columns left; therefore, all the essential prime implicants have been found

All extracted essential prime implicants: <code>00--</code>,<code>--11</code>

Minimal Quine-McCluskey Expression: $F(A, B, C, D) = A'B' + CD$
</details>
</ul>  
</details>

## Combinational Circuits
Digital logic circuits can be categorized as:
<ul>
  <li>Combinational circuits</li>
  <li>Sequential circuits</li>
</ul>

### Two-level Circuits
Input signals must pass through two levels of gates before reaching the output

Combinational logic is used to build circuits that contain basic boolean operators, inputs, and outputs. An output in a combinational circuit is always based entirely on the given inputs

<details>
    <summary>Example problem</summary>

Design a two-level NAND-NAND circuit for the Boolean expression: $F(A, B, C, D) = AB'C + BD$
<ul>  
  <details>
    <summary>Solution</summary>

$F(A, B, C, D) = AB'C + BD$<br />
$F(A, B, C, D) = (AB'C + BD)''$<br />
$F(A, B, C, D) = ((AB'C)' * (BD)')'$<br />
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given the following function: 

<div align="center">

$F(W, X, Y, Z) = (W + X)(Y + Z)$
</div>

<ol type="a">
  <li>Convert this into a two-level AND-OR form</li>
  <li>Convert this into a two level OR-AND form</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
  
$F(W, X, Y, Z) = WY + WZ + XY + XZ$</li>
  <li>

$F(W, X, Y, Z) = (W + X)(Y + Z)$</li>
</ol>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given the following function: 

<div align="center">

$F(x, y, z) = \sum m(0, 1, 4, 5, 6)$
</div>

<ol type="a">
  <li>Design an AND-OR realization for the function above</li>
  <li>Design a NAND-NAND realization for the function above</li>
  <li>Design a OR-AND realization for the function above</li>
  <li>Design a NOR-NOR realization for the function above</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>
  
<table>
  <tr>
    <th>AB \ C</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <th>00</th>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <th>01</th>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <th>11</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>10</th>
    <td>1</td>
    <td>1</td>
  </tr>
</table>

$F = Y' + XZ'$
</li>
  <li>

$F = ((Y' + XZ')')'$<br />
$F = ((Y')' * (XZ')')'$<br />
$F = (Y * (XZ')')'$<br />
</li>
<li>

<table>
  <tr>
    <th>AB \ C</th>
    <th>0</th>
    <th>1</th>
  </tr>
  <tr>
    <th>00</th>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <th>01</th>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <th>11</th>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <th>10</th>
    <td>1</td>
    <td>1</td>
  </tr>
</table>

$F = (X + Y')(Y' + Z')$
</li>
<li>

$F = (((X + Y')(Y' + Z'))')'$<br />
$F = ((X + Y')' + (Y' + Z')')'$<br />
</li>
</ol>  
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given the following function: 

<div align="center">

$F(A, B, C, D) = \sum m(1, 2, 3, 5, 6, 7, 8, 9, 12, 14)$
</div>

Design a NOR-only circuit for the following logic function
<ul>  
  <details>
    <summary>Solution</summary>

<table border="1" cellpadding="10">
      <tr>
        <th>AB \ CD</th>
        <th>00</th>
        <th>01</th>
        <th>11</th>
        <th>10</th>
      </tr>
      <tr>
        <th>00</th>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
      </tr>
      <tr>
        <th>01</th>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
      </tr>
      <tr>
        <th>11</th>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
      </tr>
      <tr>
        <th>10</th>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
      </tr>
    </table>

$F = (A + C + D)(A' + B' + D')(A' + B + C')$<br />
$F = (((A + C + D)(A' + B' + D')(A' + B + C'))')'$<br />
$F = ((A + C + D)' + (A' + B' + D')' + (A' + B + C')')'$<br />
</details>
</ul>  
</details>

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

Draw the decoder $\Pi M(0, 3, 7)$
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 14A.png" alt="Problem 1">
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Draw the decoder $\sum m(2, 4, 6)$
<ul>  
  <details>
    <summary>Solution</summary>

<img src="Images/Example Problems/Problem 15A.png" alt="Problem 1">
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

<img src="Images/Logic Gates/SR.png" alt="SR Flip-FLop" width="300" height="100">

### JK Flip-Flops
The SR flip-flop can be modified to provide a stable state when S and R inputs are both 1; this modified flip-flop is called a JK flip-flop

<img src="Images/Logic Gates/JK.png" alt="JK Flip-FLop" width="300" height="100">

### D Flip-Flops
The D flip-flop is another variant of the SR flip-flop

<img src="Images/Logic Gates/D.png" alt="JK Flip-FLop" width="300" height="100">

<details>
    <summary>Example problem</summary>

<ol type="a">
  <li>
  
  Write out the truth table for the future control signal of Q<sub>A</sub>(t + 1) and Q<sub>B</sub>(t + 1) for a given A, B, and X<br />
  <img src="Images/Example Problems/Problem 12.png" alt="Problem 12"></li>
  <li>
  
  Write out the truth table for the future control signal of Q<sub>A</sub>(t + 1) and Q<sub>B</sub>(t + 1) for a given A, B, and X<br />
  <img src="Images/Example Problems/Problem 13.png" alt="Problem 13"></li>
</ol>  
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li><img src="Images/Example Problems/Problem 12A.png" alt="Problem 12A"></li>
  <li><img src="Images/Example Problems/Problem 13A.png" alt="Problem 13A"></li>
</details>
</ul>  
</details>
