# Exp-No: 02 - Write and simulate seven segment display using Verilog HDL and verify with testbench
## Aim:

  To design and simulate a Seven Segment using Verilog HDL and verify its functionality through a testbench using the Vivado 2023.1 simulation environment.
## Apparatus Required:

  Vivado 2023.1

## Procedure:


Launch Vivado Open Vivado 2023.1 by double-clicking the Vivado icon or searching for it in the Start menu.
Create a New Project Click on "Create Project" from the Vivado Quick Start window. In the New Project Wizard: Project Name: Enter a name for the project (e.g., Mux4_to_1). Project Location: Select the folder where the project will be saved. Click Next. Project Type: Select RTL Project, then click Next. Add Sources: Click on "Add Files" to add the Verilog files (e.g., mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.). Make sure to check the box "Copy sources into project" to avoid any external file dependencies. Click Next. Add Constraints: Skip this step by clicking Next (since no constraints are needed for simulation). Default Part Selection: You can choose a part based on the FPGA board you are using (if any). If no board is used, you can choose any part, for example, xc7a35ticsg324-1L (Artix-7). Click Next, then Finish.
Add Verilog Source Files In the "Sources" window, right-click on "Design Sources" and select Add Sources if you didn't add all files earlier. Add the Verilog files (mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.) and the testbench (mux4_to_1_tb.v).
Check Syntax Expand the "Flow Navigator" on the left side of the Vivado interface. Under "Synthesis", click "Run Synthesis". Vivado will check your design for syntax errors. If any errors or warnings appear, correct them in the respective Verilog files and re-run the synthesis.
Simulate the Design In the Flow Navigator, under "Simulation", click on "Run Simulation" → "Run Behavioral Simulation". Vivado will open the Simulations Window, and the waveform window will show the signals defined in the testbench.
View and Analyze Simulation Results 
Adjust Simulation Time To run a longer simulation or adjust timing, go to the Simulation Settings by clicking "Simulation" → "Simulation Settings". Under "Simulation", modify the Run Time (e.g., set to 1000ns).
Generate Simulation Report Once the simulation is complete, you can generate a simulation report by right-clicking on the simulation results window and selecting "Export Simulation Results". Save the report for reference in your lab records.
Save and Document Results Save your project by clicking File → Save Project. Take screenshots of the waveform window and include them in your lab report to document your results. You can include the timing diagram from the simulation window showing the correct functionality of the Seven Segment across different select inputs and data inputs.
Close the Simulation Once done, by going to Simulation → "Close Simulation

## Input/Output Signal Diagram:

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/ec53a276-0495-4938-b7a4-1913f8498113" />

## RTL Code:
```
module Sevensegment(bcd,seg);
input[3:0]bcd;
output reg[6:0]seg;
always@(bcd)
begin
     case(bcd)
     4'b0000:seg=7'b0111111;
     4'b0001:seg=7'b0001010;
     4'b0010:seg=7'b1110011;
     4'b0011:seg=7'b1011011;
     4'b0100:seg=7'b1001110;
     4'b0101:seg=7'b1011101;
     4'b0110:seg=7'b1111101;
     4'b0111:seg=7'b0001011;
     4'b1000:seg=7'b1111111;
     4'b1001:seg=7'b1011111;
     default:seg=7'b0000000;
     endcase
end
endmodule
```
## TestBench:
```
module Sevensegment_tb;
  reg [3:0] bcd_tb;
  wire [6:0] seg_tb;

  Sevensegment dut(.bcd(bcd_tb),.seg(seg_tb));

initial 
  begin
    bcd_tb = 4'b0000; 
    #100;
    bcd_tb = 4'b0001; 
    #100;
    bcd_tb = 4'b0010; 
    #100;
    bcd_tb = 4'b0011; 
    #100;
    bcd_tb = 4'b0100; 
    #100;
    bcd_tb = 4'b0101; 
    #100;
    bcd_tb = 4'b0110; 
    #100;
    bcd_tb = 4'b0111; 
    #100;
    bcd_tb = 4'b1000; 
    #100;
    bcd_tb = 4'b1001; 
    #100;
  end
endmodule
```
## Output waveform:

<img width="1919" height="1199" alt="Screenshot 2025-09-07 172529" src="https://github.com/user-attachments/assets/0324a268-cd6e-4dde-b632-dfa4ee50bb60" />


## Conclusion:

The Seven Segment Display experiment successfully demonstrated how numerical values (0–9) can be represented using a combination of illuminated segments. By giving the proper binary or BCD inputs to the decoder/driver circuit, the display showed the corresponding digit clearly. This experiment helped in understanding the working principle of segment displays, the concept of active high/active low configurations, and the importance of digital logic in driving display devices. It also established the practical application of combinational logic circuits in real-time devices such as calculators, digital clocks, and measuring instruments.
