<ul>
  <li>
    <a>Binary addition:</a>
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
        <summary>Example</summary>
          <pre>
            <code>

| | | | | | | | | | 
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| carry | | 1 | 1 | 1 | 1 |  |  |  |
| | 0 | 0 | 1 | 1 | 0 | 1 | 1 | 0 |
| + | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 |
| **result:** |  **0** | **1** | **0** | **1** | **0** | **0** | **1** | **1** |  
          </code>
        </pre>   
      </details>
    <a>Binary subtraction:</a>
