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
```bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
Clone this reposetory in our project. It have standard cells of sky130 and some projects for our demo.

Then install the required softwares as week 0.
To simulate 2x1 mux we type
```bash 
iverilog good_mux.v tb_good_mux.v
```
where good_mux.v is our design and tb_good_mux.v is our testbench

to execute the simulation we type
```bash
./a.out
```
which gives one tb_good_mux.vcd file
Note: The vcd file named as Value Change Dump Contains metadata like the date the file was created, the version of the simulator, and the timescale used in the simulation. This is generate if we include two lines
```verilog
$dumpfile("tb_good_mux.vcd");
$dumpvars(0, tb_good_mux);
```
in initial block of the testbench

to invoke this we type
```bash
gtkwave tb_good_mux.vcd
```
in our terminal.
to view our simulation result we use another tool named as GTK wave. It is the waveform viewer tool which shows simulation results in waveform. note that it required.vcd file to view the result.
![Alt Text](gtkwave_goodmux.png)


## 3. Introduction to Yosys and Logic synthesis

The RTL level code is just like demo or idea which can be use to visualise the design. We need to covert it in actual hardware circuit. Their we need one synthesizer which conver the RTL level code to gate lavel. Here we need another tool name as yosys. anothe opensource tool which synthesize our RTL code.

![Alt Text](yosys_flow.png)

yosys convert the RTL code to netlist using liberary file. library file containing many standard cells. The standard cells we can say a pre define circuit madeup with mosfets or some gates. having the information about power consumption of the cells, temperature, delay information, area, and many other specification. the standart cell is provided by the foundry who makes our chip.

The netlist is the circuit version of the our design. we can simulate the gate level circuit through iverilog and GTK wave also.

By observing the library we have lots lots of standard cells having differen different logics and diffenet different specification. I observe the same mux having different different atributes, vary from slow, midium, typical, good, and many more.

this are can be use as per our design specification.
let me give you one example.
#### steup time
![Alt Text](setuptime.png)

the setuptime is time before the clock edge input should be stable. This we have to qualify otherwise our circuit goes into metastange we can't get desired output.
the total delay is given in figure. this can use to determine max frequency of the design.

#### holdtime
![Alt Text](holdtime.png)

The holdtime is time after the output. input should be stable. this is determine by in figure. here I notice that to setisfy the hold condition I have to play with the combinatinal circuit delay. which may be effect on clock frequency also.


