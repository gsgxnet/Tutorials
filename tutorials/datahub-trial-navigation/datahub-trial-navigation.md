---
title: Navigate around SAP Data Hub, trial edition
description: Find your way around SAP Data Hub, trial edition.
auto_validation: true
primary_tag: products>sap-data-hub
tags: [  tutorial>beginner, topic>big-data, products>sap-data-hub, products>sap-vora ]
---

## Prerequisites  
 - **Proficiency:** Beginner
 - You have completed [Set up SAP Data Hub, trial edition](https://www.sap.com/developer/tutorials/datahub-trial-setup.html).

## Details
### You will learn  
During this tutorial, you will learn how to find your way around SAP Data Hub, trial edition. You will also learn how to troubleshoot problems.

### Time to Complete
**15 Min**

---

[ACCORDION-BEGIN [Step 1: ](Access UIs via a web browser)]
The SAP Data Hub Cockpit serves as central entry point to all user interfaces of SAP Data Hub. You access it by opening (`https://vhcalhxedb:51076/`) via a web browser.

Enter `DATAHUB` as **HANA Username** and the password which you have selected during step 3 as **HANA Password** to logon to SAP Data Hub Cockpit. The system displays the **Overview** page.

![picture_01](./datahub-trial-navigation_01.png)  

From the SAP Data Hub Cockpit, you can navigate to:

 - SAP Data Hub Modeling tool (direct link: `https://vhcalhxedb:51058/`)
 - SAP Data Hub Pipeline Modeler (direct link: `https://vhcalruntime/app/pipeline-modeler`)
 - SAP Vora Tools (direct link: `https://vhcalruntime/app/vora-tools`)
 - SAP Data Hub System Management (direct link: `https://vhcalruntime/home/`)

Subsequently we will describe each of the user interfaces briefly.

>In a production environment you would, of course, access all user interfaces via fully-qualified domain names. SAP Data Hub, trial edition currently does not use such.

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](SAP Data Hub Modeling tool)]
The SAP Data Hub Modeling tool (direct link: `https://vhcalhxedb:51058/`) allows you to create task workflows.

![picture_02](./datahub-trial-navigation_02.png)  

Check the below screenshot and answer the question based on the same :

![picture_06](./datahub-trial-navigation_06.png)

[VALIDATE_1]

>Hint : You can hover over the button icon to know more about it.

[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: ](SAP Data Hub Pipeline Modeler)]
The SAP Data Hub Pipeline Modeler (direct link: `https://vhcalruntime/app/pipeline-modeler`) allows you to create data-driven applications, so-called data pipelines.

>Use "default" as the tenant while logging in to Data Hub Pipeline Modeler

![picture_03](./datahub-trial-navigation_03.png)  

Check the below screenshot and answer the question based on the same :

![picture_07](./datahub-trial-navigation_07.png)

[VALIDATE_2]

>Hint : You can hover over the button icon to know more about it.

[ACCORDION-END]

[ACCORDION-BEGIN [Step 4: ](SAP Vora Tools)]
The SAP Vora Tools (direct link: `https://vhcalruntime/app/vora-tools`) provide you with a data modeling environment for creating and maintaining tables and views.

![picture_04](./datahub-trial-navigation_04.png)  

[VALIDATE_3]

>Hint : You can check the welcome page of SAP Vora Tools to find the answer

[ACCORDION-END]

[ACCORDION-BEGIN [Step 5: ](SAP Data Hub System Management)]
The SAP Data Hub System Management (direct link: `https://vhcalruntime/home/`) allows you to manage applications, in particular the SAP Data Hub Pipeline Modeler and the SAP Vora Tools, as well as corresponding users.

![picture_05](./datahub-trial-navigation_05.png)  

Check the below screenshot and answer the question based on the same :

![picture_08](./datahub-trial-navigation_08.png)

[VALIDATE_4]

>Hint : You can hover over the button icons to know more about it.

[ACCORDION-END]

[ACCORDION-BEGIN [Step 6: ](Troubleshoot problems and show logs)]
To troubleshoot problems you can access the operating system of the virtual machines as well as the Kubernetes cluster underlying your solution instance. You also have access to SAP Vora Diagnostics. This is an open-source tool chain that supports you with monitoring and troubleshooting.

If you need to troubleshoot problems, please refer to the corresponding chapters of the [**Getting Started with SAP Data Hub, trial edition**] (https://caldocs.hana.ondemand.com/caldocs/help/Getting_Started_Data_Hub_SP04.pdf) guide.

[DONE]

[ACCORDION-END]

---
