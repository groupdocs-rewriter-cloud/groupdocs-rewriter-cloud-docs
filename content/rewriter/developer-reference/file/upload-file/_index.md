---
id: "file-upload"
weight: 10
date: "2023-11-01"
author: "Vladimir Lapin"
type: docs
url: /rewriter/file/upload/
productName: "GroupDocs.Rewriter Cloud"
title: Upload file
description: How to upload file to Cloud storage.
keywords:
- rewrite
- file
- content
- queue
- upload
---
Before starting processing file, you should upload your file to Cloud S3 storage and only then send request to the corresponding endpoint. To do this, send **POST** request to `https://api.groupdocs.cloud/v2.0/rewriter/file/upload` GroupDocs.Rewriter Cloud REST API endpoint. This request doesn't require authorization. 

You should provide a local path to your file  in the request body.

As a result, you will receive URL to your file, that you should provide in request body.


## cURL example

```bash
curl --location --request POST 'https://api.groupdocs.cloud/v2.0/rewriter/file/upload' \
--header 'Content-Type: application/json' \
--F "path=@/path/to/myfile.pdf"
```
