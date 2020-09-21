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

Available versions of the service and corresponding WSDL, XSD and sample
requests can be found below.

OpenAgency 3.0 is considered the primary production version as per. October 1, 2020.

<span style="color:red">End-of-life date for versions older than 3.0 is January 1, 2021.</span>

## Versions

| Version | Environment | Endpoint | WSDL | XSD |
|---------|-------------|----------|------|-----|
| 2.34    | production  | [http://openagency.addi.dk/2.34/](http://openagency.addi.dk/2.34/) | [http://openagency.addi.dk/2.34/?wsdl](http://openagency.addi.dk/2.34/?wsdl) | [http://openagency.addi.dk/2.34/openagency.xsd](http://openagency.addi.dk/2.34/openagency.xsd) |
| 2.34    | extern test | [http://openagency.addi.dk/test_2.34/](http://openagency.addi.dk/test_2.34/) | [http://openagency.addi.dk/test_2.34/?wsdl](http://openagency.addi.dk/test_2.34/?wsdl) | [http://openagency.addi.dk/test_2.34/openagency.xsd](http://openagency.addi.dk/test_2.34/openagency.xsd) |
| 2.34    | staging     | [http://openagency.addi.dk/next_2.34/](http://openagency.addi.dk/next_2.34/) | [http://openagency.addi.dk/next_2.34/?wsdl](http://openagency.addi.dk/next_2.34/?wsdl) | [http://openagency.addi.dk/next_2.34/openagency.xsd](http://openagency.addi.dk/next_2.34/openagency.xsd) |
| 3.0    | production  | [http://openagency.addi.dk/3.0/](http://openagency.addi.dk/3.0/) | [http://openagency.addi.dk/3.0/soap?wsdl](http://openagency.addi.dk/3.0/soap?wsdl) | [http://openagency.addi.dk/3.0/soap?xsd=1](http://openagency.addi.dk/3.0/soap?xsd=1) |
| 3.0    | extern test | [http://openagency.test.addi.dk/3.0/](http://openagency.test.addi.dk/3.0/) | [http://openagency.test.addi.dk/3.0/soap?wsdl](http://openagency.test.addi.dk/3.0/soap?wsdl) | [http://openagency.test.addi.dk/3.0/soap?xsd=1](http://openagency.test.addi.dk/3.0/soap?xsd=1) |
| 3.0    | staging     | [http://openagency.stg.addi.dk/3.0/](http://openagency.stg.addi.dk/3.0/) | [http://openagency.stg.addi.dk/3.0/soap?wsdl](http://openagency.stg.addi.dk/3.0/soap?wsdl) | [http://openagency.stg.addi.dk/3.0/soap?xsd=1](http://openagency.stg.addi.dk/3.0/soap?xsd=1) |

## 3.0 and 2.34 differences

Since the introduction of version 3.0 a number of changes has been made.

### 2.34:
* Can accept requests in XML (SOAP) and as URL parameters (URL parameter example: http://openagency.addi.dk/2.34/?action=endUserOrderPolicy&agencyId=725300&orderMaterialType=monograph&ownedByAgency=false&outputType=xml)
* Can return answers in XML (SOAP) and JSON (badgerfish variant)

### 3.0:
* Will only accept XML (SOAP) requests
* Will only return XML (SOAP) answers 
* Removed the following elements from the XSD:
  * Callback
  * OutputType
  * Search via coordinates in FindLibrary

## Service operations
***Automation***

This operation provides information about the agencies' preferences regarding
automatic forwarding of end user requests as ill requests to other agencies.
This operation is used by the Open Resource Sharing system.

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* autService: autPotential, autRequester or autProvider
* materialType: integer
* trackingId

***Encryption***

Operation for looking up encryption information related to a specific email
address, used when sending encrypted emails to an agency. This operation is used
by the Open Resource Sharing system.

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* email: make a guess
* trackingId

***End User Order Policy***

This operation makes it possible to look up whether a specific agency wants to
recieve orders from endusers on this type of material. The operation is used by
the Open Order sevice.

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* orderMaterialType: one of: cdrom, journal, monograph, music, newspaper, video
* ownedByAgency: true or false
* trackingId

***Find Library***

Operation for searching general contact information and alike about a given library

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* agencyAddress: library address
* agencyName: library name
* postalCode: 
* city:
* stilNumber:
* anyField:
* libraryType: Folkebibliotek, Forskningsbibliotek, Skolebibliotek or empty
* libraryStatus: include libraries: alle, usynlig, slettet or empty
* pickupAllowed: Indicator whether materials can be picked up at the given branch/agency
* sort: agencyId, agencyName, agencyAddress, postalCode, city, libraryType
* trackingId

***Get CULR Profile***

Retrieve information about a library's CULR-profile

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* profileName: Name of profile to fetch
* requesterIp: IP of requester
* trackingId

***Get Registry Info***

Provides contact information, server adresses and ILL-parameters for local registry updates

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* agencyName: library name
* lastUpdated: date
* libraryType: Folkebibliotek, Forskningsbibliotek or empty
* libraryStatus: include libraries: alle, usynlig, slettet or empty
* trackingId

***Get SAOU License Info***

Retrieve information on how to to access remote content

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* trackingId

***Library Rules***

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* trackingId

***Library Type List***

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* trackingId

***Name List***

This operation is for receiving a list of agency ids (ISIL numbers) and names of
either public libraries (Folkebibliotek) or university and research libraries
(Forskningsbibliotek).

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* libraryType: Folkebibliotek, Forskningsbibliotek or empty
* trackingId

***Open Search Profile***

This operation retrieves information about which data sources are included in a
given library's profile when the searching with Open Search.

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* profileName: Name of profile to fetch
* profileVersion: 2 or 3
* trackingId

***Pickup Agency List***

This operation can be used for retrieving a list of all public and/or research
libraries including contact information, pickup agency information and opening
hours.

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* agencyAddress: library address
* agencyName: library name
* postalCode:
* city:
* libraryType: Folkebibliotek, Forskningsbibliotek or empty
* libraryStatus: include libraries: alle, usynlig, slettet or empty
* pickupAllowed: Indicator whether materials can be picked up at the given branch/agency
* trackingId

***Remote Access***

Using this operation, you can get information about an agency's subscriptions to
licensed resources with remote access.

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* trackingId

***Request order***

This operation retrieves a prioritised list of which agencies materials must be
ordered from for a given agency.

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* trackingId

***Search Collection***

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* trackingId

***Service***

The service operation looks up information about a specific agency regarding
various services provided by that agency. It can also look up directory
information about an agency. The following services are available (most of them
are used in ORS):

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* service: 
  * information: directory information about an agency, e.g. address and branch information
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
  * serverInformation: information about an agency's z39.50 server
  * userOrderParameters: which order parameters must be present for local and ILL orders of various material types
  * userParameters: what type of information is needed for authetication of the end user, e.g when the user wants to place an item request (cpr, common, barcode, cardno, or optional)
* trackingId

***Show Order***

* authentication: login triple in subtags: groupIdAut, passwordAut, userIdAut
* agencyId: library code, like DK-790900
* trackingId

## License Terms
The web service is published under the [GPLv3](http://gplv3.fsf.org/) license.
