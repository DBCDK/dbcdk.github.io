---
title: OpenOrder-webservice
permalink: OpenOrderWebservice.html
---
# Description of OpenOrder-webservice

## Introduction
This repo contains the OpenOrder webservice and client. It is part of the Open Library System Suite.

The Open Order web service is a service for requesting materials that are either owned by the user's library or is not owned by the library (inter library loan). The policies for ordering materials are based on those used by bibliotek.dk, and are controlled by the agencies (libraries) in the VIP database.

The OpenOrder service serves several functions related to ordering of materials managed by libraries.
The service can provide definitive information on whether a specific resource can be ordered, it can receive orders and pass them on for further processing in the OLS Base Over Bestillinger (BOB) system, and it can update the status of registered orders.

Supported protocols are SOAP over HTTPS.

The service consists of two operations: checkOrderPolicy and PlaceOrder.

CheckOrderPolicy checks that a given agency will allow for enduser ill on the material. If the pid is omitted, the operation will check that a given agency allows for ill.

PlaceOrder creates an order in the orderSystem. It implicitly calls checkOrderPolicy to test if the given agency accepts ill on the pid supplied.

WSDL: [https://openorder.addi.dk/3.0?wsdl](https://openorder.addi.dk/3.0?wsdl) <br/>
XSD: [https://openorder.addi.dk/3.0?xsd=1](https://openorder.addi.dk/3.0?xsd=1)

Possible responses from the two operations checkOrderPolicy and placeOrder:

- `OWNED_ACCEPTED`:                   item available at pickupAgency, order accepted
- `NOT_OWNED_ILL_LOC`:                item not available at pickupAgency, item localised for ILL
- `OWNED_WRONG_MEDIUM_TYPE`:          item available at pickupAgency, order of mediumType not accepted
- `NOT_OWNED_WRONG_ILL_MEDIUM_TYPE`:  item not available at pickupAgency, ILL of mediumType not accepted
- `NOT_OWNED_NO_ILL_LOC`:             item not available at pickupAgency, item not localised for ILL
- `OWNED_OWN_CATALOGUE`:              item available at pickupAgency, item may be ordered through the library's catalogue
- `SERVICE_UNAVAILABLE`:              service unavailable
- `UNKNOWN_PICKUP_AGENCY`:            pickupAgency not found
- `UNKNOWN_USER`:                     user not found
- `INVALID_ORDER`:                    Order does not validate (only placeOrder)
- `ORS_ERROR`:                        Error sending order to ORS (only placeOrder)
- `NO_SERVICE_REQUESTER`:             serviceRequester is obligatory
- `AUTHENTICATION_ERROR`:             authentication error
- `INVALID_NEED_BEFORE_DATE`          the need before date is either in an invalid data format or the date is before now

**NB!** The XSD uses a combination of lowercase, uppercase, underscore and camelcase, but the service is implemented in Java, and the possible replies as Java object enum types (all uppercase and camelcase replaced by and underscore - e.g. `owned_wrong_mediumType` → `OWNED_WRONG_MEDIUM_TYPE`).

The following possibility from the XSD is no longer used: `not_owned_accepted_by_consortia`

## License Terms
Use of the web service requires [subscription of a DanBib license](http://www.dbc.dk/produkter-services/databaser_tjenester_produktoversigt/danbib) (Netpunkt password).
The web service is published under the GPLv3 License.

## License
DBC-Software Copyright ?. 2009, Danish Library Center, dbc as.

This library is Open source middleware/backend software developed and distributed under the following licenstype:

GNU, General Public License Version 3. If any software components linked together in this library have legal conflicts with distribution under GNU 3 it will apply to the original license type.

Software distributed under the License is distributed on an "AS IS" basis, WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License for the specific language governing rights and limitations under the License.

Around this software library an Open Source Community is established. Please leave back code based upon our software back to this community in accordance to the concept behind GNU.

You should have received a copy of the GNU Lesser General Public License along with this library; if not, write to the Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA
