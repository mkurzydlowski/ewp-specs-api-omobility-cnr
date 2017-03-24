Outgoing Mobility CNR API
=========================

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

This document describes the **Outgoing Mobility CNR API**. This API is
implemented by the receiving institution if it wants to be notified whenever
mobilities kept on their partner institutions' servers are changed.

CNR stands for Change Notification Receiver. For a detailed introduction on how
CNR APIs work, please read [this page][cnr-intro].


Request method
--------------

 * Requests MUST be made with HTTP POST method. Servers MAY reject all other
   request methods.


Request parameters
------------------

Parameters MUST be provided in the `application/x-www-form-urlencoded` format.


### `sending_hei_id` (required)

Identifier of the sending HEI - the master of the Outgoing Mobility objects
which just have been changed.


### `mobility_id` (repeatable, required)

A list of identifiers of Outgoing Mobility objects (no more than
`<max-mobility-ids>` items). These are the Mobility objects which have been
recently updated (or created) on the caller's side. Please note, that the
sending institution SHOULD send this notification to you even when it is *you*
who actually initiated the update (e.g. via the `update` endpoint of Outgoing
Mobilities API).

This parameter is *repeatable*, so the request MAY contain multiple occurrences
of it. The server SHOULD process all of them. Server implementers provide their
own chosen value of `<max-mobility-ids>` via their manifest entry (see
[manifest-entry.xsd](manifest-entry.xsd)). Clients SHOULD parse this value (or
assume it's equal to `1`).


Permissions
-----------

* Servers SHOULD allow this API to be called by all EWP Hosts in the network.


Handling of invalid parameters
------------------------------

 * General [error handling rules][error-handling] apply.

 * Please note, that receiving unknown `mobility_id` values is NOT an error.
   This usually indicates that a new Outgoing Mobility has been created, and
   you probably want to fetch it (a new student has been nominated for the
   mobility).

 * Servers MUST return a valid (HTTP 200) XML response whenever the request has
   been properly received. Unless HTTP 200 is received, clients are RECOMMENDED
   to automatically retry the request after some time.


Response
--------

Servers MUST respond with a valid XML document described by the
[response.xsd](response.xsd) schema. See the schema annotations for further information.


Safety measures
---------------

It is NOT guaranteed that all notifications will be delivered to you promptly.
Some notifications may also **not reach you at all**, e.g. due to
implementation errors on the sending institution's server, or the fact that no
Notification Sender daemon has been implemented there (see
`<sends-notifications>` element in [Outgoing Mobilities API][mobilities-api]'s
`manifest-entry.xsd`).

Therefore, you SHOULD periodically verify if your copies are up-to-date (or,
simply, choose to *not store* these copies). Proper caching techniques and/or
periodical use of `index` endpoint of [Outgoing Mobilities API][mobilities-api]
can help you with that.


[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses
[registry-spec]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[discovery-api]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery
[echo]: https://github.com/erasmus-without-paper/ewp-specs-api-echo
[error-handling]: https://github.com/erasmus-without-paper/ewp-specs-architecture#error-handling
[institutions-api]: https://github.com/erasmus-without-paper/ewp-specs-api-institutions
[iias-api]: https://github.com/erasmus-without-paper/ewp-specs-api-iias
[mobilities-api]: https://github.com/erasmus-without-paper/ewp-specs-api-mobilities
[cnr-intro]: https://github.com/erasmus-without-paper/ewp-specs-architecture#cnr
