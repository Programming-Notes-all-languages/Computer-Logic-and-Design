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

<details>
    <summary>Example problem</summary>

<img src="Images/Example Problems/Problem 1.png" alt="Problem 1">
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

<details>
    <summary>Example problem</summary>

<img src="Images/Example Problems/Problem 2.png" alt="Problem 2">
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