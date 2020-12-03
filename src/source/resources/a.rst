
.. _reference-as:

==========
Resource A
==========

Represents A of the FooBar platform.


.. contents::
   :local:
   :depth: 2


A details ``/as/<a_id>/``
=========================

Operatons on single A.


GET
---

Requests must be authenticated as described in :ref:`authorization <overview-authentication>`

The response data is composed of the following object:

.. _reference-a-object:

**A**:

===========  =======  ===================================
Field        Type     Description
===========  =======  ===================================
id           Integer  The ID of the a
things       String   Things of the a
stuff        String   Stuff of the a
===========  =======  ===================================


.. http:get:: /as/<a_id>/

    Fetch A with id ('a_id').

    :requestheader X-Auth: API access token
    :statuscode 200: OK - success
    :statuscode 401: UNAUTHORIZED - invalid or missing token
    :statuscode 403: FORBIDDEN - Does not have access to this resource
    :statuscode 404: NOT_FOUND - Resource does not exist

    **Example request**:

    .. sourcecode:: http

        GET /as/8/
        X-Auth: 1c01d5a1-fdef-401b-993c-1a7a93193a82
        Accept: application/json

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
            "stuff": "good",
            "things": "better",
            "id": 8
        }


PUT
---

Update an A.

The response data is composed of the :ref:`a object<reference-a-object>`.

.. http:put:: /as/<a_id>/

    Update A with id ('a_id').

    :jsonparam string stuff: New stuff for the a
    :jsonparam string things: New things for the a
    :requestheader X-Auth: API access token
    :statuscode 200: OK - success
    :statuscode 401: UNAUTHORIZED - invalid or missing token
    :statuscode 403: FORBIDDEN - Does not have access to this resource
    :statuscode 404: NOT_FOUND - Resource does not exist

    **Example request**:

    .. sourcecode:: http

        PUT /as/8/
        X-Auth: 1c01d5a1-fdef-401b-993c-1a7a93193a82
        Accept: application/json

        {
            "stuff": "very good",
            "things": "much better",
        }

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
            "stuff": "very good",
            "things": "much better",
            "id": 8
        }

    **Error Messages**:

    .. sourcecode:: http

        HTTP/1.1 400 BAD_REQUEST
        Content-Type: application/json

        {
            "error": "Bad request. Unknown stuff"
        }

    .. sourcecode:: http

        HTTP/1.1 400 BAD_REQUEST
        Content-Type: application/json

        {
            "error": "Bad request. Unknown things"
        }


DELETE
------

Text and example request here


As ``/as/``
===========

Bulk operatons and creation of As.

Calls must be authenticated as described in :ref:`authorization <overview-authentication>`


GET
---

Get As in bulk. Interesting note here!

Requests must be authenticated as described in :ref:`authorization <overview-authentication>`

The response data is composed of the following object:

===========  =======  ===================================
Field        Type     Description
===========  =======  ===================================
objects      List     List of :ref:`a objects<reference-a-object>`
pagination   Object   A :ref:`pagination object<reference-pagination-object>`
===========  =======  ===================================


.. http:get:: /as/

    Fetch a list of As
    Allows cool_feature by: id, role, username

    :param custom cool_feature: A :ref:`cool feature<reference-cool-common-feature>` to be applied
    :param integer limit: Number of records to retrieve. If 0, will return all records and offset
    :param integer offset: Starting position. Used for :ref:`pagination <reference-pagination>` purposes
    :statuscode 200: OK - success
    :statuscode 401: UNAUTHORIZED - invalid or missing token
    :statuscode 403: FORBIDDEN - Does not have access to this resource

    **Example request**:

    .. sourcecode:: http

        GET /as/?filter=[role exact admin]&limit=25
        X-Auth: 1c01d5a1-fdef-401b-993c-1a7a93193a82
        Accept: application/json

    **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
            "objects: [
                {
                    "stuff": "good",
                    "things": "better",
                    "id": 8
                },
                "..."
            ],
            "pagination": {
                "total": 213,
                "offset": 0,
                "limit": 25
            }
        }


POST
----

Create a new A.

Text and example request here
