# Day 1 - Introduction to Verilog RTL design and Synthesis

The Reposetory is about day 1 of week 1 of RISC‑V Reference SoC Tapeout Program.
In this day I learn about RTL design and synthesys.

table of content
1. Introduction to open-source simulator iverilog
2. Labs using iverilog and gtkwave
3. Introduction to Yosys and Logic synthesis
4. Labs using Yosys and Sky130 PDKs

## 1. Introduction to open-source simulator iverilog

In this lecture I learn about the verilog HDL and iverilog. Verilog is hardware discription language. which describe the behaviour of the hardwave. To language are currently exict 1. verilog. 2. VHDl. Verilog is based on C language, case sensitive language.
iverilog is the tool which helps to simulaten the verilog code. Here I learn about the RTL simulation.

The flow of the iverilog is as shown below.
![Alt Text](iverilog_flow.png)

To simulate our design we need two file. 1. design file. 2. Testbench. The design file is having the code of out design and testbench file have the funcionlity to verify our design. There are two approch to verify out design. 1. teshbench 2. DUT. in testbench we simply apply our testvector and get our output and compare it with desired vectors. But in DUT. we design testbench which generate test vectors [ may having same functionality or not] and design. put in DUT. which verify our design. gives scores feedbacks 

## 2. Labs using iverilog and gtkwave

First we have to clone our project from the github
'''bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
'''
Clone this reposetory in our project. It have standard cells of sky130 and some projects for our demo.

Then install the required softwares as week 0.
To simulate 2x1 mux we type
'''bash 
iverilog good_mux.v tb_good_mux.v
'''
where good_mux.v is our design and tb_good_mux.v is our testbench

to execute the simulation we type
'''bash
./a.out
'''
which gives one tb_good_mux.vcd file
Note: The vcd file named as Value Change Dump Contains metadata like the date the file was created, the version of the simulator, and the timescale used in the simulation. This is generate if we include two lines
'''verilog
$dumpfile("tb_good_mux.vcd");
$dumpvars(0, tb_good_mux);
''' 
in initial block of the testbench

to view our simulation result we use another tool named as GTK wave. It is the waveform viewer tool which shows simulation results in waveform. note that it required.vcd file to view the result.
![Alt Text](
gtkwave_goodmux.png)
