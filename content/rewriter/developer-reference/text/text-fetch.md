---
id: "text-fetch"
weight: 20
date: "2023-11-01"
author: "Vladimir Lapin"
type: docs
url: rewriter/text/fetch/
productName: "GroupDocs.Rewriter Cloud"
title: Fetching results
description: How to fetch the result from the GroupDocs.Rewriter Cloud queue.
keywords:
- paraphrase
- summarize
- simplify
- text
- content
- queue
- get
- obtain
- fetch
- result
---

When text is submitted for processing, it is queued to ensure a stable response even under high load. To obtain the results, send a **GET** request to the `https://api.groupdocs.cloud/v2.0/rewriter/{task}/text/{request ID}` GroupDocs.Rewriter Cloud REST API endpoint, where **task** means what you want to do: detect, paraphrase, simpllify, summarize or synonymize. This request does not require [access token](/rewriter/authorization/).

## Processed texts

Processed texts are returned in JSON format in the response body and are slightly different according to task.

{{< tabs "example1">}}
{{< tab "Detect" >}}

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
`probability` | Probability that provided text was paraphrased.
`isParaphrased` | If provided text was paraphrased.
{{< /tab >}}
{{< tab "Paraphrase" >}}

```json
{
  "status": status code,
  "message": string,
  "paraphraseResult": string,
  "paraphraseResults": list of strings
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`paraphraseResult` | Paraphrased text, this property is returned if a single text was sent.
`paraphraseResults` | Paraphrased texts, this property is returned if several texts were sent for paraphrasing.
{{< /tab >}}
{{< tab "Simplify" >}}

```json
{
  "status": status code,
  "message": string,
  "simplifyResult": string,
  "simplifyResults": list of strings
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`simplifyResult` | Simpllified text, this property is returned if a single text was sent.
`simplifyResults` | Simplified texts, this property is returned if several texts were sent for simplifying.
{{< /tab >}}
{{< tab "Summarize" >}}

```json
{
  "status": status code,
  "message": string,
  "summarizationResult": string,
  "sumarizationResults": list of strings
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`summarizationResult` | Summarized text, this property is returned if a single text was sent.
`summarizationResults` | Summarized texts, this property is returned if several texts were sent for summarization.
{{< /tab >}}
{{< tab "Synonymize" >}}

```json
{
  "status": status code,
  "message": string,
  "synonymizerResults": list of strings
}
```

Property | Description
-------- | -----------
`status` | HTTP response status code.
`message` | Verbose status message.
`paraphraseResults` | List of synonyms for the provided word or phrase
{{< /tab >}}
{{< /tabs >}}
If the text is not yet processed, try fetching the result in a couple of seconds using the same ID.

{{% alert color="primary" %}} 
Results are stored in the GroupDocs cloud and can be obtained by the task ID within **24 hours** after the text was sent for processing.
{{% /alert %}}

## cURL example for authorized paraphrasing

{{< tabs "example2">}}
{{< tab "Request" >}}

```bash
curl --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/text/dae5390e-3658-4bff-85bf-4a77cc04eaa5_text' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...LxLejtsVFwrZpHA'
```
{{< /tab >}}
{{< tab "Response" >}}

```json
{
    "paraphraseReult": "Hello, everyone! We are going to try to recast this text as something new.",
    "paraphraseResults": null,
    "sourceList": null,
    "targetList": null,
    "statusCode": 200,
    "message": "Text processed successfully"
}
```
{{< /tab >}}
{{< /tabs >}}
