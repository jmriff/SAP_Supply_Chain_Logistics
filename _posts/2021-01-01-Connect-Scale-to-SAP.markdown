---
layout: post
title: How to connect a weighing scale to SAP
categories: parcel-shipping
---

# TOP TIP - How to connect a weighing scale to SAP

## Abstract
This post explains how to use the Setup_scale.exe program
(provided by SAP) to create registry entries on a Widows PC that
are accessed via RFC from #SAP. It also covers the setup procedure
for #WinWedge so that it can interpret the data stream coming from
a #scale. For each weigh scale/packing station, perform the
following:

## Procedure

### Step 1: Software installation
- assign the packing station a unique number (in our example here, we used NCI by +Avery Weigh-Tronix; +METTLER TOLEDO also makes excellent scales)
- connect the scale to COM1 of the packing station PC
- install WinWedge Std from +TALtech Technologies (www.taltech.com)
- create a WinWedge configuration file that interprets the
  data stream coming from the scale

### Step 2: Software configuration
Run scale_for_r3.exe program. This will create an entry in the Windows registration for NCI:

- make an entry in the Name der Waage im R/3 field: NCI
- press the first button from the top on the right hand side
- change the entry in the (LinkVal) field to field(1)
- change the entry in the (LinkUnit) field to field(2)
- make an entry in the (LinkScaleId) field: [Sendout(’W’,.13)]
- press the orange button on the bottom right hand side

![Scale_for_R3.exe](/images/scaleForR3.png){: width="647px"}

### Step 3: Registry check
- check your registry details by going the Run prompt and typing REGEDIT
- select OK
- select the following menu path: HKEY_CURRENT_USERS → Software → VB and VBA Program Settings
- you should see that node ’HUDDEDRV’ is created. Within this a node with the name of the scale SCALENAME (Note: This name has to be the same as entered in the packing station profile)
- confirm that the entries for your scale match the entries in this figure

![Windows registry entries for scale](/images/registryEntries.png){: width="647px"}

### Step 4: Shortcuts
Create a shortcut to Scale_for_R3.exe.

- The ’Scale\_for\_R3.exe’ program must exist on the PC. Do not start the program directly, instead use a batch-file with the following contents: scale_for_r3.exe -aSCALE_AT_PACKINGSTATIONXX -gHOST –xSERVICE
- Edit the shortcut to add the following:
-aSCALE\_<unique id from step 1> -g<gateway host> -x <gateway number>
- Note: make sure that -g is set the to correct SAP system and the –x is the correct gateway number. This will vary by SAP system.  Basis will provide these details. Figure-3 is an example.
- Create a shortcut for the WinWedge program
- Edit the shortcut to add the following: config.sw3
- Move the both shortcuts to the Startup folder so that they will execute on system start

![Batch file](/images/BATFile.png){: width="647px"}

### Step 5: R/3 configuration
In R/3, create an RFC destination in transaction SM59 with the following characteristics:

- Name: SCALE_<unique id from step 1>
- Type: T
- Description: Packaging Scale <unique id from step 1>
- Technical settngs:
- Activation Type: Registered Server Program
- Program ID: SCALE_<unique id from step 1>

Reboot the PC and then test the connection from R/3 to ensure the Scale_for_R3 program is registering correctly.

Webpage for the Express Shipping Solution for SAP → http://www.blueharbors.com/xss  
For help implementing SAP with your parcel #carriers, contact Blue Harbors Consulting → info@blueharbors.com
