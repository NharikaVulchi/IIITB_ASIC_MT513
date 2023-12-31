## DAY 0 Software Installation
<details>
    <summary>
Yosys  
        </summary>
I installed Yosys using the following commands:  

```
$ git clone https://github.com/YosysHQ/yosys.git  
$ cd yosys-master   
$ sudo apt install make (If make is not installed please install it)   
$ sudo apt-get install build-essential clang bison flex \  
    libreadline-dev gawk tcl-dev libffi-dev git \  
    graphviz xdot pkg-config python3 libboost-system-dev \  
    libboost-python-dev libboost-filesystem-dev zlib1g-dev  
$ make config-gcc  
$ make   
$ sudo make install
```
Below is the screenshot showing successfull launch  
![Screenshot from 2023-08-01 16-03-00](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/fb581d7c-6b2c-46b2-bdbf-7c7918120f3d)
</details>
<details>
    <summary>
iverilog  
    </summary>
verilog is installed using the following command 

    
```
$ sudo apt-get install iverilog
```
Screenshot of successfull installation
![Screenshot from 2023-08-01 16-03-21](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/b8d04ceb-79a9-4d3a-aa28-5dad568500a9)
</details>
<details>
    <summary>
gtkwave
    </summary>
installation steps

    
```
$ sudo apt-get install gtkwave
```
![Screenshot from 2023-08-01 16-03-35](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/ae5859fc-87db-4f9d-948b-a1a20f28ed24)
![Screenshot from 2023-08-01 16-03-49](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/2e1bbbfd-b976-45f4-b460-92bc185b882e)

</details>

<details>
    <summary>
        OpenSTA
    </summary>
Install the dependencies using the following command:

    
```
$ sudo apt-get install cmake clang gcc tcl swig bison flex 
```   
Install OpenSTA using the below code:

```
$ git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
$cd OpenSTA
$mkdir build
$cd build
$cmake ..
$make
```
Screenshot showing successful installation
![Screenshot from 2023-08-03 19-29-33](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/40c8e64b-f50a-4946-9738-fd40501accd8)
</details> 
<details>
    <summary>
        NGSPICE
    </summary>
Dowmload the tarball from https://sourceforge.net/projects/ngspice/files/ and use the following code to unpack and install ngspice:

```
$ tar -zxvf ngspice-40.tar.gz
$ cd ngspice-40
$ mkdir release
$ cd release
$ ../configure  --with-x --with-readline=yes --disable-debug
$ make
$ sudo make install
```
Screenshot showing successful installation:


![Screenshot from 2023-08-03 19-20-49](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/a56e723d-878b-444f-82c8-a7a63dd2a615)
</details>
<details>
    <summary>
        Magic
    </summary>

Install magic using the following code snippet:
```
$sudo apt-get install m4
$sudo apt-get install tcsh
$sudo apt-get install csh
$sudo apt-get install libx11-dev
$sudo apt-get install tcl-dev tk-dev
$sudo apt-get install libcairo2-dev
$sudo apt-get install mesa-common-dev libglu1-mesa-dev
$sudo apt-get install libncurses-dev
$git clone https://github.com/RTimothyEdwards/magic
$cd magic
$./configure
$make
$make install
```
Screenshot of installation:
![Screenshot from 2023-08-03 20-23-37](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/c6b967d1-5b7e-4814-abf3-13fae2b6fa81)

</details>

<details>
    <summary>
        OpenLANE
    </summary>


Pre-installation steps:
```
$sudo apt-get update
$sudo apt-get upgrade
$sudo apt install -y build-essential python3 python3-venv python3-pip make git
```

Docker Installation:
```
$sudo apt install apt-transport-https ca-certificates curl software-properties-commoncurl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

$echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

$sudo apt update
$sudo apt install docker-ce docker-ce-cli containerd.io
$sudo docker run hello-world

$sudo groupadd docker
$sudo usermod -aG docker $USER
$sudo reboot
```
After system reboot, check for installation using:
```
$sudo docker run hello-world
```

Steps to install PDKs and Tools:
```
$cd $HOME
$git clone https://github.com/The-OpenROAD-Project/OpenLane
$cd OpenLane



$make
$make test
```
</details>



## DAY 1 Working with Yosys and iverilog
<details>
    <summary>
        Introduction
    </summary>
Iverilog is a Verilog simulation and synthesis tool, enabling digital design verification. GTKWave is a waveform viewer for analyzing simulation results. Yosys is a synthesis tool that converts Verilog designs into gate-level representations, facilitating hardware synthesis. Simulation of a 2x1 MUX is shown in this section using iverilog and gtkwave, design is further synthesized using yosys and a gate level representation of MUX is viewed.
</details>

<details>
    <summary>
        Pre working steps
    </summary>
    Clone to the github repository https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git using the following command

    
```
$git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```

    
This will install all the necessary code files and libraries into your system which are used for the synthesis and generation.
</details>

<details>
    <summary>
        Simulation of verilog code and visualizing the results
    </summary>
    Use the folllowing commands to load the file "good_mux.v" into iverilog and dump the vcd file to gtkwave 

    
```
iverilog good_mux.v tb_good_mux.v
./a.out
gtkwave tb_good_mux.vcd
```


The output of 2x1 MUX is visualised in gtkwave window as shown below:
 ![Screenshot from 2023-08-08 18-52-39](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/d24e114c-b4c2-4238-9ae0-b6609994e851)


</details>
<details>
    <summary>
        Synthesis of the RTL design using Yosys
    </summary>
Move to the lib directory and invoke yosys to generate the synthesis of our design using the following commands:

```
yosys> read_liberty -lib <give the path to lib file>
yosys> read_verilog <give the path to verilog file>
yosys> synth -top <top_module_name>
yosys> abc -liberty <give the path to lib file>
yosys> show
```


The below figure shows our output synthesis design:


![Screenshot from 2023-08-08 19-38-49](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/d9c8403f-4030-49bd-9b69-c86b8876e95d)


This figure shows the results for the cells used:
![Screenshot from 2023-08-08 19-37-17](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/6fe8760e-546e-40d2-b2e4-b9429e05fd04)



Run the following code to generate the netlist file :


```
yosys> write_verilog good_mux_netlist.v
yosys> write_verilog -noattr good_mux_netlist.v
```


The below image shows the netlist file:


![Screenshot from 2023-08-08 19-57-50](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/0c3726d3-3c1f-47ad-b424-0bdf310ca367)


</details>
<details>
    <summary>
        References
    </summary>

    
https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
</details>


## DAY 2 TIMING LIBS AND OPTIMIZATION TECHNIQUES
<details>
<summary>
Introduction to dot lib
</summary>
We use the library "sky130_fd_sc_hd__tt_025C_1v80" for the RTL synthesis. This is a SkyWater PDK. It specifies the operating conditions such as process(tt-typical), voltage(1v80) and temperature (025C) of the fabrication.
The below figure shows the specifications:

    
![Screenshot from 2023-08-14 14-44-38](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/5d8845d0-99ca-451a-acf2-ca26f7301fd0)


Using this lib file, we get access to different types of cells which has vast number of variants in terms of number of inputs and ouputs along with the functionality.

Leakage power, delay, area, power ports of all the cells is specified within the file for all the input combinations of the given gate.

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/d31acc4b-11f8-414d-a80a-11a8d5ef75e4)




</details>
<details>
<summary>
Hierarchial vs Flat Synthesis
</summary>
Hierarchial Synthesis: Hierarchical synthesis in physical design involves breaking down the entire chip design into smaller, manageable modules or blocks. Each module is designed and optimized separately, and then these modules are integrated at a higher level to create the complete chip layout. This approach allows for better control over the design process, reduces complexity, and enables efficient reuse of standardized blocks. All the modules are preserved.


Flat Synthesis: Flat synthesis in physical design involves designing the entire chip layout as a single, monolithic entity without explicit hierarchical divisions. This approach treats the entire design as a cohesive unit, potentially resulting in a simpler layout. It flattens out the modules into gates with higher efficiency and performance.


The below screenshots demonstrate the gate level simulation for Hierarchial and Flat synthesis respectiely.
![Screenshot from 2023-08-14 15-03-02](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/21e3eee0-f0b1-42d0-bf33-12c01647d675)



![Screenshot from 2023-08-14 15-17-48](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/3612aa17-576c-4ac6-b888-a434376b82fe)


Code: Invoke yosys and use the following code for viewing the ouput
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

show 

//flat synthesis
flatten
show
```

We can also synthesise each module at a time. This is called as "sub-module synthesis".This is used when:


--> We have multiple instances of the same module 

--> We have a larger design , we break down synthesis to sub-module synthesis to make a detailed picture of the netlist.

This is done using the following command ```synth -top <sub-module name> ```

</details>

<details>
<summary>
Flop coding styles
</summary>
<u>--> Why do we use flip-flops?</u>

    
There is a propogation delay in combinational circuits, there is a glitch in the output due to this delay. More the amount of combinational circuits, more is the number of glitches we see. 
So to overcome this problem in the output of a circuit, we introduce a storage element, a flop, in between the combinational circuits which gives a stable output always.This is because a flop is triggered only on the positive edge of the clock.

Initialisation of the flop is done with the control pins on the flop which are reset/set.


The figure shows a D flip-flop
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/1d4911bd-0a8f-4d59-996b-d22101df451c)


<u>--> Coding flops:</u>

**1. Asynchronous reset**

   
Irrespective of the clk signal, if the reset value is high, flop output comes down to zero.

Verilog code describing D flop with asynchronous reset which is positive edge triggered:
```
 module dff_asyncres ( input clk ,  input async_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
	if(async_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

Simulation in gtkwave: Asynchronous reset

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/8258b766-c2de-4cae-b43b-7401a6a91894)


Simulation in gtkwave: Asynchronous reset


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/859dcd47-2368-4f24-a9fe-eb088bd29554)


Synthesis:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/d0c7f021-dde5-47cf-b8fd-9208311ef67a)
We see a inverter in the synthesis because the flop used by the tool has a active low reset.

**2. Synchronous reset**


Reset awaits the clock edge to drive the output to low.

Verilog code describing D flop with synchronous reset which is positive edge triggered:
```
module dff_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
always @ (posedge clk )
begin
	if (sync_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```


Simulation in gtkwave:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/3558bdbe-d61e-4ddd-ba4d-9b428cb44c41)


Synthesis:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/b07f8ac9-34c2-4443-8f8d-06b19b78ee3d)



**3. Asynchronous/Synchronous reset**

Flop is triggered with both the asynchronous and synchronous signals explained in the below figure.


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/dfb8425c-ad23-467b-a416-aece22c09cbd)

Verilog code testing the same:

```
module dff_asyncres_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
    if(async_reset)
            q <= 1'b0;
    else if (sync_reset)
            q <= 1'b0;
    else
            q <= d;
end
endmodule
```

<u>--> Optimization </u>


**illustration 1**
A 3 bit number multiplied by 2 gives a 4 bit output,whose first 3 MSB bits are the input bits and the LSB is 0. Thus, output is input appended with zero in the end. This is explained in the below truth table. Taking note of this we can reduce the hardware usage in our design.

	Input (3 bits)	    Output (4 bits)
	  000			0000
	  001			0010
	  010			0100
	  011			0110
	  100			1000
	  101			1010
	  110			1100
	  111			1110


Verilog code for implementing:

```
module mul2 (input [2:0] a, output [3:0] y);
assign y = a * 2;
endmodule
```

When we synthesise the above code we donot see any cells which are being in use:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/2481d7a7-7efc-4405-a222-ad0554e701c3)


The final gate level synthesis:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/1dfcf7c4-92f4-4b5f-bfbf-f3eda5f69d0a)





</details>

## DAY 3 COMBINATIONAL AND SEQUENTIAL OPTIMIZATIONS

**COMBINATIONAL LOGIC OPTIMIZATION**
 Minimizing the logic to get most optimized design which is efficient in terms of area and power

 Techniques for optimization:

 
1. Maintaining constant propogation
2. Boolean optimization using K-Map

**Lab sessions**

**Combinational**
<details>
Illustration 1:

```
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```

Synthesis:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/8aeef909-fe53-4901-b4dc-d8445823a398)


Netlist:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/a7a62470-f51a-4000-b448-83ffb9544dbd)


Illustration 2:

```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

Synthesis:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/e92b72f5-4055-4934-a84c-62c220e3b032)


Netlist:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/8a5bd032-1ecf-462f-8552-989c26b1f4c3)


Illustartion 3:

```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```


Synthesis:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/234aa9c1-c196-4b80-a60b-721e55d9f6ec)


netlist:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/f24424b5-42ae-4f8a-ba61-21bbe2ef3ba4)

</details>



**Sequential**

<details>
Example 1:

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

Synthesis:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/04ab3a4c-16b3-4165-aa2a-a58c9941cded)


Netlist:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/92ddbaf3-d8d9-4d25-a291-ee70265440b8)



Example 2:

```
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```


Synthesis:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/78d0c079-522a-4f2e-ba26-fbb9e1c184fe)


Netlist:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/8aaeaf50-f2f7-4d3a-aab1-90d4537612c1)


Example 3:

```
	module dff_const5(input clk, input reset, output reg q);
reg q1;
always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b0;
			q1 <= 1'b0;
		end
	else
		begin
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```


Synthesis:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/103cfaa3-727a-4d13-aa2a-b535022d4f88)


Netlist:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/c8d13532-03b0-432b-bf3e-06fec29cb8ec)

</details>


**Counter optimization**
<details>
Code:

```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```


Synthesis:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/f577afbb-b1d3-4a53-ac00-2a69bbe95707)


Netlist:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/608f32df-788e-4adb-9105-8ab5cc35beea)


Code 2: Infers 3 flipflops even after optimization

```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count==3'b100;

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```

Synthesis:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/24c20d18-e194-4e5b-acd4-800a00eb9316)

Netlist:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/87d00dde-1c20-461f-b499-56f0d5dd9ec0)
</details>


## DAY 4 INTRODUCTION TO GLS AND SYNTHESIS-SIMULATION MISMATCH

**Gate Level Synthesis (GLS):**
<details>
1. We will run the test bench with netlist as design under test.
2. Netlist is logically same as RTL code
3. Gate level verilog models can be timing aware or functional.


Why GLS?

1. To verify the logical correctness of the design after synthesis
2. To meet the timing requirements of the design, this is done using delay annotation.
3. To test the funcionality of the netlist because there can be synthesis-simulation mismatch

The below figure depicts the GLS synthesis flow:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/3f95024b-bda4-4b11-b2eb-7089f193cd1b)



</details>


**Synthesis Simulation Mismatch**

<details>
What are the causes?


1. Missing sensitivity list
2. Blocking vs Non-Blocking Assignment
3. Non standard verilog coding

</details>


**Missing sensitivity list**


Simulator always looks for a change in activity.

Observing the below code, we find that always block is evaluating only when 'sel' is changing. So when there is a change in the input , the change is not reflected in ouput until there is a change in 'sel'.This does not give us the desired output.


```
always @(sel)
begin
if (sel)
 out = i1;
else
 out = i0;
end
```
<details>
Simulation using gtkwave:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/43ef2523-b96f-49c6-ac36-cb214c520dfa)




This can be corrected by using the following command.
This makes sure that output is sensitive to any change in input


```
always (*)
```


The above code has a synthesis simulation mismatch because -->
1. Synthesiser looks at the functionality and will create a MUX
2. Whereas a simulator will simulate it consdiering it as double edge flop.
</details>


**Blocking and Non-blocking statements in verilog**

1. Blocking Assignment [ = ]


Executes the statements sequentially

2. Non Blocking Assignment [ <= ]

Executes the statements in parallel. RHS is executed and assigned to LHS

**Caveats with Blocking Statements**


EXAMPLE 1: Consider the below code:


```

if (reset)
  begin
    q0=1'b0;
    q =1'b0;
  end
else
  begin
    q=q0;
    q0=d;
  end
```

This will evaluate to a design shown in the below figure:



```
if (reset)
  begin
    q0=1'b0;
    q =1'b0;
  end
else
  begin
    q0=d;
    q=q0;
  end
```

This will evaluate to a design shown in the below figure:


So the usage of non-blocking statements become beneficial in sequential circuits.

EXAMPLE 2: Consider the below code which is used to design y=(a+b)&c

Part 1:


```
always @(*)
begin
  y  =  q0 & c;
  q0 =  a  | b;
end
```

Here, the previous value of q0 is assigned to y, before the actual value of q0 is evaluated. So here q0 will mimic a flop, because old value is being stored.


```
always @(*)
begin
  q0 =  a  | b;
  y  =  q0 & c;
end
```

Here, the latest value of q0 is used in simulation.

The synthesis of both the codes give the same synthesis output which is not actually happening, so there is a synthesis-simulation mismatch.

So it is important to run GLS and match the output of synthesis and simulation.
<details>

RTL simulation of Part 1:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/508eec48-1178-4686-be7c-6bdf261e9e2b)


Synthesis:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/cfb7204b-54c0-4a24-a322-51a05c099ec7)


GLS simulation of Part 1:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/61ee1f21-315f-4c9f-9dda-0b7d241bd905)




We can see that irrespective of expression evaluation , we get the old value of q0 for calculating output.So we can see a synthesis-simulation mismatch for the blocking statement.
</details>


**LAB SESSION**

**MUX**

<details>
Simulation of the RTL design:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/43ef2523-b96f-49c6-ac36-cb214c520dfa)



Simulation of the netlist design:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/58de709f-90d3-4ee2-b813-f45fcfa5eb17)

So the code explained in missing sensitivity list shows synthesis-simulation mismatch.
</details>


**ternary operator**
<details>
Consider the below code:

```
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
assign y = sel?i1:i0;
endmodule
```

We will observe the RTL and GLS simulation


RTL simulation result: output follows input according to select line
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/43c1ac68-93f0-477b-a9f9-25c219972e36)



Synthesis:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/34594d94-5fab-4db6-acb5-802907f8e8a6)



GLS simulation:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/f7c896b2-b020-4c7d-96ed-3dab9da913f6)

</details>


**Blocking statement simulation synthesis mismatch**
<details>
Consider the below code:


```
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
d = x & c;
x = a | b;
end
endmodule
```
</details>


### DAY 5 IF CASS FOR 


**if**

Used for priority logic estimation.if statement is used to conditionally execute a block of code based on a given condition.

```
if (condition)
    // Code to be executed if the condition is true
else
    // Code to be executed if the condition is false
```

<details>
Equivalent hardware design of if else construct:


![Screenshot from 2023-08-15 12-24-32](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/b00167ef-64b9-406d-9e49-f85ae8ac7c7d)
</details>


Caution with if:


Inferred Latches(due to inefficient coding) which is due to incomplete if statement.

<details>

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/cf835dec-7b90-4c1d-a8a5-4abef9e97391)


Exception : counter

Consider the below code with incomplete **if**:

```
always @(posedge clk, posedge reset)
begin
 if (reset)
   count <=3'b000;
else if(en)
   count <=count + 1;
end
```

Here without the **else** statement, the output is latched on to the previous value which is useful because the ouput should be stable on previous **count** value without **enable** being high.

In a combinational circuit we can not have a inferred latch.
</details>



**case**

1. if, case are used in **always** block
2. So we use a **reg** variable

Syntax:

```
 case(choice)
choice1: begin
     --------
 --------
 end
choice2: begin
 --------
 --------
 end
 default: <statements>
 endcase
```

Caveats in **case**

1. incomplete case statements --> can be resolved by default, this do not create inferred latches
2. partial assignments in case statements --> explained in the below figure, we should ssign all the outputs in all the segments of case.
3. overlapping **case**
<details>

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/2c8eb835-3854-4d69-b1b0-6840035aefe1)
</details>


**LAB SESSIONS**

**incomplete if** : Latch is inferred due to imcomplete **if** statement

```
module incomp_if (input i0 , input i1 , input i2 , output reg y);
always @ (*)
begin
if(i0)
	y <= i1;
end
endmodule
```
<details>

RTL simulation: when i0 is low output is unpredictable
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/f3fec974-80c8-4014-bfc9-c1aaea66e578)


Synthesis: D latch is inferred for MUX
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/81fc914e-2b0c-4de7-8146-9fec5e264be8)
</details>

**illustration 2**

```
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

<details>
RTL simulation: When i0 is high, y is i1 ; when i0 is low, it looks for i2, and if i2 is low, y is constant, if i2 is high , y is i3.


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/3d7b5c61-84f9-4813-bda1-d84c0e2ec1fd)

Synthesis: 


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/dde35889-d71e-4d95-9b2c-009a71df3184)
</details>

**incomplete case**


**illustration 1:** missing case values


```
module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
case(sel)
	2'b00 : y = i0;
	2'b01 : y = i1;
endcase
end
endmodule
```
<details>

This can be inferred as below:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/fb8f6838-bc14-4770-934b-609c996c05b1)


RTL:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/b5a1ac1e-5133-4892-a913-d88973e0e464)

</details>


**illustration 2** case with default


```
module comp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
case(sel)
	2'b00 : y = i0;
	2'b01 : y = i1;
	default : y = i2;
endcase
end
endmodule
```
<details>
Latch is not inferred here, because for the missing case values, **default** is executed.
The above code has its equivalent hardware implementation as follows:


![Screenshot from 2023-08-15 14-30-55](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/a0c389f0-7e12-443a-ae5b-102d2245d7c4)


RTL simulation: When **sel** is 10 or 11 **y** is **i2**
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/3d87456a-a008-4d96-bdb1-be337623e049)


Synthesis: We donot see any latch as seen in earlier case
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/418fedb2-33a5-4d36-b75d-31f21dd8c0bc)



</details>


**illustration 3**: Partial case: output of **x** is not given clearly

```
module partial_case_assign (input i0 , input i1 , input i2 , input [1:0] sel, output reg y , output reg x);
always @ (*)
begin
case(sel)
	2'b00 : begin
		y = i0;
		x = i2;
		end
	2'b01 : y = i1;
	default : begin
         	  x = i1;
		  y = i2;
	 	 end
endcase
end
endmodule
```
<details>
Hardware implementation:

 
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/dd100cf3-9530-4e05-973a-f19d3b277004)


Synthesis :

Sir ouput:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/b4e62e90-4c70-40dd-a04f-d791f55013e5)


My output:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/b3b6b813-f1c3-46e3-a0ef-668c4dcf9e40)


</details>

**LOOPING CONSTRUCTS**

1. for loop: --> used in **always** block, used for evaluating expressions

<details> 
Any MUX design can be evauated easily by writing it in a **for** loop.

Example for a 32x1 MUX :

```
input reg [31:0] inp;
integer i;
always @(*)
begin
  for (i=0;i<32;i=i+1)
  begin
    if(i == sel)
      y = inp[i];
  end
end 
```
</details>  


2. generate for loop: cannot be used inside **always** block, used for generating/instantiating hardware multiple times

<details>

 
instantiating a  **and** gate multiple times

```
genvar i;
generate
  for(i=0;i<8;i=i+1)
    begin
      and u_and (.a(inp1[i]) , .b(inp2[i]) , .y(y[i]));
    end
endgenerate
```


</details>

<details>
<summary>

 
**LAB SESSIONS**


</summary>



**Illustration 1**: MUX using **for**


```
module mux_for (input i0 , input i1, input i2 , input i3 , input [1:0] sel  , output reg y);
wire [3:0] i_int;
assign i_int = {i3,i2,i1,i0};
integer k;
always @ (*)
begin
for(k = 0; k < 4; k=k+1) begin
	if(k == sel)
	y = i_int[k];
	end
end
endmodule
```

Simulation:


![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/d51e6b78-5007-4f38-87d7-36cb24d451d0)



Synthesis:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/1424d106-730f-464a-ad6c-3a0b641b88fa)


GLS simulation:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/bea9c6d9-9387-41fc-b845-fdd05327cce6)






**Illustration 2**: DEMUX using case and for


**case code:**


```
module demux_case (output o0 , output o1, output o2 , output o3, output o4, output o5, output o6 , output o7 , input [2:0] sel  , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;
always @ (*)
begin
y_int = 8'b0;
	case(sel)
		3'b000 : y_int[0] = i;
		3'b001 : y_int[1] = i;
		3'b010 : y_int[2] = i;
		3'b011 : y_int[3] = i;
		3'b100 : y_int[4] = i;
		3'b101 : y_int[5] = i;
		3'b110 : y_int[6] = i;
		3'b111 : y_int[7] = i;
	endcase

end
endmodule

```


Simulation for case:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/b773e08a-5f70-4de3-ae37-8ac6516092f2)

**Code using for:**

```
module demux_generate (output o0 , output o1, output o2 , output o3, output o4, output o5, output o6 , output 				o7 , input [2:0] sel  , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;
always @ (*)
begin
y_int = 8'b0;
for(k = 0; k < 8; k++) begin
	if(k == sel)
	y_int[k] = i;
end
end
endmodule
```

Simulation:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/7d8d84c6-b292-4b67-a013-00d5bda08868)



Synthesis:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/7ad41b32-c506-4798-9a25-c80fb1883b55)



GLS simulation:
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/c2750f55-dde0-488e-9509-b62223369992)


**We can see that the ouput follows input according to select line for both the codes**


**Illustration 3** Ripple Carry Adder


Full adder


```
module fa (input a , input b , input c, output co , output sum);
	assign {co,sum}  = a + b + c ;
endmodule
```


Ripple Carry Adder


```
module rca (input [7:0] num1 , input [7:0] num2 , output [8:0] sum);
wire [7:0] int_sum;
wire [7:0]int_co;

genvar i;
generate
for (i = 1 ; i < 8; i=i+1) begin
	fa u_fa_1 (.a(num1[i]),.b(num2[i]),.c(int_co[i-1]),.co(int_co[i]),.sum(int_sum[i]));
end

endgenerate
fa u_fa_0 (.a(num1[0]),.b(num2[0]),.c(1'b0),.co(int_co[0]),.sum(int_sum[0]));


assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule
```

Simulation:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/43884307-df7f-4141-8f83-b2ff311e8fdf)


Synthesis:



![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/c8ea86db-61f3-4225-b6bc-7399e8fa3d5b)


```
read_verilog rca.v fa.v
synth -top rca
show rca
```

GLS simulation:

![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/2f644d22-7474-4e12-a82d-b6cef6ab29b9)


</details>







