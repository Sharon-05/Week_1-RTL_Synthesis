# Day 1: Introduction to Verilog RTL Design & Synthesis
### Table of Contents

-   Lab: Simulating a 2-to-1 Multiplexer
-   Verilog Code Analysis
-   Introduction to Yosys & Gate Libraries
-   Synthesis Lab with Yosys
-   Summary

---


`iverilog` is an open-source simulator for Verilog. Here’s the typical simulation flow:

-   Both the design and testbench are provided as input to `iverilog`.
-   The simulator produces a `.vcd` file for waveform viewing in `GTKWave`.


**Step 1: Clone the Workshop Repository**
```bash
git clone [https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git](https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git)
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
```

<img width="1280" height="800" alt="Screenshot from 2025-09-27 16-26-32" src="https://github.com/user-attachments/assets/843c0510-764d-4fa7-9bf5-adece86ab45a" />

```
sudo apt install iverilog
sudo apt install gtkwave
```
<img width="1280" height="800" alt="Screenshot from 2025-09-27 16-28-43" src="https://github.com/user-attachments/assets/aa3dfcd1-61cb-4d40-adb9-8679f80bcfd1" />

```
iverilog good_mux.v tb_good_mux.v
```

```
gtkwave tb_good_mux.vcd
```
<img width="1280" height="800" alt="Screenshot from 2025-09-27 16-46-36" src="https://github.com/user-attachments/assets/4dfe708f-27e1-4dfe-a7e1-8e0561df25d8" />


<img width="1280" height="800" alt="Screenshot from 2025-09-27 16-28-43" src="https://github.com/user-attachments/assets/3cba7cb3-ab38-4063-bf0a-52fbc9be1c29" />

```
module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*)
begin
if(sel)
y <= i1;
else
y <= i0;
end
endmodule


`timescale 1ns / 1ps
module tb_good_mux;
// Inputs
reg i0,i1,sel;
// Outputs
wire y;

        // Instantiate the Unit Under Test (UUT)
good_mux uut (
.sel(sel),
.i0(i0),
.i1(i1),
.y(y)
);

initial begin
$dumpfile("tb_good_mux.vcd");
$dumpvars(0,tb_good_mux);
// Initialize Inputs
sel = 0;
i0 = 0;
i1 = 0;
#300 $finish;
end

always #75 sel = ~sel;
always #10 i0 = ~i0;
always #55 i1 = ~i1;
endmodule

yosys
```
<img width="1210" height="773" alt="Screenshot from 2025-09-27 18-08-17" src="https://github.com/user-attachments/assets/1b26372a-d8fc-4605-be9e-5d40e586ad34" />

```


read_liberty -lib /path/to/your/sky130_fd_sc_hd__tt_025C_1v80.lib

read_verilog ./good_mux.v
```


<img width="1210" height="773" alt="Screenshot from 2025-09-27 18-59-44" src="https://github.com/user-attachments/assets/4ac8c76b-cf6f-45c3-bb8d-08b3af4183a0" />


```
abc -liberty /path/to/your/sky130_fd_sc_hd__tt_025C_1v80.libabc -liberty /path/to/your/sky130_fd_sc_hd__tt_025C_1v80.lib
```


<img width="1210" height="773" alt="Screenshot from 2025-09-27 18-12-20" src="https://github.com/user-attachments/assets/328a7c54-e72c-4e24-9a1a-2d205bf99f9e" />


**Summary**

Learned about simulators, designs, and testbenches.

Ran your first Verilog simulation with iverilog and visualized waveforms.

Analyzed the 2-to-1 mux code.

Explored Yosys and learned why gate libraries have various flavors.


<img width="1210" height="773" alt="image" src="https://github.com/user-attachments/assets/a128629b-fe56-4159-ae5e-651f0f4a56be" />



