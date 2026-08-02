---
layout: default
---



# Introduction

In this project I set up an Azure portal, set up and configure a Windows 11 VM through Azure, set up log analytics in Sentinel, and create an alert for sign ins on the VM I created in this project. 

## Header 2
This is page you are greeted with when you first create an Azure portal
![Azure Portal Created](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Azure%20Portal%20Created.png)

To get started with creating a VM I am going to be clicking on "Create a resource' which brings you to this screen
![Create Resource](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Create%20Resources.png)

I went through and configured a Windows 11 pro machine naming it "RileyVM" and intentionally left port 3389 open to collect security events
When creating this VM I needed to create a resource group to add this VM to, which I named "RileyGroup". 
![My first VM](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/My%20First%20VM%20.jpg)
![port 3389](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/My%20First%20VM%20.jpg3)

While I waited for this VM to finish setting up I went ahead and created the sentinel workspace for collecting log analytics for this VM and in creating this VM I put I added it to the "RileyGroup" resource group. I also created this workspace in the same region that I created my VM in to minimize lag.
![WorkSpaceCreated](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Sentinel%20Workspace.png)

With having created both the VM and the workspace the two need a way to communicate which led me to set up a data connector. 
![DataConnectorScreen](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Creating%20a%20data%20connector.png)
![DataConnectorImage](https://github.com/RileyThomas138/RileyThomas138.github.io/blob/main/Screeenshots%20for%20VM%20and%20Sentinel/Data%20Connector%20Image.png)


## <a href="https://rileythomas138.github.io/">Home</a><br/>
