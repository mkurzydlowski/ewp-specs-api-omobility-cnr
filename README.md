Outgoing Mobility CNR API
=========================

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

This document describes the **Outgoing Mobility CNR API**. This API is
implemented by the receiving institution if it wants to be notified whenever
the sending institution changes a related Outgoing Mobility object.


Request method
--------------

 * Requests MUST be made with HTTP POST method. Servers MAY reject all other
   request methods.


Request parameters
------------------

Parameters MUST be provided in the `application/x-www-form-urlencoded` format.


### `mobility_id` (repeatable, required)

A list of identifiers of Outgoing Mobility objects that were recently
updated or created in the caller's EWP Host. Please note, that the sending
institution MAY (but doesn't have to) send this notification to your EWP Host
even when it is *your EWP Host* who actually initiated the update (via the
Outgoing Mobility Remote Update API).

This parameter is *repeatable*, so the request MAY contain multiple occurrences
of it. The server SHOULD process all of them.


Permissions
-----------

* Servers SHOULD allow this API to be called by all EWP Hosts in the network.


Handling of invalid parameters
------------------------------

 * General [error handling rules][error-handling] apply.

 * Please note, that receiving unknown `mobility_id` values is NOT an error.
   This usually indicates that a new Outgoing Mobility has been created (a new
   student has been nominated for the mobility), and you probably want to fetch
   it. Servers MUST return a valid (HTTP 200) XML response whenever the request
   has been properly received.


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
[iias-api]: https://github.com/erasmus-without-paper/ewp-specs-api-iias
