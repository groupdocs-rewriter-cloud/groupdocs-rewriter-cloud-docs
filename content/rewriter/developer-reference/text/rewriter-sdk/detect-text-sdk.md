---
id: "detect-text-sdk"
weight: 20
date: "2023-11-01"
author: "Vladimir Lapin"
type: docs
url: /rewriter/text/sdk/detect
productName: "GroupDocs.Rewriter Cloud"
title: Detecting paraphrases in text with GroupDocs.Rewriter SDK
description: How to use GroupDocs.Rewriter Cloud SDK for paraphrase detection in texts.
keywords:
- paraphrase
- detection
- API
- program
- language
- text
- content
---

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
	  public class TextDetector
	  {
		    public TextDetector()
		    {
            Configuration config = new Configuration();
			      config.OAuthFlow = OAuthFlow.APPLICATION;
			      config.OAuthClientId = "YOU_CLIENT_ID";
			      config.OAuthClientSecret = "YOU_CLIENT_SECRET";
            config.BasePath = "https://api.groupdocs.cloud/v2.0/rewriter";
            DetectApi api = new DetectApi(conf);
            string srcText = "YOUR_TEXT";
            string sourceLanguage = "en";
            DetectionTextResponse textResponse = new DetectionTextResponse();
            DetectionTextRequest request = new DetectionTextRequest(
                language: sourceLanguage,
                text: srcText);
            StatusResponse responseId = await api.DetectTextPostAsync(request);;
            try
            {
                if (responseId.Status.ToString() == "Accepted")
                {
                    while (true)
                    {  
                        textResponse = await api.DetectTextRequestIdGetAsync(responseId.Id);
                        if (textResponse.Status.ToString() == "OK")
                        {
                            Console.WriteLine("Plain text detection probability: " + textResponse.Probability);
                            break;
                        }
                        else
                            Thread.Sleep(2000);
                    }
                }
                else
                {
                    textResponse = new DetectionTextResponse() { Status = responseId.Status, Message = responseId.Message };
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
from groupdocs_rewriter_cloud.api.detect_api import DetectApi  
from groupdocs_rewriter_cloud.models.detection_text_request import DetectionTextRequest
from groupdocs_rewriter_cloud.rest import ApiException
api = DetectApi()
file_api = FileApi()
api.api_client.configuration.client_id = "CLIENT_ID"
api.api_client.configuration.client_secret = "CLIENT_SECRET"
language = "en"
src_text = "YOUR_TEXT"
request = DetectionTextRequest(language=language, text= src_text)
status = api.detect_text_post(request)
if status.status == groupdocs_rewriter_cloud.models.HttpStatusCode.ACCEPTED:
    while True:
        text_response = api.detect_text_request_id_get(status.id)
        if text_response.status == groupdocs_rewriter_cloud.models.HttpStatusCode.OK:
            print(text_response.probability)
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
import org.openapitools.client.api.DetectApi;

public class Demo {
    public static void main(String[] args) {
        String basePath = "https://api.groupdocs.cloud/v2.0/rewriter";
        String cliendId = "YOUR_CLIENT_ID";
        String clientSecret = "YOUR_CLIENT_SECRET";

        ApiClient defaultClient = new ApiClient(basePath, cliendId, clientSecret, null);
        DetectApi apiInstance = new DetectApi(defaultClient);

        String s = "TEXT_TO_DETECT";

        DetectionTextRequest request = new DetectionTextRequest();
        request.setLanguage("en");
        request.setText(s);

        try {
            StatusResponse response = apiInstance.detectTextPost(request);
            String response_id = response.getId();
            if (!response.getStatus().toString().equals("BadRequest")){
                while (true){
                    DetectionTextResponse detectTextResponse = apiInstance.detectTextRequestIdGet(response_id);
                    if (detectTextResponse.getStatus().toString().equals("OK")) {
                        System.out.println(detectTextResponse);
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
            System.err.println("Exception when calling DetectApi#detectTextPost");
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
