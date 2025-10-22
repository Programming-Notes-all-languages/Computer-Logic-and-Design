<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#introduction'>Introduction</a>
  </li>
  <li>
    <a href='#state-register'>State Register</a>
  </li>
</ol>
</details>

## Introduction
There are two models: the Moore Model and the Mealy Model

### Moore Model
The Moore Model has an output that depends on current state only

Here is a sample Moore Machine Model in Verilog:

```verilog
module mooreFSM (
    input clk, reset, x,
    output reg y
);

    parameter A = 2'b00, B = 2'b01, C = 2'b10, D = 2'b11;

    reg [1:0] state, next_state;

    always @(posedge clk) begin
        if (reset)
            state <= A;
        else
            state <= next_state;
    end

    always @(*) begin
        case (state)
            A: if (x == 0)
                  next_state = C;
               else
                  next_state = B;
            B: if (x == 0)
                  next_state = A;
               else
                  next_state = B;
            C: if (x == 0)
                  next_state = D;
               else
                  next_state = C;
            D: if (x == 0)
                  next_state = B;
               else
                  next_state = C;
            default: next_state = A;
        endcase
    end

    always @(*) begin
        case (state)
            A, B, D: y = 0;
            C: y = 1;
            default: y = 0;
        endcase
    end
endmodule         
```

<details>
    <summary>Example problem</summary>

<img src="Images/Problem 1.png" alt="Problem 1">
<ul>  
  <details>
    <summary>Solution</summary>

<table border="1" cellpadding="5">
  <tr>
    <th>Current State</th>
    <th>Next State (x = 0)</th>
    <th>Next State (x = 1)</th>
    <th>Output (λ(state))</th>
  </tr>

  <tr>
    <td>A</td>
    <td>A</td>
    <td>B</td>
    <td>0</td>
  </tr>

  <tr>
    <td>B</td>
    <td>A</td>
    <td>C</td>
    <td>0</td>
  </tr>

  <tr>
    <td>C</td>
    <td>A</td>
    <td>D</td>
    <td>0</td>
  </tr>

  <tr>
    <td>D</td>
    <td>A</td>
    <td>D</td>
    <td>1</td>
  </tr>
</table>
</details> 
</ul>  
</details>

### Mealy Model
The Mealy Model has an output that depends on current state and inputs

Here is a sample Mealy Machine Model in Verilog:

```verilog
module mealyeFSM (
    input clk, reset, x,
    output reg y
);

    parameter A = 2'b00, B = 2'b01, C = 2'b10, D = 2'b11;

    reg [1:0] state, next_state;

    always @(posedge clk) begin
        if (reset)
            state <= A;
        else
            state <= next_state;
    end

    always @(*) begin
        case (state)
            A: 
                if (x == 0)
                    next_state = D;
                    y = 1;
                else
                    next_state = B;
                    y = 0;
            B: 
                if (x == 0)
                    next_state = D;
                    y = 1;
                else
                    next_state = C;
                    y = 0;
            C: 
                if (x == 0)
                    next_state = D;
                    y = 1;
                else
                    next_state = A;
                    y = 0;
            D: 
                if (x == 0)
                    next_state = B;
                    y = 1;
                else
                    next_state = C;
                    y = 0;
            default:
                next_state = A;
                y = 0;
        endcase
    end
endmodule         
```

<details>
    <summary>Example problem</summary>

<img src="Images/Problem 2.png" alt="Problem 2">
<ul>  
  <details>
    <summary>Solution</summary>

<table border="1" cellpadding="5">
  <tr>
    <th>Current State</th>
    <th>Next State (x = 0)</th>
    <th>Next State (x = 1)</th>
    <th>Output (λ(state) (x = 0))</th>
    <th>Output (λ(state) (x = 1))</th>
  </tr>

  <tr>
    <td>A</td>
    <td>A</td>
    <td>B</td>
    <td>0</td>
    <td>0</td>
  </tr>

  <tr>
    <td>B</td>
    <td>A</td>
    <td>C</td>
    <td>0</td>
    <td>0</td>
  </tr>

  <tr>
    <td>C</td>
    <td>A</td>
    <td>C</td>
    <td>0</td>
    <td>1</td>
  </tr>
</table>
</details> 
</ul>  
</details>

## Shifter Implementation
The code below is the implementation for a 8-bit left and right shifter

```verilog
module shifter (
    input [7:0] A,
    input [1:0] sel,
    output reg [7:0] Y
);
    always @(*) begin
        case(sel)
            2'b00: Y = A;
            2'b01: Y = A << shiftAmount; //shift left
            2'b10: Y = A >> shiftAmount; //shift right
            default: Y = 8'b0;
        endcase
    end
endmodule
```