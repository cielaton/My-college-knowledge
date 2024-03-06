---
{}
---
A module is the basic building block in Verilog. Typically, elements are grouped into modules to provide common functionality that is used at many places in the design.

>Typically, elements are grouped into modules to provide common functionality to the higher-level block through its port interface (input and output), but hides the internal implementation.

In Verilog, a module is declared by the keyword **module**. A corresponding keyword **endmodule** must appear at the end of the module definition.
Each module must have a *module_name*, which is the identifier for the module, and a *module_terminal_list*, which describes the input and output terminals of the module.

```verilog
module <module_name> (<module_terminal_list>);
...
<module internals>
...
...
endmodule
```

For example, the T-flipflop could be defined as:

```verilog
module T_FF (q, clock, reset);
.
.
<functionality of T-flipflop>
.
.
endmodule
```

---
Verilog is both a behavioral and structural language. Internals of each module can be defined at *four* levels of abstraction, depending on the needs of the design.
- Behavioral or algorithmic level
	This is the highest level of abstraction provided by Verilog HDL. A module can be implemented in terms of the design algorithm without concern for the hardware implementation details. Designing at this level is very similar to C programming.
- Dataflow level
	The module is designed by specifying the data flow. The designer is aware of how data flows between hardware registers and how the data is processed in the design.
- Gate level
	The module is implemented in terms of logic gates and interconnections between these gates.
- Switch level
	This is the lowest level of abstraction provided by Verilog. A module can be implemented in terms of switches, storage nodes, and the interconnections between them. 

The term *register transfer level* (**RTL**) is frequently used for a Verilog description that uses a combination of behavior and data flow constructs and is acceptable to logic synthesis tools.

> In the higher level language such as C, the program can be easily ported to any machine. However, assembly cannot replicate the same behavior.

