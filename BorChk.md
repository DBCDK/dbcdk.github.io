---
title: BorChk
permalink: BorChk.html
---
# Description of BorChk

## Introduction
Borrower check. Used to verify if a user is enrolled in a specific library and if the library is in the users municipality of residence.

Documentation: [http://www.danbib.dk/lanertjek-fjernadgang](http://www.danbib.dk/lanertjek-fjernadgang)

Current version is: 3.1

## Versions

| Version | Environment | Endpoint                                           | WSDL | XSD |
|---------|-------------|----------------------------------------------------|------|-----|
| 3.1    | production  | [https://borchk.addi.dk/3.1/](https://borchk.addi.dk/3.1/)         | [https://borchk.addi.dk/3.1/soap?wsdl](https://borchk.addi.dk/3.1/soap?wsdl)                     | [https://borchk.addi.dk/3.1/soap?xsd=1](https://borchk.addi.dk/3.1/soap?xsd=1) |
| 3.1    | extern test | [https://borchk.test.addi.dk/3.1/](https://borchk.test.addi.dk/3.1/) | [https://borchk.test.addi.dk/3.1/soap?wsdl](https://borchk.test.addi.dk/3.1/soap?wsdl) | [https://borchk.test.addi.dk/test_3.1/soap?xsd=1](https://borchk.test.addi.dk/3.1/soap?xsd=1) |
| 3.1    | staging     | [https://borchk.stg.addi.dk/3.1/](https://borchk.stg.addi.dk/3.1/) | [https://borchk.stg.addi.dk/3.1/soap?wsdl](https://borchk.stg.addi.dk/3.1/soap?wsdl) | [https://borchk.stg.addi.dk/test_3.1/soap?xsd=1](https://borchk.stg.addi.dk/3.1/soap?xsd=1) |
| 3.0    | production  | [https://borchk.addi.dk/3.0/](https://borchk.addi.dk/3.0/)         | [https://borchk.addi.dk/3.0/soap?wsdl](https://borchk.addi.dk/3.0/soap?wsdl)                     | [https://borchk.addi.dk/3.0/soap?xsd=1](https://borchk.addi.dk/3.0/soap?xsd=1) |
| 3.0    | extern test | [https://borchk.test.addi.dk/3.0/](https://borchk.test.addi.dk/3.0/) | [https://borchk.test.addi.dk/3.0/soap?wsdl](https://borchk.test.addi.dk/3.0/soap?wsdl) | [https://borchk.test.addi.dk/test_3.0/soap?xsd=1](https://borchk.test.addi.dk/3.0/soap?xsd=1) |
| 3.0    | staging     | [https://borchk.stg.addi.dk/3.0/](https://borchk.stg.addi.dk/3.0/) | [https://borchk.stg.addi.dk/3.0/soap?wsdl](https://borchk.stg.addi.dk/3.0/soap?wsdl) | [https://borchk.stg.addi.dk/test_3.0/soap?xsd=1](https://borchk.stg.addi.dk/3.0/soap?xsd=1) |

## Changelist

### Version 3.1

Added new BorrowerCheckComplex operation.

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

***BorrowerCheckComplex***

New in 3.1. Returns extra user information compared to BorrowerCheck operation. 

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
* userPrivilege - contains special privileges the user have, repeated 0 or more times
* municipalityNumber - users municipality number
* blocked - set to true if user is blocked from borrowing (unpaid fines etc.), otherwise false
