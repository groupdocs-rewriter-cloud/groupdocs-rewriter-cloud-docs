---
id: "file-fetch"
weight: 30
date: "2023-11-01"
author: "Vladimir Lapin"
type: docs
url: /rewriter/file/fetch/
productName: "GroupDocs.Rewriter Cloud"
title: Fetching file results
description: How to fetch the result from the GroupDocs.Rewriter Cloud queue.
keywords:
- paraphrase
- summarize
- file
- document
- content
- queue
- get
- obtain
- fetch
- result
---

When file is submitted for processing, it is queued to ensure a stable response even under high load. To obtain the results, send a **GET** request to the `https://api.groupdocs.cloud/v2.0/rewriter/{task}/document/{request ID}` GroupDocs.Rewriter Cloud REST API endpoint, where **task** means what you want to do: detect, paraphrase, simpllify or summarize. This request does not require [access token](/rewriter/authorization/).

## Processed files

Processed files are returned in JSON format in the response body and are slightly different according to task.

{{< tabs tabID="2" tabTotal="5" tabName1="Detect" tabName2="Paraphrase" tabName3="Simplify" tabName4="Summarize" >}}
{{< tab tabNum="1" >}}

```json
{
  "status": status code,
  "message": string,
  "probability": float,
  "isParaphrased": boolean
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`probability` | Probability that provided file was paraphrased.
`isParaphrased` | If provided file was paraphrased.
{{< /tab >}}
{{< tab tabNum="2" >}}

```json
{
  "status": status code,
  "message": string,
  "url": string
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`url` | Link to paraphrased file.
{{< /tab >}}
{{< tab tabNum="3" >}}

```json
{
  "status": status code,
  "message": string,
  "url": string
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`url` | Link to simplified file.
{{< /tab >}}
{{< tab tabNum="4" >}}

```json
{
  "status": status code,
  "message": string,
  "url": string
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`url` | Link to summarized file.
{{< /tab >}}
{{< /tabs >}}
If the file is not yet processed, try fetching the result in a couple of seconds using the same ID.

{{% alert color="primary" %}} 
Files are stored in the GroupDocs cloud and can be obtained by the task ID within **24 hours** after the file was sent for processing.
{{% /alert %}}

## cURL example

{{< tabs tabID="1" tabTotal="2" tabName1="Request" tabName2="Response" >}}
{{< tab tabNum="1" >}}
```bash
curl --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/document/dae5390e-3658-4bff-85bf-4a77cc04eaa5' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...LxLejtsVFwrZpHA'
```
{{< /tab >}}
{{< tab tabNum="2" >}}
```json
{
	"status": 200,
	"message": "Pdf document paraphrased",
	"url": "https://rewriter-groupdocs-app.s3.us-west-2.amazonaws.com/0cd7b09d-4d63-4bcd-a9a5-dfd72897aa17.pdf...ff474526313a24821e98"
}
```
{{< /tab >}}
{{< /tabs >}}
