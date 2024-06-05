### Reading data from input file
```verilog
if (start == 1'b1) begin
```
The **start** variable shoud be assign to a button, signal whether the read process should begin.

```verilog
temp_BMP[i] = totalMemory[i][7:0];
```
Reading each bytes of RGB value from image to temp_BMP, there is an implicit conversion expands from 8 to 32 bits since temp_BMP is declaired with integer parameter.

