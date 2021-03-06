.. _GET_listRecordset_v2__account_id__zones__zone_id__recordsets__recordset_id__recordsets:

List specified record set for a specified zone
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2/{TENANT_ID}/zones/{zone_id}/recordsets/{recordset_id}

This operation retrieves a record set with the specified record set ID.

If a request cannot be fulfilled due to insufficient or invalid data, an ``HTTP 400`` 
(Bad Request) error response will be returned with information regarding the nature of the 
failure in the body of the response. Failures in the validation process are non-recoverable 
and require the caller to correct the cause of the failure and **POST** the request again.

In the example shown below, the TTL is updated to ``3600``.

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
| Response| Name                  | Description                                 |
| Code    |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | Request succeeded.                          |
+---------+-----------------------+---------------------------------------------+
| 201     | Created               | The request has been fulfilled and resulted |
|         |                       | in a new resource being created.            |
+---------+-----------------------+---------------------------------------------+
| 400     | Bad Request           | The request is missing one or more          |
|         |                       | elements, or the values of some elements    |
|         |                       | are invalid.                                |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 403     | Forbidden             | The server has not found anything matching  |
|         |                       | the Request-URI.                            |
+---------+-----------------------+---------------------------------------------+
| 404     | Not Found             | The requested item was not found.           |
+---------+-----------------------+---------------------------------------------+
| 405     | Method Not Allowed    | The method specified in the Request-Line is |
|         |                       | not allowed for the resource identified by  |
|         |                       | the Request-URI.                            |
+---------+-----------------------+---------------------------------------------+
| 409     | Already Exists        | The item already exists.                    |
+---------+-----------------------+---------------------------------------------+
| 413     | Over Limit            | Request exceeds rate limit or quota         |
+---------+-----------------------+---------------------------------------------+
| 415     | Unsupported Media     | The server is refusing to service the       |
|         | Type                  | request because the entity of the request   |
|         |                       | is in a format not supported by the         |
|         |                       | requested resource for the requested        |
|         |                       | method.                                     |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

This table shows the URI parameters for the list record set request:

+-----------------------+---------+---------------------------------------------+
| Name                  | Type    | Description                                 |
+=======================+=========+=============================================+
| ``{TENANT_ID}``       | ​String | The account ID of the owner of the          |
|                       |         | specified account.                          |
+-----------------------+---------+---------------------------------------------+
| ``{zone_id}``         | ​String | The zone ID for the specified zone.         |
+-----------------------+---------+---------------------------------------------+
| ``{recordset_id}``    | ​String | The record set ID for the specified record  |
|                       |         | set.                                        |
+-----------------------+---------+---------------------------------------------+

 
**Example List record set request**

.. code::  

    GET /v2/123456/zones/2150b1bf-dee2-4221-9d85-11f7886fb15f/recordsets/f7b10e9b-0cae-4a91-b162-562bc6096648 HTTP/1.1
    Host: global.dns.rackspacecloud.com
    Accept: application/json
    Content-Type: application/json

This operation does not accept a request body.
 
**Example List record set response**

.. code::  

    HTTP/1.1 200 OK
    Vary: Accept
    Content-Type: application/json

    {
        "description": "This is an example recordset.",
        "links": {
            "self": "https://global.dns.api.rackspacecloud.com/v2/123456/zones/2150b1bf-dee2-4221-9d85-11f7886fb15f/recordsets/f7b10e9b-0cae-4a91-b162-562bc6096648"
        },
        "updated_at": null,
        "records": [
            "10.1.0.2"
        ],
        "ttl": 3600,
        "id": "f7b10e9b-0cae-4a91-b162-562bc6096648",
        "name": "example.org.",
        "zone_id": "2150b1bf-dee2-4221-9d85-11f7886fb15f",
        "created_at": "2014-10-24T19:59:44.000000",
        "version": 1,
        "type": "A"
    }
