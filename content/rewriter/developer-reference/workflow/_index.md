---
id: "workflow"
weight: 10
date: "2023-12-15"
author: "Vladimir Lapin"
type: docs
url: rewriter/workflow
aliases:
- rewriter/introduction
- rewriter/json-request-details
- rewriter/supported-formats
- rewriter/working-with-files
- rewriter/working-with-folders
- rewriter/working-with-storage
productName: "GroupDocs.Rewriter Cloud"
title: Content processing workflow
description: An overview of the GroupDocs.Rewriter Cloud workflow.
keywords:
- flow
- process
- steps
- diagram
- process
- request
- response
---

GroupDocs.Rewriter Cloud can paraphrase, summarize, simplify and otherwise process texts and and documents in a [number of formats](/rewriter/supported-file-formats/) with just 2 REST API calls or a few lines of code in any programming language supported by [SDK](/rewriter/sdk/). Read [Hello, world!](/rewriter/hello-world/) article for a hands-on example.

![GroupDocs.Rewriter Cloud workflow](/rewriter/workflow/groupdocs-rewriter-flow.png)

## 1. Send text or file for processing

In the request body, provide JSON with a plain text or a _Base64_ encoded file along with mandatory and optional processing parameters.

To authorize the request to use GroupDocs.Rewriter Cloud, pass the [access token](/rewriter/authorization/) in _Authorization_ header of the request (_Bearer Token_).

{{% alert color="primary" %}} 
If you are using [GroupDocs.Rewriter Cloud SDK](/rewriter/sdk/), you do not have to worry about content encoding, getting an access token, setting request headers, and other technical details. The SDK will perform all routine operations: from establishing a connection with the GroupDocs.Rewriter Cloud API to receiving and parsing the response.
{{% /alert %}} 

## 2. Get the request ID

Your content processing request is queued and you will receive a unique identifier that can be used to retrieve results.

For more information on what happens in the cloud, read [Behind the scenes](#behind-the-scenes) section.

## 3. Fetch the processed content

Just call the GroupDocs.Rewriter Cloud API with the ID of the request received on the previous step to retrieve the processed content. The processing may take a second or two, depending on the file size and complexity and the current GroupDocs.Rewriter load. For more information on what happens in the cloud, read [Behind the scenes](#behind-the-scenes) section.

To authorize your request, pass the [access token](/rewriter/authorization/) in _Authorization_ header.

{{% alert color="primary" %}} 
If you are using [GroupDocs.Rewriter Cloud SDK](/rewriter/available-sdks/), it will handle all authorization routines.
{{% /alert %}} 

## 4. Working with the processed content

If the processing is successful, you will receive the results in JSON format along with processing statistics. Processed files are returned as URLs which can be downloaded, displayed on the screen, or written to a database. Processed text is returned as an array of strings.

{{% alert color="primary" %}}
[GroupDocs.Rewriter Cloud SDK](/rewriter/available-sdks/) takes care of all the routine operations so you can get content directly with no extra effort.
{{% /alert %}}

## Behind the scenes

Natural language processing is a resource-intensive process that involves sophisticated neural networks and complex calculations. Even with high-performance servers, this can take some time, especially when processing large amounts of content and reading large files.

To balance resources under high load and ensure reliable and secure operation, we have introduced _queued processing_. Instead of being immediately processed, the source text or file is placed in a queue under a unique identifier. The queue is constantly monitored and processed in the background using advanced load balancing techniques.

Once the processing is finished, the result is saved to internal storage, from where it can be retrieved using the unique ID within **24 hours** after a content processing request has been made.
