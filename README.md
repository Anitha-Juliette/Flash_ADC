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
## <div align="center"> WEEK4 AI's
### ANALOG PART - 1 BIT ADC
  ![image](https://user-images.githubusercontent.com/86735438/224346331-c96e4896-2435-48e9-9844-26ff2c181561.png)
#### 1. Schematic of Opamp
  ![image](https://user-images.githubusercontent.com/86735438/224349110-4c73df55-8efd-40bf-95c4-90c84a6405c6.png)
#### 2. Testing of Opamp - opamp.spice
        .lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
        XM1 net1 net1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1 m=1
        XM3 net1 Vm net2 net2 sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XM4 Out1 Vp net2 net2 sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XM5 net2 Vint Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XM6 Vint Vint Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XR1 Vint Vdd GND sky130_fd_pr__res_xhigh_po_0p69 L=100 mult=1 m=1
        XM7 Out1 net1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1 m=1
        XM8 out2 Out1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1 m=1
        XM9 out2 Vint Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        V1 Vdd GND dc 1.8
        V2 Vss GND dc -1.8
        V3 Vp GND sine(0 1 60)
        V4 Vm GND sine(0 -1 60)
        .tran 1m 0.1
        .control
        run
        plot v(Vm)
        plot v(Vp)
        plot v(out2)
        .endc
        .end
#### 3. Opamp - inputs & outputs
  ![image](https://user-images.githubusercontent.com/86735438/224351012-752df467-a0ed-4555-a866-fcb777b318a4.png)
![image](https://user-images.githubusercontent.com/86735438/224351121-aa3c17bc-ec1f-441e-915a-045cdeb6124c.png)
![image](https://user-images.githubusercontent.com/86735438/224351217-2649e526-8eb8-444b-acad-a90c8f77a0c3.png)
#### 4. Opamp - Differential Gain - Spice file & output  
        .lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
        XM1 net1 net1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1 m=1
        XM3 net1 Vm net2 net2 sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XM4 Out1 Vp net2 net2 sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XM5 net2 Vint Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XM6 Vint Vint Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        XR1 Vint Vdd GND sky130_fd_pr__res_xhigh_po_0p69 L=100 mult=1 m=1
        XM7 Out1 net1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1 m=1
        XM8 out2 Out1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1 m=1
        XM9 out2 Vint Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1 m=1
        V1 Vdd GND dc 1.8
        V2 Vss GND dc -1.8
        V3 Vm gnd ac 1
        V4 Vp gnd dc 0
        .ac dec 101 1 1g
        .control
        run
        plot db(V(out2)/V(Vm))
        plot 180/PI*phase(V(out2))
        .endc
        .end  
![image](https://user-images.githubusercontent.com/86735438/224377717-2634155b-9e71-41e7-b88c-ef3a001ecbb5.png)
![image](https://user-images.githubusercontent.com/86735438/224377800-c54fc4b9-6d2d-41ca-b124-f41404568c99.png) 
#### 5. Schematic - ADC
  ![image](https://user-images.githubusercontent.com/86735438/224352697-75254ade-48f3-4b40-9ea0-a02765f51b8b.png)
#### 6. Testing of ADC - ADC.spice
        .lib /usr/local/share/pdk/sky130A/libs.tech/ngspice/sky130.lib.spice tt
        x1 Vdd Out Vref_2 Vin Vss opamp
        XR1 Vref_2 Vref GND sky130_fd_pr__res_xhigh_po_0p69 L=100
        XR2 GND Vref_2 GND sky130_fd_pr__res_xhigh_po_0p69 L=100
        .subckt opamp Vdd out2 Vm Vp Vss
        XM1 net1 net1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1
        XM3 net1 Vm net2 net2 sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1
        XM4 Out1 Vp net2 net2 sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1
        XM5 net2 Vref Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1
        XM6 Vref Vref Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1
        XR3 Vref Vdd GND sky130_fd_pr__res_xhigh_po_0p69 L=100
        XM7 Out1 net1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1
        XM8 out2 Out1 Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=4 nf=1
        XM9 out2 Vref Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=2 nf=1
        .ends
        V1 Vdd GND dc 1.8
        V2 Vss GND dc -1.8
        V3 Vin GND sine(0 1.8 60)
        V4 Vref GND dc 1
        .tran 1m 0.1
        .control
        run
        plot v(Vin)
        plot v(Vref)
        plot v(Vref_2)
        plot v(out)
        .endc
        .end
 #### 7. ADC - inputs & outputs
 ![image](https://user-images.githubusercontent.com/86735438/224357165-22335cec-2624-41d4-a4a5-2cc79c441842.png)
![image](https://user-images.githubusercontent.com/86735438/224357261-452b3f04-0972-42df-b5d6-3e5e166677fa.png)
![image](https://user-images.githubusercontent.com/86735438/224357334-e4b12fa6-13ba-4ba4-aed1-517ce9df1c7a.png)
![image](https://user-images.githubusercontent.com/86735438/224357406-6f128b93-2569-4aba-9633-667254e65812.png)



  
  
  



