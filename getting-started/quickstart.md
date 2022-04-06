---
id: "quickstart"
url: "rewriter/quickstart"
title: "Quickstart"
productName: "GroupDocs.Rewriter Cloud"
weight: 4
description: ""
keywords: ""
---

####   ####

#### Create an account ####

Creating an account is very simple. Go to [https://dashboard.groupdocs.cloud](https://dashboard.groupdocs.cloud) to create a free account.


#### Get Client Id and Client Secret ####

Before you can make any requests to GroupDocs Cloud API you need to get Client Id and Client Secret.\
This will be used to invoke the GroupDocs Cloud API.

You can get it from any existing Application or you can create a new Application.\
For further details see [Create New Application and Get Client Id and Client Secret]({{< ref "total/getting-started/ui-topics/creating-and-managing-application.md" >}})


#### Get your JWT token ####

After you have created a new application you can obtain a JWT token. See [this page]({{< ref "total/getting-started/overview-rest-api/authenticating-api-requests.md" >}}) for further details about this.


#### Call Rest API ####

When you’ve got your access_token you can make Rest API call by adding to Headers of your request:

* Authorization: Bearer access_token

##### To rewrite plain text #####

###### cURL ######

Request

```
curl -X POST "https://api.groupdocs.cloud/v1.0/rewriter/text" \
-H "Authorization: Bearer TOKEN" \
-H "Content-Type: application/json" \
-d "'[{"language": "en", "text": "Our shop is closed next week"}]'"
```

Response

``` 
{
    "status": "ok",
    "message": "Text rewrited successfully",
    "result": "Our shop will be closed next week"
}
```



###### SDKs ######

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Rewrite_Text.cs >}}

{{< /tab >}} {{< /tabs >}}

##### To rewrite a document #####

###### cURL ######

Request

``` 
curl -X POST "https://api.groupdocs.cloud/v1.0/rewriter/document" \
-H "Authorization: Bearer TOKEN" \
-H "Content-Type: application/json" \
-d "'[ { \"format\":\"docx\", \"outformat\":\"docx\", \"language\":\"en\", \"name\":\"document.docx\", \"folder\":\"myFolder\", \"savepath\":\"myFolder\", \"savefile\":\"paraphrasedDoc.docx\", \"storage\":\"MyStorage\"}]'"
```

Response

``` 
{
    "status": "ok",
    "message": ".docx file saved successfully, file was fully rewrited"
}
```

###### SDKs ######

{{< tabs tabTotal="1" tabID="1" tabName1="C#" >}} {{< tab tabNum="1" >}}

{{< gist groupdocs-rewriter-cloud-gists c5e9dcef763dd8ea30c0f1b92213b8ed Rewriter_CSharp_Rewrite_Document.cs >}}

{{< /tab >}} {{< /tabs >}}

