Simple Course Replication API
=============================

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

This document describes the **Simple Course Replication API**. This API can be
implemented by any HEI, even it is does not take part in EWP mobility process.
Once implemented, it allows the clients to replicate its catalogue of courses
conducted on this HEI. This in turn allows the clients to build rich course
searching experience.

In the draft stages of the design process, this API was referred to as **Course
Search API**. However, as the result of [this issue]
(https://github.com/erasmus-without-paper/ewp-specs-api-course-replication/issues/3),
we have dropped this name along with some of its initially planned filtering
functionality.


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
be validated by the server even if the server covers only a single HEI.


### `modified_since` (optional)

A date in the ISO 8601 format, e.g. `2004-02-12T15:19:21+01:00`.

If not given, then servers MUST return a full list of all their Course IDs.
This includes courses not currently conducted (if the server keeps record of
such courses).

If `modified_since` is given, then the server SHOULD filter the returned Course
IDs to the ones which have been *modified* since the provided point in time.

 * Servers MAY include courses which were *not* modified. For example, if the
   server only *suspects* that the course was modified, then it is okay to
   include the course's ID in the response.

 * Servers MAY ignore the `modified_since` parameter completely, and *always*
   respond with the full list of course IDs. If, for some reason, the server
   cannot reliably identify when courses are updated, then it's better to
   include all the courses for every request.

 * Servers MAY cache the response, but if they do, then they MUST do it in a
   way which will allows the clients to receive all the changes in a standard,
   predictable way (though with a delay).

   For example, if you want to cache the response for 24 hours, then such
   cached response MUST also include all courses modified since 24 hours
   *before* the moment such response was generated. Otherwise, the clients
   would be missing some changes.


Permissions
-----------

 * All requests from the EWP Network MUST be allowed to access this API.

 * Additionally, implementers MAY allow this API to be accessed by
   **anonymous** external clients too (without the need of using any client
   certificate). Servers MAY send a filtered response to such clients (for
   example, with email addresses removed).


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


Data model entities involved in the response
--------------------------------------------

 * Learning Opportunity Specification
 * Learning Opportunity Instance
 * Academic Term


[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses
[registry-spec]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[discovery-api]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery
[echo]: https://github.com/erasmus-without-paper/ewp-specs-api-echo
[error-handling]: https://github.com/erasmus-without-paper/ewp-specs-architecture#error-handling
[institutions-api]: https://github.com/erasmus-without-paper/ewp-specs-api-institutions
