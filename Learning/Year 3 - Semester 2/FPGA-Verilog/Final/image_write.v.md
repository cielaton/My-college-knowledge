In module declaration, using parameter `OUTPUT_FILE` instead of `INFILE` in the document.

### Writing data to the temp memory
The main write operation:
```verilog
bmpOut[WIDTH*3*(HEIGHT-rowIndex-1)+6*colIndex+2] <= DATA_WRITE_R0;
bmpOut[WIDTH*3*(HEIGHT-rowIndex-1)+6*colIndex+1] <= DATA_WRITE_G0;
bmpOut[WIDTH*3*(HEIGHT-rowIndex-1)+6*colIndex+0] <= DATA_WRITE_B0;
bmpOut[WIDTH*3*(HEIGHT-rowIndex-1)+6*colIndex+5] <= DATA_WRITE_R1;
bmpOut[WIDTH*3*(HEIGHT-rowIndex-1)+6*colIndex+4] <= DATA_WRITE_G1;
bmpOut[WIDTH*3*(HEIGHT-rowIndex-1)+6*colIndex+3] <= DATA_WRITE_B1;
```
Here, we write in the inverse row direction just the same as read operation, but write 6 values (2pixels a time). Also, the Blue value comes first, then Green, then Red.
