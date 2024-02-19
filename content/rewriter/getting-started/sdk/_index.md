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

All SDKs are open-source distributed under [MIT License](https://opensource.org/licenses/MIT). You can freely use them for any projects, including commercial and proprietary applications, as well as modify any part of the code.

The provided code is fully tested and ready to run out of the box.

## SDK usage examples

See the examples below for a quick overview of how SDKs can make your development easier.

### Paraphrasing the text 

{{< tabs tabTotal="1" tabID="1" tabName1=".NET (C#)">}}
{{< tab tabNum="1" >}}
```csharp
public TextResponse RewriteText(Configuration conf)
{
    string language = "en";
    string text = "The client’s mission is to make the world a healthier place and to make traveling and visiting public places safer and more comfortable for people.";
    // Initialize GroupDocs.Rewriter API
    RewriterApi api = new RewriterApi(conf);
    // Send text for processing
    RewriteTextRequest request = api.CreateTextRequest(language, text);
    // Return paraphrased text
    TextResponse response = api.RunRewritingTextTask(request);
    return response;
}
```

Visit our GitHub repository for a working code and sample files: https://github.com/groupdocs-rewriter-cloud/groupdocs-rewriter-cloud-dotnet
{{< /tab >}}
{{< /tabs >}}
