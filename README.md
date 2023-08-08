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
