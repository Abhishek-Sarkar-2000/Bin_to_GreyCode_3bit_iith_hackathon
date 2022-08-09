# 3-bit Binary to Grey Code Converter using Low Voltage XOR Gates
* This is a submission repo for the final circuit design implemented and simulated in custom compiler by [Synopsys, Inc.](https://www.synopsys.com/) on 28nm CMOS technology as a result of literature survey conducted, for [IITH Analog IC Design Hackathon](https://hackathoniith.in/), 2022.
* The aforementioned literature survey can be referred [here](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/3-bit%20Binary%20to%20Grey%20Code%20Converter%20using%20Low%20Voltage%20XOR%20Gates.pdf) in the repository.
* The repo contains, apart from the main circuit and its waveforms, a comparison of output waveform for the XOR gate made with varying _w/l_ ratios on the MOS transistors, and also a method to scale the circuit by cascading the 3-bit binary-to-grey code converter IC designed.
* [UPDATE] Click [here](IC_Des_hackathon.pdf) to view the Certificate of Appreciation.


# Table of Contents
  * [Introduction](#introduction)
- [Simulation in Synopsys](#simulation-in-synopsys)
  - [Schematic and Symbols](#schematic-and-symbols)
    * [XOR gate](#xor-gate)
    * [Converter Circuit](#converter-circuit)
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

# Simulation in Synopsys
## Schematic and Symbols
### XOR Gate
![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_ckt2.png)

_Fig. 1(i): Implementation of XOR circuit_

<img src="https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_sym.png" width="500"/>

_Fig. 1(ii): Symbol for the XOR circuit_

### Converter Circuit
![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/BGC_ckt2.png)

_Fig. 2(i): Implementation of the 3-bit Binary to Grey Code converter circuit_

<img src="https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/BGC_sym.png" width="500"/>

_Fig. 2(ii): Symbol designed for the circuit_

![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/BCG_simulation.png)

_Fig. 2(iii): Final circuit for simulation_

## Implementation
* Each XOR gate is implemented as a combination of CMOS transmission-gate and CMOS inverters, and is sized uniformly with (W/L)pFET/(W/L)nFET = **(0.55u/0.15u)/(0.42u/0.15u)**.
* The final IC has total **20 transistors**, two XOR gates having 8 transistors each and 4 transistors forming a buffer for getting g2 directly from input b2.
* Each XOR gate is made up of three CMOS inverters and one transmission-gate with transistors sized over a constant width of 0.3 um.
* The sizing for the two **inverters catching the inputs** is taken to be (W/L)pFET/(W/L)nFET = **(0.3u/0.09u)/(0.3u/0.09u)**
* The transistors in the **transmission gate** is sized following the sizing rule as (W/L)pFET/(W/L)nFET = **(0.3u/0.05u)/(0.3u/0.05u)**
* The **inverter at the output** is has (W/L)pFET/(W/L)nFET = **(0.3u/0.05u)/(0.3u/0.06u)**
* The **buffer transistors** in the final circuit have a sizing of (W/L)pFET/(W/L)nFET = **(0.3u/0.03u)/(0.3u/0.03u)**

## Netlist
```
*  Generated for: PrimeSim
*  Design library name: abhishek_lib
*  Design cell name: bgc_3bit_tb
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Tue Mar  1 11:57:41 2022

.global gnd! vdd!
********************************************************************************
* Library          : abhishek_lib
* Cell             : XOR
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt xor a b gnd_1 out vdd vt_bulk_n_gnd! vt_bulk_p_vdd!
xm8 out net24 gnd_1 vt_bulk_n_gnd! n105 w=0.3u l=0.06u nf=1 m=1
xm2 net24 a b vt_bulk_n_gnd! n105 w=0.3u l=0.05u nf=1 m=1
xm1 net24 b a vt_bulk_n_gnd! n105 w=0.3u l=0.09u nf=1 m=1
xm0 net11 a gnd_1 vt_bulk_n_gnd! n105 w=0.9u l=0.09u nf=1 m=1
xm9 out net24 vdd vt_bulk_p_vdd! p105 w=0.3u l=0.05u nf=1 m=1
xm5 net24 net11 b vt_bulk_p_vdd! p105 w=0.3u l=0.05u nf=1 m=1
xm4 net24 b net11 vt_bulk_p_vdd! p105 w=0.3u l=0.09u nf=1 m=1
xm3 net11 a vdd vt_bulk_p_vdd! p105 w=0.3u l=0.09u nf=1 m=1
.ends xor

********************************************************************************
* Library          : abhishek_lib
* Cell             : bin_grcode_conv_3bit
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt bin_grcode_conv_3bit gnd_1 vdd b0 b1 b2 g0 g1 g2 vt_bulk_n_gnd!
+ vt_bulk_p_vdd!
xi1 b1 b0 gnd_1 g0 vdd vt_bulk_n_gnd! vt_bulk_p_vdd! xor
xi0 b2 b1 gnd_1 g1 vdd vt_bulk_n_gnd! vt_bulk_p_vdd! xor
xm10 g2 net40 gnd_1 vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 net40 b2 gnd_1 vt_bulk_n_gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm9 g2 net40 vdd vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm8 net40 b2 vdd vt_bulk_p_vdd! p105 w=0.1u l=0.03u nf=1 m=1
.ends bin_grcode_conv_3bit

********************************************************************************
* Library          : abhishek_lib
* Cell             : bgc_3bit_tb
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi1 gnd! net24 b0 b1 b2 g0 g1 g2 gnd! vdd! bin_grcode_conv_3bit
v4 b2 gnd! dc=0 pat ( 1.05 0 0 0.01u 0.03u 1u b00001111 )
v3 b1 gnd! dc=0 pat ( 1.05 0 0 0.01u 0.03u 1u b00110011 )
v2 b0 gnd! dc=0 pat ( 1.05 0 0 0.01u 0.03u 1u b01010101 )
v5 net24 gnd! dc=1.2
c8 g0 gnd! c=1p
c7 g1 gnd! c=1p
c6 g2 gnd! c=1p








.tran '0.5u' '8u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(b0) v(b1) v(b2) v(g0) v(g1) v(g2)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end
```
## Waveforms
![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/BGC_wav.png)

_Fig. 5: Output waveforms corresponding to fig. 3(iii) in order of **g2, b2, g1, b1, g0, b0** from top to bottom_
  
  Note #1: The order is similar to the reference waveform given in the [literature survey](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/3-bit%20Binary%20to%20Grey%20Code%20Converter%20using%20Low%20Voltage%20XOR%20Gates.pdf).
  Note #2: Rise time and fall time for the inputs are set as 0.01 us and 0.03 us respectively

## Comparison of _w/l_ values
Here is a graphical comparison of the effect of various _w/l_ values of the inverter at the output on the waveform of the XOR output in simulation of the following circuit:

![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_sim.png)

* (W/L)pFET/(W/L)nFET = **(0.3u/0.05u)/(0.3u/0.06u)**

![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_1.png)

* (W/L)pFET/(W/L)nFET = **(0.3u/0.05u)/(0.3u/0.04u)**

![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_2.png)

* (W/L)pFET/(W/L)nFET = **(0.3u/0.05u)/(0.3u/0.08u)**

![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_3.png)

* (W/L)pFET/(W/L)nFET = **(0.3u/0.08u)/(0.3u/0.06u)**

![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_4.png)

* (W/L)pFET/(W/L)nFET = **(0.3u/0.04u)/(0.3u/0.06u)**

![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/XOR_5.png)

As we can see, there is an unwanted disturbance in the waveform which is because of the rise and fall time delay of the transistors. We used such values which provided an output close to ideal in the final 3-bit binary to grey code converter circuit.

## Scaling

We can scale the converter to include more number of bits by cascading multiple 3-bit converters as: 
![image](https://github.com/Abhishek-Sarkar-2000/Bin_to_GreyCode_3bit_iith_hackathon/blob/main/screenshots/BGC_cascaded.png)

## Conclusion
Thus, the output waveforms obtained match perfectly with the output waveforms observed in the literature survey, for a similar set of inputs. Hence, our required design for the 3-bit binary to grey code converter the receives three binary inputs and provides the 3-bit grey code output correctly corresponding to the truth table, has been implemented and verified using Synopsys Custom Compiler on 28nm CMOS technology. As per design requirements, the 3-bit binary to grey code converter can be cascaded to convert a binary number with more bits. The designed circuit is purely combinational, and hence independent of any clock signal.

## Acknowledgement
1. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
2. Chinmay panda, IIT Hyderabad
3. Sameer Durgoji, NIT Karnataka
4. Synopsys Team/Company
5. https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/

## References
* J.Wang, S.Fang and W.Feng, "New EfEcient Designs for XOR and XNOR Functions on the Transistor Level," IEEE Journal on Solid-State Circuits, vol. 29, No.7, pp. 780--786, July 1994.
* Hanho Lee and G. E. Sobelman, "New low-voltage circuits for XOR and XNOR," Proceedings IEEE SOUTHEASTCON '97. 'Engineering the New Century', 1997, pp. 225-229, doi: 10.1109/SECON.1997.598676.
* L. Li and J. Hu, "A transmission gate flip-flop based on dual-threshold CMOS techniques," 2009 52nd IEEE International Midwest Symposium on Circuits and Systems, 2009, pp. 539-542, doi: 10.1109/MWSCAS.2009.5236037.



