---
title: SAP HANA XS Classic, Enable XSODATA in your SAP HANA XSC Application
description: In this tutorial you willenable XSODATA in the SAP HANA XSC application you just created.
primary_tag: products>sap-hana
tags: [ products>sap-hana, products>sap-hana-studio, products>sap-cloud-platform, topic>sql, topic>big-data, tutorial>beginner]
time: 10
---

## Prerequisites  
- **Proficiency:** Beginner
- **Tutorials:** [Access your first data in a SAP HANA XSC Application](https://www.sap.com/developer/tutorials/hana-data-access-authorizations.html)

## Next Steps
- [Consume XSODATA in your SAP HANA XSC Application](https://www.sap.com/developer/tutorials/hana-consume-xsodata.html)

## Details
### You will learn  
  - How to create a simple `xsodata` service

&nbsp;
> **DEPRECATED:** SAP HANA XS Classic is deprecated as of SPS02. Please use XS Advanced, and learn about how to get started with the new mission [Get Started with XS Advanced Development](https://www.sap.com/developer/missions/xsa-get-started.html).

&nbsp;



---

[ACCORDION-BEGIN [Step 1: Create a sub package for your services](Create a sub package for your services)]

Now that you have a table with data in it, you need to be able to access the data and for that you will need to create and `.xsodata` file which defines an OData service. To start create a new sub package for your services.

![Service sub package](4.png)

[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: Create your service definition](Create your service definition)]

Next create a new file `library.xsodata` and add the following code to it, the file name itself is only important in the sense that it is part of the URL when it is called most important though is that the ending of the file is `.xsodata`

```
service namespace "codejam.services" {
	"codejam.data::mydata.Book" as "library";
}
```

[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: Access your service](Access your service)]

At this point you should be able to launch your XSODATA file in your browser or right click and choose the `OData Explorer` to view and see the data from your table.

![OData Explorer](7.png)

![Raw broswer output](8.png)

Congratulations: You have just enabled a simple REST interface for your application.

[ACCORDION-END]

### Optional: Related Information
[SAP HANA Development Information - Official Documentation](https://help.sap.com/hana_platform#section6)
