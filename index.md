---
layout: default
---

**Name:** **John Jefferson L. Doyon**

[LinkedIn Profile](https://www.linkedin.com/in/johnjefferson11/).

I like to help companies reduce cybersecurity risks --- Independent Advisor at Microsoft Community



# About

I like to help companies reduce cybersecurity risks. With a background in IT support, I’m a fast learner with strong problem-solving abilities and a focus on effective decision-making. I’m dedicated to applying my skills in cybersecurity to monitor, analyze, and respond to security incidents. My goal is to support organizations in maintaining strong security postures and achieving their security objectives.

## Portfolio projects
**Table of Contents:**

* [Drafting a professional statement](#Drafting-a-professional-statement)
* [Conducting a security audit](#Conducting-a-security-audit)
* [Usage](#usage)
* [Contributing](#contributing)
  * [License](#license)


<h2 id="Drafting-a-professional-statement">Drafting a professional statement</h2>
I like to help companies reduce cybersecurity risks. With a background in IT support, I’m a fast learner with strong problem-solving abilities and a focus on effective decision-making. I’m dedicated to applying my skills in cybersecurity to monitor, analyze, and respond to security incidents. My goal is to support organizations in maintaining strong security postures and achieving their security objectives.


<h2 id="Conducting-a-security-audit">Conducting a security audit



## Building A SIEM Using Microsoft Azure And Deploying Microsoft Sentinel And Crafting Custom Rules

I created my own Security Operations Center (SOC) by deploying my own Security Information and Event Management (SIEM) that monitors and generates alerts for my device. I set up a Threat Intelligence (TI) feed that sends my SIEM information of a Indicator of Compromise (IoC) using Microsoft Azure. 

First I created an Azure account using the free trial and created my first Virtual Machine (VM). After clicking the Virtual Machine icon, I click “Create” and select “Azure virtual machine with preset configuration” and click “Continue”. I created a new resource group and named it JohnnyVM_group it is my container that holds related resources for an Azure solution. My VM name is JohnnyVM and I set the region in (Asia Pacific) East Asia. In the Image section I selected Windows 11 Pro, version 22H2 - x64 Gen2 (free services eligible) then I created an administrator account. In Inbound port rules I intentionally allow RDP (3389) ports to get immediate traffic for a test. Confirmed licensing and click through Disk, Network, Management, Monitoring, Advanced, and Tags, and leave it as default. In Review + create it shows the price and since Microsoft provides 200 usd credit it is essentially free for 1 month while I'm testing the Azure environment, I clicked “Create” and patiently waited for VM to successfully deploy. 

Next, I deployed Microsoft Sentinel, “a scalable, cloud-native security information and event management (SIEM) that delivers an intelligent and comprehensive solution for SIEM and security orchestration, automation, and response (SOAR)”. I search Microsoft Sentinel and click “Create Microsoft Sentinel” then “Create a new workspace”. In the Resource group I selected JohnnyVM_group I created earlier. Under the Instance details, in the Name section I input JohnnyVM-LogAnalytics and set the region to East Asia similar to the region where my VM is deployed to eliminate potential lags. I click “Review + create” and click “Create” and patiently wait for it to successfully deploy to my resource group JohnnyVM_group. 

Once JohnnyVM-LogAnalytics is deployed I click it to highlight and click add “Add” and wait patiently for it to successfully add Microsoft Sentinel to workspace JohnnyVM-LogAnalytics. Then I search for Log Analytics Workspace and open JohnnyVM-LogAnalytics, then I will add the VM I created earlier and its event logs and send it to my Log Analytics Workspace to then going to send it to Microsoft Sentinel. I clicked “Agents” under Settings and checked to verify that there are currently 0 Windows computers connected, meaning that my VM is actively logging events but it is not showing since it wasn't added. To pool those events from the endpoint and put them to Microsoft Sentinel I set up a data connection. I search and open Microsoft Sentinel, expand configuration and click “Data connectors” and click “Content hub” I then search for Azure Monitor Agent, from the result I click “Windows Security Events” and click “Install” and patiently wait for it to successfully install. I then go back to Microsoft Sentinel Data connector and click “Refresh” and verify it Windows Security Events via AMA is added. 

To create Data Collection Rule Association and or simply add an event rule I click on Windows Security Events via AMA to open its properties and click “Open connector page” and click “Create data collection rule” then in the rule name I put “WindowsEventstoSentinel” and click “Next: Resources”. Under Resources I put a check on the box next to Azure subscription 1 and expand it to verify my VM I created earlier is selected and click “Next: Collect”, I selected “All Security Events” and click “Next: Review + Create” and click “Create” and patiently wait for it. I then go back to Microsoft Sentinel Data connectors and click Windows Security Events via AMA and patiently wait for logs to be collected. 

Next I created a rule that checks for successful logins via RDP that is not a system accounts logins. I click “Logs” in the left pane, and clear queries and type:
```python
SecurityEvents where Activity contains "success" and Account !contains "system"
```

After that I set the Time range to “Last 3 days” then click “Run” to check if there is any system showing. Then click “New alert rule” and click “Create Microsoft Sentinel alert”. I name it Successful Local Sign Ins, set the Severity to Medium and click “Next: Set rule logic”. In Query scheduling I set it to run queries every 5 minutes and lookup data from the last 5 minutes, and click through till I get to the Review + create section and click “Save”. 

I then go back to Microsoft Sentinel and click “Analytics” from the left pane and patiently wait for any logs that are successfully local sign-ins, and finally after 5 minutes it shows that there are successful sign-ins via RDP. 

Then I click “Incidents” from the left pane to view if there is any incidents were found and there is. Yay, I finally built my own SIEM!. 



# My Project

## Introduction

This is a brief introduction to my project.

## Features

<h2 id="features">Features</h2>

* Feature 1
* Feature 2
* Feature 3

## Usage

<h2 id="usage">Usage</h2>

1. **Step 1:** Do this
2. **Step 2:** Do that

## Contributing

<h2 id="contributing">Contributing</h2>

If you want to contribute to this project, please follow these guidelines.

### License

<h3 id="license">License</h3>

This project is licensed under the MIT License.

**Table of Contents:**

* [Introduction](#introduction)
* [Features](#features)
* [Usage](#usage)
* [Contributing](#contributing)
  * [License](#license)


