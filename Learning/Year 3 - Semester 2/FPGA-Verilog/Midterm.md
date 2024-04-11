### Problem 1:
1. What is Verilog and what it is used for?
	Verilog is a general purpose hardware description language use to design hardware. It can also be used to describe the functionality of hardware as well as it's implementation.
2. What are the different types of data types in Verilog?
- Scalar: a single bit. The value can be one of: 
	- 0 
	- 1
	- x - Unknown
	- z - High-impedance
- Vector: Multi-bit quantity
	- Example: `wire [msb:lsb] w1`;
- Integer: Signed, 2-s complement value. It is delared in an integer statement, and it is a register.
- Real: Real values contained in registers which are declared as real.
- Time: 64-bit value, unsigned intergers, use to store simulation time quantities.
3. How do you specify a delay in Verilog?
	You can specify the delay using the hash character with a delay time: `#<delay time unit>`.
4. What is an always block in Verilog and when it is used?
5. **Always** is a procedural blocks in Verilog, it allows you to write executable statements. With **always**, after the block is done executing, it will be execute again.

### Problem 2:
Write a switch-level model of a static RAM below:
![[Screenshot_20240329_160532.png]]

```verilog
module staticRam (
    din,
    write,
    addr,
    dout
);
  input din, write, addr;
  output dout;

  wire dio, dv, ds;

  bufif1 wctl (dio, din, write);
  tranif1 ag (dv, dio, addr);

  not s1 (ds, dv), s2 (dv, ds);

  buf b1 (dout, dio);
endmodule
```

### Problem 3:
Write a 1-bit full adder.
```verilog
module dffWithSynchronousEnable (
    d,
    en,
    clk,
    reset,
    q
);
  input d, en, clk, reset;
  output q;
  wire r_next;

  clkGen #(10) clk_gen (clk);

  muxer main_muxer (
      .d(d),
      .en(en),
      .r_reg(q),
      .r_next(r_next)
  );
  base_dff main_dff (
      .d(r_next),
      .clk(clk),
      .reset(reset),
      .q(q)
  );


endmodule

module base_dff (
    d,
    q,
    clk,
    reset
);
  input d, clk, reset;
  output q;
  reg qTemp;

  always @(posedge clk) begin
    if (reset) qTemp <= 1'b0;
    else qTemp <= d;
  end

  assign q = qTemp;
endmodule

module muxer (
    d,
    en,
    r_reg,
    r_next
);
  input d, en, r_reg;
  output r_next;

  assign r_next = en ? d : r_reg;
endmodule

module clkGen (
    clk
);
  parameter period = 2;
  reg clk;
  output clk;

  initial clk = 0;
  always #(period / 2) clk = ~clk;
endmodule

```

### Problem 4:
1. Write the code that implement the 1-bit comparator with UDP:
![[Screenshot_20240329_155641.png]]

```verilog
module comparator (
    i0,
    i1,
    eq
);
  input i0, i1;
  output eq;

  wire i0_, i1_, p0, p1;

  not_udp not0 (
      i0_,
      i0
  );
  not_udp not1 (
      i1_,
      i1
  );

  and_udp
      and_neg (
          p0,
          i0_,
          i1_
      ),
      and_norm (
          p1,
          i0,
          i1
      );

  or_udp out_eq (
      eq,
      p0,
      p1
  );
  
endmodule


primitive not_udp(out, in);
  input in;
  output out;

  table
    // in : out;
    0 : 1;
    1 : 0;
  endtable
endprimitive

primitive and_udp(out, in1, in2);
  input in1, in2;
  output out;

  table
    //in1 in2 : out 
    0 0 : 0;
    0 1 : 0;
    1 0 : 0;
    1 1 : 1;
  endtable
endprimitive

primitive or_udp(out, in1, in2);
  input in1, in2;
  output out;

  table
    //in1 in2 : out
    0 0 : 0;
    0 1 : 1;
    1 0 : 1;
    1 1 : 1;
  endtable
endprimitive

```

2. Rewrite using Gate-level implementation:
```verilog
module comparator (
    i0,
    i1,
    eq
);
  input i0, i1;
  output eq;

  wire i0_, i1_, p0, p1;

  not not0 (i0_, i0);
  not not1 (i1_, i1);


  and and_neg (p0, i0_, i1_), and_norm (p1, i0, i1);

  or out_eq (eq, p0, p1);

endmodule
```

3. Rewrite using RTL always block:
```verilog
module comparator (
    i0,
    i1,
    eq
);
  input i0, i1;
  output eq;

  reg i0_, i1_, p0, p1, eq_val;

  always @(*) begin
    i0_ = ~i0;
    i1_ = ~i1;

    p0 = i0_ & i1_;
    p1 = i0 & i1;

    eq_val = p0 | p1;
  end

  assign eq = eq_val;
endmodule
```

### Problem 5:
Write the code that implement a DFF with synchronous enable: 
![[Screenshot_20240329_160216.png]]

```verilog
module dffWithSynchronousEnable (
    d,
    en,
    clk,
    reset,
    q
);
  input d, en, clk, reset;
  output q;
  wire r_next;

  clkGen #(10) clk_gen (clk);

  muxer main_muxer (
      .d(d),
      .en(en),
      .r_reg(q),
      .r_next(r_next)
  );
  base_dff main_dff (
      .d(r_next),
      .clk(clk),
      .reset(reset),
      .q(q)
  );


endmodule

module base_dff (
    d,
    q,
    clk,
    reset
);
  input d, clk, reset;
  output q;
  reg qTemp;

  always @(posedge clk) begin
    if (reset) qTemp <= 1'b0;
    else qTemp <= d;
  end

  assign q = qTemp;
endmodule

module muxer (
    d,
    en,
    r_reg,
    r_next
);
  input d, en, r_reg;
  output r_next;

  assign r_next = en ? d : r_reg;
endmodule

module clkGen (
    clk
);
  parameter period = 2;
  reg clk;
  output clk;

  initial clk = 0;
  always #(period / 2) clk = ~clk;
endmodule

```