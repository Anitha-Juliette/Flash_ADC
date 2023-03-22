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
#### 7.  POST LAYOUT OUTPUT
![image](https://user-images.githubusercontent.com/86735438/227033552-f8162829-01d4-4815-8202-711f5d05337e.png)
