##Aim:
Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

#Tool Required:
Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

#Synthesis: Genus

#Step 1: Getting Started
Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

◦ SDC (Synopsis Design Constraint) File (.sdc)

#Step 2 : Creating an SDC File
• In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

• The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii, iii → Sets Clock Rise and Fall time to 100ps.

iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

Step 3 : Performing Synthesis
The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#Synthesis RTL Schematic :
4 exp
![WhatsApp Image 2024-11-14 at 14 21 40_0fd0d85c](https://github.com/user-attachments/assets/51a8b520-b981-46cc-8bad-652006f4c3b2)

#Area report:
exp part 2
![WhatsApp Image 2024-11-14 at 14 21 53_9159fea9](https://github.com/user-attachments/assets/d65de4cb-1649-4774-a7b0-e2b89156a23f)

#Power Report:
exp part 3
![WhatsApp Image 2024-11-14 at 14 22 14_462dc2b8](https://github.com/user-attachments/assets/fa6aad81-3c1f-4b29-a7b0-5eaf1a2a5deb)

#Timing Report:
exp part 4
![WhatsApp Image 2024-11-14 at 14 22 26_a16b9a98](https://github.com/user-attachments/assets/25ba451d-25e6-4c2c-b58f-d23d11b762ab)


#Result:
The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.
