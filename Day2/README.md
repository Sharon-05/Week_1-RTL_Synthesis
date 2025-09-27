Day 2: Timing Libraries, Synthesis Approaches, and Efficient Flip-Flop Coding

Contents
Timing Libraries

Hierarchical vs. Flattened Synthesis

Flip-Flop Coding Styles

Simulation and Synthesis Workflow

Summary

1. Timing Libraries
SKY130 PDK Overview
The SKY130 PDK is an open-source Process Design Kit based on SkyWater Technology's 130nm CMOS technology. It provides essential models and libraries for integrated circuit (IC) design, including timing, power, and process variation information.

Decoding tt_025C_1v80 in the SKY130 PDK
tt: Typical-Typical (TT) process corner.

025C: Represents a temperature of 25°C, relevant for temperature-dependent performance.

1v80: Indicates a core voltage of 1.8V.

This naming convention clarifies which process, voltage, and temperature (PVT) conditions the library models.

Opening and Exploring the .lib File
To open the sky130_fd_sc_hd__tt_025C_1v80.lib file:

<img width="1210" height="773" alt="Screenshot from 2025-09-27 23-43-39" src="https://github.com/user-attachments/assets/14567575-79af-46c5-b420-59c62e47722d" />



```
```
2

Verilog

module dff_asyncres (
    input clk, 
    input async_reset, 
    input d, 
    output reg q
);
  always @ (posedge clk, posedge async_reset)
    if (async_reset)
      q <= 1'b0;
    else
      q <= d;
endmodule
Asynchronous Set D Flip-Flop
Overrides the clock to set the output to 1 immediately.

Verilog

module dff_async_set (
    input clk, 
    input async_set, 
    input d, 
    output reg q
);
  always @ (posedge clk, posedge async_set)
    if (async_set)
      q <= 1'b1;
    else
      q <= d;
endmodule
Synchronous Reset D Flip-Flop
The reset only takes effect on the next rising clock edge.

Verilog

module dff_syncres (
    input clk, 
    input sync_reset, 
    input d, 
    output reg q
);
  always @ (posedge clk)
    if (sync_reset)
      q <= 1'b0;
    else
      q <= d;
endmodule
```
multiple_modules.v
```
<img width="1210" height="773" alt="Screenshot from 2025-09-28 00-08-53" src="https://github.com/user-attachments/assets/4dabcd19-bc2e-4054-920a-a69bf831fe8d" />

```
synthesizing

```

<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/949a30ba-1863-4697-b731-b6370798c34f" />

```
running abc

```
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/1af78980-1f1e-4b16-aae0-39f2988dd1bf" />

heir.v
<img width="1210" height="773" alt="image" src="https://github.com/user-attachments/assets/fb9342b3-4a18-4aed-84f6-5e8592750b9e" />

show multiple_modules.v

<img width="1210" height="773" alt="image" src="https://github.com/user-attachments/assets/692eb081-c62b-4621-ac55-ce574569dc89" />






5. Summary
This overview provides you with practical insights into timing libraries, synthesis strategies, and reliable coding practices for flip-flops. Continue experimenting with these concepts to deepen your understanding of RTL design and synthesis.
