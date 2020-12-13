---
layout: post
title: OSS Note 366914 - XSI Activation and Configuration
date: 2019-05-31 02:03:24 +0100
categories: XSI update
---

## Highlights from SAP OSS note 366914

This note provides an excellent overview of XSI and includes
information about activation, configuration of the Express
Shipping Interface.

This document address the following topics:
- How is XSI activated?
- What is 'meta data' configuration?
- What does "load all master data" do?
- Description of the RFC destinations in the cockpit
- What are the capabilities/limitations of the Express Shipping
  Interface?
- The Business Connector (BC) is out of maintenance. What is the
  further strategy regarding XSI?

Other Terms: XSI, VTRC, Express Shipping Interface, parcel
carrier, cockpit configuration.

General remarks:
XSI should be configured and activated at the shipping / handling
unit level. This is done by specifying a document category of 'X'
(shipping unit) and a higher level document category of 'J'
(Delivery note) for each meta data tag (more details to follow).
It is also possible to have the data determination based on the
Shipment Document (document category '8') and its related/assigned
Handling Units (document category 'X'). The Shipment Document is
also an option to enable a "Manifest" (also known as
"end-of-day-file"). This means that all relevant deliveries with
assigned Handling Units could be put into one Shipment Document
per day. Then either a carrier-specific EDI-File can be generated
via standard output-control or the standard Shipment Idocs (e.g.
SHPMNT05) can be utilized for mapping into a carrier-specific
format (e.g by use of XI). The mentioned options have to be
enabled via implementation projects.

_Q: How is XSI Activated?_  
A: To begin, a configuration must be maintained via transaction
VTRC. Select 'Create express delivery company' from the menu
'Express Delivery Company'. Any identifier may be specified here;
however each carrier may have a specific XSI carrier name that
must be specified in the cockpit configuration.

Before proceeding, identify or create a vendor that has partner
type 'Forwarding agent'.

Mandatory: Assign the vendor to the XSI carrier by clicking the
'Assign service agent' pushbutton on the 'Exp. dlv. cmpny control'
tab. This establishes the link between the XSI configuration and
the SAP application document/object. (Remark: please consider the
field "Export indicator". If an express delivery company shall
handle domestic as well as international shipments, two records in
this customizing table are necessary. One with "Export indicator"
= true and a second line with "Export indicator" = false. The
check is done against the delivery-documents export indicator -
LIKP-EXPKZ.)

Optional: Next, specify the shipper's account number in the
'Account w/ExpDlvCo' field. This account number is part of the set
of indentifiers sent to the carrier in each transmission. Remark:
as mentioned also in the F1-help for this field, the account
number can be also determined via an own (Z-) Function Module with
a more sophisticated logic!

Mandatory: Choose 'Goto->Global Settings->Activate Globally',
enter an 'X' in the 'ExpDelivCmpnyActive', then click 'Save'

Mandatory: Make a 'meta data' configuration for at least one meta
data on delivery document (higher level document category of 'J')
or on shipment-document (higher level document category of '8')
level.

_Q: What is 'meta data' configuration?_  
A: Meta data is a collection of tag symbols and associated
attributes that control the determination of a tag's value. These
tags are used as placeholders to create data determination
"formulas", for example, the tag sequence used for generating
tracking numbers locally. Meta data tags have value
re-determination criteria, print and message output controls and
the ability to determine a tag's value locally or remotely via
RFC/RFC-XML (not recommended due to performance reasons!).

Tags can be assigned default values, a number range object
interval, an ABAP field reference, other meta data tags or be
determined via a function call (these can be any function modules
with an interface like that of 'XSI_GET_CARRIER_ROUTING').

Meta data tags are also used in the URL templates for browser
based tracking. If required, meta data tags can be defined to
ensure unique values for a shipping point. This feature useful if,
for example, a parcel carrier assigns unique number ranges to a
shipper for each shipping location.

Meta data tags have two attributes which controls the application
object for which meta data will be determined and (tracking
control) entries will be created for: Document Category and Higher
Level Doc. Category. The valid values are: 'X' - Handling unit;
'J' - Delivery note; '8' - Shipment; '7' - Shipping notification.

For example, if the meta tag is set (often important: TRACKN) to
"doc. cat. 'X'", "higher level cat. 'J'", that will cause XSI to
determine data and create tracking control entries for Handling
Units on a delivery note (recommended configuration).

At a minimum, there are two meta data tags that should always be
defined: TRACKN and SHIPACCT. The value determination sequence,
etc. differs between carriers.

Please note, meta data configuration is a key element in
generating XSI tracking headers within ERP. Without these tracking
control headers, XSI functionality for the delivery, shipment,
etc. will not be active, even if a service agent that references
an active XSI carrier is specified on delivery, etc. The
configuration can be done completely manually. An automatic setup
as described subsequently is just an assistance if available!

_Q: What does "load all master data" do?_  
A: "Load all master data" provides the ability to download and
save a cockpit configuration for a specific parcel carrier,
directly from the carrier's system. This button becomes active
when the cockpit is switched into the "non-SAP System" view by
clicking the "non-SAP System" pushbutton. This also provides the
ability to copy an existing configuration via an RFC link to
another SAP system. Please note, that there is currently no
carrier who provides a full-blown automatic setup. As of now, all
known active setups where done manually and usually by help of
consultants. (Contact Blue Harbors Consulting at
info@blueharbors.com for help with the setup.)

Description of the RFC Destinations and used RFCs in the Cockpit
- In the "header" area of the cockpit (next to the field Account
  w/ExpDlvCo.):
Remote Function Call (RFC) destination that targets a system that
supports Cockpit configuration download (see above "load all
master data").

Technically, the following RFCs are involved for this
download-option:
> BAPI_CAR_PRVD_META
> BAPI_CAR_PRVD_NUMBER_RANGE
> BAPI_CAR_PRVD_PRDCD
> BAPI_CAR_PRVD_ROUTING
> BAPI_CAR_PRVD_SRVC_CD
> BAPI_CAR_PRVD_TRKS - BAPI_CAR_PRVD_URL
The configurations supported or required differs from carrier to
carrier. This destination can target a SAP system, providing the
ability to copy an existing configuration.

- On the Exp. Dlv. Cmpny Control tab under the "XML Tracking"
  frame: RFC destination that targets a system that supports the
XSI BAPI 'BAPI_CAR_PRVD_TRACK_STATUS'.

- On the Exp. Dlv. Cmpny Control tab under the "Data
  determination" frame: RFC destination that targets the receiver
of the XSI BAPI 'BAPI_CAR_PRVD_LABEL_DATA'.

_Q: What are the capabilities/limitations of the Express Shipping Interface?_  
A:
1. Please note, that the XSI provides useful features and
	 functionalities INDEPENDENT FROM any existing certifications.
As mentioned above, necessary settings/customizing for a
parcel-shipping-specific data determination including label
printing etc. can be done manually. The only issue is, that SAP
can't roll out carrier-specific pre-settings. The carrier- and
customer-specific settings have to be done via implementation
projects. (Contact Blue Harbors Consulting at info@blueharbors.com
for help with the setup.)

2. Nevertheless, the Express Shipping Interface has certifiable
	 interfaces for:
- Automatic configuration and setup (7 possible BAPIs)
- Links/containers for carrier provided HTML documentation
- Parcel tracking via BAPI call (1 BAPI)
- Browser based parcel tracking (URL 'template' based)

3. Label Printing Labels produced from XSI need to be certified by
	 each parcel carrier for completeness, format or print
tolerances individually. As mentioned, SAP does not roll out any
pre-certified, carrier-specific forms and implementations. But it
is generally possible to fullfill the requirements of many
well-known parcel carriers by use of the XSI resp. ERP features.
(In most cases, XSI can be set up to generate the requested labels
and the end-of-day processing without additional 3rd party
software. It can be also feasible to use XSI only partially e.g.
as a "router" or "link" to a carrier-specific 3rd party software -
means labels are printed by external piece of software whereas XSI
is only prepared to hold a tracking number in its related
database-tables for the later parcel tracking.)

Current configuration and demo-printing program R_XSI_LABEL_PRINT
provides support for only a single device type and label format.
The demo R_XSI_LABEL_PRINT does also not support determining label
type/format per service level (most parcel carriers use different
labels formats for different types of shipments). But these
features can be implemented relatively easy by modifying the
R_XSI_LABEL_PRINT-pattern to the customer-specific needs and by
utilizing the standard output-control features on Handling Unit
level (printer determination etc.).

4. Miscellaneous/General
No pre-configuration for service level or address validation.
(Contact Blue Harbors Consulting at info@blueharbors.com for help
with the setup.)

No pre-configuration for retrieving shipment cost, transit time.
On the other hand, the flexible data-determination (see
'meta-data' configuration above) allows to latch any own function
module to enable these kind of requirements as long as the parcel
carrier is able and willing to provide the necessary data sources.
(Contact Blue Harbors Consulting at info@blueharbors.com for help
with the setup.)

_Q: The Business Connector (BC) is out of maintenance. How is the further strategy regarding XSI?_  
A: The SAP Business Connector is no longer part of the modern
XSI-based shipping solution. BC is not used to integrate your SAP
system with your parcel carriers; instead ECC communicates
directly with carriers via web services / APIs.



![OSS Note 366914](/images/OSSNote366914.png)

Webpage for the Express Shipping Solution for SAP → [www.blueharbors.com/xss][xss].

For help implementing SAP with your parcel carriers, contact Blue Harbors Consulting → [info@blueharbors.com](mailto:info@blueharbors.com).

[xss]: https://www.blueharbors.com/xss
