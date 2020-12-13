---
layout: post
title: SAP's Long-term Strategy for XSI (Express Shipping Interface)
date: 2019-06-01 02:03:24 +0100
categories: XSI update
---

Are you interested in using SAP to generate shipping labels and
perform parcel tracking with your favorite carriers? Do you like
the idea of having an integrated tracking solution that you can
call from SO, PO, delivery note and shipment documents? 

XSI is SAP's interface for integrating with parcel carriers. It is
standard functionality, available to use straight out of the box
in ECC as part of your existing SAP licencing. You may have found
information on the internet related to XSI telling you that
carriers like #UPS, #FedEx, #USPS and #DHL are no longer
supporting new implementations of SAP or that SAP is not longer
supporting XSI. This isn't true.

First of all, #SAP plans to support #XSI into the foreseeable
future and has even included it in current versions of their
software (S/4Hana, EWM, etc.). Other, non-XSI options are also
available - for example, SAP Event Manager or Transportation
Management on SCM also support parcel shipping. Depending on your
SAP landscape, SAP provides several approaches for integrating
with parcel carriers.

Secondly, every major #carrier on the planet now provides a Web
Service or API that you can call from SAP to generate #shipping
labels and get #tracking, costing and shipment related info back
into #DELIVERY and #SHIPMENT documents for easy access. Carriers
have been steadily increasing their investment in web based
shipping - improving infrastructure and offerings.

Note: SAP does not deliver any carrier specific
solution/coding/mapping. 
Integrating with the carriers via XSI requires a fair amount of
setup (configuration and coding). Each carrier website provides
detailed documentation for using their web services offering.
Basically, you create an XML request file, call a BAPI and send it
to UPS, DHL or FedEx, then you get an XML reply transaction into
SAP with your info. Then you read XML file into ABAP program and
update (XSI tables) VTRKH & VLBL via standard FM.

There is no shortage of SAP consulting companies out there that
can connect your SAP system to the carriers which you use. +Blue
Harbors Express Shipping Solution for SAP is a complete parcel
shipping solution built by an experienced and knowledgeable SAP
supply chain logistics consulting team. Learn more at
http://www.blueharbors.com/xss or contact them directly at
info@blueharbors.com.

![SAP Support for XSI](/images/helpDesk.jpg)

Webpage for the Express Shipping Solution for SAP → [www.blueharbors.com/xss][xss].

For help implementing SAP with your parcel carriers, contact Blue Harbors Consulting → [info@blueharbors.com](mailto:info@blueharbors.com).

[xss]: https://www.blueharbors.com/xss
