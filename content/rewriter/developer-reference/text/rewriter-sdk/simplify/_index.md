---
id: "simplify-text-sdk"
weight: 40
date: "2023-11-01"
author: "Vladimir Lapin"
type: docs
url: /rewriter/text/sdk/simmplify
productName: "GroupDocs.Rewriter Cloud"
title: Simplifying text with GroupDocs.Rewriter SDK
description: How to use GroupDocs.Rewriter Cloud SDK for texts simplification.
keywords:
- simplify
- API
- porogram
- language
- text
- content
---

## Learn more

Although you can directly call the GroupDocs.Rewriter Cloud REST API to [send text](/rewriter/text/request/) and [fetch the result](/rewriter/text/fetch/), there is a much easier way to implement required functionality in your applications. We provide software development kits (SDKs) for all popular programming languages. They wrap up all routine operations such as establishing connections, sending API requests, and parsing responses into a few simple methods. It makes interaction with GroupDocs.Rewriter Cloud services much easier, allowing you to focus on business logic rather than technical details.

{{< tabs "example1">}}

{{< tab ".NET (C#)" >}}

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
	  public class TextSimplifier
	  {
		    public TextSimplifier()
		    {
            Configuration config = new Configuration();
			      config.OAuthFlow = OAuthFlow.APPLICATION;
			      config.OAuthClientId = "YOU_CLIENT_ID";
			      config.OAuthClientSecret = "YOU_CLIENT_SECRET";
            config.BasePath = "https://api.groupdocs.cloud/v2.0/rewriter";
            SimplifyApi api = new SimplifyApi(conf);
            string srcText = "YOUR_TEXT";
            string sourceLanguage = "en";
            SimplifyTextResponse textResponse = new SimplifyTextResponse();
            BaseTextRequest request = new BaseTextRequest(
                language: sourceLanguage,
                text: srcText);
            StatusResponse responseId = await api.SimplifyTextPostAsync(request);
            try
            {
                if (responseId.Status.ToString() == "Accepted")
                {
                    while (true)
                    {
                        textResponse = await api.SimplifyTextRequestIdGetAsync(responseId.Id);
                        if (textResponse.Status.ToString() == "OK")
                        {
                            Console.WriteLine("Plain text simplified: " + textResponse.SimplifyReult);
                            break;
                        }
                        else
                            Thread.Sleep(200);
                    }
                }
                else
                {
                    textResponse = new SimplifyTextResponse() { Status = responseId.Status, Message = responseId.Message };
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

{{< tab "Python" >}}

```python
import time
import groupdocs_rewriter_cloud
from groupdocs_rewriter_cloud.api.simplify_api import SimplifyApi  
from groupdocs_rewriter_cloud.rest import ApiException
from groupdocs_rewriter_cloud.models import SimplifyTextRequest

api = SimplifyApi()
file_api = FileApi()
api.api_client.configuration.client_id = "CLIENT_ID"
api.api_client.configuration.client_secret = "CLIENT_SECRET"
language = "en"
src_text = "YOUR_TEXT"
request = SimplifyTextRequest(language=language, text=src_text)
status = api.simplify_text_post(request)
if status.status == groupdocs_rewriter_cloud.models.HttpStatusCode.ACCEPTED:
    while True:
        text_response = api.simplify_text_request_id_get(status.id)
        if text_response.status == groupdocs_rewriter_cloud.models.HttpStatusCode.OK:
            print(text_response.simplify_result)
            break
        time.sleep(2)
```
Visit our GitHub repository for a working code and sample files: https://github.com/groupdocs-rewriter-cloud/groupdocs-rewriter-cloud-python
{{< /tab >}}

{{< tab "Java" >}}

```java
package com.groupdocs;
// Import classes:

import com.groupdocs.model.*;
import org.openapitools.client.api.SimplifyApi;

public class Demo {
    public static void main(String[] args) {
        String basePath = "https://api.groupdocs.cloud/v2.0/rewriter";
        String cliendId = "YOUR_CLIENT_ID";
        String clientSecret = "YOUR_CLIENT_SECRET";

        ApiClient defaultClient = new ApiClient(basePath, cliendId, clientSecret, null);
        SimplifyApi apiInstance = new SimplifyApi(defaultClient);

        String s = "TEXT_TO_SIMPLIFY";

        BaseTextRequest request = new BaseTextRequest();
        request.setLanguage("en");
        request.setText(s);

        try {
            StatusResponse response = apiInstance.simplifyTextPost(request);
            String response_id = response.getId();
            if (!response.getStatus().toString().equals("BadRequest")){
                while (true){
                    SimplifyTextResponse simplifyTextResponse = apiInstance.simplifyTextRequestIdGet(response_id);
                    if (simplifyTextResponse.getStatus().toString().equals("OK")) {
                        System.out.println(simplifyTextResponse);
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
            System.err.println("Exception when calling SimplifyApi#simplifyTextPost");
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
