---
id: "working-with-folders"
url: "rewriter/working-with-folders"
title: "Working With Folders"
productName: "GroupDocs.Rewriter Cloud"
weight: 7
description: ""
keywords: ""
---

 





# Get the File Listing of a Specific Folder #

This API allows you to get a list of all files of a specific folder from the specified Cloud Storage. If you do not pass storage name API will find the folder in GroupDocs Cloud Storage. 

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/) lets you try out [List Files in a Folder API](https://apireference.groupdocs.cloud/rewriter/#/Folder/GetFilesList) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**path**|Path of the file including file name and extension e.g. /Folder1/file.ext<br>Required. Can be passed as a query string parameter or as part of the URL|
|storageName|Name of the storage. If not set, then default storage used|


## cURL Example ##


Request

``` 
curl -X GET "https://api.groupdocs.cloud/v1.0/rewriter/storage/folder/editordocs?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

``` 
{
  "value": [
    {
      "name": "four-pages.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:35:38+00:00",
      "size": 8651,
      "path": "/editordocs/four-pages.docx"
    },
    {
      "name": "one-page.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:17:34+00:00",
      "size": 351348,
      "path": "/editordocs/one-page.docx"
    },
    {
      "name": "password-protected.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:35:40+00:00",
      "size": 10240,
      "path": "/editordocs/password-protected.docx"
    },
    {
      "name": "three-layouts.pdf",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:26:42+00:00",
      "size": 15433,
      "path": "/editordocs/three-layouts.pdf"
    },
  ]
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Files_List.cs >}}

{{< /tab >}} {{< /tabs >}}

# Create a New Folder #

This API allows you to create a new folder in the specified Cloud Storage. If you do not pass storage name API will create New Folder in default Cloud Storage.

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/) lets you try out [Create Folder API](https://apireference.groupdocs.cloud/rewriter/#/Folder/CreateFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**path**|Target folder’s path e.g. Folder1/Folder2/. The folders will be created recursively<br>Required. Can be passed as a query string parameter or as part of the URL|
|storageName|Name of the storage. If not set, then default storage used|

## cURL Example ##

Request

``` 
curl -X POST "https://api.groupdocs.cloud/v1.0/rewriter/storage/folder/editordocs?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

``` 
{  
  "code": 200,
  "status": "OK"
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Create_Folder.cs >}}

{{< /tab >}} {{< /tabs >}}

# Delete a Particular Folder #

This API allows you to delete a particular folder in the specified Cloud Storage. If you do not pass storage name API will create New Folder in default Cloud Storage. To remove recursively inner folder/files you need to pass true value to a recursive parameter in Request. If it is set to false and folder contains data then API throws the exception.

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/#/) lets you try out [Delete a Particular Folder API](https://apireference.groupdocs.cloud/rewriter/#/Folder/DeleteFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose. 

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**path**|Folder path e.g. /Folder1<br>Required. Can be passed as a query string parameter or as part of the URL|
|storageName|Name of the storage. If not set, then default storage used|

## cURL Example ##

Request

``` 
curl -X DELETE "https://api.groupdocs.cloud/v1.0/rewriter/storage/folder/editordocs?storageName#MyStorage&#x26;recursive#true" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

``` 
{  
  "code": 200,
  "status": "OK"
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Delete_Folder.cs >}}

{{< /tab >}} {{< /tabs >}}

# Copy Specific Folder #

This API allows you to copy a folder to another location in the GroupDocs Cloud Storage. If you do not pass source and destination storage names API will copy Folder within default Cloud Storage.

## API Explorer ##

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/#/) lets you try out [Copy Folder API](https://apireference.groupdocs.cloud/rewriter/#/Folder/CopyFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**srcPath**|Source folder path e.g. /Folder1<br>Required. Can be passed as a query string parameter or as part of the URL|
|**destPath**|Destination folder path. Required|
|srcStorageName|Name of the storage of source folder. If not set, then default storage used|
|destStorageName|Name of the storage of destination folder. If not set, then default storage used|

## cURL Example ##

Request

``` 
curl -X PUT "https://api.groupdocs.cloud/v1.0/rewriter/storage/folder/copy/editordocs?destPath#viewerdocs1&#x26;srcStorageName#MyStorage&#x26;destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

``` 
{  
  "code": 200,
  "status": "OK"
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Copy_Folder.cs >}}

{{< /tab >}} {{< /tabs >}}

# Move a Specific Folder #

This API allows you to move a folder to another location in the GroupDocs Cloud Storage. If you do not pass source and destination storage names API will move Folder within default Cloud Storage.

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter/#/) lets you try out [Move a Folder API](https://apireference.groupdocs.cloud/rewriter/#/Folder/MoveFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**srcPath**|Source folder path e.g. /Folder1<br>Required. Can be passed as a query string parameter or as part of the URL|
|**destPath**|Destination folder path. Required|
|srcStorageName|Name of the storage of source folder. If not set, then default storage used|
|destStorageName|Name of the storage of destination folder. If not set, then default storage used|

## cURL Example ##

Request

``` 
curl -X PUT "https://api.groupdocs.cloud/v1.0/rewriter/storage/folder/move/editordocs?destPath#viewerdocs1&#x26;srcStorageName#MyStorage&#x26;destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"  
```

Response

``` 
{  
  "code": 200,
  "status": "OK"
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Move_Folder.cs >}}

{{< /tab >}} {{< /tabs >}}