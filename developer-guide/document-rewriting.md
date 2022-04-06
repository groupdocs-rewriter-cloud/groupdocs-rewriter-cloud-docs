---
id: "document-rewriting"
url: "rewriter/document-rewriting"
title: "Document Rewriting"
productName: "GroupDocs.Rewriter Cloud"
description: ""
keywords: ""
---

# Rewrite Document API #

This API allows you to rewrite (or paraphrase) a document from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).

## API Explorer ##

[GroupDocs.Rewriter Cloud API Reference](https://apireference.groupdocs.cloud/rewriter) lets you try out [Rewrite Document API](https://apireference.groupdocs.cloud/rewriter/#/Transport/PostRunRewriterTask) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|**Parameter**|**Description**|
|---|---|
|**userRequest**|String that represents list of JSONs precised in [JSON Request Details](rewriter/json-request-details).<br>Required.|

## cURL Example ##

Request

``` 
curl -X POST "https://api.groupdocs.cloud/v1.0/rewriter/document" \
-H "Authorization: Bearer TOKEN" \
-H "Content-Type: application/json" \
-d "'[ { \"format\":\"docx\", \"outformat\":\"docx\", \"language\":\"en\", \"name\":\"document.docx\", \"folder\":\"myFolder\", \"savepath\":\"myFolder\", \"savefile\":\"paraphrasedDoc.docx\", \"storage\":\"MyStorage\" }]'"
```

Response

``` 
{
    "status": "ok",
    "message": ".docx file saved successfully, file was fully rewrited"
}
```

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-rewriter-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-rewriter-cloud), it hides the [File API](https://apireference.groupdocs.cloud/rewriter/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Rewrite_Document.cs >}}

{{< /tab >}} {{< /tabs >}}