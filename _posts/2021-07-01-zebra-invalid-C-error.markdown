---
layout: post
title: Zebra Printer / INVALID-C error message
categories: XSI update
---

*Symptom*

When printing a FedEx Air Waybill on a Zebra printer, the
message “INVALID-C” prints where a barcode is expected.

*Solution*
The “Invalid-C” message is created by the Zebra printer, not by
FedEx.
FedEx labels contain numerous barcode symbologies, including
PDF-417, GS1-128 and SSCC-18. The printer is not able to interpret
the specific barcode symbology being used to construct the AWB
label. Try updating the firmware on your Zebra printer. Here is a
link to the Zebra webpage for updating printer software -
[www.zebra.com/us/en/support-downloads/printers.html](https://www.zebra.com/us/en/support-downloads/printers.html).


Webpage for the Express Shipping Solution for SAP → [www.blueharbors.com/xss][xss].

For help implementing SAP with your parcel carriers, contact Blue Harbors Consulting → [info@blueharbors.com](mailto:info@blueharbors.com).

[xss]: https://www.blueharbors.com/xss
