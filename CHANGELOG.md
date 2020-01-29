Release notes
=============

This document describes all the changes made to the *Outgoing Mobility CNR API*
document, starting from its first beta draft version.


1.0.0
-----

* First stable release.


0.4.1
-----

* Added an explanation of what "properly received" means exactly.
* Fixed typos.


0.4.0
-----

Performed a refactoring caused by the planned introduction of the
Incoming Mobilities API (more information
[here](https://github.com/erasmus-without-paper/ewp-specs-api-mobilities/issues/27)).
XML namespaces, element and parameter names were changed.

 * All XML namespaces beginning with
   `https://github.com/erasmus-without-paper/ewp-specs-api-mobility-cnr/`
   now begin with
   `https://github.com/erasmus-without-paper/ewp-specs-api-omobility-cnr/`.

 * In `response.xsd`, the `mobility-cnr-response` element is now named
   `omobility-cnr-response`.

 * In `manifest-entry.xsd`, the `mobility-cnr` element is now named
   `omobility-cnr`, and the `max-mobility-ids` element is now named
   `max-omobility-ids`.

 * The `mobility_id` parameter is now named `omobility_id`.


0.3.0
-----

 * This API now requires implementers to upgrade their implementations to
   [Version 2](https://github.com/erasmus-without-paper/ewp-specs-sec-intro/tree/stable-v2)
   of the *Authentication and Security* document.

   In particular, this means that the clients MUST be aware of the fact, that
   the server is no longer required to support methods of authentication and
   encryption which it *was* required to support in the previous versions of
   this API. Clients SHOULD consult the newly introduced `<http-security>`
   element in the server's manifest entry before making their requests.


0.2.1
-----

* Explicitly declare that this version still requires the use of
  [Version 1](https://github.com/erasmus-without-paper/ewp-specs-sec-intro/tree/stable-v1)
  of the *Authentication and Security* document. You can find more information
  on the planned process of updating security requirements
  [here](https://github.com/erasmus-without-paper/ewp-specs-sec-intro/issues/1).


0.2.0
-----

* Changed XML namespaces (as part of
  [this issue](https://github.com/erasmus-without-paper/ewp-specs-api-iias/issues/22)).
  Since this version, this API is in the `stable-v1` XML namespace.

  This does not mean that this API is stable. It can still change in
  backward-incompatible ways, until version `1.0.0` is released.


0.1.1
-----

* `minOccurs` and `maxOccurs` are now provided explicitly
  ([why?](https://github.com/erasmus-without-paper/general-issues/issues/22)).

* Updated links.


0.1.0
-----

Initial release.
