---
title: "List the published apps from the Microsoft Teams app catalog"
description: "List apps from the Microsoft Teams app catalog. "
author: "nkramer"
localization_priority: Normal
ms.prod: "microsoft-teams"
---

# List the published apps from the Microsoft Teams app catalog

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

List [apps](../resources/teamsapp.md) from the Microsoft Teams app catalog. 
This includes apps from the Microsoft Teams store, as well as apps from your organization's app catalog (the tenant app catalog). To get apps from your organization's app catalog only, specify `Organization` as the **distributionMethod** in the [teamsCatalogApp](../resources/teamsapp.md) resource.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

>**Note:** Only global administrators can call this API. 

| Permission Type                        | Permissions (from least to most privileged)|
|:----------------------------------     |:-------------|
| Delegated (work or school account)     | AppCatalog.ReadWrite.All |
| Delegated (personal Microsoft account) | Not supported|
| Application                            | Not supported|

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /appCatalogs/teamsApps
```

## Optional query parameters
This method supports the $filter, $select, and $expand [OData query parameters](/graph/query-parameters) to help customize the response.

## Request headers

| Header        | Value           |
|:--------------|:--------------  |
| Authorization | Bearer {token}. Required.  |

## Request body
None.

>**Note:** You can filter on any of the fields of the [teamsCatalogApp](../resources/teamsapp.md) object to shorten the list of results. You can use any of the following filter operations: Equal, not-equal, and, or, and not.

## Response
If successful, this method returns a `200 OK` response code and a list of [teamsCatalogApp](../resources/teamsapp.md) objects in the response body.

## Examples
### Example 1
The following example lists all applications that are specific to your tenant.

#### Request
```
GET https://graph.microsoft.com/beta/appCatalogs/teamsApps?$filter=distributionMethod eq 'organization'
```

#### Response
```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "name": "Test App",
      "version": "1.0.1",
      "distributionMethod":"Organization"
    }
  ]
}
```

### Example 2

The following example lists applications with a given ID.

#### Request
```
GET https://graph.microsoft.com/beta/appCatalogs/teamsApps?$filter=id%20eq%20'b1c5353a-7aca-41b3-830f-27d5218fe0e5'
```

#### Response
```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
      "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
      "name": "Test App",
      "version": "1.0.1",
      "distributionMethod":"Organization"
    }
  ]
}
```

<!--
{
  "type": "#page.annotation",
  "suppressions": [
    "Error: /api-reference/beta/api/teamsapp-list.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->
