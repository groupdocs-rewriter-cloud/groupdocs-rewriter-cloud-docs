---
id: "working-with-storage"
url: "rewriter/working-with-storage"
title: "Working With Storage"
productName: "GroupDocs.Rewriter Cloud"
weight: 8
description: ""
keywords: ""
---

 





# Storage existence API #

This API intended for checking the existence of cloud storage with a given name from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/#/) lets you try out [Storage existence API](https://apireference.groupdocs.cloud/rewriter/#/Storage/StorageExists) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**storageName**|Storage name|

## cURL Example ##

Request

``` 
curl -X GET "https://api.groupdocs.cloud/v1.0/rewriter/storage/MyStorage/exist" -H  "accept: application/json" -H  "authorization: Bearer  [Access Token]"
```
Response

``` 
{
  "exists": true
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Storage_Exists.cs >}}

{{< /tab >}} {{< /tabs >}}

# Storage object existence API #

This API intended for checking the existence of a file or folder in [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/#/) lets you try out [Storage existence API](https://apireference.groupdocs.cloud/rewriter/#/Storage/StorageExists) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**path**|Path of the file or folder<br>Required. Can be passed as a query string parameter or as part of the URL|
|storageName|Name of the storage. If not set, then default storage used|
|versionId|File version id|

## cURL Example ##

Request

``` 
curl -X GET "https://api.groupdocs.cloud/v1.0/rewriter/storage/exist/editordocs?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

``` 
{
  "exists": true,
  "isFolder": true
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Object_Exists.cs >}}

{{< /tab >}} {{< /tabs >}}

# Storage Space Usage API #

This API intended for getting total and used space of the[ GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud)

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/#/) lets you try out [storage space usage API](https://apireference.groupdocs.cloud/rewriter/#/Storage/GetDiscUsage) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|storageName|Name of the storage. If not set, then default storage used|

## cURL Example ##

Request

``` 
curl -X GET "https://api.groupdocs.cloud/v1.0/rewriter/storage/disc?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

``` 
{
  "usedSize": 31032368,
  "totalSize": 3221225472
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Space_Usage.cs >}}

{{< /tab >}} {{< /tabs >}}

# Storage File Versions API #

This API intended for getting the list of file versions, stored in the [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud)

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/#/) lets you try out [Storage File Versions API](https://apireference.groupdocs.cloud/rewriter/#/Storage/GetFileVersions) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**path**|Path of the file including file name and extension e.g. /Folder1/file.ext<br>Required. Can be passed as a query string parameter or as part of the URL|
|storageName|Name of the storage. If not set, then default storage used|

## cURL Example ##

Request

``` 
curl -X GET "https://api.groupdocs.cloud/v1.0/rewriter/storage/version/one-page.docx?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

``` 
{
  "value": [
    {
      "versionId": "null",
      "isLatest": true,
      "name": "one-page.docx",
      "isFolder": false,
      "modifiedDate": "2018-08-16T19:45:05+00:00",
      "size": 347612,
      "path": "/one-page.docx"
    }
  ]
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_File_Versions.cs >}}

{{< /tab >}} {{< /tabs >}}