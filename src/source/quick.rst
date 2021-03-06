.. _quick-reference:

===============
Quick Reference
===============

This section is meant to be a quick reference for FooBar's API.

You can use it to perform simple tests but most of the times you will need the detailed description
from the :ref:`reference` to do exactly what you need to.

.. contents::
   :local:
   :depth: 1


Resources
=========

This table shows an overview of the resources and the available HTTP methods for each.

===================  ==============================  =================================================================================
Resource             Methods                         Description
===================  ==============================  =================================================================================
A                    GET, PUT, DELETE and POST       Represents an A
B                    GET                             Represents Bs of an A
===================  ==============================  =================================================================================


Resource/URI Mapping
====================

This table represents the combination of the Resources and URIs tables above. It shows which HTTP methods are available for each URI and what they do.

+---------------+---------------------------------------+-----------------------------------------------------------------------------------------------------------------------+------------------+
|               |                                       | HTTP Methods                                                                                                          |                  |
+---------------+---------------------------------------+-------------------------------+----------------------+----------------------+--------------------+--------------------+------------------+
| Resource      | URI                                   | GET                           | PUT                  | DELETE               | PATCH              | POST               | Mandatory Token  |
+===============+=======================================+===============================+======================+======================+====================+====================+==================+
| A             | /as/                                  | Retrieve list of As           | Update list of As    | Bulk delete As       | Upsert list of As  | Create a new A     |                  |
+               +---------------------------------------+-------------------------------+----------------------+----------------------+--------------------+--------------------+------------------+
|               | /as/<a_id>/                           | Details for the A             | Update the A         | Delete the A         | Parital update A   | N/A                |                  |
+---------------+---------------------------------------+-------------------------------+----------------------+----------------------+--------------------+--------------------+------------------+
| B             | /as/<a_id>/bs/                        | List of Bs for the A          | Update Bs for the A  | Bulk delete A's Bs   | Upsert A's Bs      | Create an B for A  | GET, DELETE,     |
|               |                                       |                               |                      |                      |                    |                    | POST             |
+               +---------------------------------------+-------------------------------+----------------------+----------------------+--------------------+--------------------+------------------+
|               | /as/<a_id>/bs/<b_id>/                 | Details for the B             | Update the B         | Remove the B         | Partially update B | N/A                | GET, PUT, DELETE |
+---------------+---------------------------------------+-------------------------------+----------------------+----------------------+--------------------+--------------------+------------------+


Examples
========

Text here
