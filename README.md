In this exercise, you will learn how to use Node-RED to build and POST
sensor data to Maximo meters using REST APIs. The reason you are
learning this alternative method is because it is sometimes useful for
demos in which case you need to show real-time responses to changes in
sensor data. NOTE: Be cautious about the volume of data you’re sending
to Maximo. Again, the Maximo database was not designed to handle high
traffic.

**If you do not have an instance of Node-RED available, create one
directly using the following button:**

[![Deploy to IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/mbenav3/ibm-iotp-maximo-node-red/app)

Note: This repository will create an instance of Node-RED with the following nodes:  
- **[IBM Watson IoT Platform Node-RED node](https://flows.nodered.org/node/node-red-contrib-scx-ibmiotapp)**

- **[Throttle Node-RED node](https://www.npmjs.com/package/node-red-contrib-throttle)**

**If you already have an instance, skip to step 10.**

1.  Clicking the button above will take you to the IBM Cloud deployment configuration
    page to help you create your new Node-RED instance. **You may be asked to sign in to
    your IBM Cloud account.**

3.  Verify that the *Region* and the *Organization* are set to where you
    want your instance deployed. Click on the Delivery Pipeline tab and
    click on the *New* button:

![A screenshot of a cell phone Description automatically
generated](./media/image2.png)

4.  Click the *OK* button on the *Create a new API key with full access*
    window.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image3.png)

5.  Verify that the Region, Organization, and Space are set to where you
    want your new instance deployed. Click the *Create* button on the
    top right corner of the screen.

6.  Your new Node-RED instance is now being created. The page you are
    viewing is your Node-RED instance’s deployment overview Toolchain.
    Click on the *Deliver* task to monitor the progress of your
    deployment:

![A screenshot of a cell phone Description automatically
generated](./media/image4.png)

7.  Your app is ready when the Build and Deploy stages are successfully
    executed: ![A screenshot of a social media post Description
    automatically generated](./media/image5.png)

8.  Once both stages are successful, navigate back to your deployment
    Toolchain overview page using the breadcrumbs on the top left part
    of the page

![A screenshot of a cell phone Description automatically
generated](./media/image6.png)

9.  Your Delivery Pipeline will now also indicate that the task was
    successfully executed.

![A screenshot of a cell phone Description automatically
generated](./media/image7.png)

10. Now that your Node-RED instance is ready, click on the *Visit App
    URL* on the top right section of your screen. Follow the wizard to
    secure your application. **(Skip to step 13)**

11. From menu in the top right-hand corner, select **Manage Palette**.
    Click the **Install** tab and search **throttle**. Install the
    **node-red-contrib-throttle** node as shown in the image below:

![A screenshot of a cell phone Description automatically
generated](./media/image8.png)

12. Repeat step 9 for the **node-red-contrib-scx-ibmiotapp** node.

![A screenshot of a social media post Description automatically
generated](./media/image9.png)

13. Copy the contents of the **[IoT Platform to Maximo JSON file](https://github.com/mbenav3/ibm-iotp-maximo-node-red/blob/master/IoT_platform_to_maximo.json)** file. 


14. Navigate back to your Node-RED application and click on the menu button on the
    top right-hand corner. Select **Import** and on the **Clipboard** tab, paste the
    json object you copied in the previous step. Finally, click the **import** button. You should see 3 tabs, as shown below:

![A screenshot of a social media post Description automatically
generated](./media/image10.png)

16. Create a new tab by clicking the + sign on the top right-hand corner
    and call the tab **Maximo Meter REST API**:

![A picture containing clock, game Description automatically
generated](./media/image11.png)

17. Copy the flow from the **Maximo METER API (Ref)** tab and paste the
    flows into the **Maximo Meter REST API** tab.

18. Open the **IoT PLATFORM** node and click the **Pencil Icon** as
    shown below:

![A screenshot of a cell phone Description automatically
generated](./media/image12.png)

19. Enter the credentials to your instance of the IoT Platform that you
    used in Exercise 4-1 of the lab, Step4. NOTE: URL is
    \<org-id\>.messaging.internetofthings.ibmcloud.com

20. Click the **Update** button. Click the checkbox next to the **Device
    ID** label to edit the Device ID field, enter the name of the device
    (ex. DBNT). Leave the checkbox unchecked.

21. Click **Done** and then **Deploy** the Node-RED flow. The IoT
    PLATFORM node should now say connected. If not, check the
    credentials or notify the lab instructor.

22. Open the **Build METER REST API URL** node. Follow the instructions
    outlined in the node and replace the appropriate variables. For your
    convenience, all of the configurable variables have been placed at
    the beginning of the node.

![A screenshot of a social media post Description automatically
generated](./media/image13.png)

23. Repeat **Step 8** for the **Evaluate METER & Build REST API URL**.

24. Copy and paste every node after the IoT Platform node and repeat
    **Steps 8 & 9** for any additional meters. The Node-RED flow should
    look similar to the one shown on the following page. NOTE: Turn on
    the **Debug** nodes and confirm that values are being posted to
    Maximo (400 = Successful. 200 = Failed).![A screenshot of a social
    media post Description automatically generated](./media/image14.png)

25. You are now finished with **Exercise 4-2**. You’ve successfully
    posted sensor readings to Maximo in the form of meters. If you
    haven’t already noticed, the throttle node is meant to simulate
    normal operating data at the desired rate. The Evaluate METER node
    is meant to send only data points that exceed the thresholds. In the
    following exercise, you will view your sensors readings in the
    HEALTH UI from the perspective of the Reliability Engineer.
    Exercise– Using HEALTH
