---
title: journal resource type 
description: A journal in Dynamics 365 Business Central.
services: project-madeira
documentationcenter: ''
author: SusanneWindfeldPedersen

ms.service: dynamics365-businesscentral
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: solsen
ms.prod: "dynamics-365-business-central"
---

# journal resource type
Represents a journal in Dynamics 365 Business Central.

## Methods

| Method                                            |Return Type|Description    |
|:--------------------------------------------------|:----------|:--------------|
|[Get journal](../api/dynamics_journal_get.md)      |journal    |Gets a journal.   |
|[Post journal](../api/dynamics_create_journal.md)  |journal    |Creates a journal.|
|[Patch journal](../api/dynamics_journal_update.md) |journal    |Updates a journal.|
|[Delete journal](../api/dynamics_journal_delete.md)|none       |Deletes a journal.|

## Properties
| Property	         | Type	                 |Description                                           |
|:-------------------|:----------------------|:-----------------------------------------------------|
|id                  |GUID                   |The unique ID of the journal. Non-editable.           |
|code                |string, maximum size 10| The code of the journal.                             |
|displayName         |string, maximum size 50| The display name of the journal.                     |
|lastModifiedDateTime|datetime               |The last datetime the journal was modified. Read-Only.|

## Bound actions
The journal resource type offers a bound action called `post` which posts the corresponding general journal batch.

Posting the general journal batch is illustrated in the following example:  
`POST https://graph.microsoft.com/beta/financials/companies{id}/journals{id}/post`.

The response has no content; the response code is 204.

## JSON representation

Here is a JSON representation of the resource.


```json
{
  "id": "GUID",
  "code": "string",
  "displayName": "string",
  "lastModifiedDateTime": "datetime"
}
```
