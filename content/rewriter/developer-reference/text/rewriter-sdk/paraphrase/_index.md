---
id: "paraphrase-text-sdk"
weight: 30
date: "2023-11-01"
author: "Vladimir Lapin"
type: docs
url: /rewriter/text/sdk/paraphrase
productName: "GroupDocs.Rewriter Cloud"
title: Paraphrase text with GroupDocs.Rewriter SDK
description: How to use GroupDocs.Rewriter Cloud SDK for paraphrasing texts.
keywords:
- paraphrase
- API
- program
- language
- text
- content
---

## Learn more

Although you can directly call the GroupDocs.Rewriter Cloud REST API to [send text](/rewriter/text/request/) and [fetch the result](/rewriter/text/fetch/), there is a much easier way to implement required functionality in your applications. We provide software development kits (SDKs) for all popular programming languages. They wrap up all routine operations such as establishing connections, sending API requests, and parsing responses into a few simple methods. It makes interaction with GroupDocs.Rewriter Cloud services much easier, allowing you to focus on business logic rather than technical details.

{{< tabs tabID="1" tabTotal="3" tabName1=".NET (C#)" tabName2="Python" tabName3="Java"  >}}

{{< tab tabNum="1" >}}

```csharp
using GroupDocs.Rewriter.Cloud.Sdk.Api;
using GroupDocs.Rewriter.Cloud.Sdk.Client;
using GroupDocs.Rewriter.Cloud.Sdk.Client.Auth;
using GroupDocs.Rewriter.Cloud.Sdk.Model;
using Configuration = GroupDocs.Rewriter.Cloud.Sdk.Client.Configuration;
using System.Diagnostics;
using System.IO;
using System.Collections.Generic;
using System.Net.Http;
using HttpStatusCode = System.Net.HttpStatusCode;
namespace GroupDocs.Rewriter.Cloud.Sdk
{
	  public class TextRewriter
	  {
		    public TextRewriter()
		    {
            Configuration config = new Configuration();
			      config.OAuthFlow = OAuthFlow.APPLICATION;
			      config.OAuthClientId = "YOU_CLIENT_ID";
			      config.OAuthClientSecret = "YOU_CLIENT_SECRET";
            config.BasePath = "https://api.groupdocs.cloud/v2.0/rewriter";
            ParaphraseApi api = new ParaphraseApi(conf);
            string srcText = "Hello, everyone! We will try to rephrase this text into something new.";
            string sourceLanguage = "en";
            ParaphraseTextResponse textResponse = new ParaphraseTextResponse();
            ParaphraseTextRequest req = new ParaphraseTextRequest(
                language: sourceLanguage,
                text: srcText,
                suggestions: ParaphraseTextRequest.SuggestionsEnum.One,
                diversityDegree: DegreeEnum.Off);
            StatusResponse responseId = await api.ParaphraseTextPostAsync(req);
            try
            {
                if (responseId.Status.ToString() == "Accepted")
                {
                    while (true)
                    {
                        textResponse = await api.ParaphraseTextRequestIdGetAsync(responseId.Id);
                        if (textResponse.Status.ToString() == "OK")
                        {
                            Console.WriteLine("Plain text paraphrasing: " + textResponse.ParaphraseReult);
                            break;
                        }
                        else
                            Thread.Sleep(200);
                    }
                }
                else
                {
                    textResponse = new ParaphraseTextResponse() { Status = responseId.Status, Message = responseId.Message };
                    Console.WriteLine("Text error: " + textResponse.Message);
                }
            }   
            catch (Exception ex)
            {   
                Console.WriteLine("Text exception: " + ex.ToString());
            }                
        }
    }
}
```
Visit our GitHub repository for a working code and sample files: https://github.com/groupdocs-rewriter-cloud/groupdocs-rewriter-cloud-dotnet
{{< /tab >}}

{{< tab tabNum="2" >}}

```python
import time
import groupdocs_rewriter_cloud
from groupdocs_rewriter_cloud.api.paraphrase_api import ParaphraseApi  
from groupdocs_rewriter_cloud.rest import ApiException
from groupdocs_rewriter_cloud.models import HttpStatusCode, ParaphraseTextRequest

api = ParaphraseApi()
file_api = FileApi()
api.api_client.configuration.client_id = "CLIENT_ID"
api.api_client.configuration.client_secret = "CLIENT_SECRET"
language = "en"
src_text = "YOUR_TEXT"
request = ParaphraseTextRequest(language=language, text=src_text)
status = api.paraphrase_text_post(request)
if status.status == groupdocs_rewriter_cloud.models.HttpStatusCode.ACCEPTED:
    while True:
        text_response = api.paraphrase_text_request_id_get(status.id)
        if text_response.status == groupdocs_rewriter_cloud.models.HttpStatusCode.OK:
            print(text_response.paraphrase_result)
            break
        time.sleep(2)
```
Visit our GitHub repository for a working code and sample files: https://github.com/groupdocs-rewriter-cloud/groupdocs-rewriter-cloud-python
{{< /tab >}}

{{< tab tabNum="3" >}}

```java
package com.groupdocs;
// Import classes:

import com.groupdocs.model.*;
import org.openapitools.client.api.ParaphraseApi;

public class Demo {
    public static void main(String[] args) {
        String basePath = "https://api.groupdocs.cloud/v2.0/rewriter";
        String cliendId = "YOUR_CLIENT_ID";
        String clientSecret = "YOUR_CLIENT_SECRET";

        ApiClient defaultClient = new ApiClient(basePath, cliendId, clientSecret, null);
        ParaphraseApi apiInstance = new ParaphraseApi(defaultClient);

        String s = "TEXT_TO_PARAPHRASE";

        ParaphraseTextRequest request = new ParaphraseTextRequest();
        request.setLanguage("en");
        request.setText(s);

        try {
            StatusResponse response = apiInstance.paraphraseTextPost(request);
            String response_id = response.getId();
            if (!response.getStatus().toString().equals("BadRequest")){
                while (true){
                    ParaphraseTextResponse paraphraseTextResponse = apiInstance.paraphraseTextRequestIdGet(response_id);
                    if (paraphraseTextResponse.getStatus().toString().equals("OK")) {
                        System.out.println(paraphraseTextResponse);
                        break;
                    }
                    try {
                        Thread.sleep(2000);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        } catch (ApiException e) {
            System.err.println("Exception when calling ParaphraseApi#paraphraseTextPost");
            System.err.println("Status code: " + e.getCode());
            System.err.println("Reason: " + e.getResponseBody());
            System.err.println("Response headers: " + e.getResponseHeaders());
            e.printStackTrace();
        }
    }
}
```
Visit our GitHub repository for a working code and sample files: https://github.com/groupdocs-rewriter-cloud/groupdocs-rewriter-cloud-java
{{< /tab >}}

{{< /tabs >}}
