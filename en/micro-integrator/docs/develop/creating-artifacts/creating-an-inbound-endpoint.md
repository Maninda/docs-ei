# Creating an Inbound Endpoint

Follow the instructions given below to create a new Inbound Endpoint artifact in WSO2 Integration Studio.

## Instructions

Follow the steps below to create a new inbound endpoint.

1.  If you have already created an [ESB Config project](../../creating-projects/#esb-config-project), right-click the project in the navigator and go to **New → Inbound Endpoint** to open the **New Inbound Endpoint Artifact** dialog:

    ![](attachments/119130498/119130502.png)

2. Select **Create a New Inbound Endpoint** and click **Next** .
3. Enter a unique name for the inbound endpoint, and select an **Inbound Endpoint Creation Type** from the list shown below.

    ![](attachments/119130498/119130501.png)
    
4.  For certain protocols ( HL7, KAFKA, Custom, MQTT, RabbitMq, WSO2_MB, WS, and  WSS) the main sequence and error sequence are mandatory fields. You can select sequences that already exists in the workspace and add them to the **Sequence** and **Error sequence** fields (shown below). If you don't have any sequences incthe workspace, click **Generate Sequence and Error Sequence** to generate new sequences for the inbound endpoint.  
    ![](attachments/119130498/119130500.png)  
5.  Specify the **ESB Solution** project where Inbound Endpoint should be saved.
6.  Click **Finish** to generate the inbound endpoint. The artifact will
    now be saved in the ESB project.

!!! Note
    **Redeployment of listening inbound endpoints fail?**

    A [listening inbound endpoint](_Listening_Inbound_Endpoints_) opens the port for itself during deployment. Therefore, if you are **redeploying** a listening inbound endpoint artifact, the redeployment will not be successful until the port that was previously opened for the inbound endpoint is closed.
    
    By default, the system will wait for 10 seconds for the previously opened port to close down. If you want to increase this waiting time beyond 10 seconds, be sure to add the following system property in the `         carbon.properties        ` file, which is stored in the `MI_HOME/conf/        ` directory and restart the server before redeploying the artifacts.

    ``` java
    -Dsynapse.transport.portCloseVerifyTimeout=20
    ```

    Note that this setting may be required in Windows environments as the process of closing a port can sometimes take longer than 10 seconds.xss

## Examples
..

## Guides
...