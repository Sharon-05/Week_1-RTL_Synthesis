
# Day 4: Gate-Level Simulation (GLS), Blocking vs. Non-Blocking in Verilog, and Synthesis-Simulation Mismatch  

---



### 3.1 Blocking Statements (`=`)  
- Sequential execution  
- Good for combinational logic  
```verilog
always @(*) y = a & b;
```

### Lab 1: Ternary Operator MUX
```

module ternary_operator_mux (input i0, input i1, input sel, output y);
  assign y = sel ? i1 : i0;
endmodule
```

Function: y = sel ? i1 : i0

<img width="1210" height="773" alt="image" src="https://github.com/user-attachments/assets/9deb816f-d445-4da4-ae1a-5ef5d43234e6" />


<img width="1210" height="773" alt="Screenshot from 2025-10-01 18-12-50" src="https://github.com/user-attachments/assets/7dcc23b4-0958-44f4-b1eb-16d55b39f6c2" />

### Lab 2: Synthesis Using Yosys

Synthesize MUX with Yosys standard flow.

### Lab 3: GLS of MUX

### Lab 4: Bad MUX Example
```
module bad_mux (input i0, input i1, input sel, output reg y);
 always @(*) begin
  if (sel)
    y = i1;
  else
    y = i0;
end

```
<img width="1278" height="793" alt="image" src="https://github.com/user-attachments/assets/dc6ba5fe-c320-471e-a72c-55b455f7564e" />


<img width="1272" height="799" alt="image" src="https://github.com/user-attachments/assets/b22f0528-6722-43b7-af5f-18c389edcbfb" />


### Lab 6: Blocking Assignment Caveat
```
module blocking_caveat (input a, input b, input c, output reg d);
  reg x;
always @(*) begin
  x = a | b;
  d = x & c;
end
```

Output:
<img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/ea99e8a7-7298-4153-b050-69020767688c" />




### Lab 7: Synthesis of Blocking Caveat

Synthesize corrected module and check results.

Output:


<img width="1275" height="796" alt="image" src="https://github.com/user-attachments/assets/84a6df08-3041-4d2e-82b6-50dad5ce4bb5" />


### Summary

GLS: Validates netlist functionality, timing, and testability.

Mismatch: Caused by bad RTL practices → avoid non-synthesizable constructs.

Blocking vs. Non-Blocking: Use = for combinational, <= for sequential logic.

Labs: Practiced good coding style and checked GLS outputs.

