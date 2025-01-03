# Digital VLSI SoC Design and Planning Program
## Overview
This is a two-week long workshop conducted by VSD in collaboration with NASSCOM. This course provides a comprehensive outlook of the RTL2GDSII flow, making us understand how to convert high-level designs into a format ready for silicon fabrication. This repository demonstrates my learnings and work regarding the same. 
## Tools Used
1. **_Sky130 PDK_**: The SKY130 is a mature 180nm-130nm hybrid technology originally developed internally by Cypress Semiconductor before being spun out into SkyWater Technology and made accessible to general industry. SkyWater and Google’s collaboration is now making this technology accessible to everyone!
## Table of Content
* [Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK](#Day-1---Inception-of-open---source-EDA-,-OpenLANE-and-Sky130-PDK)
* [Day 2 - Good floorplan vs bad floorplan and introduction to library cells](#Day-2---Good-floorplan-vs-bad-floorplan-and-introduction-to-library-cells)
## Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
### OBJECTIVES:
**1. To start OpenLANE in Interactive Mode:**
   
   ![OpenLANE in Interactive mode](https://github.com/user-attachments/assets/42757203-6ae1-4684-86ed-9a4f344b5a19)
**2. To Run Synthesis:**
   
   ![Screenshot (588)](https://github.com/user-attachments/assets/d3cc703d-61c0-4e8a-a1d2-ac53e8d46fe4)
**3. To Calculate the Flop Ratio:**
   
   $$
   Flop \ Ratio = \frac{No. \ of \ D \ Flip-Flops}{Total \ no. \ of \ cells}=\frac{1613}{14876}=0.108429
   $$
 
   ![Screenshot (589)](https://github.com/user-attachments/assets/337462f1-7d34-4da7-8288-de02d24b6a15)

## Day 2 - Good floorplan vs bad floorplan and introduction to library cells
## Chip Floor planning considerations
* ### Core: 
  A 'core' is the section of the chip where the fundamental design of the logic is placed.
* ### Die:
  A 'die', which consists of core, is small semiconductor material speciman on which the fundamental circuit is fabricated. 
* ### Utilisation factor: 
$$
Utilization \ Factor = \frac{Area \ occupied \ by \ netlist}{Total \ area \ of \ the \ core}
$$
* ### Aspect Ratio: 
$$
Aspect \ Ratio = \frac{Height \ of \ the \ core}{Width \ of \ the \ core}
$$
## OBJECTIVES
**1. Run Floorplan using OpenLANE:**

![Screenshot (593)](https://github.com/user-attachments/assets/bc9ae883-b398-42b3-9773-8ac2ede57b11)
![Screenshot (594)](https://github.com/user-attachments/assets/38bdc5c4-ba50-412a-ab15-ded9a2e0208c)
![Screenshot (595)](https://github.com/user-attachments/assets/2fefac27-d65c-4d35-832f-0f7ca04347a8)

**Once the Floorplanning has been executed, we can view the results in the 'Floorplan' directory and analyse factors like the 'Die Area':**

![Screenshot (596)](https://github.com/user-attachments/assets/647cac8f-10c5-444f-92d9-222baebdd84b)

**2. To see the actual layout after Floorplan, we can use use the MAGIC Tool:**

We can use the command:-
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/02-01_11-58/results/floorplan/
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

```

![Screenshot (597)](https://github.com/user-attachments/assets/8384dc26-e72a-41d7-a0d4-2c17abeab2de)















 
  

   






