---
layout: post
title: Carrier of the Week - FedEx
date: 2019-06-01 04:03:24 +0100
categories: XSI update
---

Few carriers have invested as heavily in their Web Services
infrastructure as +FedEx. A vast collection of their shipping
functions can be accessed via XML, growing year over year. All the
integration details are clearly captured in the FedEx Web Services
Developer Guide. I will just provide a high-level summary of the
offering here, so consult the Developer Guide for more
information.

![FedEx logo](/images/FedExLogo.jpg){: width="300px"}

## Resources

- FedEx Developer Resource Center: http://fedex.com/developer
- FedEx Services At-a-Glance: http://fedex.com/us/services
- FedEx Service Guide available at http://fedex.com/us/service-guide
- World Wide Web Consortium XML: http://w3.org/XML/
- World Wide Web Consortium XML Schema: http://w3.org/XML/Schema
- Microsoft Web Services: http://msdn.microsoft.com/en-us/library/ms950421.aspx
- O’Reilly XML.com: http://xml.com
- Secure Socket Layer Certificates: http://fedex.com/us/developer/downloads/dev_cert.zip
- Web Services organization home page: http://w3.org/2000/xp/Group/

## Support

- Contact FedEx Web Services technical support at websupport@fedex.com.
- Regional contact email addresses are:
  - For Europe - emeawebservices@fedex.com
  - For Indian Subcontinent, Middle East and Africa - meisawebservices@fedex.com
  - For Asia Pacific - apacwebservices@fedex.com
- For technical support, call 1.877.339.2774 and state “API” at the voice prompt.
- Support hours are Monday through Friday, 7:00 a.m. to 9:00 p.m.  CST, and Saturday, 9:00 a.m. to 3:00 p.m. CST.
- For FedEx Customer Service, call 1.800.GoFedEx 1.800.463.3339.
- Customers using a FedEx Compatible Solutions Program automation solution should contact their software provider for support.

## Functionality

### Address Validation Service

Use the Address Validation Service
(AVS) to validate or complete recipient addresses. Correct
addresses on the shipping label will help eliminate delivery
delays and additional service fees. Do not use this service to
determine the deliver-ability of an address. FedEx does not offer
delivery service to every valid address. However, FedEx does not
deliver to PO Boxes (except via SmartPost). Address resolution
results vary by country.

### Close Service Shipment

The Close Service WSDL allows you to
reconcile shipping information for your FedEx Ground or FedEx
SmartPost shipments and print a ground manifest for your ground
driver. The ground manifest is generated after a successful close
and must be printed before your ground shipments are tendered to
FedEx. You may continue to ship ground packages after a close has
been performed. The Close is optional but recommended. It is only
required if you need any of the generated reports. FedEx Express
shipments are automatically closed and do not require a specific
close operation. Close by Reference allows you to identify those,
and only those, packages that are finalized, and upload that
specific package data to FedEx. This is accomplished by closing
the corresponding FedEx Ground (US domestic and international) or
SmartPost shipment via one of the customer reference fields.

### Consolidation Services

FedEx offers consolidation services for
shippers who want to consolidate their FedEx Express and Ground
international shipments for customs clearance at a single entry
and then, within the destination country, break the shipment down
into smaller components to distribute to individual recipients.
FedEx International DirectDistribution Surface Solutions (IDD
Surface) lets you streamline large shipments from Canada and
Mexico for distribution in the U.S. FedEx Consolidation services
are specific to Canadian shipments and allows qualified U.S.
shippers to consolidate FedEx Ground shipments for distribution
within Canada by either FedEx Trade Networks or a broker of your
choice. The shipment clears Canadian customs as a single shipment
and is broken down into smaller shipments once inside Canada.
After your shipment clears customs you will receive access to the
full range of FedEx services.

### Country Service

Country Service enables customers to validate
postal codes and service commitments. Supports city, postal,
country and Origin-Destination related lookups and validations.
Also returns postal and location details in the
ValidatePostalReply.

### Create a Label

FedEx Web Services supports a variety of label
options, including thermal, plain paper, and customizable labels.
With FedEx Web Services, you can use the Ship Service and OpenShip
Service to produce a wide variety of labels. In this section, you
will find instructions for generating the labels you need to
support your shipping application.
FedEx offers 2 label formats to support shipping services: (1)
Thermal Labels and (2) Laser Labels

### Dangerous Goods and HazMat

Shipments with dangerous goods must
be tendered to FedEx Express® in accordance with current
International Air Transport Association (IATA) regulations for air
transport and the FedEx Express Terms and Conditions. FedEx
provides the option to upload your Dangerous Goods or Hazardous
Materials information to FedEx before processing DG or Hazmat
shipments.

### FedEx DG Ready & Dangerous Good Data Service

FedEx DG Ready is
an optional program that gives dangerous goods (DG) and hazardous
materials (hazmat) shippers added confidence that DG or hazmat
shipments are ready to offer to FedEx Express, FedEx Ground, or
FedEx Freight. The program works with 3rd party FedEx DG Ready
software solutions capable of transmitting DG declaration or
hazmat shipping paper data to FedEx Dangerous Goods Data Service
(DGDS). DGDS is the FedEx system created to receive Dangerous
Goods declaration or Hazmat shipping paper data from shippers
using a FedEx DG Ready solution or proprietary software system and
publish uploaded DG data to FedEx operational systems. After
receiving the uploaded DG data, the service returns a FedEx
tracking number if the data is accepted or returns an error if
data is incomplete or does not comply with regulations, FedEx
operator variations, or FedEx customer account authorizations.

### Electronic Trade Documents

FedEx Electronic Trade Documents
(ETD) is an international shipping solution that simplifies your
international shipping needs. You can submit most of your trade
documentation electronically and no longer have to print and
attach trade documents. Capturing and sharing critical trade
information as early as possible optimizes the customs clearance
process. Customs and other agencies receive documents sent
electronically faster than paper copies. You have two choices for
using FedEx Electronic Trade Documents. You can either upload your
own documents or let FedEx generate them for you. See Shipping
Document Service section for details on documents that FedEx can
generate).

### Estimated Duties and Taxes (Express and Ground)

FedEx
Estimated Duties and Taxes allows you to request a complete
international shipping rate quote for FedEx Express® and FedEx
Ground International shipping rate, including applicable duties
and taxes. The Estimated Duties and Taxes feature supports the
shipping of any product that is classified under the Harmonized
Tariff Code and is shipped to or from supported countries. To sign
up for FedEx Estimated Duties and Taxes, contact your FedEx
account executive.

### FedEx Express U.S. Shipping

Use the Shipping service to access
the FedEx Express U.S. shipping features.

### FedEx Express Freight Services - U.S.

FedEx Express Freight
Services is used when for packages that exceed 150 lbs. The
freight must be shrink-wrapped and/or banded to a skid. It must be
palletized, stackable, and forkliftable.

### FedEx Freight Services

One streamlined network, FedEx
Freight®, offers you two easy service options: FedEx Freight
Priority (formerly FedEx Freight) for speed, and FedEx Freight
Economy (formerly FedEx National LTL) for savings. The change in
services allows FedEx to offer you two levels of service, priority
or economy freight, in one fully integrated, nationwide pickup and
delivery network.

### FedEx Ground U.S. Shipping

Use the Shipping service to access
the FedEx Ground U.S. shipping features.

### FedEx Intra-Country Shipping

Use this Shipping service to ship
domestically within specific countries (supported countries are
listed in the FedEx Web Services Developer Guide).

### FedEx SmartPost Shipping

FedEx SmartPost and FedEx SmartPost
Returns each require a service contract. To sign up for FedEx
SmartPost outbound shipping or FedEx SmartPost Returns, contact
your FedEx account executive. FedEx SmartPost helps you
consolidate and deliver high volumes of low-weight, non
time-critical business-to-consumer packages using the United
States Postal Service (USPS) for final delivery to residences.
This service provides delivery Monday through Saturday to all
residential addresses in the U.S., including P.O. boxes and
military APO and FPO destinations. FedEx SmartPost also offers
FedEx SmartPost Returns service, delivery and shipment email
notifications for U.S. outbound shipments, customizable labels,
and Future Day shipping.

### In-Flight Shipment Service

In-Flight Shipment Service provides
the capability to request a redirect to hold for an in-flight
package. The redirect to hold capability is supported via Web
Services for U.S. destination FedEx Express and Ground packages -
all origins (to a U.S. destination) are supported.

### International Shipping

FedEx Web Services offers FedEx Express
international shipping from anywhere-to-anywhere, which means that
you can create shipping transactions both to and from any
prescribed country whose service is supported by FedEx.

### Locations Service

The Locations Service WSDL searches for, and
returns, the addresses of the nearest FedEx package drop-off
locations, including FedEx Office Print and Ship Center, Drop Box
and Ship and Get Locker locations. Use the Locations Service WSDL
to request FedEx locations available for FedEx Express and FedEx
Ground package drop-off. This transaction searches for and returns
the addresses of the nearest FedEx location. You can also use the
Locations service to find FedEx locations that provide Hold at
Location service.

### Open Shipping

Open Shipping is a highly flexible feature that
allows you to create and enter information for a shipment as it is
received throughout the day, rather than entering all of the
shipping information only when the shipment is ready to be
processed. The shipment remains “open” for a five-day period and
accepts package additions, deletions or edits during that time. At
the end of five days, the shipment must be confirmed or it will be
purged. Open Ship shipments are often multiple-piece shipments but
can also be shipments that contain single packages, referred to as
single-piece shipments.

### Pickup Service

The Pickup Service WSDL allows you to schedule
a courier to pick up a shipment, cancel a pickup request, or check
for pickup availability. Use the Pickup Service to schedule
courier pickup of a shipment at the location specified in the
transaction.

### Rate Services

Use the RateService WSDL to request pre-ship
rating information and to determine estimated or courtesy billing
quotes. Time in Transit can be returned with the rates if it is
specified in the request.

### Returns Shipping

Returns are available for intra-country and
international shipping in a variety of areas wherever existing
FedEx Express and FedEx Ground services are available. You can
associate or "link" an outbound shipment with a return shipment
using the tracking numbers. When processing your global return
package with FedEx automation, you'll need to provide a reason for
that return for customs clearance purposes, on both the outbound
and return shipments, when processing your package.

### Special Services also supported by FedEx Web Services

- Alcohol Shipping
- Delivery Signature Options
- FedEx Priority Alert Options
- Saturday Service
- FedEx Express Collect on Delivery (C.O.D.)
- FedEx Ground U.S. Collect On Delivery (C.O.D.)
- Ground E.C.O.D.
- Hold at Location
- Shipping Document Service
- Upload Images

### Tracking and Visibility Services

The TrackService WSDL
provides several services to actively track your shipments.

- Tracking Service > Use the TrackService WSDL to obtain
real-time tracking information for FedEx Express, FedEx Ground,
FedEx SmartPost, FedEx Home Delivery, FedEx Express Freight, FedEx
Freight and FedEx Custom Critical shipments.

- Signature Proof of Delivery (SPOD) › Use FedEx SPOD to request
a proof of delivery letter or Fax that includes a graphic image of
your recipient’s signature after your shipment has been delivered.

- Notification › Use Notification to have FedEx automatically
notify you and/or your customer and/or another third party by
email of significant shipment events, such as clearance delays,
delivery attempts, releases, and pre-alerts. FedEx offers a new
email notification of Tendered, which may be specified with the
shipment request, in addition to the existing Delivery, Exception,
and Shipment email notifications. Use the Tendered email
notification if you want an email notification sent to the
specified recipients once the shipment has been tendered to FedEx.
This notification is supported for FedEx Express, FedEx Ground,
FedEx Freight® Economy, and FedEx SmartPost®. FedEx also offers a
new email notification for Estimated Delivery which triggers an
email on the delivery date.

- FedEx InSight › FedEx InSight is a web-based application that
enables you to view the status of your inbound, outbound, and
third-party shipments without a tracking number. All you need is
your account number and/or company name and address. You can see
information about the status of your shipments so you can more
effectively manage your supply-chain processes. FedEx InSight also
notifies you by email or fax of significant shipment events, such
as clearance delays, delivery attempts, releases, consolidated
proof of delivery, and delivery pre-alerts. For more information
regarding FedEx InSight, go to fedex.com/insight.

### Validation Availability And Commitment Service

Check service availability, route and postal codes of your shipment.



Webpage for the Express Shipping Solution for SAP → [www.blueharbors.com/xss][xss].

For help implementing SAP with your parcel carriers, contact Blue Harbors Consulting → [info@blueharbors.com](mailto:info@blueharbors.com).

[xss]: https://www.blueharbors.com/xss
