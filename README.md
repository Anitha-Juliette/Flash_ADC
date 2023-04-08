# <div align="center"> VSD Mixed-signal PD Research Program - Flash_ADC  
## <div align="center"> WEEK0 AI's
###                  VSD OPENSOURCE TOOLS INSTALLATION  
#### Vsdflow creation  
   * sudo apt-get install git  
   * git clone https://github.com/kunalg123/vsdflow.git  
#### Magic installation  
   * $ sudo apt-get install m4 // Install M4 preprocessor  
   * $ sudo apt-get install tcsh // Install tcsh shell  
   * $ sudo apt-get install csh // Install csh shell  
   * $ sudo apt-get install libx11-dev // Install xlib  
//If you wish to have the Tcl/Tk wrapper around magic (recommended) you will need to install the Tcl/Tk libraries. Version 8.5 or higher is highly recommended.Tcl/Tk// 
   * $ sudo apt-get install tcl-dev tk-dev  
// Cairo graphics interface ("magic -d XR")//  
   * $ sudo apt-get install libcairo2-dev  
// The OpenGL interface//  
   * $ sudo apt-get install mesa-common-dev libglu1-mesa-dev  
// ncurses library //  
   * $ sudo apt-get install libncurses-dev  
   * $ cd magic  
   * $ ./configure  
   * $ make  
   * $  sudo make install
#### Netgen installation  
   * $ git clone git://opencircuitdesign.com/netgen  
   * $ cd netgen  
   * $ ./configure  
   * $  make  
   * $  sudo make install
#### xcschem installation  
   * $ git clone https://github.com/StefanSchippers/xschem.git xschem_git  
   * $ sudo apt-get install flex  
   * $ sudo apt-get install bison  
   * $ sudo apt-get install libxpm-dev  

#### ngspice installation  
   * $ sudo apt-get update  
   * $ sudo apt-get install ngspice  
   * $ ngspice -v  

#### Openpdks installation  
   * $ git clone git://opencircuitdesign.com/open_pdks  
   * $ cd open_pdks  
   * $	./configure --enable-sky130-pdk  
   * $  make  
   * $  sudo make install

#### Align installation
   * $ sudo apt-get install libboost-all-dev
   * $ sudo apt-get update  
   * $ sudo apt-get install lp-solve  
   * $ export CC=/usr/bin/gcc  
   * $ export CXX=/usr/bin/g++  
   * $ git clone https://github.com/ALIGN-analoglayout/ALIGN-public  
   * cd ALIGN-public  
   * //Create a Python virtualenv//  
   * $ python -m venv general  
   * $ source general/bin/activate  
   * $ python -m pip install pip --upgrade  
   * // Install ALIGN as a USER //  
   * $ pip install -v .  
   * // Install ALIGN as a DEVELOPER //  
   * $ pip install -e .  
   * $ pip install setuptools wheel pybind11 scikit-build cmake ninja  
   * $ python3 -m pip install --upgrade pip setuptools wheel  
   * $ pip install -v -e .[test] --no-build-isolation  
   * $ pip install -v --no-build-isolation -e . --no-deps --install-option=' DBUILD_TESTING=ON'  
   * $ git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130  
   * $ move SKY130_PDK folder to /home/ani/ALIGN-public/pdks 

#### Running Align tool with examples  
   * $ python -m venv general  
   * $ source general/bin/activate  
   * mkdir work  
   * cd work  
   //Example 1//  
   * $ schematic2layout.py ../examples/telescopic_ota -p ../pdks/FinFET14nm_Mock_PDK/
   ![Screenshot from 2023-02-08 15-49-18](https://user-images.githubusercontent.com/86735438/217503607-9e016f6d-b93c-403d-a58a-6c0fdca412d9.png)  
   //Klayout opening//  
   * $ XDG_SESSION_TYPE=x11  
   * klayout  
   ![Screenshot from 2023-02-08 16-21-58](https://user-images.githubusercontent.com/86735438/217509630-9d701012-17e6-4076-886e-cfb4e2c5def8.png)

   ![Screenshot from 2023-02-08 16-24-09](https://user-images.githubusercontent.com/86735438/217510003-bbef36ae-3282-42b3-95e2-e801b049965a.png)

   ![Screenshot from 2023-02-08 16-25-52](https://user-images.githubusercontent.com/86735438/217510361-c27afb3e-ed98-4166-9869-97e15458fc08.png)

   ![Screenshot from 2023-02-08 16-26-39](https://user-images.githubusercontent.com/86735438/217510586-6eb96b5a-f8d6-45fb-a3cd-b073e41ba7ac.png)

### Verifying openpdk installation  
   $ mkdir Lab1_and  
   $ cd Lab1_and  
   $ mkdir mag  
   $ mkdir netgen  
   $ mkdir xschem  
   $ cd xschem  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/xschem/xschemrc .  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/ngspice/spinit .spiceinit  
   $ cd ../mag  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/magic/sky130A.magicrc .magicrc  
   $ cd ../netgen  
   $ cp /usr/local/share/pdk/sky130A/libs.tech/netgen//sky130A_setup.tcl .
![image](https://user-images.githubusercontent.com/86735438/218258897-31956dfc-05a7-49ba-9650-d00fd3d7217e.png)
#### magic test
![image](https://user-images.githubusercontent.com/86735438/218021669-23945e4e-9878-4e21-bd13-fa0dd40c3580.png)
#### xschem test  
![image](https://user-images.githubusercontent.com/86735438/218042832-459f7237-9ffb-4544-a7b5-128601d14a87.png)
#### netgen test
![image](https://user-images.githubusercontent.com/86735438/218021867-2bf931d3-4af7-4cba-89dc-9c8193aee448.png)  
### DESIGN 1 - INVERTER 
#### INVERTER CREATION using xschem  
###### An inverter Schematic is created by importing components from Open Pdk library. 
![image](https://user-images.githubusercontent.com/86735438/218141200-37a986a8-eb03-4f02-ad32-8d8814b8835b.png)
#### SYMBOL CREATION  
###### Inorder for the subcircuit to be used in higher level circuits, a symbol is     created for the sub circuit inverter.
![image](https://user-images.githubusercontent.com/86735438/218079115-b6c12b92-8e34-4b1a-afc5-b6c054249006.png)
#### TESTBENCH CREATION
###### A testbench is created to invoke the Inverter symbol, reference the libraries and set up the simulation environment- transient /dc analysis
![image](https://user-images.githubusercontent.com/86735438/218113858-cc41f642-78cd-4d3a-a07f-93c618ebd188.png)
#### inverter_tb.spice Netlist
###### A Spice Netlist for the inverter testbench is created.
![image](https://user-images.githubusercontent.com/86735438/219472680-cc08fef7-3ed3-4d51-8056-1848f1bb4f34.png)  
#### Invoking ngspice from xschem to run Netlist
###### Through ngspice, the netlist is invoked and pre-layout simulation is executed.
![image](https://user-images.githubusercontent.com/86735438/218296498-726f4ec4-4ed3-482d-829c-5e286e3d8805.png)
#### Simulation
![image](https://user-images.githubusercontent.com/86735438/219472386-9894635c-fa6c-486a-852c-83de01a2b6dd.png)
### CREATING INVERTER LAYOUT IN MAGIC(invoked from Netlist from ngspice) - EXPORTING NETLIST & POST LAYOUT SIMULATION
  ![image](https://user-images.githubusercontent.com/86735438/219448463-560e803a-d8e5-4e86-8401-ef9082ca39e4.png)
![image](https://user-images.githubusercontent.com/86735438/219465982-eafd6c2a-b2fd-48c0-a3b7-c64b6cd5ea40.png)
![image](https://user-images.githubusercontent.com/86735438/219462668-209208d7-8fe0-4500-82dc-d2966a05fee2.png)
![image](https://user-images.githubusercontent.com/86735438/219463391-24da5f0b-45ab-4e64-a5f9-8bdd51445e3c.png)
![image](https://user-images.githubusercontent.com/86735438/219463202-0d7349d2-d6aa-435d-9486-2f1220516c82.png)
![image](https://user-images.githubusercontent.com/86735438/219471010-d805927c-c9d3-4d33-8e84-189d0a09767b.png)
![image](https://user-images.githubusercontent.com/86735438/218332205-f5a7ba8c-d75a-410b-91b8-1e092f369336.png)  
## <div align="center"> WEEK1 AI's  
** INVERTER USING ALIGN
  ![image](https://user-images.githubusercontent.com/86735438/219578385-481cd7de-9958-4b1a-8846-bbf74bc1e92a.png)
![image](https://user-images.githubusercontent.com/86735438/219578504-77c43f40-778d-42d6-a613-200218dc60b2.png)
![image](https://user-images.githubusercontent.com/86735438/219665164-9d1d5c4f-4628-44c7-96b2-031d12edcf69.png)
![image](https://user-images.githubusercontent.com/86735438/219665225-d17d7784-8d69-4b5a-9071-545f1da95950.png)
  ![image](https://user-images.githubusercontent.com/86735438/219665323-55499ea0-490e-475e-ac32-628fb0592897.png)
  ![image](https://user-images.githubusercontent.com/86735438/219681463-b567e966-f130-4c9a-9c7e-c6658e4fbfdb.png)
![image](https://user-images.githubusercontent.com/86735438/219681490-8c2cb897-ffe0-41f0-a6f7-ef89b93fcfd1.png)
  ![image](https://user-images.githubusercontent.com/86735438/219680963-be93df16-9c35-4aa6-888a-5e8d109dc01a.png)
  
  ###                  PRELAYOUT SIMULATION OF COMPLEX FUNCTION  
  ![image](https://user-images.githubusercontent.com/86735438/219808918-db63d678-aad1-4b63-b85b-e9e28d6a8cc3.png)

 ![image](https://user-images.githubusercontent.com/86735438/219808556-1a10b36c-5e17-4a51-8413-59c466b99a37.png)
  ###                  POSTLAYOUT SIMULATION OF COMPLEX FUNCTION 
![image](https://user-images.githubusercontent.com/86735438/219812937-a921017c-59e2-4d0e-baf6-c7912fb0551a.png)
  ![image](https://user-images.githubusercontent.com/86735438/219793613-62ca25c1-4927-4e72-9d2a-f790de890478.png)
  ![image](https://user-images.githubusercontent.com/86735438/219793747-8d532d13-1bae-46fc-b4ab-daf092bb0bfe.png)
![image](https://user-images.githubusercontent.com/86735438/219793830-b1eca535-3caa-4bb5-bd03-b7e62b308219.png)
 ###                  ALIGN - POSTLAYOUT SIMULATION OF COMPLEX FUNCTION 
  ![image](https://user-images.githubusercontent.com/86735438/219811115-9ecc610b-4e0c-4d2b-9964-1186b2f53d6a.png)
  
  ![image](https://user-images.githubusercontent.com/86735438/220686364-6440d9e6-c540-4ffb-9888-761db2342835.png)
  
  ![image](https://user-images.githubusercontent.com/86735438/220685358-ccfd9c6d-4ae5-4798-a81c-f2cd1ab3a555.png)

## <div align="center"> WEEK2 AI's

#### HEADER.gds

![image](https://user-images.githubusercontent.com/86735438/221184521-a1a25464-09ae-4034-9556-880b60dd0f75.png)

#### SLC.gds

![image](https://user-images.githubusercontent.com/86735438/221184984-cf9bb679-540d-468d-bc8e-62a2a3209e49.png)
  
#### Verilog generation  
  ![image](https://user-images.githubusercontent.com/86735438/221192890-5ae4736e-4fca-47e9-ab55-120d42081367.png)
  
#### test.json
  ![image](https://user-images.githubusercontent.com/86735438/221193664-550e31ff-996e-41b0-9ca9-1c908b356779.png)
  
#### modelfile.csv
  ![image](https://user-images.githubusercontent.com/86735438/221194455-75799596-f497-4bb9-a4a2-bb88c09386d8.png)

#### generic verilog file for counter
  ![image](https://user-images.githubusercontent.com/86735438/221195559-e0db885e-0b08-42a4-a94a-8bdd5cb973a4.png)

#### modified counter file after optimization
  ![image](https://user-images.githubusercontent.com/86735438/221195871-6110c473-0f3a-428e-8310-44318640768d.png)
  
#### Synthesis
  ![image](https://user-images.githubusercontent.com/86735438/221258463-d6da4ec6-ecfc-48d9-bd71-c6ec76a28a7d.png)

#### Floorplan
  ![image](https://user-images.githubusercontent.com/86735438/221258636-d48c5b04-1e02-4252-9ce1-f2667517fc7b.png)

#### Floorplan Power report
  ![image](https://user-images.githubusercontent.com/86735438/221259996-d05e4a79-ec06-402d-92c2-804be88a5100.png)

#### Global Place and Route
  ![image](https://user-images.githubusercontent.com/86735438/221260137-1db96446-5c93-4fec-b7ff-56908f26e76a.png)

#### Global place Power Report
  ![image](https://user-images.githubusercontent.com/86735438/221260275-1984b37a-a267-4a2b-bf7e-e7134ac2fcc6.png)

#### Design area
  ![image](https://user-images.githubusercontent.com/86735438/221260654-ff042ac3-c5b9-4b55-bd7f-515792996907.png)

#### Delay
  ![image](https://user-images.githubusercontent.com/86735438/221261146-99e376c7-826e-4873-8151-ebd5ebc5c71b.png)

#### DRC
  ![image](https://user-images.githubusercontent.com/86735438/221261336-278b26dd-746b-4066-bb54-2f28e749f140.png)
  
#### SPICE generation
  ![image](https://user-images.githubusercontent.com/86735438/221261836-04d44b6e-7955-4ced-8c4e-19c475005284.png)

#### LVS
  ![image](https://user-images.githubusercontent.com/86735438/221262292-79783a7f-c263-41c1-bfa6-ef9c95ffbff0.png)
 
#### 6_final.gds
  ![image](https://user-images.githubusercontent.com/86735438/221264170-4dc7b60a-72c2-4fd3-9437-ea6379a00a84.png)

## <div align="center"> WEEK3 AI's
### Ring Oscillator design using Xschem
#### 1. Schematic
  ![image](https://user-images.githubusercontent.com/86735438/222793105-99cb285b-1f91-43c7-886d-c2f9b8bf2707.png)
#### 2. Netlist file generated from Xschem with Testbench
        ** sch_path: /home/ani/pd_research/week3/analog/xschem/osc.sch
        **.subckt osc out
        *.opin out
        XM1 net1 out VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
        + pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
        + sa=0 sb=0 sd=0 mult=1 m=1
        XM2 net1 out GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
        + pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
        + sa=0 sb=0 sd=0 mult=1 m=1
        XC1 net1 GND sky130_fd_pr__cap_mim_m3_1 W=1 L=1 MF=1 m=1
        XM3 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
        + pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
        + sa=0 sb=0 sd=0 mult=1 m=1
        XM4 net2 net1 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
        + pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
        + sa=0 sb=0 sd=0 mult=1 m=1
        XC2 net2 GND sky130_fd_pr__cap_mim_m3_1 W=1 L=1 MF=1 m=1
        XM5 out net2 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
        + pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
        + sa=0 sb=0 sd=0 mult=1 m=1
        XM6 out net2 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=1 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
        + pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
        + sa=0 sb=0 sd=0 mult=1 m=1
        XC3 out GND sky130_fd_pr__cap_mim_m3_1 W=1 L=1 MF=1 m=1
        **** begin user architecture code
        V1 VDD GND 1.8
        .ic V(out)=0
        .lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
        .control
        save all
        tran 1p 1n
        plot v(out)
        .endc
        **** end user architecture code
        .GLOBAL VDD
        .GLOBAL GND
        .end
  #### 3. Prelayout simulation of Ring Oscillator
  ![image](https://user-images.githubusercontent.com/86735438/222804610-dcf37724-9692-4823-ba75-d71ea9c480f4.png)
  #### 4. osc.sp file : Input to align
        .subckt osc VDD GND out
        XM1 net1 out VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=21e-7 nf=10 m=1
        XM2 net1 out GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=21e-7 nf=10 m=1
        XM3 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=21e-7 nf=10 m=1
        XM4 net2 net1 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=21e-7 nf=10 m=1
        XM5 out net2 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=21e-7 nf=10 m=1
        XM6 out net2 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=21e-7 nf=10 m=1
        .ends
  #### 5. osc.gds file generation from osc.sp
  ![image](https://user-images.githubusercontent.com/86735438/222805214-5b7cdb87-ea5a-4143-a93c-bf907882e67c.png)
  #### 6. Open magic -T command from mag folder
  ![image](https://user-images.githubusercontent.com/86735438/222805444-ce482e80-13b3-447c-9d33-d880128e2fcb.png)
  #### 7. Read osc.gds and export osc_0.spice file
  ![image](https://user-images.githubusercontent.com/86735438/222805727-8193a26c-3a56-4522-9495-1c80a80a3921.png)
  #### 8. Modify osc_0.spice file with testbench
        * SPICE3 file created from OSC_0.ext - technology: sky130A
        x1 VDD GND OUT osc_align
        .subckt osc_align VDD GND OUT
        X0 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.5565 ps=4.73 w=2.1 l=0.15
        X1 VDD STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X2 VDD STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X3 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X4 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X5 VDD STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X6 VDD STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X7 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X8 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X9 VDD STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# VDD sky130_fd_pr__pfet_01v8 ad=0.5565 pd=4.73 as=0.294 ps=2.38 w=2.1 l=0.15
        X10 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT VDD VDD sky130_fd_pr__pfet_01v8 ad=2.94 pd=23.8 as=10.395 ps=85.5 w=2.1 l=0.15
        X11 VDD OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X12 VDD OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X13 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT VDD VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X14 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT VDD VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X15 VDD OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X16 VDD OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X17 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT VDD VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X18 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT VDD VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X19 VDD OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X20 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X21 GND STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# GND sky130_fd_pr__nfet_01v8 ad=0.5565 pd=4.73 as=0.294 ps=2.38 w=2.1 l=0.15
        X22 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.5565 ps=4.73 w=2.1 l=0.15
        X23 GND STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X24 GND STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X25 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X26 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X27 GND STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X28 GND STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# m1_828_1568# GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X29 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X30 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT GND GND sky130_fd_pr__nfet_01v8 ad=2.94 pd=23.8 as=10.395 ps=85.5 w=2.1 l=0.15
        X31 GND OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X32 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT GND GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X33 GND OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X34 GND OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X35 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT GND GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X36 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT GND GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X37 GND OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X38 GND OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X39 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# OUT GND GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=2.1 l=0.15
        X40 OUT m1_828_1568# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.5565 ps=4.73 w=2.1 l=0.15
        X41 VDD m1_828_1568# OUT VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X42 VDD m1_828_1568# OUT VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X43 OUT m1_828_1568# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X44 OUT m1_828_1568# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X45 VDD m1_828_1568# OUT VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X46 VDD m1_828_1568# OUT VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X47 OUT m1_828_1568# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X48 OUT m1_828_1568# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X49 VDD m1_828_1568# OUT VDD sky130_fd_pr__pfet_01v8 ad=0.5565 pd=4.73 as=0.294 ps=2.38 w=2.1 l=0.15
        X50 OUT m1_828_1568# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X51 GND m1_828_1568# OUT GND sky130_fd_pr__nfet_01v8 ad=0.5565 pd=4.73 as=0.294 ps=2.38 w=2.1 l=0.15
        X52 OUT m1_828_1568# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.5565 ps=4.73 w=2.1 l=0.15
        X53 GND m1_828_1568# OUT GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X54 GND m1_828_1568# OUT GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X55 OUT m1_828_1568# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X56 OUT m1_828_1568# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X57 GND m1_828_1568# OUT GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X58 GND m1_828_1568# OUT GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        X59 OUT m1_828_1568# GND GND sky130_fd_pr__nfet_01v8 ad=0.294 pd=2.38 as=0.294 ps=2.38 w=2.1 l=0.15
        C0 OUT VDD 7.84fF
        C1 OUT STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# 1.24fF
        C2 m1_828_1568# OUT 1.62fF
        C3 VDD STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# 7.79fF
        C4 m1_828_1568# VDD 7.18fF
        C5 m1_828_1568# STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# 1.61fF
        C6 OUT GND 5.86fF
        C7 m1_828_1568# GND 5.95fF
        C8 STAGE2_INV_66085670_0_0_1677870230_0/li_1179_1495# GND 4.82fF
        C9 VDD GND 17.11fF
        .ends
        V1 VDD GND 1.8
        .ic V(OUT)=0
        .lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
        .control
        save all
        tran 1p 1n
        plot v(OUT)
        .endc
        **** end user architecture code
  #### 9. Align - Post layout simulation waveform
  ![image](https://user-images.githubusercontent.com/86735438/222814049-d228f3f4-7c22-457f-b6bf-cec4bfafb3f2.png)
## <div align="center"> WEEK4 & WEEK5 AI's
### ANALOG PART - 1 BIT ADC
  ![image](https://user-images.githubusercontent.com/86735438/224346331-c96e4896-2435-48e9-9844-26ff2c181561.png)
#### 1. Schematic of 1 bit ADC using Opamp as Comparator
  ![image](https://user-images.githubusercontent.com/86735438/227016970-ca0f19b9-294d-41e5-a317-8e2818df265e.png)
#### 2. Testing of Opamp - opamp.spice
<details>
<summary>Netlist Xschem</summary>
<pre>** sch_path: /home/ani/ALIGN-public/examples/opamp_mod/xschem/opamp_mod.sch
**.subckt opamp_mod OUT VDD GND INP INN BIAS
*.opin OUT
*.iopin VDD
*.iopin GND
*.ipin INP
*.ipin INN
*.iopin BIAS
V2 VDD GND 1.8
.save i(v2)
V3 INN GND 1
.save i(v3)
V4 INP GND sine(0 1.8 100000000)
.save i(v4)
XM1 net1 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM3 net1 INN net3 GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM4 net2 INP net3 GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM5 net3 BIAS GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
V1 BIAS GND 0.9
.save i(v1)
XM6 net4 net2 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM7 net4 net2 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM8 net5 net4 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM9 net5 net4 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM10 OUT net5 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM11 OUT net5 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
**** begin user architecture code
.lib ~/open_pdks/sources/sky130-pdk/libraries/sky130_fd_pr/latest/models/sky130.lib.spice tt
*.options savecurrents
.control
tran 0.1n 100n
plot v(out) v(inp)
.endc
**** end user architecture code
**.ends
.GLOBAL GND
.end
</pre>
</details>
        
#### 3. ADC output - Xschem
  ![image](https://user-images.githubusercontent.com/86735438/227015271-6c02eaa8-ec78-47ab-bb56-dc476456b0b6.png)
#### 4. Modified Spice file .sp given as input to align Layout of 1 bit ADC - generated from Align
        .subckt opamp_mod INN INP BIAS OUT VDD GND
        M1 net1 INN net3 net3 sky130_fd_pr__nfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M2 net2 INP net3 GND sky130_fd_pr__nfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M3 net3 BIAS GND GND sky130_fd_pr__nfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M4 net4 net2 GND GND sky130_fd_pr__nfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M5 net5 net4 GND GND sky130_fd_pr__nfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M6 OUT net5 GND GND sky130_fd_pr__nfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M7 net1 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M8 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M9 net4 net2 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M10 net5 net4 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        M11 OUT net5 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-9 W=8.4e-7 nf=2 m=1
        .ends opamp_mod
#### 5. Layout of 1 bit ADC - generated from Align
![image](https://user-images.githubusercontent.com/86735438/225376162-83f41ea8-baf8-40a9-bae7-d9eef9c2d1ce.png)
  ![image](https://user-images.githubusercontent.com/86735438/226058362-20d8bc16-2141-4429-9690-c9dfecc88290.png)
![image](https://user-images.githubusercontent.com/86735438/226061351-3ae491bd-be90-4a1b-a13c-c1d9836bbcf9.png)
#### NOTE : The output was always clamped to max voltage as shown below
<details>
<summary>ADC post layout align netlist with control statements</summary>
<pre>** SPICE3 file created from OPAMP_MOD_0.ext - technology: sky130A
X1 OUT VDD GND INP INN BIAS OPAMP_MOD_0
V2 VDD GND 1.8
V3 INN GND 1
V4 INP GND sine(0 1.8 100000000)
V1 BIAS GND 0.9
.lib ~/open_pdks/sources/sky130-pdk/libraries/sky130_fd_pr/latest/models/sky130.lib.spice tt
*.options savecurrents
.control
tran 0.1n 100n
plot v(OUT) v(inp)
.endc
.subckt OPAMP_MOD_0 OUT VDD GND INP INN BIAS
X0 li_2039_1495# INP GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X1 GND INP li_2039_1495# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X2 m1_2290_1400# m1_2290_1400# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X3 VDD m1_2290_1400# m1_2290_1400# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X4 li_2039_1495# m1_2290_1400# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X5 VDD m1_2290_1400# li_2039_1495# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X6 li_405_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X7 VDD STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_405_1495# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X8 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_2039_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.2352 pd=2.24 as=2.016 ps=19.92 w=0.84 l=0.15
X9 VDD li_2039_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=0.84 l=0.15
X10 li_405_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X11 GND STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_405_1495# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X12 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_2039_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.2352 pd=2.24 as=2.9064 ps=28.76 w=0.84 l=0.15
X13 GND li_2039_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=0.84 l=0.15
X14 INV_72761973_PG0_0_0_1679509284_0/m1_140_1400# li_405_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X15 GND li_405_1495# INV_72761973_PG0_0_0_1679509284_0/m1_140_1400# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X16 INV_72761973_PG0_0_0_1679509284_0/m1_140_1400# li_405_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X17 VDD li_405_1495# INV_72761973_PG0_0_0_1679509284_0/m1_140_1400# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X18 GND NMOS_S_48172527_X1_Y1_1679509287_0/a_200_252# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X19 GND NMOS_S_48172527_X1_Y1_1679509287_0/a_200_252# GND GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X20 m1_2290_1400# NMOS_S_48172527_X1_Y1_1679509287_1/a_200_252# GND GND sky130_fd_pr__nfet_01v8 ad=0.2352 pd=2.24 as=0 ps=0 w=0.84 l=0.15
X21 GND NMOS_S_48172527_X1_Y1_1679509287_1/a_200_252# m1_2290_1400# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=0.84 l=0.15
C0 li_405_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.37fF
C1 INN li_2039_1495# 0.02fF
C2 INN STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.00fF
C3 m1_2290_1400# li_405_1495# 0.00fF
C4 INN m1_2290_1400# 0.00fF
C5 INN BIAS 0.05fF
C6 li_2039_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.77fF
C7 INP li_405_1495# 0.00fF
C8 VDD INV_72761973_PG0_0_0_1679509284_0/m1_140_1400# 0.79fF
C9 VDD li_405_1495# 3.19fF
C10 VDD INN 0.08fF
C11 m1_2290_1400# li_2039_1495# 0.46fF
C12 m1_2290_1400# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.01fF
C13 li_2039_1495# BIAS 0.00fF
C14 li_405_1495# OUT 0.09fF
C15 m1_2290_1400# BIAS 0.00fF
C16 INP li_2039_1495# 0.15fF
C17 INP STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.00fF
C18 VDD li_2039_1495# 3.48fF
C19 VDD STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 3.09fF
C20 INP m1_2290_1400# 0.05fF
C21 li_2039_1495# OUT 0.00fF
C22 VDD m1_2290_1400# 2.57fF
C23 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# OUT 0.00fF
C24 VDD BIAS 0.06fF
C25 NMOS_S_48172527_X1_Y1_1679509287_1/a_200_252# m1_2290_1400# 0.11fF
C26 VDD INP 0.07fF
C27 INV_72761973_PG0_0_0_1679509284_0/m1_140_1400# li_405_1495# 0.31fF
C28 VDD OUT 0.31fF
C29 li_2039_1495# li_405_1495# 0.01fF
C30 BIAS GND 0.02fF
C31 INN GND 0.04fF
C32 OUT GND 0.09fF
C33 li_2039_1495# GND 1.82fF
C34 m1_2290_1400# GND 0.98fF
C35 NMOS_S_48172527_X1_Y1_1679509287_1/a_200_252# GND 0.89fF
C36 NMOS_S_48172527_X1_Y1_1679509287_0/a_200_252# GND 1.00fF
C37 INV_72761973_PG0_0_0_1679509284_0/m1_140_1400# GND 0.69fF
C38 li_405_1495# GND 0.53fF
C39 VDD GND 17.18fF
C40 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# GND 1.29fF
C41 INP GND 0.85fF
.ends
</pre>
</details>
  
#### HOW POST LAYOUT WAS MATCHED WITH PRE LAYOUT SIMULATION
A careful observation of the above netlist showed that INN, BIAS, OUT were not reflected in FET instances. Also the Drain terminal of Bias transistor was connected to GND eventhough it was not as uch in spice.
A careful modification of netlist to reflect INN, BIAS, OUT and temp(Drain terminal of Bias transistor) was done as shown in the code below:
<details>
<summary> MODIFIED ADC post layout align netlist with control statements</summary>
<pre>* SPICE3 file created from OPAMP_MOD_0.ext - technology: sky130A
X1 OUT VDD GND INP INN BIAS OPAMP_MOD_0
V2 VDD GND 1.8
V3 INN GND 1
V4 INP GND sine(0 1.8 100000000)
V1 BIAS GND 0.9
.lib ~/open_pdks/sources/sky130-pdk/libraries/sky130_fd_pr/latest/models/sky130.lib.spice tt
*.options savecurrents
.control
tran 0.1n 100n
plot v(OUT) v(inp)
.endc
.subckt OPAMP_MOD_0 OUT VDD GND INP INN BIAS
X0 li_2039_1495# INP temp GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X1 temp INP li_2039_1495# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X20 m1_2290_1400# INN temp GND sky130_fd_pr__nfet_01v8 ad=0.2352 pd=2.24 as=0 ps=0 w=0.84 l=0.15
X21 temp INN m1_2290_1400# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=0.84 l=0.15
X2 m1_2290_1400# m1_2290_1400# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X3 VDD m1_2290_1400# m1_2290_1400# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X4 li_2039_1495# m1_2290_1400# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X5 VDD m1_2290_1400# li_2039_1495# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X8 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_2039_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.2352 pd=2.24 as=2.016 ps=19.92 w=0.84 l=0.15
X9 VDD li_2039_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# VDD sky130_fd_pr__pfet_01v8 ad=0 pd=0 as=0 ps=0 w=0.84 l=0.15
X12 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_2039_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.2352 pd=2.24 as=2.9064 ps=28.76 w=0.84 l=0.15
X13 GND li_2039_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# GND sky130_fd_pr__nfet_01v8 ad=0 pd=0 as=0 ps=0 w=0.84 l=0.15
X6 li_405_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X7 VDD STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_405_1495# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X10 li_405_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X11 GND STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_405_1495# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X16 OUT li_405_1495# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X17 VDD li_405_1495# OUT VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X14 OUT li_405_1495# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X15 GND li_405_1495# OUT GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X18 temp BIAS GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X19 temp BIAS GND GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
C0 m1_2290_1400# BIAS 0.00fF
C1 INN BIAS 0.05fF
C2 VDD OUT 0.79fF
C3 li_405_1495# OUT 0.31fF
C4 m1_2290_1400# INP 0.05fF
C5 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# INP 0.00fF
C6 li_405_1495# VDD 3.19fF
C7 VDD BIAS 0.06fF
C8 m1_2290_1400# li_2039_1495# 0.46fF
C9 INP VDD 0.07fF
C10 INN li_2039_1495# 0.02fF
C11 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# li_2039_1495# 0.77fF
C12 li_405_1495# INP 0.00fF
C13 OUT li_2039_1495# 0.00fF
C14 NMOS_S_48172527_X1_Y1_1679509287_1/a_200_252# m1_2290_1400# 0.11fF
C15 m1_2290_1400# INN 0.00fF
C16 m1_2290_1400# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.01fF
C17 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# INN 0.00fF
C18 OUT STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.00fF
C19 li_2039_1495# VDD 3.48fF
C20 li_405_1495# li_2039_1495# 0.01fF
C21 li_2039_1495# BIAS 0.00fF
C22 m1_2290_1400# VDD 2.57fF
C23 INN VDD 0.08fF
C24 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# VDD 3.09fF
C25 li_405_1495# m1_2290_1400# 0.00fF
C26 OUT VDD 0.31fF
C27 INP li_2039_1495# 0.15fF
C28 li_405_1495# STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# 0.37fF
C29 OUT li_405_1495# 0.09fF
C30 BIAS GND 0.02fF
C31 INN GND 0.04fF
C32 OUT GND 0.09fF
C33 li_2039_1495# GND 1.82fF
C34 m1_2290_1400# GND 0.98fF
C35 NMOS_S_48172527_X1_Y1_1679509287_1/a_200_252# GND 0.89fF
C36 BIAS GND 1.00fF
C37 OUT GND 0.69fF
C38 li_405_1495# GND 0.53fF
C39 VDD GND 17.18fF
C40 STAGE2_INV_89790208_PG0_0_0_1679509285_0/li_405_571# GND 1.29fF
C41 INP GND 0.85fF
.ends
</pre>
</details>
  
#### 6. Screenshots of modifications
![image](https://user-images.githubusercontent.com/86735438/227035322-1cacd7e0-68ba-4de8-9ba9-ed6038ead2e7.png)
![image](https://user-images.githubusercontent.com/86735438/227035385-874107d4-e64d-44f4-80ea-2c51362f634f.png)
![image](https://user-images.githubusercontent.com/86735438/227035540-fc2a31e0-184a-45cb-a32b-a97c675aa89a.png)
![image](https://user-images.githubusercontent.com/86735438/227035760-851acf79-deef-4dbb-8afd-897626ce8917.png)
#### 7.  POST LAYOUT OUTPUT OF 1- BIT ADC
![image](https://user-images.githubusercontent.com/86735438/227033552-f8162829-01d4-4815-8202-711f5d05337e.png)
## <div align="center"> WEEK6 AI's
### Creation of Verilog files & Merging Analog lef & gds with Openroad flow using Openfasoc and generate file GDS II file
#### 1. Verilog files
        module vsdudc(
        input bias,
        input inn,
        output out
        );
        wire temp;
 
        COMPARATOR adc1(.INP(temp),.INN(inn),.BIAS(bias),.OUT(out)
       );
 
       OSC_0 osc1(.OUT(temp)
       );
       endmodule
 
        module COMPARATOR(
            input INP,
            input INN,
            input BIAS,
            output OUT
        );
        endmodule
        module OSC_0(
            output OUT
        );
        endmodule
   
#### 2. Heirarchial directory structure for Openfasoc flow
##### Created a design folder vsdudc-gen with heirarchial structure
![image](https://user-images.githubusercontent.com/86735438/227647090-9f856dc8-237d-43e7-ba0a-d099fcf06c45.png)
#### 3. Modify config.mk : DESIGN_NICKNAME, DESIGN_NAME, LEF & GDS of Auxillary cells
![image](https://user-images.githubusercontent.com/86735438/227649075-bc358ed3-05cd-4b52-a78f-52f4f585896e.png)
#### 4. Execute 
      make vsdudc_sky13hd_verilog
#### Verilog files are generated
![image](https://user-images.githubusercontent.com/86735438/227652813-33dae4f1-8234-458e-872c-2eb4d7ff4334.png)
#### 5. cd into flow directory and start the Verilog to GDS II
    $ export OPENROAD=~/OpenROAD-flow-scripts/tools/OpenROAD
    $ export PATH=~/OpenROAD-flow-scripts/tools/install/OpenROAD/bin:~/OpenROAD-flow-scripts/tools/install/yosys/bin:~       /OpenROAD-flow-scripts/tools/install/LSOracle/bin:$PATH
    $ export PDK_ROOT=/usr/local/share/pdk
    $ make synth
###### Synthesis was completed
![image](https://user-images.githubusercontent.com/86735438/227653381-ad88d7b3-ad28-410d-b663-422a64bf73da.png)
    $ make floorplan
###### Floor plan was completed
![image](https://user-images.githubusercontent.com/86735438/227769940-054005a6-db53-4976-9ff2-7c31ea8b4b30.png)
![image](https://user-images.githubusercontent.com/86735438/227769962-8c18a05f-dd4f-479a-8737-fc17eb12a0c0.png)
![image](https://user-images.githubusercontent.com/86735438/227769984-9b2905d9-c5db-4c11-8ae0-224cb5402292.png)
![image](https://user-images.githubusercontent.com/86735438/227770060-8ffaee1e-93ec-45af-8de9-d2bb13b93a5a.png)
![image](https://user-images.githubusercontent.com/86735438/227770079-076e4a1c-bced-4da2-b2f3-68ce9910ae57.png)
    $ make gui_floorplan
![image](https://user-images.githubusercontent.com/86735438/227770100-b92b1969-f22d-4651-aef8-5782801e53e8.png)
![image](https://user-images.githubusercontent.com/86735438/227770170-c78d9adb-9382-46f7-8170-ff9ee1a91b94.png)
![image](https://user-images.githubusercontent.com/86735438/227770291-da809910-c265-4c1b-a730-4d3ce011af80.png)
  $ make gui_floorplan
  $ run place
###### Placement was completed
  ![image](https://user-images.githubusercontent.com/86735438/227795628-fc48d47b-33d6-448c-877e-abbbfbe51ed6.png)
  ![image](https://user-images.githubusercontent.com/86735438/227795689-be124de2-56d3-481f-8f1a-f54328fb1a17.png)
  $ run route
###### Routing was completed
  ![image](https://user-images.githubusercontent.com/86735438/227797138-7efdd74e-1b3c-4372-a506-8dfd0146f173.png)
  ![image](https://user-images.githubusercontent.com/86735438/227797171-5188b8d9-7733-4105-a277-c7815b891667.png)
  ![image](https://user-images.githubusercontent.com/86735438/227797214-13a7e9d2-50fa-4c2a-9087-7179bc9702f0.png)
  ![image](https://user-images.githubusercontent.com/86735438/227797297-04914480-e7d0-4d95-8160-ee205bd80435.png)
  ![image](https://user-images.githubusercontent.com/86735438/227797329-a68466a5-54ef-4e94-9385-19909b6dc4b7.png)
  ![image](https://user-images.githubusercontent.com/86735438/227797356-27b61bd3-58e8-4b5a-97fb-07e39aab5f70.png)
  $ run finish
  #### gds generated
  ![image](https://user-images.githubusercontent.com/86735438/227798249-a80d2cd6-8896-4284-89be-f8401db7b33d.png)
## <div align="center"> WEEK7 AI - 3 BIT FLASH ADC 
## To design the analog parts of 3 bit Flash ADC
## Circuit Diagram of 3 bit Flash Type ADC
![image](https://user-images.githubusercontent.com/86735438/230716088-830a27e5-9a03-48d4-865f-13268e67834b.png)
#### 1. Design of analog parts of Flash ADC using Xschem. Since resistors are not supported by Align, direct Voltage references have been used.
![image](https://user-images.githubusercontent.com/86735438/230716153-a47aaaf0-57ff-4af2-9129-502bbf903686.png)
<details>
<summary>Xschem Netlist for 3 bit Flash ADC</summary>
<pre>x1 VDD D7 VR7 INP BIAS GND opamp_mod
x2 VDD D6 VR6 INP BIAS GND opamp_mod
x3 VDD D5 VR5 INP BIAS GND opamp_mod
x4 VDD D4 VR4 INP BIAS GND opamp_mod
x5 VDD D3 VR3 INP BIAS GND opamp_mod
x6 VDD D2 VR2 INP BIAS GND opamp_mod
x7 VDD D1 VR1 INP BIAS GND opamp_mod
V1 VR7 GND 2.625
.save i(v1)
V2 VR6 GND 2.25
.save i(v2)
V3 VR5 GND 1.875
.save i(v3)
V4 VR4 GND 1.5
.save i(v4)
V5 VR3 GND 1.125
.save i(v5)
V6 VR2 GND 0.75
.save i(v6)
V7 VR1 GND 0.375
.save i(v7)
V8 VDD GND 3
.save i(v8)
V9 INP GND sine(0 3 100000000)
.save i(v9)
V10 BIAS GND 1.5
.save i(v10)
**** begin user architecture code

.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt


.control
save all
tran 100p 4n
plot v(D7) v(D6) v(D5) v(D4) v(D3) v(D2) v(D1) v(INP)
.endc

**** end user architecture code
**.ends

* expanding   symbol:  opamp_mod.sym # of pins=6
** sym_path: /home/ani/flash_adc/xschem/opamp_mod.sym
** sch_path: /home/ani/flash_adc/xschem/opamp_mod.sch
.subckt opamp_mod VDD OUT INN INP BIAS GND
*.opin OUT
*.ipin INP
*.ipin INN
*.ipin VDD
*.ipin GND
*.ipin BIAS
XM1 net1 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM2 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM3 net1 INN net3 GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM4 net2 INP net3 GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM5 net3 BIAS GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM6 net4 net2 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM7 net4 net2 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM8 net5 net4 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM9 net5 net4 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM10 OUT net5 VDD VDD sky130_fd_pr__pfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
XM11 OUT net5 GND GND sky130_fd_pr__nfet_01v8 L=0.15 W=0.84 nf=1 ad='int((nf+1)/2) * W/nf * 0.29' as='int((nf+2)/2) * W/nf * 0.29'
+ pd='2*int((nf+1)/2) * (W/nf + 0.29)' ps='2*int((nf+2)/2) * (W/nf + 0.29)' nrd='0.29 / W' nrs='0.29 / W'
+ sa=0 sb=0 sd=0 mult=1 m=1
.ends

.GLOBAL GND
.end
</pre>
</details>
  
### 2. Presimulation in ngspice
  ![image](https://user-images.githubusercontent.com/86735438/230716338-85d6c2a8-eb51-42cd-93dd-16e26b9af4ba.png)
### 3. Align Flow for analog blocks of Flash ADC
    $ python -m venv general
    $ source general/bin/activate
    $ schematic2layout.py /home/ani/flash_adc/xschem -p /home/ani/ALIGN-public/pdks/SKY130_PDK
#### Spice Netlist
<details>
<summary>Align Spice Netlist for 3 bit Flash ADC - flash_adc.sp</summary>
<pre>
.subckt opamp_mod VDD OUT INN INP BIAS GND
XM1 net1 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-09 W=840e-09 nf=2
XM2 net2 net1 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-09 W=840e-09 nf=2
XM3 net1 INN net3 GND sky130_fd_pr__nfet_01v8 L=150e-09 W=840e-09 nf=2 m=2
XM4 net2 INP net3 GND sky130_fd_pr__nfet_01v8 L=150e-09 W=840e-09 nf=2
XM5 net3 BIAS GND GND sky130_fd_pr__nfet_01v8 L=150e-09 W=840e-09 nf=2
XM6 net4 net2 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-09 W=840e-09 nf=2
XM7 net4 net2 GND GND sky130_fd_pr__nfet_01v8 L=150e-09 W=840e-09 nf=2
XM8 net5 net4 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-09 W=840e-09 nf=2
XM9 net5 net4 GND GND sky130_fd_pr__nfet_01v8 L=150e-09 W=840e-09 nf=2
XM10 OUT net5 VDD VDD sky130_fd_pr__pfet_01v8 L=150e-09 W=840e-09 nf=2
XM11 OUT net5 GND GND sky130_fd_pr__nfet_01v8 L=150e-09 W=840e-09 nf=2
.ends
.subckt flash_adc D7 D6 D5 D4 D3 D2 D1 VR7 VR6 VR5 VR4 VR3 VR2 VR1 VDD INP GND
x1 VDD D7 VR7 INP BIAS GND opamp_mod
x2 VDD D6 VR6 INP BIAS GND opamp_mod
x3 VDD D5 VR5 INP BIAS GND opamp_mod
x4 VDD D4 VR4 INP BIAS GND opamp_mod
x5 VDD D3 VR3 INP BIAS GND opamp_mod
x6 VDD D2 VR2 INP BIAS GND opamp_mod
x7 VDD D1 VR1 INP BIAS GND opamp_mod
.ends
</pre>
</details>
  
#### 3. FLASH_ADC_0.gds 
  ![image](https://user-images.githubusercontent.com/86735438/230718819-755f8ec3-4037-4f4e-b3c1-ecd91f5ff49d.png)
  
<details>
<summary>Align Post Spice with Testbench for 3 bit Flash ADC</summary>
<pre>
V1 VR7 GND 2.625
.save i(v1)
V2 VR6 GND 2.25
.save i(v2)
V3 VR5 GND 1.875
.save i(v3)
V4 VR4 GND 1.5
.save i(v4)
V5 VR3 GND 1.125
.save i(v5)
V6 VR2 GND 0.75
.save i(v6)
V7 VR1 GND 0.375
.save i(v7)
V8 VDD GND 3
.save i(v8)
V9 INP GND sine(0 3 100000000)
.save i(v9)
x1 D7 D6 D5 D4 D3 D2 D1 VR7 VR6 VR5 VR4 VR3 VR2 VR1 INP VDD GND FLASH_ADC_0
.lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
.control
save all
tran 100p 4n
plot v(D7) v(D6) v(D5) v(D4) v(D3) v(D2) v(D1) v(INP)
.endc
.subckt FLASH_ADC_0 D7 D6 D5 D4 D3 D2 D1 VR7 VR6 VR5 VR4 VR3 VR2 VR1 INP VDD GND
X0 a_10416_8163# a_9728_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X1 a_21222_7863# a_21738_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X2 a_9728_8163# VR4 a_9645_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X3 D3 a_14200_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X4 a_12480_8163# VR3 a_12397_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X5 D1 a_25208_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X6 GND a_9182_9066# a_9645_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X7 GND a_9182_9066# a_12397_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X8 a_23405_8163# VR1 a_23488_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X9 VDD a_10416_8163# a_10932_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X10 GND a_15920_8163# a_16436_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X11 a_23405_8163# a_9182_9066# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X12 a_20706_7863# a_21222_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X13 a_14200_8163# a_13684_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X14 a_23488_8163# a_23488_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X15 a_10932_8163# a_10416_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X16 GND a_16436_8163# a_16952_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X17 VDD a_9728_8163# a_10416_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X18 GND a_21738_7863# a_21222_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X19 GND a_14200_8163# D3 GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X20 VDD a_25208_8163# D1 VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X21 D6 a_16952_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X22 a_10416_8163# INP a_9645_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X23 a_18986_7863# a_19502_9066# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X24 D1 a_25208_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X25 a_23488_8163# VR1 a_23405_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X26 a_12480_8163# VR3 a_12397_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X27 GND a_9182_9066# a_23405_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X28 GND a_10416_8163# a_10932_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X29 a_15232_8163# a_15232_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X30 VDD a_19502_9066# a_18986_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X31 a_9645_8163# INP a_10416_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X32 VDD a_16952_8163# D6 VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X33 GND a_25208_8163# D1 GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X34 a_13168_8163# a_12480_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X35 a_12397_8163# a_9182_9066# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X36 D6 a_16952_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X37 VDD a_7978_7863# a_7462_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X38 a_18986_7863# INP a_19449_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X39 VDD a_15232_8163# a_15232_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X40 VDD a_18986_7863# a_18470_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X41 a_8494_9066# a_8494_9066# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X42 a_11448_8163# a_10932_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X43 a_19502_9066# a_19502_9066# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X44 VDD a_12480_8163# a_13168_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X45 a_19449_8163# INP a_18986_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X46 GND a_16952_8163# D6 GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X47 D5 a_6946_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X48 a_13168_8163# INP a_12397_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X49 a_24176_8163# a_23488_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X50 a_15232_8163# VR6 a_15149_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X51 D2 a_17954_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X52 GND a_7978_7863# a_7462_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X53 VDD a_8494_9066# a_8494_9066# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X54 VDD a_10932_8163# a_11448_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X55 VDD a_24176_8163# a_24692_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X56 GND a_18986_7863# a_18470_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X57 a_7978_7863# a_8494_9066# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X58 VDD a_19502_9066# a_19502_9066# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X59 a_22254_9066# a_22254_9066# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X60 a_11448_8163# a_10932_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X61 VDD a_12480_8163# a_12480_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X62 a_15149_8163# VR6 a_15232_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X63 a_12397_8163# INP a_13168_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X64 VDD a_23488_8163# a_24176_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X65 VDD a_15232_8163# a_15920_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X66 a_19502_9066# VR2 a_19449_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X67 D5 a_6946_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X68 a_15149_8163# a_9182_9066# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X69 D7 a_20706_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X70 a_24176_8163# INP a_23405_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X71 a_13684_8163# a_13168_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X72 D2 a_17954_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X73 VDD a_8494_9066# a_7978_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X74 VDD a_22254_9066# a_22254_9066# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X75 GND a_24176_8163# a_24692_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X76 GND a_10932_8163# a_11448_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X77 a_7978_7863# INP a_8441_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X78 a_21738_7863# a_22254_9066# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X79 a_15232_8163# VR6 a_15149_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X80 D4 a_11448_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X81 GND a_9182_9066# a_15149_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X82 a_19449_8163# VR2 a_19502_9066# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X83 a_23405_8163# INP a_24176_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X84 VDD a_23488_8163# a_23488_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X85 VDD a_13168_8163# a_13684_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X86 a_15149_8163# INP a_15920_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X87 D7 a_20706_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X88 a_13684_8163# a_13168_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X89 a_24692_8163# a_24176_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X90 VDD a_22254_9066# a_21738_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X91 a_8441_8163# INP a_7978_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X92 a_15149_8163# VR6 a_15232_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X93 a_21738_7863# INP a_22201_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X94 a_15920_8163# a_15232_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X95 D4 a_11448_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X96 a_22201_8163# VR7 a_22254_9066# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X97 GND a_13168_8163# a_13684_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X98 a_16436_8163# a_15920_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X99 a_24692_8163# a_24176_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X100 a_19449_8163# VR2 a_19502_9066# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X101 a_22201_8163# INP a_21738_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X102 a_22254_9066# VR7 a_22201_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X103 VDD a_7462_7863# a_6946_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X104 a_15920_8163# INP a_15149_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X105 VDD a_18470_7863# a_17954_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X106 a_16436_8163# a_15920_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X107 VDD a_6946_7863# D5 VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X108 GND a_9182_9066# a_19449_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X109 a_8441_8163# VR5 a_8494_9066# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X110 VDD a_20706_7863# D7 VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X111 VDD a_17954_7863# D2 VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X112 a_8494_9066# VR5 a_8441_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X113 a_22201_8163# a_9182_9066# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X114 a_22254_9066# VR7 a_22201_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X115 GND a_7462_7863# a_6946_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X116 VDD a_21222_7863# a_20706_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X117 VDD a_13684_8163# a_14200_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X118 GND a_18470_7863# a_17954_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X119 a_7462_7863# a_7978_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X120 a_19502_9066# VR2 a_19449_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X121 a_25208_8163# a_24692_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X122 GND a_9182_9066# a_8441_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X123 a_16952_8163# a_16436_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X124 a_18470_7863# a_18986_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X125 a_8441_8163# VR5 a_8494_9066# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X126 GND a_6946_7863# D5 GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X127 a_22201_8163# VR7 a_22254_9066# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X128 a_9645_8163# VR4 a_9728_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X129 GND a_20706_7863# D7 GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X130 a_12397_8163# VR3 a_12480_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X131 GND a_17954_7863# D2 GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X132 a_6946_7863# a_7462_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X133 a_9728_8163# VR4 a_9645_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X134 a_9728_8163# a_9728_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X135 a_17954_7863# a_18470_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X136 GND a_21222_7863# a_20706_7863# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X137 VDD a_11448_8163# D4 VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X138 GND a_13684_8163# a_14200_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X139 VDD a_24692_8163# a_25208_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X140 a_19449_8163# a_9182_9066# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X141 a_8494_9066# VR5 a_8441_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X142 a_7462_7863# a_7978_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X143 a_21222_7863# a_21738_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X144 a_25208_8163# a_24692_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X145 D3 a_14200_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X146 GND a_9182_9066# a_22201_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X147 a_18470_7863# a_18986_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X148 a_16952_8163# a_16436_8163# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X149 a_9645_8163# VR4 a_9728_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X150 VDD a_9728_8163# a_9728_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X151 a_23405_8163# VR1 a_23488_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X152 a_12397_8163# VR3 a_12480_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.1176 ps=1.12 w=0.84 l=0.15
X153 a_9645_8163# a_9182_9066# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X154 VDD a_15920_8163# a_16436_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X155 a_6946_7863# a_7462_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X156 a_20706_7863# a_21222_7863# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X157 a_23488_8163# VR1 a_23405_8163# GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X158 a_14200_8163# a_13684_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X159 a_10932_8163# a_10416_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X160 a_12480_8163# a_12480_8163# VDD VDD sky130_fd_pr__pfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X161 a_17954_7863# a_18470_7863# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X162 VDD a_16436_8163# a_16952_8163# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X163 VDD a_21738_7863# a_21222_7863# VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X164 GND a_24692_8163# a_25208_8163# GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X165 GND a_11448_8163# D4 GND sky130_fd_pr__nfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
X166 a_8441_8163# a_9182_9066# GND GND sky130_fd_pr__nfet_01v8 ad=0.1176 pd=1.12 as=0.2226 ps=2.21 w=0.84 l=0.15
X167 VDD a_14200_8163# D3 VDD sky130_fd_pr__pfet_01v8 ad=0.2226 pd=2.21 as=0.1176 ps=1.12 w=0.84 l=0.15
C0 a_11448_8163# a_10416_8163# 0.01fF
C1 a_13168_8163# a_9182_9066# 0.41fF
C2 VDD D3 0.88fF
C3 a_15920_8163# D2 0.00fF
C4 a_16436_8163# D6 0.00fF
C5 a_11448_8163# a_9728_8163# 0.00fF
C6 a_12480_8163# a_9182_9066# 0.58fF
C7 VDD D4 0.88fF
C8 a_16436_8163# D3 0.00fF
C9 a_15920_8163# D6 0.00fF
C10 a_11448_8163# a_9182_9066# 0.44fF
C11 VR4 VDD 0.00fF
C12 a_19449_8163# D2 0.00fF
C13 VDD D5 0.80fF
C14 a_15232_8163# D6 0.00fF
C15 a_15920_8163# D3 0.00fF
C16 VR5 VDD 0.00fF
C17 a_15232_8163# D3 0.01fF
C18 INP a_17954_7863# 0.24fF
C19 INP VDD 0.03fF
C20 INP a_16952_8163# 0.25fF
C21 VR1 INP 0.34fF
C22 D1 VDD 0.84fF
C23 INP a_16436_8163# 0.47fF
C24 VR7 INP 0.33fF
C25 a_8441_8163# a_9645_8163# 0.07fF
C26 INP a_23405_8163# 0.17fF
C27 D7 VDD 0.82fF
C28 INP a_15920_8163# 0.45fF
C29 VR2 INP 0.34fF
C30 D1 a_23405_8163# 0.00fF
C31 INP a_22201_8163# 0.14fF
C32 INP a_15232_8163# 0.00fF
C33 VR6 INP 0.37fF
C34 INP a_19449_8163# 0.14fF
C35 VR3 INP 0.40fF
C36 a_20706_7863# a_21222_7863# 0.35fF
C37 D7 a_22201_8163# 0.00fF
C38 a_19502_9066# a_21222_7863# 0.00fF
C39 D7 a_19449_8163# 0.01fF
C40 a_10932_8163# a_12397_8163# 0.00fF
C41 a_19502_9066# a_20706_7863# 0.01fF
C42 a_10416_8163# a_12397_8163# 0.00fF
C43 a_10932_8163# a_9645_8163# 0.00fF
C44 a_18986_7863# a_20706_7863# 0.00fF
C45 a_10932_8163# a_8441_8163# 0.00fF
C46 a_10416_8163# a_9645_8163# 0.90fF
C47 a_9182_9066# a_15149_8163# 0.11fF
C48 a_18470_7863# a_20706_7863# 0.00fF
C49 a_18986_7863# a_19502_9066# 0.50fF
C50 a_14200_8163# D3 0.67fF
C51 a_9182_9066# a_12397_8163# 0.11fF
C52 a_9728_8163# a_9645_8163# 1.89fF
C53 a_10416_8163# a_8441_8163# 0.00fF
C54 a_18470_7863# a_19502_9066# 0.01fF
C55 a_13684_8163# D3 0.00fF
C56 a_9182_9066# a_9645_8163# 0.10fF
C57 a_9728_8163# a_8441_8163# 0.00fF
C58 VDD a_17954_7863# 2.82fF
C59 a_18470_7863# a_18986_7863# 0.85fF
C60 a_13684_8163# D4 0.00fF
C61 a_13168_8163# D3 0.00fF
C62 a_16952_8163# a_17954_7863# 0.43fF
C63 a_8494_9066# a_9645_8163# 0.00fF
C64 a_9182_9066# a_8441_8163# 0.10fF
C65 VDD a_16952_8163# 2.64fF
C66 a_9182_9066# a_21222_7863# 0.52fF
C67 VR1 VDD 0.00fF
C68 a_16436_8163# a_17954_7863# 0.00fF
C69 a_13168_8163# D4 0.00fF
C70 a_12480_8163# D3 0.00fF
C71 a_8494_9066# a_8441_8163# 1.90fF
C72 VDD a_16436_8163# 3.02fF
C73 a_9182_9066# a_20706_7863# 0.42fF
C74 VR7 VDD 0.00fF
C75 a_15920_8163# a_17954_7863# 0.00fF
C76 a_16436_8163# a_16952_8163# 0.35fF
C77 a_12480_8163# D4 0.01fF
C78 a_14200_8163# INP 0.26fF
C79 a_23405_8163# VDD 0.15fF
C80 VR7 VR1 0.04fF
C81 VDD a_15920_8163# 2.72fF
C82 VR2 VDD 0.01fF
C83 a_9182_9066# a_19502_9066# 0.54fF
C84 VR1 a_23405_8163# 0.22fF
C85 a_11448_8163# D4 0.67fF
C86 a_15920_8163# a_16952_8163# 0.01fF
C87 a_13684_8163# INP 0.48fF
C88 a_22201_8163# VDD 0.15fF
C89 a_24692_8163# a_25208_8163# 0.35fF
C90 a_19449_8163# a_17954_7863# 0.00fF
C91 VDD a_15232_8163# 2.77fF
C92 VR6 VDD 0.00fF
C93 a_9182_9066# a_18986_7863# 0.34fF
C94 VR1 a_22201_8163# 0.00fF
C95 VR7 a_23405_8163# 0.00fF
C96 a_15232_8163# a_16952_8163# 0.00fF
C97 a_15920_8163# a_16436_8163# 0.88fF
C98 a_13168_8163# INP 0.47fF
C99 a_10416_8163# a_10932_8163# 0.88fF
C100 a_19449_8163# VDD 0.09fF
C101 a_24176_8163# a_25208_8163# 0.01fF
C102 a_7978_7863# a_9645_8163# 0.00fF
C103 VR3 VDD 0.00fF
C104 a_9182_9066# a_18470_7863# 0.53fF
C105 VR7 a_22201_8163# 0.24fF
C106 a_15232_8163# a_16436_8163# 0.01fF
C107 a_23488_8163# a_21222_7863# 0.00fF
C108 a_9728_8163# a_10932_8163# 0.01fF
C109 a_12480_8163# INP 0.00fF
C110 VR6 a_16436_8163# 0.00fF
C111 a_22201_8163# a_23405_8163# 0.07fF
C112 a_23488_8163# a_25208_8163# 0.00fF
C113 a_7978_7863# a_8441_8163# 0.87fF
C114 a_7462_7863# a_9645_8163# 0.00fF
C115 a_15232_8163# a_15920_8163# 0.49fF
C116 a_22254_9066# a_21222_7863# 0.01fF
C117 a_9728_8163# a_10416_8163# 0.49fF
C118 a_9182_9066# a_10932_8163# 0.61fF
C119 a_11448_8163# INP 0.28fF
C120 VR6 a_15920_8163# 0.01fF
C121 a_7462_7863# a_8441_8163# 0.00fF
C122 VR2 a_19449_8163# 0.26fF
C123 a_22254_9066# a_20706_7863# 0.00fF
C124 a_21738_7863# a_21222_7863# 0.85fF
C125 a_8494_9066# a_10932_8163# 0.00fF
C126 a_9182_9066# a_10416_8163# 0.44fF
C127 VR6 a_15232_8163# 0.24fF
C128 a_6946_7863# a_8441_8163# 0.00fF
C129 a_21738_7863# a_20706_7863# 0.02fF
C130 a_9182_9066# a_9728_8163# 0.62fF
C131 a_8494_9066# a_10416_8163# 0.00fF
C132 a_21738_7863# a_19502_9066# 0.00fF
C133 a_8494_9066# a_9728_8163# 0.01fF
C134 a_8494_9066# a_9182_9066# 0.05fF
C135 a_24692_8163# a_9182_9066# 0.00fF
C136 D6 a_15149_8163# 0.00fF
C137 a_24176_8163# a_9182_9066# 0.00fF
C138 a_10416_8163# a_7978_7863# 0.00fF
C139 D3 a_15149_8163# 0.01fF
C140 a_23488_8163# a_9182_9066# 0.06fF
C141 a_9728_8163# a_7978_7863# 0.00fF
C142 a_14200_8163# VDD 2.59fF
C143 D3 a_12397_8163# 0.00fF
C144 a_22254_9066# a_9182_9066# 0.44fF
C145 a_9728_8163# a_7462_7863# 0.00fF
C146 a_24176_8163# a_24692_8163# 0.88fF
C147 a_9182_9066# a_7978_7863# 0.00fF
C148 a_13684_8163# VDD 3.01fF
C149 a_14200_8163# a_16436_8163# 0.00fF
C150 D4 a_12397_8163# 0.01fF
C151 a_21738_7863# a_9182_9066# 0.33fF
C152 a_8494_9066# a_7978_7863# 0.50fF
C153 a_23488_8163# a_24692_8163# 0.01fF
C154 a_9182_9066# a_7462_7863# 0.00fF
C155 a_13168_8163# VDD 2.70fF
C156 a_14200_8163# a_15920_8163# 0.01fF
C157 D4 a_9645_8163# 0.00fF
C158 a_23488_8163# a_24176_8163# 0.49fF
C159 a_22254_9066# a_24692_8163# 0.00fF
C160 a_8494_9066# a_7462_7863# 0.01fF
C161 a_12480_8163# VDD 2.77fF
C162 a_14200_8163# a_15232_8163# 0.01fF
C163 VR4 a_9645_8163# 0.22fF
C164 INP a_15149_8163# 0.18fF
C165 a_14200_8163# VR6 0.05fF
C166 a_18986_7863# D2 0.00fF
C167 a_22254_9066# a_24176_8163# 0.00fF
C168 a_8494_9066# a_6946_7863# 0.00fF
C169 a_11448_8163# VDD 2.63fF
C170 a_13684_8163# a_15232_8163# 0.00fF
C171 D5 a_8441_8163# 0.00fF
C172 VR5 a_9645_8163# 0.00fF
C173 VR4 a_8441_8163# 0.00fF
C174 INP a_12397_8163# 0.18fF
C175 a_18986_7863# D6 0.00fF
C176 a_18470_7863# D2 0.00fF
C177 a_21738_7863# a_24176_8163# 0.00fF
C178 a_22254_9066# a_23488_8163# 0.01fF
C179 a_13168_8163# a_15232_8163# 0.00fF
C180 INP a_9645_8163# 0.18fF
C181 VR5 a_8441_8163# 0.26fF
C182 a_13684_8163# VR3 0.00fF
C183 a_18470_7863# D6 0.00fF
C184 a_21738_7863# a_23488_8163# 0.00fF
C185 INP a_8441_8163# 0.16fF
C186 a_13168_8163# VR3 0.01fF
C187 INP a_21222_7863# 0.46fF
C188 a_21738_7863# a_22254_9066# 0.49fF
C189 a_7462_7863# a_7978_7863# 0.85fF
C190 a_12480_8163# VR3 0.24fF
C191 INP a_20706_7863# 0.24fF
C192 a_6946_7863# a_7978_7863# 0.02fF
C193 D1 a_25208_8163# 0.68fF
C194 a_11448_8163# VR3 0.05fF
C195 INP a_19502_9066# 0.00fF
C196 D7 a_21222_7863# 0.00fF
C197 a_9182_9066# D2 0.00fF
C198 a_10932_8163# D4 0.00fF
C199 a_6946_7863# a_7462_7863# 0.35fF
C200 INP a_18986_7863# 0.46fF
C201 D7 a_20706_7863# 0.66fF
C202 a_10416_8163# D4 0.00fF
C203 a_9182_9066# D6 0.00fF
C204 VR4 a_10932_8163# 0.00fF
C205 D7 a_19502_9066# 0.01fF
C206 INP a_18470_7863# 0.46fF
C207 a_9182_9066# D3 0.01fF
C208 a_9728_8163# D4 0.00fF
C209 VR4 a_10416_8163# 0.00fF
C210 D7 a_18986_7863# 0.00fF
C211 a_9182_9066# D4 0.01fF
C212 INP a_10932_8163# 0.49fF
C213 VR5 a_10416_8163# 0.00fF
C214 VR4 a_9728_8163# 0.24fF
C215 D7 a_18470_7863# 0.00fF
C216 VR4 a_9182_9066# 0.00fF
C217 INP a_10416_8163# 0.48fF
C218 VR5 a_9182_9066# 0.00fF
C219 INP a_9728_8163# 0.00fF
C220 a_13684_8163# a_14200_8163# 0.35fF
C221 VDD a_15149_8163# 0.15fF
C222 INP a_9182_9066# 0.00fF
C223 VR5 a_8494_9066# 0.24fF
C224 a_16952_8163# a_15149_8163# 0.00fF
C225 a_13168_8163# a_14200_8163# 0.01fF
C226 VDD a_12397_8163# 0.15fF
C227 INP a_8494_9066# 0.00fF
C228 a_13168_8163# a_13684_8163# 0.88fF
C229 a_16436_8163# a_15149_8163# 0.00fF
C230 a_12480_8163# a_14200_8163# 0.00fF
C231 VDD a_9645_8163# 0.15fF
C232 D7 a_9182_9066# 0.03fF
C233 a_12480_8163# a_13684_8163# 0.01fF
C234 a_15920_8163# a_15149_8163# 0.92fF
C235 a_24692_8163# INP 0.00fF
C236 VDD a_8441_8163# 0.15fF
C237 a_11448_8163# a_13684_8163# 0.00fF
C238 a_15232_8163# a_15149_8163# 1.92fF
C239 a_12480_8163# a_13168_8163# 0.49fF
C240 a_24176_8163# INP 0.17fF
C241 a_24692_8163# D1 0.00fF
C242 a_21222_7863# VDD 3.04fF
C243 a_7978_7863# D5 0.00fF
C244 VR6 a_15149_8163# 0.24fF
C245 VDD a_25208_8163# 2.42fF
C246 a_11448_8163# a_13168_8163# 0.01fF
C247 a_24176_8163# D1 0.00fF
C248 a_23488_8163# INP 0.00fF
C249 a_7462_7863# D5 0.00fF
C250 a_20706_7863# VDD 2.47fF
C251 VR5 a_7978_7863# 0.00fF
C252 a_19502_9066# a_17954_7863# 0.00fF
C253 VR7 a_21222_7863# 0.00fF
C254 a_11448_8163# a_12480_8163# 0.01fF
C255 a_23488_8163# D1 0.00fF
C256 a_22254_9066# INP 0.00fF
C257 a_19502_9066# VDD 2.71fF
C258 a_21222_7863# a_23405_8163# 0.00fF
C259 a_6946_7863# D5 0.68fF
C260 VR5 a_7462_7863# 0.00fF
C261 VR3 a_12397_8163# 0.24fF
C262 INP a_7978_7863# 0.17fF
C263 a_18986_7863# a_17954_7863# 0.02fF
C264 a_23405_8163# a_25208_8163# 0.00fF
C265 VR2 a_21222_7863# 0.00fF
C266 a_21738_7863# INP 0.45fF
C267 a_18986_7863# VDD 3.18fF
C268 a_21222_7863# a_22201_8163# 0.00fF
C269 INP a_7462_7863# 0.00fF
C270 a_18986_7863# a_16952_8163# 0.00fF
C271 a_18470_7863# a_17954_7863# 0.35fF
C272 VR2 a_20706_7863# 0.05fF
C273 a_21222_7863# a_19449_8163# 0.00fF
C274 a_18470_7863# VDD 3.34fF
C275 a_20706_7863# a_22201_8163# 0.00fF
C276 INP a_6946_7863# 0.00fF
C277 a_18470_7863# a_16952_8163# 0.00fF
C278 VR2 a_19502_9066# 0.24fF
C279 a_21738_7863# D7 0.00fF
C280 a_20706_7863# a_19449_8163# 0.06fF
C281 D6 D2 0.07fF
C282 a_10932_8163# VDD 3.11fF
C283 VR2 a_18986_7863# 0.01fF
C284 a_19502_9066# a_19449_8163# 1.90fF
C285 a_10416_8163# VDD 2.78fF
C286 VR2 a_18470_7863# 0.00fF
C287 a_18986_7863# a_19449_8163# 0.88fF
C288 a_9728_8163# VDD 2.78fF
C289 a_9182_9066# a_17954_7863# 0.32fF
C290 a_18470_7863# a_19449_8163# 0.00fF
C291 a_9182_9066# VDD 28.62fF
C292 a_9182_9066# a_16952_8163# 0.33fF
C293 VR1 a_9182_9066# 0.00fF
C294 a_8494_9066# VDD 2.89fF
C295 a_9182_9066# a_16436_8163# 0.55fF
C296 a_14200_8163# a_15149_8163# 0.08fF
C297 VR7 a_9182_9066# 0.00fF
C298 a_9182_9066# a_23405_8163# 0.10fF
C299 INP D2 0.00fF
C300 a_24692_8163# VDD 3.35fF
C301 a_9182_9066# a_15920_8163# 0.38fF
C302 a_14200_8163# a_12397_8163# 0.00fF
C303 a_13684_8163# a_15149_8163# 0.00fF
C304 VR2 a_9182_9066# 0.00fF
C305 a_24692_8163# VR1 0.00fF
C306 a_9182_9066# a_22201_8163# 0.10fF
C307 INP D6 0.00fF
C308 a_24176_8163# VDD 2.95fF
C309 a_9182_9066# a_15232_8163# 0.54fF
C310 VR6 a_9182_9066# 0.00fF
C311 a_13684_8163# a_12397_8163# 0.00fF
C312 a_13168_8163# a_15149_8163# 0.00fF
C313 a_24176_8163# VR1 0.00fF
C314 a_9182_9066# a_19449_8163# 0.12fF
C315 INP D3 0.00fF
C316 a_24692_8163# a_23405_8163# 0.00fF
C317 a_23488_8163# VDD 3.01fF
C318 a_13168_8163# a_12397_8163# 0.92fF
C319 VR3 a_9182_9066# 0.00fF
C320 a_24176_8163# VR7 0.00fF
C321 a_23488_8163# VR1 0.24fF
C322 INP D4 0.00fF
C323 a_22254_9066# VDD 2.66fF
C324 a_24176_8163# a_23405_8163# 0.90fF
C325 VR5 VR4 0.04fF
C326 a_24692_8163# a_22201_8163# 0.00fF
C327 VDD a_7978_7863# 3.09fF
C328 a_12480_8163# a_12397_8163# 1.92fF
C329 INP VR4 0.42fF
C330 a_24176_8163# a_22201_8163# 0.00fF
C331 a_23488_8163# a_23405_8163# 1.89fF
C332 a_21738_7863# VDD 2.88fF
C333 VDD a_7462_7863# 3.34fF
C334 a_11448_8163# a_12397_8163# 0.08fF
C335 a_22254_9066# VR7 0.24fF
C336 INP VR5 0.45fF
C337 a_23488_8163# a_22201_8163# 0.00fF
C338 a_22254_9066# a_23405_8163# 0.00fF
C339 VDD a_6946_7863# 2.42fF
C340 a_11448_8163# a_9645_8163# 0.00fF
C341 a_21738_7863# VR7 0.00fF
C342 a_21738_7863# a_23405_8163# 0.00fF
C343 a_22254_9066# a_22201_8163# 1.87fF
C344 a_21738_7863# VR2 0.00fF
C345 a_21738_7863# a_22201_8163# 0.86fF
C346 D7 INP 0.00fF
C347 a_21738_7863# a_19449_8163# 0.00fF
C348 a_17954_7863# D2 0.66fF
C349 a_12480_8163# a_10932_8163# 0.00fF
C350 a_14200_8163# a_9182_9066# 0.42fF
C351 VDD D2 0.97fF
C352 a_17954_7863# D6 0.00fF
C353 a_16952_8163# D2 0.00fF
C354 a_11448_8163# a_10932_8163# 0.35fF
C355 a_13684_8163# a_9182_9066# 0.58fF
C356 a_12480_8163# a_10416_8163# 0.00fF
C357 VDD D6 0.95fF
C358 a_16436_8163# D2 0.00fF
C359 a_16952_8163# D6 0.67fF
C360 VR1 GND 1.08fF
C361 VR7 GND 1.11fF
C362 VR2 GND 1.10fF
C363 VR6 GND 1.09fF
C364 VR3 GND 1.09fF
C365 VR4 GND 1.09fF
C366 VR5 GND 1.10fF
C367 D1 GND 0.56fF
C368 D7 GND 0.67fF
C369 D2 GND 0.56fF
C370 D6 GND 0.58fF
C371 D3 GND 0.58fF
C372 D4 GND 0.58fF
C373 D5 GND 0.59fF
C374 VDD GND 21.78fF
C375 a_23405_8163# GND 1.05fF
C376 a_22201_8163# GND 1.17fF
C377 a_19449_8163# GND 1.07fF
C378 a_15149_8163# GND 0.87fF
C379 a_12397_8163# GND 0.87fF
C380 a_9645_8163# GND 1.04fF
C381 a_8441_8163# GND 1.07fF
C382 a_25208_8163# GND 1.52fF
C383 a_24692_8163# GND 0.83fF
C384 a_24176_8163# GND 0.02fF
C385 a_21222_7863# GND 0.79fF
C386 a_20706_7863# GND 1.03fF
C387 a_18470_7863# GND 0.84fF
C388 a_17954_7863# GND 0.83fF
C389 a_16952_8163# GND 1.46fF
C390 a_16436_8163# GND 0.83fF
C391 a_14200_8163# GND 1.07fF
C392 a_13684_8163# GND 0.79fF
C393 a_11448_8163# GND 1.07fF
C394 a_10932_8163# GND 0.79fF
C395 a_7978_7863# GND 0.08fF
C396 a_7462_7863# GND 0.81fF
C397 a_6946_7863# GND 0.92fF
.ends
</pre>
</details>

  ![image](https://user-images.githubusercontent.com/86735438/230720518-29fb6f13-4bd5-4d4b-b858-356b2cf593c5.png)

#### 4. Align Post Layout simulation for 3 bit Flash ADC
  ![image](https://user-images.githubusercontent.com/86735438/230720792-48337e78-6df5-43d9-a50c-51880e2621c8.png)
