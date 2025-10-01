
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
  always @ (sel) begin
    if (sel)
      y <= i1;
    else 
      y <= i0;
  end
endmodule
```
<img width="1278" height="793" alt="image" src="https://github.com/user-attachments/assets/dc6ba5fe-c320-471e-a72c-55b455f7564e" />

<img width="957" height="611" alt="image" src="https://github.com/user-attachments/assets/ae2fde86-472c-4ee4-845e-a6f53e649622" />



