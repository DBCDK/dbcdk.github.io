---
title OpenAgency
permalink: OpenAgency.html
---
# Description of the Open Agency service

## General description
Open Agency is a web service interface for looking up various parameters for
libraries and other service vendors in the VIP-database
([https://vip.dbc.dk](https://vip.dbc.dk)).
These include technical information such as encryption parameters, order
policies for use in ORS, Open Search profiles as well as practical information
about a library (contact information, opening hours).

Supported communication methods are SOAP, HTTP POST (XML-requests) and HTTP GET
(URL-requests). Supported output formats are SOAP and XML.

Available versions of the service and corresponding WSDL, XSD and sample
requests can be found below.

<span style="color:red">End-of-life date for versions older than 2.34 is October 1, 2018.</span>

## Versions

| Version | Environment | Endpoint                                           | WSDL | XSD |
|---------|-------------|----------------------------------------------------|------|-----|
| 2.34    | production  | http://openagency.addi.dk/2.34/                    | http://openagency.addi.dk/2.34/?wsdl | http://openagency.addi.dk/2.34/openagency.xsd |
| 2.34    | extern test | http://openagency.addi.dk/test_2.34/               | http://openagency.addi.dk/test_2.34/?wsdl | http://openagency.addi.dk/test_2.34/openagency.xsd |
| 2.34    | staging     | http://openagency.addi.dk/next_2.34/               | http://openagency.addi.dk/next_2.34/?wsdl | http://openagency.addi.dk/next_2.34/openagency.xsd |


## Service operations
***Automation***

This operation provides information about the agencies' preferences regarding
automatic forwarding of end user requests as ill requests to other agencies.
This operation is used by the Open Resource Sharing system.

***Encryption***

Operation for looking up encryption information related to a specific email
address, used when sending encrypted emails to an agency. This operation is used
by the Open Resource Sharing system.

***End User Order Policy***

This operation makes it possible to look up whether a specific agency wants to
recieve orders from endusers on this type of material. The operation is used by
the Open Order sevice.

***Find Library***

Operation for searching general contact information and alike about a given library

***Get CULR Profile***

Retrieve information about a library's CULR-profile

***Get Registry Info***

Provides contact information, server adresses and ILL-parameters for local registry updates

***Get SAOU License Info***

Retrieve information on how to to access remote content

***Name List***

This operation is for receiving a list of agency ids (ISIL numbers) and names of
either public libraries (Folkebibliotek) or university and research libraries
(Forskningsbibliotek).

***Open Search Profile***

This operation retrieves information about which data sources are included in a
given library's profile when the searching with Open Search.

***Pickup Agency List***

This operation can be used for retrieving a list of all public and/or research
libraries including contact information, pickup agency information and opening
hours.

***Remote Access***

Using this operation, you can get information about an agency's subscriptions to
licensed resources with remote access.

***Request order***

This operation retrieves a prioritised list of which agencies materials must be
ordered from for a given agency.

***Service***

The service operation looks up information about a specific agency regarding
various services provided by that agency. It can also look up directory
information about an agency. The following services are available (most of the
are used in ORS):

* information: directory information about an agency, e.g. address and branch information
* serverInformation: information about an agency's z39.50 server
* orsItemRequest: whether an agency wants to receive ILL requests and how they want to receive the messages
* orsAnswer: whether an agency wants to receive ILL answers and how they want to receive the messages
* orsReceipt: whether an agency wants to receive receipts on their ILL requests and how they want to receive the messages
* orsCancel: whether an agency wants to receive cancellations of ILL requests and how they want to receive the messages
* orsCancelReply: whether an agency wants to receive replies to cancellations of ILL requests and how they want to receive the messages
* orsShipping: whether an agency wants to receive shipping information and how they want to receive the messages
* orsRenew: whether an agency wants to receive renewals on ILL loans and how they want to receive the messages
* orsRenewAnswer: whether an agency wants to receive answers to renewals on ILL loans  and how they want to receive the messages
* orsEndUserRequest: whether an agency wants to receive requests from end users on their own material and how they want to receive the messages
* orsEndUserIllRequest: whether an agency wants to receive requests from end users on material owned by other agencies and how they want to receive the messages
* orsCancelRequestUser: whether an agency wants to receive cancellations of requests from end users and how they want to receive the messages
* orsRenewItemUser: whether an agency wants to receive renewals of loans from end users and how they want to receive the messages
* orsLookupUser: whether an agency wants to receive lookup user requests and how they wamt to receive the messages
* userOrderParameters: which order parameters must be present for local and ILL orders of various material types
* userParameters: what type of information is needed for authetication of the end user, e.g when the user wants to place an item request (cpr, common, barcode, cardno, or optional)

## License Terms
The web service is published under the [GPLv3](http://gplv3.fsf.org/) license.
