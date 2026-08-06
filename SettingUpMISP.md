
layout: default
---



# Building a Microsoft Sentinel Workspace and Creating a VM - Introduction

In this project I set up MISP Threat Intelligence

## Details
First I am going to set up a new Ubuntu Server VM for MISP
I create a new Resource Group named "RileyMISP_Group"
I name the machine RileyMISP
<img width="1011" height="662" alt="Screenshot 2026-08-02 024625" src="https://github.com/user-attachments/assets/8cf79969-3f70-4e30-82db-5dd32c1fddd7" />
<br/> 

after creating the VM I am going to install Docker enigne
<img width="1698" height="1383" alt="Screenshot 2026-08-02 031042" src="https://github.com/user-attachments/assets/87772df5-14f4-4f45-956e-c8f46265cdf4" />
<br/> 
After installing Docker I make sure that it was successful by running the hello-world image
<img width="1426" height="687" alt="Screenshot 2026-08-02 031218" src="https://github.com/user-attachments/assets/1adff2a8-3a30-4171-95a8-9c683022651a" />
<br/> 
Now I go on to install MISP with the git clone command
<img width="1120" height="199" alt="Screenshot 2026-08-02 222108" src="https://github.com/user-attachments/assets/f10c5c40-0a81-4ccf-966c-e18b88af4fdf" />
<br/> 

I then followed the Getting Started instructions from the misp-docker github 
I copied template.env from the MISP-Docker dir to .env. I then added the public IP address for RileyMISP to BASE_URL by using Nano to edit .env
<img width="1240" height="636" alt="Public IP to Env" src="https://github.com/user-attachments/assets/935b7090-413c-4415-96b8-4382bf576470" />
<br/> 

I ran docker compose pull to build the image and then docker compose up. 
<img width="1244" height="621" alt="Screenshot 2026-08-02 223637" src="https://github.com/user-attachments/assets/8344129b-d2b7-4753-8929-95301369a770" />

<img width="1142" height="897" alt="Screenshot 2026-08-02 224714" src="https://github.com/user-attachments/assets/db2350d5-4e4d-4fd6-8577-4be40f022dbe" />
<br/> 

I then added an inbound port rule under the RileyMISP network settings to open up port 443 to allow the connection to be started from anywhere. 
<img width="675" height="676" alt="Screenshot 2026-08-02 224134" src="https://github.com/user-attachments/assets/bc36594e-9587-412e-87e6-22b017a72f98" />
<br/> 

I was then able to log into MISP threat sharing by visiting the public IP address for the RileyMISP VM that I entered into .env earlier. For this first login I used the default credentials provided in the Github for misp-docker 
<img width="1237" height="555" alt="Screenshot 2026-08-02 224810" src="https://github.com/user-attachments/assets/e892823b-2ec7-4ed1-9e04-71e000c3836c" />
<br/> 

I immediately changed the password as this is a public facing machine and the default password is admin
<img width="2544" height="760" alt="Screenshot 2026-08-02 225158" src="https://github.com/user-attachments/assets/88ad2b8c-6ec6-4088-be4f-442d63d56f17" />
<br/> 
I then went back to the MISP site to find and download their default feed JSON
<img width="1245" height="963" alt="Screenshot 2026-08-02 225412" src="https://github.com/user-attachments/assets/b229fd2d-bc9d-4683-a7c9-7f8675e27eac" />

<img width="1243" height="1004" alt="Screenshot 2026-08-02 225422" src="https://github.com/user-attachments/assets/efd7bf26-5ef9-415b-8304-6d88135de634" />
<br/> 

After this I went back to the MISP threat sharing and added this default feed to Feeds under Sync Actions by using the Import Feeds from JSON option. Once all the Feeds were added I had to select all of them and enable them. 
<img width="1225" height="793" alt="Screenshot 2026-08-02 230113" src="https://github.com/user-attachments/assets/c02861dc-3f38-47c2-8443-c57efaa65150" />
<img width="1051" height="359" alt="Screenshot 2026-08-02 235627" src="https://github.com/user-attachments/assets/ae0827b5-eaa9-4b5e-86ca-7706be14e02d" />
<br/> 

After enabling all the feeds I clicked on "Fetch and store all feed data" and now the home page reflects all of these feeds
<img width="2541" height="1104" alt="Screenshot 2026-08-02 233154" src="https://github.com/user-attachments/assets/df0636b9-7a24-4726-b62a-683afdbcec3e" />
<br/> 

Now in order to pull these threat indicators into Sentinel I went to the data connectors section of my workspace and went to the content hub to download the data connector MISP2Sentinel
<img width="1589" height="1121" alt="Screenshot 2026-08-02 233819" src="https://github.com/user-attachments/assets/635d132b-0298-4656-aa4d-29dad8d9b96b" />
<br/> 

Now following the instructions in the github page for MISP2Sentinel I created an azure application and named it RileyMISPSentinel
<img width="1646" height="1199" alt="Screenshot 2026-08-03 215744" src="https://github.com/user-attachments/assets/f6ee6b07-52fa-4739-a07d-c7daa22cb191" />
<br/> 

Then I went to my log analytics workspace and added RileyMISPSentinel as a Microsoft Sentinel Contributor
<img width="1021" height="927" alt="Screenshot 2026-08-02 234620" src="https://github.com/user-attachments/assets/c3842351-7b3b-47c3-8b31-8cc1076c2974" />
<br/> 

Then I created an auth key in MISP
<img width="1051" height="359" alt="Screenshot 2026-08-02 235627" src="https://github.com/user-attachments/assets/f49ac7eb-290e-4a66-b88d-a518c2e28460" />
<br/> 
Then I created a function app in azure to avoid having to create one on the RileyMISP VM
<img width="968" height="1093" alt="Screenshot 2026-08-03 000426" src="https://github.com/user-attachments/assets/07a627b3-bc3c-4810-ab64-af76de52db45" />
<br/> 

I then downloaded the repository from the Misp2Sentinel Github and opened that in VS code
<img width="1689" height="896" alt="Screenshot 2026-08-03 222115" src="https://github.com/user-attachments/assets/2170747b-5598-4a97-9010-b6e1017426b8" />
<br/> 

I right clicked on the AzureFunction folder and clicked deploy to fuinction app
<img width="627" height="828" alt="Screenshot 2026-08-03 222744" src="https://github.com/user-attachments/assets/bada7746-25bf-4853-ab70-be656db174f3" />
<img width="1905" height="279" alt="Screenshot 2026-08-03 223105" src="https://github.com/user-attachments/assets/98d6c0fe-6837-4106-871e-a19a858d3ed0" />
<br/> 

I waited for the this process to finish and went back to Azure to confirm that this was successful
<img width="2244" height="1159" alt="Screenshot 2026-08-03 223658" src="https://github.com/user-attachments/assets/14c5df5c-4a41-4889-8e38-bfe67d409110" />
<br/> 
Before continuing on I created a Key Vault to store tenant information and the MISP auth key
<img width="1294" height="583" alt="Screenshot 2026-08-05 222616" src="https://github.com/user-attachments/assets/59b0d99a-46a3-49bd-bb47-c36538fa3151" />
<br/> 
I needed to make myself a key vault admin and I needed to make the function app a Key Vault Secrets User to allow it to grab the tenants and mispkey variables needed
<img width="1277" height="739" alt="Screenshot 2026-08-05 222644" src="https://github.com/user-attachments/assets/683121b8-abdc-4b38-9df8-ee802d5f569f" />
<br/> 
I then created two secrets, tenants and mispkey
<img width="1296" height="533" alt="Screenshot 2026-08-05 222658" src="https://github.com/user-attachments/assets/83284bb0-40c0-4c35-9754-31afb31033e0" />
<br/> 
tenants had the following value
<img width="511" height="155" alt="image" src="https://github.com/user-attachments/assets/f3d42c42-da98-4659-b060-60a615e8ab35" />
<br/> 

I then went into the environment variables under settings for this function app and began to add a few variables

I created the teneants variable and pointed it to the tenants secret in the key vault
Then I added mispkey and pointed it to the tenants secret in the key vault
Then I added mispurl and entered the url for my instance of MISP 
Then I added timerTriggerSchedule and entered  "0* /2 * * *" to have it run every two hours
Finally I added local_mode and gave it the value "true"

<img width="1899" height="1045" alt="image" src="https://github.com/user-attachments/assets/665fefed-d36c-435e-8742-acc1ca9da737" />
<br/> 

After Adding all of these variables tested the function app to make sure that it would run 
<img width="2297" height="1203" alt="Screenshot 2026-08-04 001335" src="https://github.com/user-attachments/assets/b5951a6a-5186-4f31-90d9-45d84e6c45d5" />
<br/> 

This confirmed that the function app could run, however when running it would pull in the first page of 100 indicators and freeze. This led me to believe that my RileyMISPVM was struggling to ingest this many indicators at a time so I searched the Python code for the function that was setting the MISP events on a page to 100 and I lowered it to 25 with the hope that this would solve my issue.
<img width="1520" height="73" alt="Screenshot 2026-08-05 222318" src="https://github.com/user-attachments/assets/f9b30c83-bfc5-4c10-856e-001618187025" />
<br/> 
<img width="1719" height="521" alt="Screenshot 2026-08-05 011122" src="https://github.com/user-attachments/assets/d9f849db-0fa8-4608-9254-23e988183f13" />
<br/> 
This was the result I got when running the function app again
<img width="2486" height="1176" alt="Screenshot 2026-08-05 010028" src="https://github.com/user-attachments/assets/b719ad2e-dac9-4892-b0bd-eff5d7ae8a19" />
<br/> 
And I could see that Sentinel was now pulling in ThreatIndicator logs which confirmed this was succesful
<img width="2457" height="1139" alt="Screenshot 2026-08-05 005810" src="https://github.com/user-attachments/assets/90628d2e-2e25-4579-89f4-3fe9ce6e1d8b" />


## <a href="">View the page on Github </a><br/> 

## <a href="https://rileythomas138.github.io/">Home</a><br/>
