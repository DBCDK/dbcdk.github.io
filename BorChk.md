---
title: BorChk
permalink: BorChk.html
---
# Description of BorChk

## Introduction
Lånertjek. Bruges til at tjekke om en bruger er indmeldt på et givent bibliotek, og om biblioteket er beliggende i brugerens hjemkommune. 

Dokumentation: [http://www.danbib.dk/lanertjek-fjernadgang](http://www.danbib.dk/lanertjek-fjernadgang)

## Versions

BorChk 3.0 is considered the primary production version.

_Unless specifically mentioned all information is about 3.0._

<span style="color:red">Versions older than 3.0 will go end-of-life soon.</span>


| Version | Environment | Endpoint                                           | WSDL | XSD |
|---------|-------------|----------------------------------------------------|------|-----|
| 2.6    | production  | [https://borchk.addi.dk/2.6/](https://borchk.addi.dk/2.6/)           | [https://borchk.addi.dk/2.6/?wsdl](https://borchk.addi.dk/2.6/?wsdl)           | [https://borchk.addi.dk/2.6/borchk.xsd](https://borchk.addi.dk/2.6/borchk.xsd) |
| 2.6    | extern test | [https://borchk.addi.dk/test_2.6/](https://borchk.addi.dk/test_2.6/) | [https://borchk.addi.dk/test_2.6/?wsdl](https://borchk.addi.dk/test_2.6/?wsdl) | [https://borchk.addi.dk/test_2.6/borchk.xsd](https://borchk.addi.dk/test_2.6/borchk.xsd) |
| 2.6    | staging     | [https://borchk.addi.dk/next_2.6/](https://borchk.addi.dk/next_2.6/) | [https://borchk.addi.dk/next_2.6/?wsdl](https://borchk.addi.dk/next_2.6/?wsdl) | [https://borchk.addi.dk/next_2.6/borchk.xsd](https://borchk.addi.dk/next_2.6/borchk.xsd) |
| 3.0    | production  | [https://borchk.addi.dk/3.0/](https://borchk.addi.dk/3.0/)         | [https://borchk.addi.dk/3.0/soap?wsdl](https://borchk.addi.dk/3.0/soap?wsdl)                     | [https://borchk.addi.dk/3.0/soap?xsd=1](https://borchk.addi.dk/3.0/soap?xsd=1) |
| 3.0    | extern test | [https://borchk.test.addi.dk/3.0/](https://borchk.test.addi.dk/3.0/) | [https://borchk.test.addi.dk/3.0/soap?wsdl](https://borchk.test.addi.dk/3.0/soap?wsdl) | [https://borchk.test.addi.dk/test_3.0/soap?xsd=1](https://borchk.test.addi.dk/3.0/soap?xsd=1) |
| 3.0    | staging     | [https://borchk.stg.addi.dk/3.0/](https://borchk.stg.addi.dk/3.0/) | [https://borchk.stg.addi.dk/3.0/soap?wsdl](https://borchk.stg.addi.dk/3.0/soap?wsdl) | [https://borchk.stg.addi.dk/test_3.0/soap?xsd=1](https://borchk.stg.addi.dk/3.0/soap?xsd=1) |

### 2.6

Version 2.6 did nok introduce any new functionality but only removed the possibility to use http url parameters. This means that the following is no longer possible:
* https://borchk.addi.dk/2.6?action=borrowerCheck&serviceRequester=AAAAAA&libraryCode=DK-BBBBBB&userId=CCCCCCCCCC&userPincode=DDDD

Only soap xml is supported in this release.

### 3.0

Like 2.6 only soap xml is supported in 3.0.

3.0 is a maintenance release which removed some no longer usable options from the xsd.

The following options are no longer supported:
* callback
* outputType
* debugging

## Service operations

***BorrowerCheck***

Used to verify a user is enrolled in a specific library and if that library is located in the users home municipality.

Request:
* serviceRequester - required
* libraryCode - required
* userId - required
* userPincode - optional

Response:
* userId - same as input
* requestStatus - one of the following options:
  * ok
  * service_not_licensed
  * service_unavailable
  * library_not_found
  * borrowercheck_not_allowed
  * borrower_not_found
  * borrower_not_in_municipality
  * municipality_check_not_supported_by_library
  * no_user_in_request
  * error_in_request
