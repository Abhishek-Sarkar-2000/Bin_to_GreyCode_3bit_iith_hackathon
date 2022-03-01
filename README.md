# 3-bit Binary to Grey Code Converter using Low Voltage XOR Gates
* This is a submission repo for the final circuit design implemented and simulated in custom compiler by [Synopsys, Inc.](https://www.synopsys.com/) on 28nm CMOS technology as a result of literature survey conducted, for [IITH Analog IC Design Hackathon](https://hackathoniith.in/), 2022.
* The aforementioned literature survey can be referred [here](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/3-bit%20Binary%20to%20Grey%20Code%20Converter%20using%20Low%20Voltage%20XOR%20Gates.pdf) in the repository.
* The repo contains, apart from the main circuit and its waveforms, a comparison of output waveform for the XOR gate made with varying _w/l_ ratios on the MOS transistors, and also a method to scale the circuit by cascading the 3-bit binary-to-grey code converter IC designed.


# Table of Contents
  * [Introduction](#introduction)
  * [Reference Circuit](#reference-circuit)
- [Simulation in Synopsys](#simulation-in-synopsys)
  - [Schematic](#schematic)
    * [XOR gate](#xor-gate)
    * [Converter Circuit](#converter-circuit)
  * [Symbols](#symbols)
  * [Implementation](#implementation) 
  * [Netlist](#netlist)
  * [Waveforms](#waveforms)
  * [Comparison of _w/l_ values](#comparison-of-w/l-values)
  * [Scaling](#scaling)
  * [Conclusion](#conclusion)
  * [Acknowledgement](#acknowledgement)
  * [References](#references)


## Introduction

Gray codes are very useful for creating a normal sequence of binary numbers that may result in an error when two successive values differ by only one bit (binary digit). Recognizing Gray codes is very easy since they refer to an ordering of binary numbers in which successive values differ by only one bit.
The binary to gray code converter is based on a very common transmission gate technology. For operating at low supply voltages(below 2V), double pass-transistor(DPL) XOR
and XNOR circuits were used to improve circuit performance and reduce area.

## Reference Circuit


# Simulation in Synopsys
## Schematic
### XOR Gate
![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_ckt.png)

Fig. 2(i): Implementation of XOR circuit

<img src="https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_sym.png" width="500"/>

Fig. 2(ii): Symbol for the XOR circuit.

### Converter Circuit
![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/BGC_ckt.png)

Fig. 3(i): Implementation of the 3-bit Binary to Grey Code converter circuit

<img src="https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/BGC_sym.png" width="500"/>

Fig. 3(ii): Symbol designed for the circuit.

## Symbols
![image](https://user-images.githubusercontent.com/70422874/155395211-46a552b1-bb5b-46b6-8c6b-2f2644efc1c9.png)

   Fig. 6(i): NOR_2 symbol   


![image](https://user-images.githubusercontent.com/70422874/155393369-71c9335b-19d2-4000-ae9c-e6aefe08ab2a.png)

   Fig. 6(ii): NOR_2 schematic
   
   
 ![image](https://user-images.githubusercontent.com/70422874/155395532-ce04e960-efd8-4d69-885d-67d11b43cca7.png)

    Fig. 7(i): NOT_2 symbol  
   
![image](https://user-images.githubusercontent.com/70422874/155393400-51ab7b79-6a65-4160-892d-a8d0ca3e5332.png)

    Fig. 7(ii): NOT_2 schematic
        
![image](https://user-images.githubusercontent.com/70422874/155396013-98aaf6d4-464b-4163-82ce-7be0ba5ab453.png)

 Fig. 8(i): NOR_4 symbol
    
![image](https://user-images.githubusercontent.com/70422874/155395881-4531da61-646d-4454-8788-574b423e16e3.png)
    <p align="center">
Fig. 8(ii): NOR_4 schematic
    
    
  </p>
Note: To make the CMOS Level circuit more compatible and Industry ready a Symbol reference has been created. So, it makes easy whenever a testbench of different Parameters needs to be tested.

## Parameters set for Voltage Source for inputs
![image](https://user-images.githubusercontent.com/70422874/155529254-db5e778c-b6bd-4893-af09-7475bd618c08.png)

 <p align="center">
  Fig. 9(i): Voltage Source Input at A.
  </p>
  
![image](https://user-images.githubusercontent.com/70422874/155529693-ed483e7a-fcf7-4794-b17a-9611bb446921.png)

<p align="center">
  Fig. 9(ii): Voltage Source Input at B.
  </p>

![image](https://user-images.githubusercontent.com/70422874/155529889-582dc467-1f8b-4902-99d1-e5e588a26865.png)
<p align="center">
Fig. 9(iii): Voltage Source Input at C.  

</p>

## Parameters set for DC Voltage Source for VDD
![image](https://user-images.githubusercontent.com/70422874/155530830-8109a26c-d14d-4e33-a19b-5f666a7b59ce.png)
<p align="center">
  Fig. 10: VDD Supply voltage
</p>


## Transient Settings
![image](https://user-images.githubusercontent.com/70422874/155531098-e85de0da-2f43-40a4-bc41-49c69e29d961.png)
<p align="center">
  Fig. 11: The Transient Analysis Inputs run at 1us step with stop time 100us 
</p>

## Netlist
```
*  Generated for: PrimeSim
*  Design library name: my_design
*  Design cell name: design
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Wed Feb 23 19:46:53 2022

.global gnd!
********************************************************************************
* Library          : my_design
* Cell             : NOR_2
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt nor_2 net2 net9 net12 net16 net27
xm5 net31 net27 net9 net31 p105 w=0.654u l=0.03u nf=1 m=1
xm0 net31 net12 net2 net2 p105 w=0.654u l=0.03u nf=1 m=1
xm4 net16 net27 net9 net16 n105 w=0.518u l=0.03u nf=1 m=1
xm2 net9 net12 net16 net16 n105 w=0.518u l=0.03u nf=1 m=1
.ends nor_2

********************************************************************************
* Library          : my_design
* Cell             : NOR_4_1
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt nor_4_1 net4 net5 net14 net15 net18 net21 net22
xi4 net18 net21 net48 net22 net53 nor_2
xi3 net18 net53 net51 net22 net51 nor_2
xi2 net18 net51 net14 net22 net15 nor_2
xi1 net18 net48 net50 net22 net50 nor_2
xi0 net18 net50 net4 net22 net5 nor_2
.ends nor_4_1

********************************************************************************
* Library          : my_design
* Cell             : NOT_2
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt not_2 net9 net12 net13 net14
xm1 net9 net14 net13 net9 n105 w=0.518u l=0.03u nf=1 m=1
xm2 net13 net14 net12 net12 p105 w=1.06u l=0.03u nf=1 m=1
.ends not_2

********************************************************************************
* Library          : my_design
* Cell             : design
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi4 net70 net50 net84 net71 net81 net25 gnd! nor_4_1
xi3 net46 net84 net25 net24 net81 net50 gnd! nor_4_1
xi0 net42 net50 net8 net25 net81 net84 gnd! nor_4_1
xi5 net81 net71 net25 gnd! net74 nor_2
xi2 net81 net24 net50 gnd! net49 nor_2
xi1 net81 net8 net84 gnd! net85 nor_2
xi9 gnd! net81 net70 net74 not_2
xi7 gnd! net81 net42 net85 not_2
xi8 gnd! net81 net46 net49 not_2
v10 net81 gnd! dc=1.2
c15 net84 gnd! c=1p
c14 net25 gnd! c=1p
c13 net50 gnd! c=1p
v23 net49 gnd! dc=0 pat ( 1.2 0 0 0.1u 0.1u 5u b001001110010 )
v22 net85 gnd! dc=0 pat ( 1.2 0 0 0.1u 0.1u 5u b011100100010 )
v24 net74 gnd! dc=0 pat ( 1.2 0 0 0.1u 0.1u 5u b000100100111 )








.tran '1u' '100u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(net25) v(net49) v(net50) v(net74) v(net84) v(net85)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end

```
## Output Waveforms
![image](https://user-images.githubusercontent.com/70422874/155396831-0b9b3acf-57ae-49d3-a4c5-2b237eda43e1.png)

  Fig. 12: Required Simulation Waveforms 
  
  Note: The 1st 3 waveforms are the inputs A, B, and C respectively, while the last 3 are the outputs Q1, Q2, and Q3 respectively, which is same as depicted in above expected waveform representation.
</p>

## Explanation for Observed Waveforms
![output waveforms_2](https://user-images.githubusercontent.com/70422874/155540594-344ba5d0-19c4-427b-bd31-658dee3f7072.jpg)

In time interval T1, input A goes high first. The output follows this input only, while any change in voltage of the other two inputs has NO effect on the output, in this time interval, ie. until input A remains high. Similar changes take place in time intervals T2 and T3.

## Conclusion
Thus, the observed output waveforms match perfectly with our hand drawn output waveforms, for the required set of inputs. Hence, our required design for CMOS digital combinational logic based electronic buzzer circuit with 3 inputs that selects the output based on  the relative time of application of input(which is assumed here as input going from low to high voltage levels), has been implemented and verified using Synopsys Custom Compiler on 28nm CMOS technology. As per design requirements, similar logic can be applied  for a greater number of inputs.
The designed circuit is purely combinational, and hence independent of any clock signal.

## Acknowledgement
1. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
2. Chinmay panda, IIT Hyderabad
3. Sameer Durgoji, NIT Karnataka
4. Synopsys Team/Company
5. https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/

## References
[1] Balraj Singh, Mukesh Kumar, and J. S. Ubhi, “Analysis of CMOS based
NAND and NOR Gates at 45mm Technology”, IJEECS, ISSN 2348-
117X, Volume 6, Issue 4, April 2017.
[2] Sudhakar Alluri1, Uma Umaheshwar, B. Rajendra Naik and
N.S.S.Reddy, “Design and Performance Analysis of VLSI Circuits in
180nm Technology”, IJCRT, ISSN: 2320-2882, Volume 6, Issue 2 April
2018



