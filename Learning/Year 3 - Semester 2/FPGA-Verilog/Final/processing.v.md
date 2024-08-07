### Variable declairation
```verilog
reg [ 9:0] rowIndex;
reg [10:0] colIndex;
reg [18:0] pixelDataCount;
```
The size of each variable cover the maximum value it can handle:
- rowIndex: 512
- colIndex: 768
- pixelDataCount: 196607

### Reading data from input file
```verilog
if (start == 1'b1) begin
```
The **start** variable is controlled through reset button.

```verilog
temp_BMP[i] = totalMemory[i][7:0];
```
Reading each bytes of RGB value from image to temp_BMP, there is an implicit conversion expands from 8 to 32 bits since temp_BMP is declaired with integer parameter.

```verilog
      for (i = 0; i < HEIGHT; i = i + 1) begin
        for (j = 0; j < WIDTH; j = j + 1) begin
          tempRedValue[WIDTH*i+j]   = temp_BMP[WIDTH*3*(HEIGHT-i-1)+3*j+0];
          tempGreenValue[WIDTH*i+j] = temp_BMP[WIDTH*3*(HEIGHT-i-1)+3*j+1];
          tempBlueValue[WIDTH*i+j]  = temp_BMP[WIDTH*3*(HEIGHT-i-1)+3*j+2];
        end
      end
```
Here, we write all of the red, green, blue pixels to corresponding temporary variables, the iteration will go for each column from each row.
We access the corresponding value in temp_BMP variable by indexing using: 
- `WIDTH*3`: To skip the entire column of one row.
- `WIDTH*3*(HEIGHT-i-1)`: To skip the number of rows specified by **i**, here we are accessing from bottom to top so we will use the subtraction.
- `+3*j+0`: The corresponding value of Red, Green or Blue indexed by **j**.

### FSM for reading RGB888 and creating hsync and vsync pulse
```verilog
if (~HRESET) currentState <= ST_IDLE;
```
Here, we are using ~HRESET instead of !HRESET.

### Data counting
```verilog
assign ctrl_done = (pixelDataCount == 196607) ? 1'b1 : 1'b0;
```
The **196607** value indicates the maximum index of the entire image pixels. Since we are processing 2 pixels at the same time, it will be `768*512/2 = 196607`

### IMAGE PROCESSING
##### BRIGHTNESS ADDITION
Optimized from 
```verilog
tempConBriR0 = tempRedValue[WIDTH*rowIndex+colIndex] + BRIGHTNESS_VALUE;
	if (tempConBriR0 > 255) DATA_R0 = 255;
	else DATA_R0 = tempRedValue[WIDTH*rowIndex+colIndex] + BRIGHTNESS_VALUE;
```
To
```verilog
tempConBriR0 = tempRedValue[WIDTH*rowIndex+colIndex] + BRIGHTNESS_VALUE;
    if (tempConBriR0 > 255) DATA_R0 = 255;
    else DATA_R0 = tempConBriR0;
```
