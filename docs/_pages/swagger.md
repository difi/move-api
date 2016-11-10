---
layout: page
---

# Grenseløse grensenitt - nextMove

<a name="overview"></a>

## Overview
Neste generasjon grensesnitt for å bygge utgående og konsumere inngående meldinger for en virksomhet


### Version information
*Version* : 1.0.0

<a name="paths"></a>

## Paths

<a name="out-types-get"></a>

### GET /out/types

#### Description
Get messagetypes supported by this local endpoint for a given recipient organization


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Query**|**receiver**  <br>*optional*|Filter to supported types by organization identified (orgnumber)|string|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful response|< [MessageType](#messagetype) > array|

<a name="messagetype"></a>

**MessageType**

|Name|Schema|
|---|---|
|**id**  <br>*optional*|string|
|**infrastructure**  <br>*optional*|string|
|**name**  <br>*optional*|string|
|**schema**  <br>*optional*|string|
|**version**  <br>*optional*|string|


<a name="out-types-messagetypeid-prototype-get"></a>

### GET /out/types/{messageTypeId}/prototype

#### Description
Get a prototype object with mandatory fields needed to create message of the given type


#### Parameters

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**messageTypeId**  <br>*required*|valid id of message type|string|
|**Query**|**receiver**  <br>*optional*|Intended reciever of message|string|


#### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful response|No Content|
