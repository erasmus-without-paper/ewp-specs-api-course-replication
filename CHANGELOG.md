Release notes
=============

This document describes all the changes made to the *Institutions API*
document, starting from its first beta draft version.


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
  [new format](https://github.com/erasmus-without-paper/ewp-specs-api-mobilities/issues/9).
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
