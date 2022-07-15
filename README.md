#  PHYSICAL DESIGN WORK - OPENLANE EDA - VSDIAT     
![image](https://user-images.githubusercontent.com/107180943/175544822-8728494a-3364-4668-891c-bb449899e3cc.png)

## Synthesis
Design setup 


![image](https://user-images.githubusercontent.com/107180943/175610575-d02d40b7-854b-4ded-94c7-17fcb7b97222.png)

Prepare the design picorv32a 

![image](https://user-images.githubusercontent.com/107180943/175610918-d8475bc5-e792-4b92-899b-94f4d41927ee.png)

Running a synthesis step

![image](https://user-images.githubusercontent.com/107180943/175613031-a1c0d87b-0da9-4774-9226-813a4a21e78f.png)

synthesis.tcl for setting up design variables (system default)

Next priority is config.tcl 

![image](https://user-images.githubusercontent.com/107180943/175616210-1aaa1495-aa3f-4d04-a9ed-fabdd575e2ba.png)

High priority we have design specific config file 

![image](https://user-images.githubusercontent.com/107180943/175616266-fc467235-b133-47cc-a6a5-a3cf1c8623de.png)




![image](https://user-images.githubusercontent.com/107180943/175615721-66788d81-d219-45c9-acb1-43349f0b471c.png)


Synthesis got succesful 

![image](https://user-images.githubusercontent.com/107180943/175612443-855252fe-b7b8-437d-b5b2-0291d53c269d.png)

Synthesis cell wise statistics

 - Dff count is 1613 

![image](https://user-images.githubusercontent.com/107180943/175612506-c1e232df-0080-4952-a703-32e69135ddcf.png)


Synthesis reports 

- synthesis step will run both yosys and openSTA tools underhood , we will do synthesis and also perform initial Static timing analysis 


![image](https://user-images.githubusercontent.com/107180943/175614077-b1d020e2-953a-461e-b5bf-914df8405459.png)

Initial Static timing analysis report 

![image](https://user-images.githubusercontent.com/107180943/175614737-908ebabc-dd18-4951-bd7f-a6ccd8021bfa.png)



## FloorPlan

Floor plan step 

Running floorlan

![image](https://user-images.githubusercontent.com/107180943/175617038-9ec648f1-d095-45bd-bc26-2b2fff34f02b.png)


Floorplan outputs 

After floor plan , floor def will be created 

![image](https://user-images.githubusercontent.com/107180943/175617216-71ee6748-643d-499a-b4e4-e975b7690b25.png)


Opening the Floor plan DEF using magic 

![image](https://user-images.githubusercontent.com/107180943/175625932-8b01b54c-d865-4726-b9d0-8c135583e73c.png)

Floor def in magic layout 

![image](https://user-images.githubusercontent.com/107180943/175629324-a6fcf09f-1683-4871-8cec-640d18da5f54.png)

![image](https://user-images.githubusercontent.com/107180943/175633586-0e09e25e-6b29-46e7-ac20-6217c61a05d5.png)


## Placement 


Steps for placement 

![image](https://user-images.githubusercontent.com/107180943/175645042-86618cd1-7a8a-4250-bee1-12dd36d3ee2a.png)


![image](https://user-images.githubusercontent.com/107180943/177947685-fefd1d90-9142-44ec-8ae9-b70a5b566486.png)





## STANDARD CELL CHARACTERIZATION STEPS 
git clone vsdstdcelldesign 
![image](https://user-images.githubusercontent.com/107180943/175533412-40f87196-19ff-4918-bcca-e82ef5893b31.png)
![image](https://user-images.githubusercontent.com/107180943/175537288-d3017f7c-51b3-46b4-907d-63b96725ffee.png)

Inverter layout 
![image](https://user-images.githubusercontent.com/107180943/175537605-db6a446e-03ad-4e1e-ad29-c5607a2c00e0.png)


![image](https://user-images.githubusercontent.com/107180943/175572447-62508020-cc35-474e-b378-a29353d243f2.png)


![image](https://user-images.githubusercontent.com/107180943/175572510-a190689b-93c3-4aab-9adb-14da1f2db24e.png)

![image](https://user-images.githubusercontent.com/107180943/175572532-e7a19f82-20ab-41f8-882f-ff58dccb7ec0.png)



![image](https://user-images.githubusercontent.com/107180943/175586044-e4d82829-deeb-4360-96b4-e75b52da7928.png)


![image](https://user-images.githubusercontent.com/107180943/175586790-00c3ca67-65a1-4232-ba1f-805f72045242.png)



![image](https://user-images.githubusercontent.com/107180943/175592775-46ecbdff-94a4-4cb2-b146-0771c42fb84c.png)

### Write out std cell  LEF from magic inv layout 

Save the std inv layout 
![image](https://user-images.githubusercontent.com/107180943/177989689-b70df22a-73fd-447a-b2db-9fd3ef2f7217.png)


Open the new inv layout in magic 
![image](https://user-images.githubusercontent.com/107180943/177990589-11f964d8-e9d9-42e2-a1bf-28a6341cda28.png)

writing the cell LEF from magic layout 
![image](https://user-images.githubusercontent.com/107180943/177991101-165169ae-10d6-4652-91ba-3e5a54b09dd9.png)



Config file for addig New lef 
![image](https://user-images.githubusercontent.com/107180943/178006569-45665110-bffe-4b14-a0c6-f9dc2ab61464.png)


![image](https://user-images.githubusercontent.com/107180943/178014099-41108be6-538e-4468-b878-4a6b06de91df.png)

Include below commands to new lefs 

 - set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
 
 - add_lefs -src $lefs

New std cell Inv count in new synthesis output 
![image](https://user-images.githubusercontent.com/107180943/178015623-064e5158-2f26-4bcb-91e3-555e4aa8f344.png)

Before setting up variable 

Area 

![image](https://user-images.githubusercontent.com/107180943/178029355-84c1a875-31f9-4d8d-acc7-c456d74b2ead.png)

Slacks 

![image](https://user-images.githubusercontent.com/107180943/178029393-8b53e51e-f3a3-4860-ab31-7424d47f0290.png)

       
Setting variable to fix slack 

![image](https://user-images.githubusercontent.com/107180943/178029102-a1bbb121-e477-4534-8854-3a94792a56f6.png)


After setting of variables to fix the slacks issue (synth_strategy and sizing variables ) 

Area and Slacks 

![image](https://user-images.githubusercontent.com/107180943/178029659-224f8c70-0b1f-43f9-86ec-04c083092f51.png)


![image](https://user-images.githubusercontent.com/107180943/179167156-b04515cb-93ee-487a-8fbe-71389379a1b8.png)

init_floorplan
place_io
global_placement_or
detailed_placement
tap_decap_or
detailed_placement

![image](https://user-images.githubusercontent.com/107180943/179169127-7a468d7d-556a-49b7-aea6-7da778c70c49.png)





