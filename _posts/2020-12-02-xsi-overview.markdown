---
layout: post
title: Overview of SAP XSI
categories: parcel-shipping
---

## Overview of the SAP Express Shipping Interface (XSI)

The Express Shipping Interface comes standard in SAP ECC, and is
available in R/3 and S/4Hana. It resides within the shipping
(LE-SHP) module. This function enables you to map the particular
requirements of express delivery companies (UPS, FedEx, DHL,
USPS, Purolator, etc.) with regards to shipping.

These requirements affect the following three components:

- Label printing (address stickers, labels)
- EDI and day-end closing (manifest, delivery list, or end-of-day
list)
- Parcel tracking

The following options are available after correctly implementing
the Express Shipping Interface:

- Printing labels for specific express delivery companies,
including the special data fields often used without third-party
systems
- Transferring data for specific express delivery companies, using
standard IDocs and XML to the express delivery company (or a
converter)
- Using quotations from express delivery companies or parcel
tracking from the SAP system

## Note
Implementation of the interface for each express delivery company,
including creating forms, is not part of the SAP standard system.
It is recommend implementing the interface as part of a customer
project, in collaboration with, for example, Blue Harbors
Consulting (see [www.blueharbors.com/xss](https://www.blueharbors.com/xss) for more
information about the Express Shipping Solution)

## Integration
You connect express delivery companies at delivery (inbound or
outbound) document or shipment document level in the SAP system.

The express delivery functions are controlled using the Forwarding
Agent partner. This means that as soon as a forwarding agent is
assigned to the delivery or shipment, where the forwarding agent
has been flagged in Customizing as relevant for express delivery,
and the delivery or shipment is saved, the system works in the
background to determine data and update any fields relevant for
express delivery.

This data is then available when you print labels or communicate
via EDI or XML.

Once the parcel has been sent, you can start parcel tracking
either from the standard delivery and shipment transactions
(VL02N, VL03N, or VT02N/VT03N), or using a separate transaction
(VTRK).

## Prerequisites
To be able to ship parcels with express delivery companies using
the SAP system in the three components (label printing, EDI, and
parcel tracking), the following three prerequisites must be
fulfilled:

- The express delivery company has been created as a standard
creditor in the system, and can be assigned to the delivery or
shipment (depending on the process you require) as a forwarding
agent

- The express delivery company has been created and is active
(there is a specific Customizing transaction for this) (see also:
Creating an Express Delivery Company).

- You have set up label/form printing (usually this is covered by
standard message determination and message processing using print
programs and SAP forms)

- You have set up the IDoc interface for the service agent partner
(see also: Setting Up Labels for Express Delivery Companies). If
the express delivery company does not want to accept the data
directly in the form of a standard SAP IDoc (type SHPMNT or
DELVRY), either you must write your own converter for these IDocs
within customer projects, or you use workarounds within the print
programs. To do this, you need to create Z database tables whose
contents are then read and transferred as a flat file to the
service agent.

## Features
The interface for express delivery companies is available using
the standard functions of deliveries or shipments, and offers you
the following extended functions:

- You can connect several express delivery companies in parallel,
and can control them using the selection of forwarding agents in
the delivery or shipment.

- For each express delivery company you can define fields (as many
as you wish), also called metadata, then populate and save the
fields using the following options:
  - Standard function modules
  - Function modules you have written
  - Fixed values
  - Compositions of other metadata
  - Number ranges
  - Manual entries within the delivery/shipment transaction, without modifications  

- Value determination for these placeholders takes place
automatically when you save a delivery or shipment that is
relevant for the express delivery company according to the
settings.

- The values determined are available for printing (print
structure VTRK_D2) and for the IDocs SHPMNT and DELVRY in order to
transfer them to the service agent.

- There is an XML RFC interface available for both automatic
uploads of express delivery company-specific master data (such as
current route tables) and for implementing initial Customizing
settings (for example, all placeholders including the
determination method). Usage of this interface is dependent on
whether the service agent supports it. However, you can set up the
connection for a service agent entirely manually, without using
XML/RFC functions. To do this, you need to load master data, such
as route tables, into the SAP system using a report.

- Parcel tracking
  - If the express delivery company offers a Web site for parcel
tracking, you can navigate directly from the delivery or shipment
to the parcel tracking pages using either a Web browser or the
SAP HTML Viewer, as long as the above placeholder for determining
a unique tracking number (also called a bill of lading or parcel
number) is defined according to the company’s conditions.

  - There is also an XML/RFC interface that you can use to load
tracking data directly from the service agent into the SAP system,
as long as the service agent supports the interface. The parcel
tracking data that you implement in this way enables you to
perform evaluations of the express delivery company’s performance,
and of the implementation of workflows (for example, notification
of employees when deliveries are delayed/lost). These evaluations
or workflows must also be implemented within customer projects.


This post is a summary of SAP support documenation, focusing on
key highlights. The link to the origional SAP documention is
[SAP help page](https://help.sap.com/saphelp_globext607_10/helpdata/en/e5/29a5b512b511d3b481006094b9b9dd/frameset.htm).

![SAP Help page]({{ site.baseurl }}/assets/SAPHelpPage.png)

Webpage for the Express Shipping Solution for SAP → [www.blueharbors.com/xss][xss].

For help implementing SAP with your parcel carriers, contact Blue Harbors Consulting → [info@blueharbors.com](mailto:info@blueharbors.com).

[xss]: https://www.blueharbors.com/xss
