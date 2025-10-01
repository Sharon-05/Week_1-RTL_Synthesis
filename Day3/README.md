# Day 3: Combinational and Sequential Optimization  


---

### Lab 1  
**Verilog Code:**  
```verilog
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```
<img width="1280" height="800" alt="Screenshot from 2025-10-01 09-41-15" src="https://github.com/user-attachments/assets/db52b3d6-287f-48d5-a068-aff48309114f" />

### Lab 2
```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

<img width="1280" height="800" alt="Screenshot from 2025-10-01 09-43-20" src="https://github.com/user-attachments/assets/4047a910-998d-4374-9850-69b629fe99df" />


###Lab 3
```
module opt_check3 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

<img width="1280" height="800" alt="Screenshot from 2025-10-01 09-44-07" src="https://github.com/user-attachments/assets/067c27f2-ad0e-472f-954f-3e2ab8b0a2c4" />


###Lab 4
```
module opt_check4 (input a , input b , input c , output y);
 assign y = a?(b?(a & c ):c):(!c);
endmodule
```

<img width="1280" height="800" alt="Screenshot from 2025-10-01 09-44-33" src="https://github.com/user-attachments/assets/9ced4a30-9cf4-497c-9e3b-a9ae0649309f" />

### Lab 5
```
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```
<img width="1280" height="800" alt="Screenshot from 2025-10-01 09-46-59" src="https://github.com/user-attachments/assets/f053115c-f06e-4bbb-a634-7f35a6741d4e" />

### Lab 6
```module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```
<img width="1280" height="800" alt="Screenshot from 2025-10-01 09-58-40" src="https://github.com/user-attachments/assets/51be8d7e-c36f-4e06-9742-1e7ed042ea4d" />


###Summary

Focus: Optimization techniques for combinational and sequential circuits in digital design, with practical Verilog labs.

Topics Covered:

Constant Propagation

State Optimization

Cloning

Retiming

6 Labs with Verilog examples and outputs





