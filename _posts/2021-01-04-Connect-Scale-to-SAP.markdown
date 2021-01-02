---
layout: post

title: "Connect a digital shipping scale to SAP"

description: "Learn how to connect digital weighing scales for boxes, small packages, parcels
and loaded pallets directly to SAP.  This automates data collection and
streamlines outbound business functions.  SAP packing stations solicit weight
from scales via RFC connections.  We also explain the setup procedure for
WinWedge software, a PC application provided by TALtech which interprets the
serial data stream coming from a scale."  

image:  /assets/scaleForR3.png

categories: parcel-shipping
---

Learn how to connect digital weighing scales for boxes, small packages, parcels
and loaded pallets directly to SAP.  This drives automation of data collection and
streamlines outbound business functions.  
*Setup_scale.exe*, a program provided by SAP for creating registry entries on a
Widows PC, is discussed.  Once the registry settings are populated, SAP packing stations can solicit weight
from scales via RFC connections.  We also explain the setup procedure for
*WinWedge* software, a PC application provided by TALtech which interprets the
serial data stream coming from a scale.  

{% include followCompany.html %}

## Procedure for connecting a scale to SAP

### Step 1: Software installation
- assign each packing station (transaction code *HUPAST*) a unique number.  In our example here we use an NCI scale by Avery Weigh-Tronix; METTLER TOLEDO also makes excellent scales.
- connect the scale to COM1 of the packing station PC
- install *WinWedge Std* from TALtech Technologies (<https://www.taltech.com>)
- create a WinWedge configuration file that interprets the
  data stream coming from the scale

> **Comment.** Please comment and ask questions regarding this post.  I would like
to hear about your experiences connecting digital shipping scales to SAP. Thanks! [**Click here to comment on this
post**](https://www.linkedin.com/feed/update/urn:li:activity:6746632097114406912).

### Step 2: Software configuration
Obtain the *scale_for_r3.exe* program from SAP and run it on the packing station PC. This program creates an entry in the Windows registration for NCI.

- make an entry in the *Name der Waage im R/3* field: NCI
- press the first button from the top on the right hand side
- change the entry in the *LinkVal* field to field(1)
- change the entry in the *LinkUnit* field to field(2)
- make an entry in the *LinkScaleId* field: [Sendout(’W’,.13)]
- press the orange button on the bottom right hand side

![Scale_for_R3.exe screenshot]({{ site.baseurl }}/assets/scaleForR3.png){: width="647px"}

{% include consultingServicesNote.html %}

### Step 3: Registry check
- check  and confirm your registry details on the packing station PC by going the *Run* prompt in Windows and typing *REGEDIT*
- select OK
- select the following menu path: HKEY_CURRENT_USERS >> Software >> VB and VBA Program Settings
- you should see that node ’HUDDEDRV’ is created. Within this a node with the name of the scale SCALENAME (Note: This name has to be the same as entered in the packing station profile)
- confirm that the entries for your scale match the entries in this figure

![Windows registry entries for scale]({{ site.baseurl }}/assets/registryEntries.png){: width="647px"}

### Step 4: Shortcuts
Create a shortcut to Scale_for_R3.exe.

- The ’Scale\_for\_R3.exe’ program must exist on the PC. Do not start the program directly, instead use a batch-file with the following contents: scale_for_r3.exe -aSCALE_AT_PACKINGSTATIONXX -gHOST –xSERVICE
- Edit the shortcut to add the following:
-aSCALE\_<unique id from step 1> -g<gateway host> -x <gateway number>
- Note: make sure that -g is set the to correct SAP system and the –x is the correct gateway number. This will vary by SAP system.  Basis will provide these details. Figure-3 is an example.
- Create a shortcut for the WinWedge program
- Edit the shortcut to add the following: config.sw3
- Move the both shortcuts to the Startup folder so that they will execute on system start

![Batch file]({{ site.baseurl }}/assets/BATFile.png){: width="647px"}

### Step 5: R/3 configuration
In R/3, create an RFC destination in transaction SM59 with the following characteristics:

- Name: SCALE_<unique id from step 1>
- Type: T
- Description: Packaging Scale <unique id from step 1>
- Technical settings:
- Activation Type: Registered Server Program
- Program ID: SCALE_<unique id from step 1>

Reboot the PC and then test the connection from R/3 to ensure the Scale_for_R3 program is registering correctly.

Web page for the Express Shipping Solution for SAP >>  {{ site.xssHmPage }} <<
