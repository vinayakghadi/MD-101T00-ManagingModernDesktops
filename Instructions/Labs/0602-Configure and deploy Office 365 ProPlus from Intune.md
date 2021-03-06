# Practice Lab - Configure and deploy Office 365 ProPlus from Intune

## Summary

In this lab, you will practice configuring Office 365 ProPlus for deployment in Intune and deploying it to devices.


### Scenario

All the developers at A. Datum require Microsoft Office 365 ProPlus.  You've been asked to deploy  64-bit versions of Microsoft Excel, Outlook, PowerPoint and Word to their Windows 10 devices. You also need to ensure they are configured for the Semi-Annual channel for updates. This should be tested on LON-CL4.

#### Task 1: Verify installed apps on device before deployment

1.  On **LON-CL4**, on the taskbar, select **Start** and then select the
    **Settings** app.

2.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, select **Programs and Features** under Related Settings.

3.  In the **Program and Features** window, verify that **Microsoft Office 365
    ProPlus - en-us** is not listed.

#### Task 2: Create a LOB app type based on the scenario

1.  Switch to **LON-DC1**, and in the Azure portal, select **Intune** in the
    navigation pane, and then on the **Microsoft Intune** blade, select **Client
    apps**.

2.  In the **Client apps** blade, select **Apps**. In the details pane, select **+
    Add**.

3.  In the **Add app** blade, select the **Select an app type** under **App
    type** and select **Windows 10** under **Office 365 Suite**.

4.  Select **Configure App Suite**, and on the **Configure App Suite** blade,
    select the following Office 365 apps and select **OK**:

-   Excel

-   Outlook

-   PowerPoint

-   Word

5.  Back on the **Add app** blade, select **App Suite information**. Configure
    the following options and select **OK**:

-   Name: **Office 365 ProPlus (A. Datum developers)**

-   Description: **Office 365 ProPlus App for developers in A. Datum**

6.  Back on the **Add app** blade, select **App Suite Settings**. Configure the
    following options and select **OK**:

-   Office version: **64-bit**

-   Update channel: **Semi-Annual**

-   **Automatically accept the app end user license agreement**

7.  Back on the **Add app** blade, select **Add**. Wait a few seconds for the app
    to be created.

8.  On the **Office 365 ProPlus (A. Datum developers)** blade, select
    **Assignments**.

9.  On the **Office 365 ProPlus (A. Datum developers) – Assignments** blade,
    select **Add group**.

10.  On the **Add group** blade, select **Select assignment type** under
    **Assignment type** and select **Required**.

11.  Select **No groups selected Included Groups** and on the **Assign** blade,
    select **Select groups to include**.

12.  On the **Assign** blade, select **Select groups to include**, and on the
    **Select groups** blade, select **A. Datum Developer devices**, and then
    select **Select**, then **OK** twice. If you have many groups, you can search
    for groups by typing part of the name in the **Search by name or email
    address** field.

13.  Back on the **Office 365 ProPlus (A. Datum developers) - Assignments**
    blade, select **Save**. In the details pane verify that **A. Datum developer
    devices** in listed under **REQUIRED**.

#### Task 3: Force synchronization of policy from Intune console

1.  On **LON-DC1**, in the Azure portal, select **Intune** in the navigation
    pane, and then on the **Microsoft Intune** blade, select **Devices** and then
    select **All devices**.

2.  In the details pane, select **LON-CL3**. On the **LON-CL3** blade, select
    **Sync** and when prompted select **Yes**. Intune will contact the device and
    tell it to synchronize all policies. This may take up to 5 minutes.

#### Task 4: Verify on device that app is installed

1.  Switch to **LON-CL4** and wait approximately 10-15 minutes for the Office
    365 Suite to install on the device.

2.  On **LON-CL4**, on the taskbar, select **Start** and then select the
    **Settings** app.

3.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, scroll down and verify that **Microsoft Office 365 ProPlus
    - en-us** is listed.

4.  Close the **Settings** app and select the **Start** button.

5.  In the app list, scroll down to **W** and select **Word** and verify that the
    app opens.

6.  Close all open windows.

#### Task 5: Verify app installation in Intune

1.  Switch to **LON-CL3**.

2.  In the Azure portal, select **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, select **Client apps**.

3.  On the **Client apps** blade, select **App install status** under
    **Monitor**. In the details pane, select **Office 365 ProPlus (A. Datum
    developers)**.

4.  In the details pane, under **Device status** and under **User status**,
    **1** is displayed under Installed. This indicated that the app is installed
    on one device and for one user.

5.  Select **Device install status** to the left of the blue circle. In the
    details pane, you can see the devices that the app is installed on, and also
    the name of the user. The **DEVICE NAME** column should list **LON-CL4** and
    the **USER NAME** column should list **DiegoS** and the **STATUS** column
    should say **Installed**. This mean that the app is installed on LON-CL4 by
    the user DiegoS.

6.  In the Azure portal, select **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, select **Devices**.

7.  On the **Devices** blade, select **All devices** and then in the details
    pane, select **LON-CL4**.

8.  On the **LON-CL4** blade, select **Managed Apps - Preview** under
    **Monitor**.

9.  On the **LON-CL4 - Managed Apps - Preview** blade, in the details pane,
    select **Office 365 ProPlus (A. Datum developers)**.

10. On the **Office 365 ProPlus (A. Datum developers) - Installation details**
    blade, you can see the entire lifecycle of the application, that is - when
    it was created, assigned, installation time and status and the last time the
    device checked in (synced with Intune).

**END OF LAB**