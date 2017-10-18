Release notes
=============

This document describes all the changes made to the *Institutions API*
document, starting from its first beta draft version.


1.0.0-rc9
---------

* The `modified_since` parameter of the `index` endpoint is now in the
  `xs:dateTime` format (not ISO 8601 format). See
  [this thread](https://github.com/erasmus-without-paper/general-issues/issues/27).


1.0.0-rc8
---------

 * This API now requires implementers to upgrade their implementations to
   [Version 2](https://github.com/erasmus-without-paper/ewp-specs-sec-intro/tree/stable-v2)
   of the *Authentication and Security* document.

   In particular, this means that the clients MUST be aware of the fact, that
   the server is no longer required to support methods of authentication and
   encryption which it *was* required to support in the previous versions of
   this API. Clients SHOULD consult the newly introduced `<http-security>`
   element in the server's manifest entry before making their requests.

 * The `<allows-anonymous-access>` element (in `manifest-entry.xsd`) is now
   DEPRECATED. This element in planned to be removed before the final version
   of this API is released. Please use `<http-security>` element instead.


1.0.0-rc7
---------

* Fix schemaLocations.

* Explicitly declared that this version still requires the use of
  [Version 1](https://github.com/erasmus-without-paper/ewp-specs-sec-intro/tree/stable-v1)
  of the *Authentication and Security* document. You can find more information
  on the planned process of updating security requirements
  [here](https://github.com/erasmus-without-paper/ewp-specs-sec-intro/issues/1).


1.0.0-rc6
---------

* Added the *Performance note* section.
* Updated XML namespace references (see
  [this issue](https://github.com/erasmus-without-paper/ewp-specs-api-iias/issues/22)).


1.0.0-rc5
---------

* `minOccurs` and `maxOccurs` are now provided explicitly
  ([why?](https://github.com/erasmus-without-paper/general-issues/issues/22)).


1.0.0-rc4
---------

* Response example has been adjusted so that LOS IDs are now in a
  [new format](https://github.com/erasmus-without-paper/ewp-specs-api-omobilities/issues/9).
  The XSD also refers to this format (so it is now properly validated).

* Some changes to the API's manifest entry: New `<supports-modified-since>`
  element was added (and it is required), and the type of the existing
  `<allows-anonymous-access>` was changed (from `ewp:Empty` to `xs:boolean`).


1.0.0-rc3
---------

* Now this API is serving references to other LOS types too (not only
  `Course`s).


1.0.0-rc2
---------

 * The `<response>` element has been renamed to
   `<course-replication-response>`.


1.0.0-rc1
---------

Initial release. (Since this API seemed really simple, we skipped the `0.x.y`
versions altogether.)
