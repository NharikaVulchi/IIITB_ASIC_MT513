# DAY 0 Software Installation
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



# DAY 1 Working with Yosys and iverilog
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


# DAY 2 
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
--> Why do we use flip-flops?

    
There is a propogation delay in combinational circuits, there is a glitch in the output due to this delay. More the amount of combinational circuits, more is the number of glitches we see. 
So to overcome this problem in the output of a circuit, we introduce a storage element, a flop, in between the combinational circuits which gives a stable output always.This is because a flop is triggered only on the positive edge of the clock.

Initialisation of the flop is done with the control pins on the flop which are reset/set.


The figure shows a D flip-flop
![image](https://github.com/NharikaVulchi/IIITB_ASIC_MT513/assets/83216569/1d4911bd-0a8f-4d59-996b-d22101df451c)


--> Coding flops:

1. Asynchronous reset
Irrespective of the clk signal, if the reset value is high, flop output comes down to zero.

Verilog code describing D flop with asynchronous reset:
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

2. Synchronous reset
Reset awaits the clock edge to drive the output to low.

Verilog code describing D flop with synchronous reset:
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



</details>
