# VLSI-LAB-EXPERIMENTS
# AIM:  
    
    To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

# APPARATUS REQUIRED:  

     Vivado 2023.1

# PROCEDURE: 
```
STEP:1  Start the Xilinx navigator, Select and Name the New project. 
STEP:2  Select the device family, device, package and speed. 
STEP:3  Select new source in the New Project and select Verilog Module as the Source type. 
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it. 
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.
STEP:6  Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. 
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window. 
STEP:8  Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 
STEP:10  Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. 
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.
STEP:12  Load the Bit file into the SPARTAN 6 FPGA.
```
# Logic Diagram :

# LOGIC GATES:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/164987794/ec15e34b-144c-4be5-b8a8-144f0d1b367f)
# CODE:
~~~
      module gate(a,b,w1,w2,w3,w4,w5,w6,w7);
      input a,b;
      output w1,w2,w3,w4,w5,w6,w7;
      and g1 (w1,a,b);
      or g2 (w2,a,b);
      not g3 (w3,a);
      xor g4 (w4,a,b);
      xnor g5 (w5,a,b);
      nand g6 (w6,a,b);
      nor g7 (w7,a,b);
      endmodule
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/21178b59-ee9c-492c-aff9-56895d38b585)

# FULL ADDER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/164987794/3b18fd68-eacc-4aec-89d2-4a5a3b3970e7)
# CODE:
~~~
       module fulladder(a,b,cin,sum,carry);
       input a,b,cin;
       output sum,carry;
       wire w1,w2,w3;
       xor g1(w1,a,b);
       xor g2(sum,w1,cin);
       and g3(w2,w1,cin);
       and  g4(w3,a,b);
       or g5(carry,w2,w3);
       endmodule
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/7b2568c8-925a-4a56-9ef5-9fd329f0099d)

# HALF ADDER
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/164987794/c0c7db1e-81f4-4ab8-8cfd-c6d325288e19)
# CODE:
~~~
        module hs(a,b,difference,borrow);
       input a,b;
       output difference,borrow;
       wire w;
       xor g1(difference,a,b);
       and g2(borrow,w,b);
       not g3(w,a);
       endmodule
~~~

# OUTPUT:


![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/6517181d-cdbb-450a-b7e2-dbc8be3f3aa6)

# HALF SUBTRACTOR:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/164987794/79f4adc8-5a18-44ce-ac13-f2ed3a954de9)

# CODE:
~~~
       module hs(a,b,difference,borrow);
       input a,b;
       output difference,borrow;
       wire w;
       xor g1(difference,a,b);
       and g2(borrow,w,b);
       not g3(w,a);
       endmodule
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/74f7e9f5-64b1-40b2-bd9c-dffdb9d02661)

# FULL SUBTRACTOR:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/164987794/6c2366cd-2e78-44f5-90e6-f9c99d1ced54)
# CODE:
~~~
    module fs(a,b,c,diff,borrow);
    input a,b,c;
    output diff,borrow;
    wire w1,w2,w3,w4,w5;
    xor g1(w3,a,b);
    xor g2(diff,c,w3);
    and g3(w2,b,w1);
    and g4(w5,w4,c);
    not g5(w1,a);
    not g6(w4,w3);
    nor g7(borrow,w5,w2);
    endmodule   
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/ba6633a8-7b90-4aa0-91df-434b825bad5c)

# 8 RIPPLE CARRY ADDER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/164987794/67f49edb-d146-4162-8f82-b92689724425)

# CODE:
~~~
       module fa(a,b,cin,sum,carry);
       input a,b,cin;
       output sum,carry;
       wire w1,w2,w3;
       xor g1(w1,a,b);
       and g2(w3,a,b);
       xor g3(sum,w1,cin);
       and g4(w2,w1,cin);
       or g5(carry,w2,w3);
 endmodule
 
 module rca(a,b,cin,sum,cout);
        input[3:0]a,b;
        input cin;
        output [3:0]sum;
        output cout;
        wire w1,w2,w3;
      fa g1(.a(a[0]),
            .b(b[0]),
            .cin(cin),
            .sum(sum[0]),
            .carry(c1)
            );
       fa g2(.a(a[1]),
             .b(b[1]),
             .cin(c1),
             .sum(sum[1]),
             .carry(c2)
             );
       fa g3(.a(a[2]),
             .b(b[2]),
             .cin(c2),
             .sum(sum[2]),
             .carry(c3)
             );
        fa g4(.a(a[3]),
              .b(b[2]),
              .cin(c3),
              .sum(sum[3]),
              .carry(cout)
              );
       endmodule
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/9e77cc35-146e-4c43-99a9-5e8ff4192ab5)

# RESULT:
```
   Hence, the stimulation and synthesis of a Logic Gates,Adders and Subtractor was run successfully by using Xilinx ISE.
```
