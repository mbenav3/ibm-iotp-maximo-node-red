![Image result for ibm
logo](./media/image1.jpeg){width="2.3420931758530186in"
height="1.11875in"}

<<<<<<< Updated upstream
### :page_facing_up: Note
**This repository creates an instance of Node-RED pre-loaded with the following nodes**  

- [IBM Watson IoT Platform Node-RED node](https://flows.nodered.org/node/node-red-contrib-scx-ibmiotapp) as a default node in your palette
- This repository includes the [Throttle Node-RED node](https://www.npmjs.com/package/node-red-contrib-throttle) as a default node in your palette


=======
 **Exercise 4-2: Connecting Using Node-RED & REST APIs**
-------------------------------------------------------
>>>>>>> Stashed changes

In this exercise, you will learn how to use Node-RED to build and POST
sensor data to Maximo meters using REST APIs. The reason you are
learning this alternative method is because it is sometimes useful for
demos in which case you need to show real-time responses to changes in
sensor data. NOTE: Be cautious about the volume of data you're sending
to Maximo. Again, the Maximo database was not designed to handle high
traffic.

**If you do not have an instance of Node-RED available, create one
directly from the following repository:**

<<<<<<< Updated upstream
[![Deploy to IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/mbenav3/node-red-app)
=======
<https://github.com/mbenav3/node-red-app/tree/master#node-red-on-ibm-cloud>
>>>>>>> Stashed changes

Note: This instance comes with the required nodes for this lab.

**If you already have an instance, skip to step 9.**

1.  Click on the *Deploy to IBM Cloud* button in the

![A picture containing bird Description automatically
generated](./media/image2.png){width="4.15829615048119in"
height="0.7450273403324584in"}

2.  This button will take you to the IBM Cloud deployment configuration
    to create your new Node-RED instance. You may be asked to sign in to
    your IBM Cloud account.

<<<<<<< Updated upstream
### Customizing Node-RED
=======
3.  Verify that the *Region* and the *Organization* are set to where you
    want your instance deployed. Click on the Delivery Pipeline tab and
    click on the *New* button:
>>>>>>> Stashed changes

![A screenshot of a cell phone Description automatically
generated](./media/image3.tiff){width="3.343727034120735in"
height="1.348921697287839in"}

4.  Click the *OK* button on the *Create a new API key with full access*
    window.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image4.tiff){width="2.9006616360454944in"
> height="1.2234842519685039in"}

5.  Verify that the Region, Organization, and Space are set to where you
    want your new instance deployed. Click the *Create* button on the
    top right corner of the screen.

6.  Your new Node-RED instance is now being created. The page you are
    viewing is your Node-RED instance's deployment overview Toolchain.
    Click on the *Deliver* task to monitor the progress of your
    deployment:

![A screenshot of a cell phone Description automatically
generated](./media/image5.tiff){width="2.765531496062992in"
height="2.0655807086614173in"}![A screenshot of a cell phone Description
automatically
generated](./media/image6.png){width="3.0198676727909013in"
height="1.9635597112860892in"}

7.  Your app is ready when the Build and Deploy stages are successfully
    executed: ![A screenshot of a social media post Description
    automatically
    generated](./media/image7.png){width="2.7609448818897637in"
    height="1.6913724846894138in"}

8.  Once both stages are successful, navigate back to your deployment
    Toolchain overview page using the breadcrumbs on the top left part
    of the page

![A screenshot of a cell phone Description automatically
generated](./media/image8.tiff){width="4.127470472440945in"
height="0.5569444444444445in"}

9.  Your Delivery Pipeline will now also indicate that the task was
    successfully executed.

![A screenshot of a cell phone Description automatically
generated](./media/image9.tiff){width="2.3708606736657916in"
height="1.5415660542432197in"}

10. Now that your Node-RED instance is ready, click on the *Visit App
    URL* on the top right section of your screen. Follow the wizard to
    secure your application. **(Skip to step 13)\
    **

11. From menu in the top right-hand corner, select **Manage Palette**.
    Click the **Install** tab and search **throttle**. Install the
    **node-red-contrib-throttle** node as shown in the image below:

![A screenshot of a computer Description automatically
generated](./media/image10.png){width="3.609271653543307in"
height="1.8003937007874016in"}

12. Repeat step 9 for the **node-red-contrib-scx-ibmiotapp** node.

13. Navigate to an instance of Node-RED. Create a new canvas titled
    **Maximo Meter REST API**.

14. Download the **Maximo\_Meter\_RESTAPI.json** file. Open the file in
    any Text Editor and copy the code. From the menu in the top
    right-hand corner, select **Import Clipboard** and paste the code.

> ![A screenshot of a cell phone Description automatically
> generated](./media/image11.tiff){width="6.5in"
> height="1.8944444444444444in"}

15. Open the **IoT PLATFORM** node and click the **Pencil Icon**. Enter
    the credentials to your instance of the IoT Platform that you used
    in Exercise 4-1 of the lab, Step 4. NOTE: URL is
    \<org-id\>.messaging.internetofthings.ibmcloud.com

![A screenshot of a social media post Description automatically
generated](./media/image12.png){width="6.5in"
height="3.2597222222222224in"}

16. Click the **Update** button. In the **Device ID** field, enter the
    name of the device (ex. DBNT).

17. Click **Done** and then **Deploy** the Node-RED flow. The IoT
    PLATFORM node should now say connected. If not, check the
    credentials or notify the lab instructor.

18. Open the **Build METER REST API URL** node. Follow the instructions
    outlined in the node and replace the appropriate variables.

l![A screenshot of a social media post Description automatically
generated](./media/image13.png){width="5.884615048118985in"
height="2.9492235345581803in"}

19. Repeat **Step 8** for the **Evaluate METER & Build REST API URL**.

20. Copy and paste every node after the IoT Platform node and repeat
    **Steps 8 & 9** for any additional meters. The Node-RED flow should
    look similar to the one shown on the following page. NOTE: Turn on
    the **Debug** nodes and confirm that values are being posted to
    Maximo (400 = Successful. 200 = Failed).

![A screenshot of a social media post Description automatically
generated](./media/image14.png){width="6.076922572178478in"
height="3.0423567366579176in"}

21. You are now finished with **Exercise 4-2**. You've successfully
    posted sensor readings to Maximo in the form of meters. If you
    haven't already noticed, the throttle node is meant to simulate
    normal operating data at the desired rate. The Evaluate METER node
    is meant to send only data points that exceed the thresholds. In the
    following exercise, you will view your sensors readings in the
    HEALTH UI from the perspective of the Reliability Engineer.
