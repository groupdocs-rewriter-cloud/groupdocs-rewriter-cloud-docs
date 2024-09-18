---
id: "simplify-file-sdk"
weight: 40
date: "2023-11-01"
author: "Vladimir Lapin"
type: docs
url: rewriter/file/sdk/simmplify
productName: "GroupDocs.Rewriter Cloud"
title: Simplifying files with GroupDocs.Rewriter SDK
description: How to use GroupDocs.Rewriter Cloud SDK for files simplification.
keywords:
- simplify
- API
- porogram
- language
- file
- content
---

## Learn more

Although you can directly call the GroupDocs.Rewriter Cloud REST API to [send file](/rewriter/file/request/) and [fetch the result](/rewriter/file/fetch/), there is a much easier way to implement required functionality in your applications. We provide software development kits (SDKs) for all popular programming languages. They wrap up all routine operations such as establishing connections, sending API requests, and parsing responses into a few simple methods. It makes interaction with GroupDocs.Rewriter Cloud services much easier, allowing you to focus on business logic rather than technical details.

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
	  public class FileSimplifier
	  {
		    public FileSimplifier()
		    {
            Configuration config = new Configuration();
			      config.OAuthFlow = OAuthFlow.APPLICATION;
			      config.OAuthClientId = "YOU_CLIENT_ID";
			      config.OAuthClientSecret = "YOU_CLIENT_SECRET";
            config.BasePath = "https://api.groupdocs.cloud/v2.0/rewriter";
            SimplifyApi pApi = new SimplifyApi(conf);
            FileApi fileApi = new FileApi(conf);
            string sourceLanguage = "en";
            string format = "Pdf";
            string path = "/path/to/myFile.pdf";
            byte[] file = File.ReadAllBytes(path);
            MemoryStream ms = new MemoryStream(file);
            string url = fileApi.FileUploadPost(format, ms);
            SimplifyFileResponse response = new SimplifyFileResponse();
            SimplifyFileRequest request = new SimplifyFileRequest(
                format: ParaphraseFileRequest.FormatEnum.Pdf,
                outputFormat: SupportedConversionsFormats.Pdf,
                language: sourceLanguage,
                savingMode: FileSavingMode.Files,
                url: url);
            StatusResponse responseId = await api.SimplifyDocumentPostAsync(request);
            try
            {
                if (responseId.Status.ToString() == "Accepted")
                {
                    while (true)
                    {
                        response = await api.SimplifyDocumentRequestIdGetAsync(responseId.Id);
                        if (response.Status.ToString() == "OK")
                            break;
                        else
                            Thread.Sleep(2000);
                    }
                    using (var client = new HttpClient())
                    {
                        string saveName = $"/path/to/result.pdf";
                        var result = await client.GetByteArrayAsync(response.Url);
                        File.WriteAllBytes(saveName, result);
                    }
                }
                else
                {
                    response = new SimplifyFileResponse() { Status = responseId.Status, Message = responseId.Message };
                    Console.WriteLine("File error: " + response.Message);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine("File exception: " + ex.ToString());
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
from groupdocs_rewriter_cloud.models import SimplifySupportedFromats, SimplifyFileRequest, SupportedConversionsFormats

api = SimplifyApi()
file_api = FileApi()
api.api_client.configuration.client_id = "CLIENT_ID"
api.api_client.configuration.client_secret = "CLIENT_SECRET"
language = "en"
file_format = "Pdf"
file_path = "/path/to/myFile.pdf"
file_url = file_api.file_upload_post(format=file_format, file=file_path)
request = SimplifyFileRequest(language=language, url=file_url, format=SimplifySupportedFromats.PDF, outputFormat=SupportedConversionsFormats.PDF)
status = api.simplify_document_post(request)
if status.status == groupdocs_rewriter_cloud.models.HttpStatusCode.ACCEPTED:
    while True:
        file_response = api.simplify_document_request_id_get(status.id)
        if file_response.status == groupdocs_rewriter_cloud.models.HttpStatusCode.OK:
            print(f'[{file_response.status}] {file_response.message}')
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
import org.openapitools.client.api.FileApi;
import java.io.File;

public class Demo {
    public static void main(String[] args) {
        // Get Client Id and Client Secret from https://dashboard.groupdocs.cloud          
        String basePath = "https://api.groupdocs.cloud/v2.0/rewriter";
        String cliendId = "YOUR_CLIENT_ID";
        String clientSecret = "YOUR_CLIENT_SECRET";
        ApiClient defaultClient = new ApiClient(basePath, cliendId, clientSecret, null);

        // Upload file
        FileApi fileApi = new FileApi(defaultClient);
        String fileName = "FILE_PATH";
        File fileToUpload = new File(fileName);
        String file_url = null;

        try {
            String file_url = fileApi.fileUploadPost("FILE_FORMAT", fileToUpload);
        }
        catch(ApiException e){
                System.err.println("Exception when calling FileApi#fileUploadPost");
                System.err.println("Status code: " + e.getCode());
                System.err.println("Reason: " + e.getResponseBody());
                System.err.println("Response headers: " + e.getResponseHeaders());
                e.printStackTrace();
        }  

        // Create instance of the SimplifyApi if the file was uploaded successfully
        if (file_url != null){                  
            SimplifyApi apiInstance = new SimplifyApi(defaultClient);

            SimplifyFileRequest fileRequest = new SimplifyFileRequest();

            fileRequest.setLanguage("en");
            fileRequest.setFormat(SimplifySupportedFromats.PDF);
            fileRequest.setOutputFormat(SupportedConversionsFormats.PDF);
            fileRequest.setSavingMode(FileSavingMode.FILES);
            fileRequest.setUrl(file_url);
            fileRequest.setOrigin("FILE_URL");

            try {
                StatusResponse response = apiInstance.simplifyDocumentPost(fileRequest);
                String response_id = response.getId();
                if (!response.getStatus().toString().equals("BadRequest")) {
                    while (true) {
                        SimplifyFileResponse simplifyResponse = apiInstance.simplifyDocumentRequestIdGet(response_id);
                        if (simplifyResponse.getStatus().toString().equals("OK")) {
                            System.out.println(simplifyResponse);
                            break;
                        }
                        try {
                            Thread.sleep(2000);
                        } catch (InterruptedException e) {
                            e.printStackTrace();
                        }
                    }
                }
            }
            catch (ApiException e) {
                System.err.println("Exception when calling SimplifyApi#simplifyDocumentPost");
                System.err.println("Status code: " + e.getCode());
                System.err.println("Reason: " + e.getResponseBody());
                System.err.println("Response headers: " + e.getResponseHeaders());
                e.printStackTrace();
            }
        }
    }
}
```
Visit our GitHub repository for a working code and sample files: https://github.com/groupdocs-rewriter-cloud/groupdocs-rewriter-cloud-java
{{< /tab >}}

{{< /tabs >}}
