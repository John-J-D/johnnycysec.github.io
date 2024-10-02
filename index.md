---
layout: default
---

**Name:** **John Jefferson L. Doyon**

[LinkedIn Profile](https://www.linkedin.com/in/johnjefferson11/)

I like to help companies reduce cybersecurity risks --- Independent Advisor at Microsoft Community

<br>

# About

I like to help companies reduce cybersecurity risks. I have a background in IT support with experience as a Microsoft products expert, technical troubleshooter, and Independent Advisor at Microsoft Community, and I’m a fast learner with strong problem-solving abilities, a focus on effective decision-making, and the ability to effectively translate technical information to non-technical audiences. I’m dedicated to applying my skills in cybersecurity to monitor, analyze, and respond to security incidents. My goal is to support organizations in maintaining strong security postures and achieving their security objectives.

<br>

## Portfolio projects
**Google Cybersecurity Professional Certificate:**
* [Drafting a professional statement](#Drafting-a-professional-statement)
* [Conducting a security audit](#Conducting-a-security-audit)
* [Analyzing network structure and security](#Analyzing-network-structure-and-security)
* [Using Linux commands to manage file permissions](#Using-Linux-commands-to-manage-file-permissions)
* [Applying filters to SQL queries](#Applying-filters-to-SQL-queries)
* [Identifying vulnerabilities for a small business](#Identifying-vulnerabilities-for-a-small-business)
* [Documenting incidents with an incident handler’s journal](#Documenting-incidents-with-an-incident-handler’s-journal)
* [Importing and parsing a text file in a security-related scenario](#Importing-and-parsing-a-text-file-in-a-security'-'related-scenario)
* [Creating or revising a resume](#Creating-or-revising-a-resume)

**Individual projects**
* [Building a SIEM using Microsoft Azure and deploying Microsoft Sentinel and crafting custom rules](#Building-a-SIEM-using-Microsoft-Azure-and-deploying-Microsoft-Sentinel-and-crafting-custom-rules)

<br>

## Contents:

<h2 id="Drafting-a-professional-statement">Drafting a professional statement</h2>
I like to help companies reduce cybersecurity risks. I have a background in IT support with experience as a Microsoft products expert, technical troubleshooter, and Independent Advisor at Microsoft Community. I’m a fast learner with strong problem-solving abilities and a focus on effective decision-making. I also have the ability to effectively translate technical information for non-technical audiences. I’m passionate about expanding my career into cybersecurity, where my strengths in protecting people and organizations align with the core goals of the field. I’m committed to leveraging my skills to help organizations safeguard against evolving threats, maintain compliance, and adhere to industry standards. I’m excited to contribute to a safer digital landscape by monitoring, analyzing, and responding to security incidents, ultimately supporting organizations in maintaining strong security postures and achieving their cybersecurity objectives.


<h2 id="Conducting-a-security-audit">Conducting a security audit</h2>
<i>To be continued</i>


<h2 id="Analyzing-network-structure-and-security">Analyzing network structure and security</h2>
<i>To be continued</i>


<h2 id="Using-Linux-commands-to-manage-file-permissions">Using Linux commands to manage file permissions</h2>
<i>To be continued</i>


<h2 id="Applying-filters-to-SQL-queries">Applying filters to SQL queries</h2>
<i>To be continued</i>


<h2 id="Identifying-vulnerabilities-for-a-small-business">Identifying vulnerabilities for a small business</h2>
<i>To be continued</i>


<h2 id="Documenting-incidents-with-an-incident-handler’s-journal">Documenting incidents with an incident handler’s journal</h2>
<i>To be continued</i>


<h2 id="Importing-and-parsing-a-text-file-in-a-security'-'related-scenario">Importing and parsing a text file in a security-related scenario</h2>
<i>To be continued</i>


<h2 id="Creating-or-revising-a-resume">Creating or revising a resume</h2>
<i>To be continued</i>


<h2 id="Building-a-SIEM-using-Microsoft-Azure-and-deploying-Microsoft-Sentinel-and-crafting-custom-rules">Building a SIEM using Microsoft Azure and deploying Microsoft Sentinel and crafting custom rules</h2>

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



<br>
<i>To be continued</i>
<br>
<br>
<h3>To God be the glory</h3>
