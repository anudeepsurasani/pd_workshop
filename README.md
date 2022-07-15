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


Placement def 

![image](https://user-images.githubusercontent.com/107180943/179176440-6cdd6967-02ae-4182-9e2a-b55f4adc8313.png)

![image](https://user-images.githubusercontent.com/107180943/179175866-13062f49-560c-4bb4-abe7-abd557242830.png)

![image](https://user-images.githubusercontent.com/107180943/179176109-10517740-ecec-49b5-9a5a-1c6550605599.png)

## CLOCK TREE SYNTHESIS 

pre_sta.conf

![image](https://user-images.githubusercontent.com/107180943/179176884-2ef4e203-09be-40e8-946a-ea40126705c8.png)


my_base.sdc

![image](https://user-images.githubusercontent.com/107180943/179177119-ada557b8-10b4-4011-a567-8a3db8e81fbf.png)


sta pre_sta.conf

![image](https://user-images.githubusercontent.com/107180943/179178174-8fb03320-96c7-44ff-98dc-624aa19c0340.png)



![image](https://user-images.githubusercontent.com/107180943/179178746-ba8af38b-b943-48f9-9b9e-a7d77b39e4ae.png)


![image](https://user-images.githubusercontent.com/107180943/179179096-4a7f6ce8-5867-4321-9d67-c6e0a5a5e7f0.png)

![image](https://user-images.githubusercontent.com/107180943/179179287-d7bb9fc3-fedb-4759-9cb8-64bc2820e6a0.png)


After setting max fanout to 4 

![image](https://user-images.githubusercontent.com/107180943/179181665-2a07b195-771b-4858-b9db-a16e7e762d9e.png)

run_syntheseis and then do sta analysis using "sta pre_sta.conf" using the latest synthesis ourput which is given in pre_sta.conf file 

![image](https://user-images.githubusercontent.com/107180943/179181736-a0dd2df9-9640-4b19-b869-efc065e118b1.png)

![image](https://user-images.githubusercontent.com/107180943/179197318-b54d14f9-76ff-4c93-b9fb-491307a22647.png)


![image](https://user-images.githubusercontent.com/107180943/179204435-b78449f9-a376-4ce5-a066-8b09085b8fd2.png)

![image](https://user-images.githubusercontent.com/107180943/179204584-a7d8f7a4-b948-4b30-b3f6-ad34cdd77fac.png)


![image](https://user-images.githubusercontent.com/107180943/179204233-951d8ea5-e94b-4527-bdc7-e638aa459131.png)


Buffer upsizing to 4 , improve the slack 

![image](https://user-images.githubusercontent.com/107180943/179205545-e11629ca-e79e-4764-b224-4c4d08de96c7.png)

Write verilog to following , After your timing voilation got removed 

![image](https://user-images.githubusercontent.com/107180943/179209125-2091648e-a1e2-48f1-bc4c-b60d7ce1ae7d.png)


Upsizing to buf 4 , verified in new verilog netlist 

![image](https://user-images.githubusercontent.com/107180943/179208851-8751dcd1-8a09-4b0d-9c2b-c8f4fe96ba0c.png)

Do all these steps again before running the CTS 
init_floorplan

place_io

global_placement_or

detailed_placement

tap_decap_or

detailed_placement

Now run the clock tree synthesis : run_cts 

![image](https://user-images.githubusercontent.com/107180943/179210815-2f197f14-5490-44fd-92d7-47a658a1dc55.png)


After CTS , new sythesis output got added sythesis folder 

![image](https://user-images.githubusercontent.com/107180943/179223878-9afe6b13-abdc-44d6-b238-437ba66bce16.png)


![image](https://user-images.githubusercontent.com/107180943/179257432-94b5e257-5cc2-4e77-8dd0-01ca49182948.png)


![image](https://user-images.githubusercontent.com/107180943/179258471-24bfab5a-e6ce-4fe9-afce-dbe2c903856f.png)


![image](https://user-images.githubusercontent.com/107180943/179275580-9802ea19-78b3-43d1-83ed-b1a16d4514b7.png)


![image](https://user-images.githubusercontent.com/107180943/179275708-b783a5c8-b101-4aa1-941c-08ea30e4b4fb.png)


Actaully we did for min and max corner which is wrong , we need to do for the tyical corner . we exit from openroad not from openlane 

![image](https://user-images.githubusercontent.com/107180943/179277024-5908cc65-fe81-4e5f-ac85-2a22045e13f5.png)

![image](https://user-images.githubusercontent.com/107180943/179277675-5a0d78c9-fb9d-4033-a676-b04b1f1217af.png)

![image](https://user-images.githubusercontent.com/107180943/179277751-bf73ef31-0348-4d68-ae3d-1303f077cc2b.png)

![image](https://user-images.githubusercontent.com/107180943/179277917-dae8e8fa-7e93-4453-adf3-9c1d1c8b5bf6.png)

![image](https://user-images.githubusercontent.com/107180943/179278174-2e55d8a9-9721-4b22-b3dc-250d8b9cb6b6.png)


 Multi-corner analysis currently not supported by triton CTS 


![image](https://user-images.githubusercontent.com/107180943/179281966-c8ced9f0-4864-4bc1-b3e5-438f87246219.png)

![image](https://user-images.githubusercontent.com/107180943/179286231-597dc5fd-b02b-4c77-9815-a4a246c3aee3.png)


![image](https://user-images.githubusercontent.com/107180943/179286377-44fccf4f-39c3-4920-b044-5a3b09b23515.png)


![image](https://user-images.githubusercontent.com/107180943/179286433-d29b8130-4f34-4db5-baf0-ad2108565c85.png)

Clock skew 

![image](https://user-images.githubusercontent.com/107180943/179286747-6d641057-3745-4059-9919-1e2e2edf018b.png)

![image](https://user-images.githubusercontent.com/107180943/179287807-21848d64-0f6e-45c8-b888-bf63e1a61e75.png)


## POWER DELIVERY NETWORK 

Power delivery network 

gen_pdn

![image](https://user-images.githubusercontent.com/107180943/179288578-52a633f6-1097-4aad-9062-9cf3b50693fb.png)

![image](https://user-images.githubusercontent.com/107180943/179288658-ae5a6e74-e2eb-40e7-9547-fcde57d154ac.png)

![image](https://user-images.githubusercontent.com/107180943/179289171-a5f386c0-c63f-4d56-bd8a-c41263676ee8.png)

![image](https://user-images.githubusercontent.com/107180943/179288721-d527b83f-2679-4c04-a74e-26f6ef50e792.png)

![image](https://user-images.githubusercontent.com/107180943/179290461-e14214dd-8add-4138-8c3b-82c71b53a7c6.png)


## ROUTING 

run routing

fast routing :

detailed routing : 
run_routing

Routing Failed with too high congestion 

![image](https://user-images.githubusercontent.com/107180943/179297048-6f78eb49-281f-4424-81d0-32ef82eeb6c5.png)


Post routing STA analysis 


Standalone SPEF extractor 


![image](https://user-images.githubusercontent.com/107180943/179299789-203b9af4-90f8-49d8-8a3f-f43f19aaadfa.png)





