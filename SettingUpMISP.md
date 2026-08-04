
layout: default
---



# Building a Microsoft Sentinel Workspace and Creating a VM - Introduction

In this project I set up MISP Threat Intelligence

## Details
First I am going to set up a new Ubuntu Server VM for MISP
I create a new Resource Group named "RileyMISP_Group"
I name the machine RileyMISP


after creating the VM I am going to install Docker enigne


After installing Docker I make sure that it was successful by running the hello-world image

Now I go on to install MISP with the git clone command

I then followed the Getting Started instructions from the misp-docker github 
I copied template.env from the MISP-Docker dir to .env. I then added the public IP address for RileyMISP to BASE_URL by using Nano to edit .env

I ran docker compose pull to build the image and then docker compose up. 

I then added an inbound port rule under the RileyMISP network settings to open up port 443 to allow the connection to be started from anywhere. 

I was then able to log into MISP threat sharing by visiting the public IP address for the RileyMISP VM that I entered into .env earlier. For this first login I used the default credentials provided in the Github for misp-docker 

I immediately changed the password as this is a public facing machine and the default password is admin

I then went back to the MISP site to find and download their default feed JSON

After this I went back to the MISP threat sharing and added this default feed to Feeds under Sync Actions by using the Import Feeds from JSON option. Once all the Feeds were added I had to select all of them and enable them. 

After enabling all the feeds I clicked on "Fetch and store all feed data" and now the home page reflects all of these feeds

Now in order to pull these threat indicators into Sentinel I went to the data connectors section of my workspace and went to the content hub to download the data connector MISP2Sentinel

Now following the instructions in the github page for MISP2Sentinel I created an azure application and named it RileyMISPSentinel

Then I went to my log analytics workspace and added RileyMISPSentinel as a Microsoft Sentinel Contributor

Then I created an auth key in MISP

Then I created a function app in azure to avoid having to create one on the RileyMISP VM

I then downloaded the repository from the Misp2Sentinel Github and opened that in VS code

I right clicked on the AzureFunction folder and clicked deploy to fuinction app

I waited for the this process to finish and went back to Azure to confirm that this was successful

I then went into the environment variables under settings for this function app and began to add a few variables

I added tenant_id, workspace_id, and client_id and I copied the respective values from RileyMISP2Sentinel in
Then I added mispkey and copied the auth key I created earlier on in 
Then I created client_secret and copied that in 
I added mispurl and entered the url for my instance of MISP 
I added timerTriggerSchedule and entered  0* /2 * * * to have it run every two hours

After Adding all of these variables tested the function app to make sure that it would run 
<img width="2297" height="1203" alt="image" src="https://github.com/user-attachments/assets/8a7cc8b1-294c-496d-a578-a11618e84499" />


//Add the process of creating a key vault and remove the unused variables



## <a href="">View the page on Github </a><br/> 

## <a href="https://rileythomas138.github.io/">Home</a><br/>
