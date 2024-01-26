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
