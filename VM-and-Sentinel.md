---
layout: default
---



# Introduction

In this project I set up an Azure portal, set up and configure a Windows 11 VM through Azure, set up a Sentinel workspace, and create an alert for sign successful sign ins to the VM. 

## Details
This is page you are greeted with when you first create an Azure portal
![Azure Portal Created](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Azure%20Portal%20Created.png)
<br/> 
To get started with creating a VM I am going to be clicking on "Create a resource' which brings you to this screen
![Create Resource](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Create%20Resources.png)
<br/> 
I went through and configured a Windows 11 pro machine naming it "RileyVM" and intentionally left port 3389 open to collect security events
When creating this VM I needed to create a resource group to add this VM to, which I named "RileyGroup". 
![My first VM](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/My%20First%20VM%20.jpg)
![port 3389](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/My%20First%20VM%20.jpg)
<br/> 
While I waited for this VM to finish setting up I went ahead and created the sentinel workspace for collecting log analytics for this VM and in creating this VM I put I added it to the "RileyGroup" resource group. I also created this workspace in the same region that I created my VM in to minimize lag.
![WorkSpaceCreated](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Sentinel%20Workspace.png)
<br/> 
With having created both the VM and the workspace the two need a way to communicate which led me to set up a data connector. 
![DataConnectorScreen](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Creating%20a%20data%20connector.png)
![DataConnectorImage](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Data%20Connector%20Image.png)
<br/> 
I then went on to write my first rule in KQL to collect logs on successful sign in activity
![FirstQuery](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/My%20first%20KQL%20query.jpg)
<br/> 
I then went on to filter out system account sign in activity to make these logs more meaningful
![KQLTweak](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Tested%20KQL%20Query.jpg)
<br/> 
I then went on to save this query into a Microsoft Sentinel rule that would run every 5 minutes
![CreatingMyFirstRule](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Creating%20My%20First%20Sentinel%20Rule.jpg)
![FullRule](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/First%20Rule%20in%20Defender.png)
<br/> 
Now by going to the Incidents page in Microsoft Defender you can see all the times there was a succesful local login
![Ending](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Succesful%20Sign%20In%20Incidents.png)

##<a href="https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/VM-and-Sentinel.md">View the page on Github </a><br/> 

## <a href="https://rileythomas138.github.io/">Home</a><br/>
