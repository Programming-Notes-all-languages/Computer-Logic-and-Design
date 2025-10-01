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
    output y;
    input D0, D1, S;
    assign Y = (S) ? D1 : D0;
endmodule
```
</details>
</ul>  
</details>

## Conditional Logic