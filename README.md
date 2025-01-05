# **Digital VLSI SoC Design and Planning Program**
## _OVERVIEW_
This is a two-week long workshop conducted by VSD in collaboration with NASSCOM. This course provides a comprehensive outlook of the RTL2GDSII flow, making us understand how to convert high-level designs into a format ready for silicon fabrication. This repository demonstrates my learnings from the same. 
## _Tools Used_
1. **_Sky130 PDK_**: The SKY130 is a mature 180nm-130nm hybrid technology originally developed internally by Cypress Semiconductor before being spun out into SkyWater Technology and made accessible to general industry. SkyWater and Google’s collaboration is now making this technology accessible to everyone!
## _Table of Content_
* [Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK](#Day-1---Inception-of-open---source-EDA-,-OpenLANE-and-Sky130-PDK)
* [Day 2 - Good floorplan vs bad floorplan and introduction to library cells](#Day-2---Good-floorplan-vs-bad-floorplan-and-introduction-to-library-cells)
* [Day 3 - Design library cell using Magic Layout and ngspice characterization](#Day-3---Design-library-cell-using-Magic-Layout-and-ngspice-characterization)
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
## OBJECTIVES:
**1. Run Floorplan using OpenLANE:**

![Screenshot (593)](https://github.com/user-attachments/assets/bc9ae883-b398-42b3-9773-8ac2ede57b11)
![Screenshot (594)](https://github.com/user-attachments/assets/38bdc5c4-ba50-412a-ab15-ded9a2e0208c)
![Screenshot (595)](https://github.com/user-attachments/assets/2fefac27-d65c-4d35-832f-0f7ca04347a8)

**Once the Floorplanning has been executed, we can view the results in the 'Floorplan' directory and analyse factors like the 'Die Area':**

![Screenshot (596)](https://github.com/user-attachments/assets/647cac8f-10c5-444f-92d9-222baebdd84b)

**2. To see the actual layout after Floorplan, we can use the MAGIC Tool:**

_We can use the following command to open the MAGIC Tool:-_
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/02-01_11-58/results/floorplan/
```
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

```

![Screenshot (597)](https://github.com/user-attachments/assets/8384dc26-e72a-41d7-a0d4-2c17abeab2de)

**3. To run placement def in the MAGIC Tool:**

_To do so, we can use the following command in OpenLANE:-_
```
run_placement
```

![Screenshot (598)](https://github.com/user-attachments/assets/56a45752-0b1d-4f39-90b6-d5d20961060b)


_After this, go to the directory:_
```
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/02-01_11-58/results/placement/
```
_And then, enter the command to launch the placement def file in MAGIC Tool:_
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech \
lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![Screenshot (599)](https://github.com/user-attachments/assets/f1554273-5d99-4f99-9fcd-f08fab418b76)

_Now, if we zoom in, we can see the placement of the standard cells:_

![Screenshot (601)](https://github.com/user-attachments/assets/718c8fd0-764a-4c20-949a-58ba355a7131)

## Day 3 - Design library cell using Magic Layout and ngspice characterization
### Overview
In this section, we have to design a CMOS Invertor layout using the MAGIC tool and then characterize it with the Ngspice tool. For this, we will be cloning the necessary files, and then SPICE extractions of them, and then post layout SPICE simulations. 

### STEPS:
1. Clone the repository containing the inverter layout provided by Nickson Jose Sir by following the below command:
   ```
   cd Desktop/work/tools/openlane_working_dir/openlane
   git clone https://github.com/nickson-jose/vsdstdcelldesign.git
   ```
   ![Screenshot (602)](https://github.com/user-attachments/assets/9da49250-46cf-4478-b6bb-262fd85b14a1)

2. Copy **_'sky130A.tech'_** file from **_'libs.tech/magic'_** to **_'vsdstdcelldesign.git'_**
   ``` 
   cd vsdstdcelldesign
   cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
   ```
   ![Screenshot (603)](https://github.com/user-attachments/assets/ffcc83a9-ca52-4333-abae-f85963fe8091)

3. Open the inverter layout in MAGIC:
   ```
   magic -T sky130A.tech sky130_inv.mag &
   ```
   ![Screenshot (604)](https://github.com/user-attachments/assets/79340928-5554-4247-a6df-fb86a69fd8ac)

3. Identify the NMOS & PMOS region from the layout given:
   * For NMOS: Place the cursor on the intersection region of polysilicon and n-diffusion, and press _'s'_. Then go to the _'tkcon'_ window and type _'what'_.

   ![Screenshot (605)](https://github.com/user-attachments/assets/86c5444a-b408-4562-978b-375ba2d14f1a)
   *  For PMOS: Place the cursor on the intersection region of polysilicon and p-diffusion, and press _'s'_. Then go to the _'tkcon'_ window and type _'what'_.

   ![Screenshot (606)](https://github.com/user-attachments/assets/f636191c-6665-466b-ad14-058b971fe3fa)

4. Extract the layout on SPICE:
   Command used in _'tkcon'_ -
   ```
   extract all
   ext2spice cthresh 0 rthresh 0
   ext2spice
   ```
   ![Screenshot (607)](https://github.com/user-attachments/assets/32b6ea2a-d32d-428a-a469-342c0cdf3c62)
   ![Screenshot (608)](https://github.com/user-attachments/assets/c4b3f3e6-c5a4-4f87-b9d1-9d74b8fa18b1)
      
5. Run NGSPICE:
   * Write the necessary code:
     ![Screenshot (613)](https://github.com/user-attachments/assets/cbf603cf-339e-4ef0-8638-7ecbf92a7a1a)

   * Run ngpice using the command:
     ```
     ngspice sky130_inv.spice
     ```
     ![Screenshot (611)](https://github.com/user-attachments/assets/3dab695a-bc96-40d8-8c9d-81674bf4033e)

6. Plot the result:
   
   Command used - 
   ```
   plot y vs time a
   ```
   ![Screenshot (614)](https://github.com/user-attachments/assets/db1bf4f3-8678-4320-8516-d23d933730bc)

   Now, we can make changes in the load capacitance to smoothen the spikes in the plot:
   ![Screenshot (616)](https://github.com/user-attachments/assets/b6172d06-b4ed-46c0-89b9-70590f1ffeeb)


8. Characterization of Inverter using sky130 model files:
   - Parameters to characterize:
     - Rise Time: The time taken for the output waveform to transition from 20% to 80% of its maximum value.
     - Fall Time: The time taken for the output waveform to transition from 80% to 20% of its maximum value.
     - Propagation Delay: The time taken for a 50% transition at the output (0 to 1) corresponding to a 50% transition at the input (1 to 0).
     - Cell Fall Delay: The time taken for a 50% transition at the output (1 to 0) corresponding to a 50% transition at the input (0 to 1).
9. To find errors in the DRC section of the magic tech file for the sky130 process and fix them:
    * Download and unzip the DRC Test Files by using the given command step-by-step:
      ```
      cd
      wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
      tar xfz drc_tests.tgz
      cd drc_tests
      ls -al
      ```
      ![Screenshot (620)](https://github.com/user-attachments/assets/bec33246-be6c-4740-aab6-43dcb357d459)

    * View .magicrc file:
      ```
      vi .magicrc
      ```
      ![Screenshot (621)](https://github.com/user-attachments/assets/d9540470-7002-4f17-bd4f-4c8544ce8cff)

    * Open MAGIC Tool by using the command as under. This has better graphics than the traditional one.
      ```
      magic -d XR &
      ```
      ![Screenshot (622)](https://github.com/user-attachments/assets/7b2c9e32-3b7b-42da-9964-7ce623397ec2)
      ![Screenshot (624)](https://github.com/user-attachments/assets/4c27334a-4f94-4fd5-bccd-2ef54cea7fe9)


    * Open the periphery rules of metal 3:
      ```
       https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html#m3
      ```
      ![Screenshot (623)](https://github.com/user-attachments/assets/9827d0ed-a55e-47a4-bfbe-2179dd62321c)

    * Use ``` drc why ``` in the console to see which rule got violated:
      
      ![Screenshot (625)](https://github.com/user-attachments/assets/cb68da88-6435-4747-974e-74a2ddcf16b4)
      ![Screenshot (627)](https://github.com/user-attachments/assets/06962729-c793-42d4-a704-8d716572762a)

    * ```Load poly``` to see the errors:
      ![Screenshot (629)](https://github.com/user-attachments/assets/586a775e-645e-4b5e-a389-bfd779148767)

    * Search for poly.9 and make the necessary changes:
      ![Screenshot (630)](https://github.com/user-attachments/assets/a95a54ce-1b7d-4b4f-a71d-ccc5eea43bb3)
      ![Screenshot (631)](https://github.com/user-attachments/assets/6c718802-a260-46f8-86f6-5c2e9796c60f)
      ![Screenshot (632)](https://github.com/user-attachments/assets/51a25fd8-baf4-4935-abb0-22a8e27cf605)

    * Now we don't need to restart MAGIC to check this change. We can just write the given command on the command line in MAGIC Tool:
      ```
      tech load sky130A.tech
      ```
      ```
      drc check
      ```
      ![Screenshot (633)](https://github.com/user-attachments/assets/17ff8ccb-f37f-45d2-8403-982ad01c3bc1)
      ![Screenshot (634)](https://github.com/user-attachments/assets/cbbe2cbe-6644-44d5-8f6a-752eb40ae5b0)

    * Exercise to implement poly resistor spacing to diff and tap:
       



  
  


        
      
 
  
  

      
    
    
   
   
   



   

   



   



















 
  

   






