---
title: Create your own Fiori Launchpad
description: Using Portal, create your own Fiori Launchpad to host your applications
auto_validation: true
primary_tag: products>sap-fiori
tags: [  tutorial>beginner, products>sap-cloud-platform, products>sap-fiori ]
---

## Prerequisites  
 - **Proficiency:** Beginner


## Details
### You will learn  
Enable your SAP Portal service to create your very own Fiori Launchpad. Your Launchpad can be used with Web IDE to host apps that are deployed to the SAP Cloud Platform and registered with Fiori.

### Time to Complete
**10 Min**

---

[ACCORDION-BEGIN [Step 1: ](Go to Services)]

Back in your SAP Cloud Platform cockpit, go to the **Services** page.

![service in Cloud Platform cockpit](1.png)

In the search menu, search for **Portal**.

![service search for Fiori](2.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Open the Portal service)]

From the filtered down list of services, find the **Portal** service under the **User Experience** group.

**Click** on the tile for the Portal Service.

![Portal tile in services](3.png)

Make sure that the service is enabled, and if not click on **Enable**.

![Portal tile in services](3_1.png)

Once you see the green Enabled status, click on **Go to service** to launch the Fiori Launchpad Portal.

![service overview for portal](4.png)

This will load the **Fiori Launchpad Portal**.

![Fiori launchpad portal home screen](5.png)

[DONE]
[ACCORDION-END]


[ACCORDION-BEGIN [Step 3: ](Create a new site)]

On the Fiori Launchpad Portal, click on the **Create New Site** button.

![new site button on home screen](6.png)

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 4: ](Set the site properties)]

Set the **Site Name** to **`te2017frontend`**.

Select the **SAP Fiori Launchpad** as the **Template Source**.

![new site settings](7.png)

Click **Create**.

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 5: ](Fiori Configuration dashboard)]

Your Fiori Launchpad Configuration Cockpit will load.

![new site dashboard](8.png)


[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 6: ](Validate your Fiori Launchpad)]

In your **Fiori Launchpad Cockpit dashboard**, copy the **URL up to the ?** and paste it in the below box.

[VALIDATE_6]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 7: ](Open the settings)]

You can control the settings for your Launchpad from here. Click on the **Settings** tab.

![dashboard settings](9.png)

The settings page for your Fiori launchpad will open.

![settings page](10.png)


[DONE]
[ACCORDION-END]


[ACCORDION-BEGIN [Step 8: ](Update the SAPUI5 version)]

Scroll to the bottom of the settings page to find the **Edit button** in the bottom toolbar. **Click Edit**.

![edit button on settings page](11.png)

Under **System Settings**, locate the _SAPUI5 Version_. **Click the drop down** arrow and choose **Custom** from the list.

![SAPUI5 version options](12.png)

When the dialog box pops up, select **OK**.

![SAPUI5 version warning message](13.png)

From the number drop down menu, select the version number **1.40.18**.

![SAPUI5 number version options](14.png)

Verify your SAPUI5 version settings match the screenshot below and click **SAVE** in the bottom toolbar.

![settings page save button](15.png)

When the read only settings page load, verify that under **System Settings** the _SAPUI5 Version_ is `Custom (1.40.18)`

![SAPUI5 version read only](16.png)

[DONE]
[ACCORDION-END]
