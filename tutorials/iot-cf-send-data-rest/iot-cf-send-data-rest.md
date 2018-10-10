---
title: Send Data with REST
description: Send data to the SAP Cloud Platform Internet of Things Service Cloud using REST.
auto_validation: true
primary_tag: products>sap-cloud-platform-internet-of-things
tags: [ tutorial>beginner, products>sap-cloud-platform-internet-of-things, topic>internet-of-things, topic>cloud ]
---

<!-- loioe341f4746979496d8abad6f1e0d8a1dc -->

## Prerequisites
 - **Proficiency:** Beginner
 - **Tutorials:** You have completed [Install cURL](https://www.sap.com/developer/tutorials/iot-cf-install-curl.html) and [Install OpenSSL](https://www.sap.com/developer/tutorials/iot-cf-install-openssl.html).

## Details
### You will learn
- How to create a device model for the Internet of Things Service
- How to send data to the Internet of Things Service Cloud using REST
- How to use cURL as a sample client for REST

### Time to Complete
20 min

---

You have to create a device model for the Internet of Things Service using the Internet of Things Service Cockpit.

[ACCORDION-BEGIN [Step 1: ](Create a Capability)]

In the following a capability is created. A capability can be reused since it can be assigned to multiple sensor types. Each capability can have one or many properties.

1.  Log on to the Internet of Things Service Cockpit with your user credentials.

    ```bash
    https://<HOST_NAME>/iot/cockpit/
    ```

2.  On the home page, select a tenant first and then use the main menu to navigate to the *Capabilities* section of the *Device Management* category.

3.  Choose **+** (Create a capability) above the capabilities list.

4.  In the *General Information* section, enter a *Name*. Optionally enter an *Alternate ID* for the capability.

    *Name*: `MyCapability`

    *Alternate ID*: `1234`

5.  In the *Properties* section, specify additional properties. Choose **+** (Add a property) from the toolbar of the properties table.

6.  Enter a *Name* for the property.

    *Name*: `temperature`

7.  Select a *Data Type* from the dropdown box for the property.

    *Data Type*: `float`

8.  Enter a *Unit of Measure*.

    *Unit of Measure*: `Celsius`

9.  Choose *Create*.

10. Note down the *Alternate ID* of the capability.

    You get a notification that the capability was created successfully.

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Create a Sensor Type)]

In the following a sensor type is created. The previously created capability is assigned to the sensor type.

1.  Use the main menu to navigate to the *Sensor Types* section of the *Device Management* category.

2.  Choose **+** (Create a sensor type) above the sensor types list.

3.  In the *General Information* section, enter a *Name*. Optionally enter an *Alternate ID* for the sensor type.

    *Name*: `MySensorType`

4.  In the *Capabilities* section, add capabilities for this sensor type. Choose **+** (Add a capability) from the toolbar of the capabilities table.

5.  Select the previously created *Capability* from the dropdown box.

6.  Select the capability *Type* from the dropdown box.

    *Type*: `measure`

7.  Choose *Create*.

    You get a notification that the sensor type was created successfully.

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 3: ](Create a REST Device)]

In the following a device is created. The device does not have any sensors attached, yet. The device is assigned to the REST gateway.

1.  Use the main menu to navigate to the *Devices* section of the *Device Management* category.

2.  Choose **+** (Create a device) above the devices list.

3.  In the *General Information* section, enter a *Name*, and select a *Gateway* from the dropdown box. Optionally enter an *Alternate ID* for the device.

    *Name*: `MyDevice`

    *Gateway*: `IoT Gateway REST`

    *Alternate ID*: `11223344`

4.  Choose *Create*.

5.  Note down the *Alternate ID* of the device.

    You get a notification that the device was created successfully.

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 4: ](Create a Sensor)]

In the following a sensor is created. The sensor is assigned to the previously created device and is a kind of the previously created sensor type.

1.  Use the main menu to navigate to the *Devices* section of the *Device Management* category.

2.  Search for and select the previously created device.

3.  In the *Sensors* section, choose **+** (Add a sensor) to add a new sensor.

4.  In the *General Information* section, enter a *Name*, and select the previously created *Sensor Type* from the dropdown box. Optionally enter an *Alternate ID* for the sensor.

    *Name*: `MySensor`

    *Alternate ID*: `4321`

6.  Choose *Add*.

7.  Note down the *Alternate ID* of the sensor.

    You get a notification that the sensor was created successfully.

[DONE]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 5: ](Generate the Device Certificate)]

1.  Use the main menu to navigate to the *Devices* section of the *Device Management* category.

3.  Choose the previously created device.

4.  On the device details page, choose the *Certificate* tab.

5.  In the *Generate Certificate* dialog, select the type of certificate you want to generate and choose *Generate*.

    > Note:
    > Supported types are PEM and P12. Based on the certificate type you choose, the system downloads a `*-device_certificate.pem` or `*-device_certificate.p12` and a dialog opens, which shows the *Secret* key.
    >
    >

6.  Select and copy the displayed *Secret* key before closing the dialog or leaving the page, as it cannot be restored at a later point in time.

7.  Rename `*-device_certificate.pem` to `client.pem`or `*-device_certificate.p12` to `client.p12`.

[VALIDATE_1]

[ACCORDION-END]

[ACCORDION-BEGIN [Step 6: ](Publish Data With cURL Using REST)]

**Prerequisites:**

-   You have installed the REST client (cURL). A description of how to install the cURL client can be found in the tutorial [Install cURL](https://www.sap.com/developer/tutorials/iot-cf-install-curl.html).

-   You have installed OpenSSL. A description of how to install OpenSSL can be found in the tutorial [Install OpenSSL](https://www.sap.com/developer/tutorials/iot-cf-install-openssl.html).

-   You have created the device model in step 1-4.

-   You have generated a certificate for your REST device and written down the secret key.


Open the terminal (macOS) or command line tool CMD (Windows) and change the directory to the path of the extracted REST device certificate.

> Note:
> You must be connected to public Internet. Most corporate networks do not work due to port and protocol restrictions.
>
>

**Send data using cURL (only for cURL with OpenSSL on Windows or for cURL without SecureTransport using LibreSSL on macOS).**

1.  Enter and send the message string.

    ```bash
    curl -v -k -E client.pem:<SECRET_KEY> -H "Content-Type:application/json" -d "<ENCODED_JSON_MESSAGE>" <REST_ENDPOINT>
    ```

    Two formats are allowed:

    -   One with the measures specified as an array of arrays.

        ```bash
        curl -v -k -E client.pem:jJ3fF7dD0rR2rR3wW0eE2tT -H "Content-Type:application/json" -d "{ \"capabilityAlternateId\": \"1234\", \"sensorAlternateId\": \"4321\", \"measures\": [[\"25\"]] }" https://demo.eu10.cp.iot.sap/iot/gateway/rest/measures/11223344
        ```

    -   Another one, specifying measures as an array of JSON objects where the name of each property defined in the capability is the key.

        ```bash
        curl -v -k -E client.pem:jJ3fF7dD0rR2rR3wW0eE2tT -H "Content-Type:application/json" -d "{ \"capabilityAlternateId\": \"1234\", \"sensorAlternateId\": \"4321\", \"measures\": [{\"temperature\": \"25\"}] }" https://demo.eu10.cp.iot.sap/iot/gateway/rest/measures/11223344
        ```

2.  Check the response code in the terminal. The message must contain the following:

    ```bash
    * upload completely sent off: <xx> out of <xx> bytes
    ```

    ```bash
    < HTTP/1.1 200 OK
    ```

3.  You can check the incoming values using the *Data Visualization* of the device in the Internet of Things Service Cockpit or the Internet of Things API Service. For more information, please refer to the tutorial [Consume Measures](https://www.sap.com/developer/tutorials/iot-cf-consume-measures.html).


**Send data using cURL (only for cURL with SecureTransport on macOS).**

1.  Enter and send the message string.

    ```bash
    curl -v -k -E client.p12:<SECRET_KEY> -H "Content-Type:application/json" -d "<ENCODED_JSON_MESSAGE>" <REST_ENDPOINT>
    ```

    Two formats are allowed:

    -   One with the measures specified as an array of arrays.

        ```bash
        curl -v -k -E client.p12:jJ3fF7dD0rR2rR3wW0eE2tT -H "Content-Type:application/json" -d "{ \"capabilityAlternateId\": \"1234\", \"sensorAlternateId\": \4321\", \"measures\": [[\"25\"]] }" https://demo.eu10.cp.iot.sap/iot/gateway/rest/measures/11223344
        ```

    -   Another one, specifying measures as an array of JSON objects where the name of each property defined in the capability is the key.

        ```bash
        curl -v -k -E client.p12:jJ3fF7dD0rR2rR3wW0eE2tT -H "Content-Type:application/json" -d "{ \"capabilityAlternateId\": \"1234\", \"sensorAlternateId\": \"4321\", \"measures\": [{\"temperature\": \"25\"}] }" https://demo.eu10.cp.iot.sap/iot/gateway/rest/measures/11223344
        ```

2.  Check the response code in the terminal. The message must contain the following:

    ```bash
    * upload completely sent off: <xx> out of <xx> bytes
    ```

    ```bash
    < HTTP/1.1 200 OK
    ```

3.  You can check the incoming values using the *Data Visualization* of the device in the Internet of Things Service Cockpit or the Internet of Things API Service. For more information, please refer to the tutorial [Consume Measures](https://www.sap.com/developer/tutorials/iot-cf-consume-measures.html).

[DONE]

[ACCORDION-END]
