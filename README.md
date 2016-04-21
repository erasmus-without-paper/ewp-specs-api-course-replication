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

Parameters MUST be provided either in a query string (for GET requests), or in
the `application/x-www-form-urlencoded` format (for POST requests).


### `hei_id` (required)

ID of the institution in which the courses are conducted. This parameter is
required even if the host covers only a single institution.


### (more parameters to come)

More parameters will be added here after the model is specified.


Permissions
-----------

 * All requests from the EWP Network MUST be allowed access to this API.

 * Additionally, it is RECOMMENDED to allow this API to be accessed by
   **anonymous** external clients too (without the need of using a client
   certificate). It is also RECOMMENDED that servers should include an
   `Access-Control-Allow-Origin: *` header in their responses (so that
   JavaScript applications will be able to use it without a proxy).


Handling of invalid parameters
------------------------------

 * General [error handling rules][error-handling] apply.
 * Invalid (or unknown) `hei_id` MUST result in a HTTP 400 error response.


Response
--------

Servers MUST respond with a valid XML document described by the [response.xsd]
(response.xsd) schema. See the schema annotations for further information.


[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses
[registry-spec]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[discovery-api]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery
[echo]: https://github.com/erasmus-without-paper/ewp-specs-api-echo
[error-handling]: https://github.com/erasmus-without-paper/ewp-specs-architecture#error-handling
[institutions-api]: https://github.com/erasmus-without-paper/ewp-specs-api-institutions
