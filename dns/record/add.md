Portal: Dns Records
-------------------

**since** 0.0.0

dns-record:add
==============

Creates a new dns record.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/dns-record

**Access**: service edit permissions

**Parameters**:
- integer `zone_id` (required): id of the dsn zone to add the record to. @see dns-zone:list
- string `type` (required): type of record to add; one of
- string `host` (optional):
- string `target` (optional):
- integer `ttl` (optional): time to live, in seconds

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/dns-record" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{  }'
```

**Success Response**: 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 16 Jul 2019 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
X-Powered-By: PHP/7.2.15
Location: /v1/task/3b93d577-41ee-4077-913f-d36f91819bb9
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{ "id": 12, "identity": "dns-record:add (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
