
.. _reference-bs:

==========
Resource B
==========

Represent Bs of an A.


.. contents::
   :local:
   :depth: 2


B details ``/as/<a_id>/bs/<b_id>/``
===================================

Operatons on single B.


GET
---

Requests must be authenticated as described in :ref:`authorization <overview-authentication>`

The response data is composed of the following object:

.. _reference-b-object:

**B**:

================  =======  ===================================
Field             Type     Description
================  =======  ===================================
id                Integer  The ID of the B
A                 Integer  ID of the A the B is for
monday            Date     The date of the monday of the week the B is for
average_distance  Integer  Average distance in meters of the statistics entries for the week
average_speed     Integer  Average speed in meter/second of the statistics entries for the week
================  =======  ===================================


.. http:get:: /as/<a_id>/bs/<b_id>/

    Fetch a B with id ('b_id') belonging to A with id ('a_id').

    :requestheader X-Auth: API access token
    :statuscode 200: OK - success
    :statuscode 401: UNAUTHORIZED - invalid or missing token
    :statuscode 403: FORBIDDEN - Does not have access to this resource
    :statuscode 404: NOT_FOUND - Resource does not exist

    **Example request**:

    .. sourcecode:: http

        GET /a/8/bs/8/
        X-Auth: 1c01d5a1-fdef-401b-993c-1a7a93193a82
        Accept: application/json

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
            "a": 8,
            "average_distance": 2555.5,
            "average_speed": 2.13,
            "id": 8,
            "monday": "2017-01-23"
        }


Bs ``/as/<a_id>/bs/``
=====================

Bulk operatons on Bs.

Calls must be authenticated as described in :ref:`authorization <overview-authentication>`


GET
---

Get Bs in bulk.

Requests must be authenticated as described in :ref:`authorization <overview-authentication>`

The response data is composed of the following object:

===========  =======  ===================================
Field        Type     Description
===========  =======  ===================================
objects      List     List of :ref:`b objects<reference-b-object>`
pagination   Object   A :ref:`pagination object<reference-pagination-object>`
===========  =======  ===================================


.. http:get:: /as/<a_id>/bs/

    Fetch a list of Bs.
    Allows cool_feature by: id, average_distance, average_speed, monday

    :param custom filter: A :ref:`cool feature<reference-cool-common-feature>` to be applied
    :param integer limit: Number of records to retrieve. If 0, will return all records and offset
    :param integer offset: Starting position. Used for :ref:`pagination <reference-pagination>` purposes
    :statuscode 200: OK - success
    :statuscode 401: UNAUTHORIZED - invalid or missing token
    :statuscode 403: FORBIDDEN - Does not have access to this resource

    **Example request**:

    .. sourcecode:: http

        GET /as/8/bs/?filter=[average_speed gt 2]&limit=25
        X-Auth: 1c01d5a1-fdef-401b-993c-1a7a93193a82
        Accept: application/json

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
            "objects: [
                {
                    "A": 8,
                    "average_distance": 2555.5,
                    "average_speed": 2.13,
                    "id": 8,
                    "monday": "2017-01-23"
                },
                "..."
            ],
            "pagination": {
                "total": 213,
                "offset": 0,
                "limit": 25
            }
        }
