---
id: "sdk"
weight: 50
date: "2023-12-15"
author: "Vladimir Lapin"
type: docs
url: rewriter/sdk
aliases:
- rewriter/available-sdks
productName: "GroupDocs.Rewriter Cloud"
title: Available SDKs
description: Find the latest software development kits (SDKs) that help you easily integrate GroupDocs.Rewriter Cloud into your applications.
keywords:
- .NET
- Python
- code
- programming
- SDK
---

GroupDocs offers software development kits (SDKs) for popular programming languages that make interaction with GroupDocs.Rewriter cloud services much easier. It allows you to focus on business logic rather than the technical details.

SDKs handle all the routine operations such as establishing connections, sending API requests, and parsing responses, wrapping all these tasks into a few simple methods. The following programming languages are supported:

- [GroupDocs.Rewriter Cloud for .NET](https://products.groupdocs.cloud/rewriter/net/)  
  Use the content processing features in any on-premise and web-based .NET application.
- [GroupDocs.Rewriter Cloud for Python](https://products.groupdocs.cloud/rewriter/python/)  
  Natively integrate content processing features into data analytics, finance, AI, and other Python applications and notebooks.
- [GroupDocs.Rewriter Cloud for Java](https://products.groupdocs.cloud/rewriter/java)  
  Use GroupDocs.Rewriter in cross-platform Java apps.

All SDKs are open-source distributed under [MIT License](https://opensource.org/licenses/MIT). You can freely use them for any projects, including commercial and proprietary applications, as well as modify any part of the code.

The provided code is fully tested and ready to run out of the box.

## SDK usage examples

See the examples below for a quick overview of how SDKs can make your development easier.

### Paraphrasing the text 

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
                        if ((HttpStatusCode)textResponse.Status == HttpStatusCode.OK)
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
{{< /tab >}}

{{< tab "Python" >}}

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

{{< tab "Java" >}}
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
            if (!response.getStatus().toString().equals("500")){
                while (true){
                    ParaphraseTextResponse paraphraseTextResponse = apiInstance.paraphraseTextRequestIdGet(response_id);
                    if (paraphraseTextResponse.getStatus().toString().equals("200")) {
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


