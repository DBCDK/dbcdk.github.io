---
title: BorChk
permalink: BorChk.html
---
# Description of BorChk

## Introduction
Lånertjek. Bruges til at tjekke om en bruger er indmeldt på et givent bibliotek, og om biblioteket er beliggende i brugerens hjemkommune. 

Dokumentation: [http://www.danbib.dk/lanertjek-fjernadgang](http://www.danbib.dk/lanertjek-fjernadgang)

## Versions

| Version | Environment | Endpoint                                           | WSDL | XSD |
|---------|-------------|----------------------------------------------------|------|-----|
| 3.0    | production  | [https://borchk.addi.dk/3.0/](https://borchk.addi.dk/3.0/)         | [https://borchk.addi.dk/3.0/soap?wsdl](https://borchk.addi.dk/3.0/soap?wsdl)                     | [https://borchk.addi.dk/3.0/soap?xsd=1](https://borchk.addi.dk/3.0/soap?xsd=1) |
| 3.0    | extern test | [https://borchk.test.addi.dk/3.0/](https://borchk.test.addi.dk/3.0/) | [https://borchk.test.addi.dk/3.0/soap?wsdl](https://borchk.test.addi.dk/3.0/soap?wsdl) | [https://borchk.test.addi.dk/test_3.0/soap?xsd=1](https://borchk.test.addi.dk/3.0/soap?xsd=1) |
| 3.0    | staging     | [https://borchk.stg.addi.dk/3.0/](https://borchk.stg.addi.dk/3.0/) | [https://borchk.stg.addi.dk/3.0/soap?wsdl](https://borchk.stg.addi.dk/3.0/soap?wsdl) | [https://borchk.stg.addi.dk/test_3.0/soap?xsd=1](https://borchk.stg.addi.dk/3.0/soap?xsd=1) |

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
