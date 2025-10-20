<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#what-is-verilog'>What is Verilog</a>
  </li>
  <li>
    <a href='#modules'>Modules</a>
  </li>
  <li>
    <a href='#data-types'>Data Types</a>
  </li>
  <li>
    <a href='#Operators'>Operators</a>
  </li>
  <li>
    <a href='#assignments'>Assignments</a>
  </li>
  <li>
    <a href='#conditional-logic'>Conditional Logic</a>
  </li>
  <li>
    <a href='#loop-types'>Loop Types</a>
  </li>
</ol>
</details>

## What is Verilog
Verilog is a hardware description language (HDL) that describes circuits rather than step by step programs like with C++

It is used for designing and simulating digital hardware

## Modules
A <em>module</em> is the basic building block in Verilog. It acts like a class or function that defines hardware. Here is the syntax for a Verilog module

```verilog
module moduleName(inputPort A, inputPort B, outputPort C)
//statement;
endmodule
```

The ports that are associated with the module are the module's inputs and outputs

## Data Types
<em>wire</em> are the connections used with <code>assign</code>

<em>reg</em> is the storage used in <code>always</code> blocks

## Operators
### Bitwise Operators
<code>&</code> (AND),
<code>|</code> (OR),
<code>~</code> (NOT),
<code>^</code> (XOR)

### Logical Operators
<code>&&</code> (Logical AND), <code>||</code> (Logical OR), <code>!</code> (Logical NOT)

### Relational Operators
<code>==</code> (Relational EQUALS), <code>!=</code> (Relational NOT EQUALS), <code><</code> (Relational LESS THAN), <code><=</code> (Relational LESS THAN OR EQUALS), <code>></code> (Relational GREATER THAN), <code>==</code> (Relational GREATER THAN OR EQUALS)

## Assignments
### Continuous Assignment
Continuous assignment is for when inputs do not change. Here is the syntax for continuous assignment:

```verilog
assign newVariable = variableA operator variableB; 

//assign y = a & b
//y always equals a AND b
```

### Procedural Assignment
Procedural assignment means the assignment of a variable occurs whenever an input changes. Here is the syntax 

```verilog
always @(*) begin
    newVariable = variableA operator variableB; 

    //y = a & b
    //y will be evaluated whenever the inputs a and b change
end
```

<details>
    <summary>Example problem</summary>

Given a 2-to-1 MUX with output $Z$, implement $Z$ using Verilog
<ul>  
  <details>
    <summary>Solution</summary>

$Z = A'I$<sub>0</sub> $+ AI$<sub>1</sub>
```verilog
module m21(D0, D1, S, Y);
    output Y;
    input D0, D1, S;
    assign Y = (S) ? D1 : D0;
endmodule
```

This can also be done structurally
```verilog
module m21(D0, D1, S, Y)
    output Y;
    input D0, D1, S;
    wire W1, W2, notS;

    not (notS, S);
    and (W1, D0, notS);
    and (W2, D1, S);
    or (Y, W1, W2);

endmodule
```
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given a half adder with inputs $a$ and $b$ and outputs <code>sum</code> and <code>carry</code>, implement this half adder using Verilog
<ul>  
  <details>
    <summary>Solution</summary>

```verilog
module halfAdder(
    input a,
    input b,
    output wire sum,
    output wire carry
);

    assign sum = a ^ b;
    assign carry = a & b;

endmodule
```
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given a fuller adder with inputs $a$, $b$, and $cin$ and outputs <code>sum</code> and <code>cout</code>, implement this fuller adder using Verilog
<ul>  
  <details>
    <summary>Solution</summary>

$Sum = A ⊕ B ⊕ Cin$<br />

$Cout = (A$ & $B) $|$ (B$ & $Cin) $|$ (A$ & $Cin)$

```verilog
module fullAdder(
    input a,
    input b,
    input cin,
    output wire sum,
    output wire cout
);

    assign sum = a ^ b ^ cin;
    assign cout = (a & b) | (b & cin) | (a & cin);

endmodule
```
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Write a function that compares two 2-bit numbers $A$ and $B$ and outputs the result
<ul>  
  <details>
    <summary>Solution</summary>

```verilog
module comparator(
    input [1:0] A,
    input [1:0] B,
    output reg A_gt_B,
    output reg A_eq_B,
    output reg A_lt_B
);

    always @(*) begin
        A_gt_B = 0;
        A_eq_B = 0;
        A_lt_B = 0;

        if (A[1] > B[1])
            A_gt_B = 1;
        else if (A[1] == B[1]) begin
            if (A[0] > B[0])
                A_gt_B = 1;
            else if (A[0] == B[0])
                A_eq_B = 1;
            else
                A_lt_B = 1;
        end
        else
            A_lt_B = 1;
    end

endmodule
```
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

How can one use the module developed for a 2-to-1 MUX to construct an 8-to-1 MUX?
<ul>  
  <details>
    <summary>Solution</summary>

```verilog
module MUX21(
    input a,
    input b,
    input S,
    output reg Y
);

    always @(*) begin
        if (S == 0)
            Y = a;
        else
            Y = b;
    end

endmodule

module MUX41(
    input wire [3:0] d,
    input wire [1:0] sel,
    output y
);

    wire y0, y1;

    MUX21 M1(.a(d[0]), .b(d[1]), .S(sel[0]), .Y(y0));
    MUX21 M2(.a(d[2]), .b(d[3]), .S(sel[0]), .Y(y1));

    MUX21 M3(.a(y0), .b(y1), .S(sel[1]), y(y));

endmodule

module MUX81(
    input wire [7:0] d,
    input wire [2: 0] sel,
    output y
);

    wire y0, y1;

    MUX41 M1(.d(d[3:0]), .sel(sel[1:0]), .y(y0));
    MUX41 M2(.d(d[7:4]), .sel(sel[1:0]), .y(y1));

    MUX21 M3(.a(y0), .b(y1), .S(sel[2]), .y(y));
```
</details>
</ul>  
</details>

### <code>initial</code> and <code>always</code> Blocks

#### <code>initial</code> Block
The <code>initial</code> block is used for initialization. It runs once at simulation time t = 0

```verilog
initial begin
    clk = 0;
    reset = 1;
    #10 reset = 0;
end

//At time t = 0, set clk = 0 and reset = 1. After 10 time units, set reset = 0
```

#### <code>always</code> Block
Used for logic that repeats or reacts to changes. It will execute forever as long as simulation runs

Syntax:
```verilog
always @(sensitivityList)
begin
    //statements
end
```

```verilog
always @(*)
    y = a & b;
end

//whenever any input changes (a or b) recompute y
```

The block wakes up and executes whenever something in the sensitivity list changes

### Delay Control
Sometimes assignment does not happen until a certain time period such as shown below

```verilog
initial begin
    x = 0;
    #5 x = y; //after 5 time units, copy y into x
end
```

### Event Control
This means wait until a specific event occurs, then perform the assignment

```verilog
always begin
    @(posedge clock) x = y;
end

//The statement above waits until the rising edge of the clock happens; when that even occurs, it executes x = y. After that, it loops back and waits for the next rising edge, if inside an always loop
```

### Level-Sensitive Wait
This means wait until <code>enable</code> becomes true (logic 1), then execute that statement

```verilog
initial begin
    wait (enable x = y);
end

//The block pauses until the condition (enable) evaluates to true. When that happens, it executes that next statement (x = y)
```

## Conditional Logic
### <code>if-else</code> Statements
Here is the syntax for conditional logic in Verilog

```verilog
if (conditional)
    statement;
else if (conditional2)
    statement;
else
    statement;
```

<details>
    <summary>Example problem</summary>

Realize the following functions with a 4-to-1 multiplexer module

<ol type="a">
<li>

$f(a,b,c) = \sum m(2,4,5,7)$
</li>
<li>

$f(a,b,c) = $&Pi;$M(0,6,7)$
</li>
<li>

$f(a,b,c) = (a + b')(b' + c)$
</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>

For A = 0 and B = 0, regardless of C = 0 or C = 1, minterms 0 and 1 always results in a f that is 0

For A = 0 and B = 1, when C = 0, minterm 2 results in a f that is 1. when C = 1, minterm 3 results in a f that is 0. so for these minterms f = C'

For A = 1 and B = 0, when C = 0, minterm 4 results in a f that is 1. when C = 1, minterm 5 results in a f that is 1. so for these minterms f = 1

For A = 1 and B = 1, when C = 0, minterm 6 results in a f that is 0. when C = 1, minterm 7 results in a f that is 1. so for these minterms f = C

```verilog
module mux41 (
    input wire A, 
    input wire B, 
    input wire C,
    output reg f
);
    wire D0, D1, D2, D3;

    assign D0 = 0;
    assign D1 = ~C;
    assign D2 = 1;
    assign D3 = C;

    always @(*) begin
        if (A == 0 && B == 0)
            f = D0;
        else if (A == 0 && B == 1)
            f = D1;
        else if (A == 1 && B == 0)
            f = D2;
        else
            f = D3;
    end
endmodule
```
  </li>
  <li>
For A = 0 and B = 0, if C = 0, f is 0; otherwise, if C = 1, f is 1. f then equals C for minterms 0 and 1

For A = 0 and B = 1, if C = 0, f is 1; otherwise, if C = 1, f is 1. f then equals 1 for minterms 2 and 3

For A = 1 and B = 0, if C = 0, f is 1; otherwise, if C = 1, f is 1. f then equals 1 for minterms 4 and 5

For A = 1 and B = 1, if C = 0, f is 0; otherwise, if C = 1, f is 0. f then equals 0 for minterms 6 and 7

```verilog
module mux41 (
    input wire A,
    input wire B,
    input wire C,
    output reg f
);

    wire D0, D1, D2, D3;

    assign D0 = C;
    assign D1 = 1;
    assign D2 = 1;
    assign D3 = 0;

    always @(*) begin
        if (A == 0 && B == 0)
            f = D0;
        else if (A == 0 && B == 1)
            f = D1;
        else if (A == 1 && B == 0)
            f = D2;
        else
            f = D3;
    end
endmodule
```
  </li>
  <li>

$f = ab' + b' + b'c + ac$
$f = b' + ac$
Minterms are: 0, 1, 
</ol>
</details>
</ul>  
</details>

### <code>case</code> Statements
<code>case</code> statements function like a switch statement in C. The syntax for the statement is shown below:

```verilog
case (expression)
    condition: statement;
    condition2: statement2;
    default: defaultStatement;
endcase
```

## Loop Types
### <code>forever</code>
The <code>forever</code> loop must be in an initial block and is for testbenches only

```verilog
initial begin
    forever
        $5 clock = ~clock;
```

This style of loop repeats its body indefinitely until simulation stops. It is like <code>while(1)</code> in C

### <code>repeat</code>
The <code>repeat</code> loop executes its body a fixed number of times, specified by an integer expression

```verilog
repeat (N) begin
    statements
end
```

Where <code>N</code> is a positive integer (the number of iterations)
### <code>while</code>
The <code>while</code> loop in Verilog is similar to C. It repeats as long as the condition is true

Syntax:
```verilog
while (condition)
    //statement
end
```
### <code>for</code>
The <code>for</code> loop is used the same way as in C, typically for a fixed number of iterations

Syntax:
```verilog
for (initializations; condition; incrementations)
    statement;
end
```

<code>for</code> loops are synthesizable

<details>
    <summary>Example problem</summary>

Given 

<div align="center">

Y = (A + B)' * C
</div>

Write a module that defines this function in Verilog using only NAND gates
<ul>  
  <details>
    <summary>Solution</summary>

$Y = ((A'B'C)')'$

```verilog
module NANDonly(
    input A, B, C,
    output Y
);
    wire n1, n2, n3;

    nand(n1, A, A);
    nand(n2, B, B);
    nand(n3, n1, n2, C);
    nand(Y, n3, n3);

endmodule
```
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

Given 

<div align="center">

Y = (A + B)' + (C * D)'
</div>

Write a module that defines this function in Verilog using only NOR gates
<ul>  
  <details>
    <summary>Solution</summary>

$Y = (A + B)' + (C * D)'$

$Y = (A + B)' + ((C' + D')')'$

```verilog
module NORonly(
    input A, B, C, D,
    output Y
);
    wire n1, n2, n3;

    nor(n1, A, B);
    nor(n2, C, C);
    nor(n3, D, D);
    nor(n4, n2, n3);
    nor(n5, n4, n4);
    nor(n6, n1, n5);
    nor(n7, n6, n6);

endmodule
```
</details>
</ul>  
</details>