Day 5 - Optimization in synthesis

TOC

If Case constructs

Labs on "Incomplete If Case"

Labs on "Incomplete overlapping Case"

for loop and for generate

Labs on "for loop" and "for generate"

1. If Case constructs

If and case statement

how to use where to use

incomplete if and case statements

inffered latch

if without else
if we make counter. it needs

in case no overlaping cases.

Labs:
incomplete if
```verilog
module incomp_if (input i0 , input i1 , input i2 , output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
end
endmodule
```
discuss problem in short
waveform:
![](if1_gtk.png)
synthsized netlist:
![](if1_net.png)

```verilog
module incomp_if2 (input i0 , input i1 , input i2 , input i3, output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
	else if (i2)
		y <= i3;

end
endmodule
```
discuss problem in short
waveform:
![](if2_gtk.png)
synthsized netlist:
![](if2_net.png)
