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







 
  

   






