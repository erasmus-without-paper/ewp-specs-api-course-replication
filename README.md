Course Search API
=================

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

This document describes the **Course Search API**. This API can be implemented
by any HEI, even it is does not take part in EWP mobility process. It allows
other HEIs to search through a catalogue of courses conducted in this
institution.


Request method
--------------

 * Requests MUST be made with either HTTP GET or HTTP POST method. Servers MUST
   support both these methods. Servers SHOULD reject all other request methods.

 * Clients are advised to use POST when passing large number of parameters
   (servers MAY set a limit on their GET query string length).


Request parameters
------------------

Parameters MUST be provided in the regular `application/x-www-form-urlencoded`
format.


### `hei_id` (required)

ID of the institution in which the courses are conducted. This parameter MUST
be required by the server even if it covers only a single institution.


### `limit` (optional)

Positive integer of `none`. Default is **20**.

If `none` is given, the server is REQUIRED to return **all** matching
identifiers. This list can be huge, but it will allow the clients to fetch the
complete list of course identifiers (to facilitate full replication).


### (more parameters to come)

More parameters will be added here after the model is specified.


Permissions
-----------

 * All requests from the EWP Network MUST be allowed to access this API.

 * Additionally, implementers MAY allow this API to be accessed by
   **anonymous** external clients too (without the need of using any client
   certificate).


Handling of invalid parameters
------------------------------

 * General [error handling rules][error-handling] apply.
 * Invalid (or unknown) `hei_id` values MUST result in a HTTP 400 error
   response.


Response
--------

If the request was valid, then servers MUST respond with a valid XML document
described by the [response.xsd](response.xsd) schema. See the schema
annotations for further information.


[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses
[registry-spec]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[discovery-api]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery
[echo]: https://github.com/erasmus-without-paper/ewp-specs-api-echo
[error-handling]: https://github.com/erasmus-without-paper/ewp-specs-architecture#error-handling
[institutions-api]: https://github.com/erasmus-without-paper/ewp-specs-api-institutions
