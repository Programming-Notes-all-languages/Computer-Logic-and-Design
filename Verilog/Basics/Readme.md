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

## Conditional Logic
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

For A = 0 and B = 0, if C = 0, f is 1; otherwise, if C = 1, f is 1. f then equals 1 for minterms 0 and 1

For A = 0 and B = 1, if C = 0, f is 0; otherwise, if C = 1, f is 0. f then equals 0 for minterms 2 and 3

For A = 1 and B = 0, if C = 0, f is 1; otherwise, if C = 1, f is 1. f then equals 1 for minterms 4 and 5

For A = 1 and B = 1, if C = 0, f is 0; otherwise, if C = 1, f is 1. f then equals C for minterms 6 and 7

$f = ab' + b' + b'c + ac$
$f = b' + ac$
Minterms are: 0, 1, 4, 5, 7

```verilog
module mux41 (
    input wire A,
    input wire B,
    input wire C,
    output reg f
);

    wire D0, D1, D2, D3;

    assign D0 = 1;
    assign D1 = 0;
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
</ol>
</details>
</ul>  
</details>