---
id: "text-request"
weight: 10
date: "2023-10-20"
author: "Vladimir Lapin"
type: docs
url: /rewriter/text/request/
productName: "GroupDocs.Rewriter Cloud"
title: Sending texts for processing
description: How to send texts for processing to the selected language.
keywords:
- paraphrase
- summarize
- send
- input
- request
- text
- content
---

To process plain text, send a **POST** request to the `https://api.groupdocs.cloud/v2.0/rewriter/{task}/text` GroupDocs.Rewriter Cloud REST API endpoint, where **task** means what you want to do: detect, paraphrase, simpllify, summarize or synonymize.. To authorize the request, pass the [access token](/translation/authorization/) in **Authorization** header (_Bearer_ authentication).

The text and processing parameters are provided in JSON format in the request body. 

{{< tabs "example1">}}
{{< tab "Detect" >}}

```json
{
  "language": string,
  "text": string,
  "texts": list of strings
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source text.
`text` | Text to be detected for paraphrasing.
`texts` | Texts to be detected for paraphrasing.
{{< /tab >}}
{{< tab "Paraphrase" >}}

```json
{
  "language": string,
  "text": string,
  "texts": list of string,
  "suggestions": string,
  "diversityDegree": string
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source text.
`text` | Text for paraphrasing.
`texts` | Texts for paraphrasing.
`suggestions` | Number of variants to return, accepted values One, Two or Three.
`diversityDegree` | Degree of paraphrasing, accepted values Off, Medium and High.
{{< /tab >}}
{{< tab "Simplify" >}}

```json
{
  "language": string,
  "text": string,
  "texts": list of strings
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source text.
`text` | Text for simplification.
`texts` | Texts for simplification.
{{< /tab >}}
{{< tab "Summarize" >}}

```json
{
  "language": string,
  "text": string,
  "texts": list of strings
  "summarizationDegree": string
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source text.
`text` | Text to be detected for summarization.
`texts` | Texts to be detected for summarization.
`summarizationDegree ` | Summarization degree, accepted values Off, Medium and High.
{{< /tab >}}
{{< tab "Synonymize" >}}

```json
{
  "language": string,
  "text": string,
  "texts": list of strings
  "synonyms": string
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source text.
`text` | Text to be detected for paraphrasing
`texts` | Texts to be detected for paraphrasing.
`synonyms` | Number of synonyms to return, accepted values One to Five and All.
{{< /tab >}}
{{< /tabs >}}

{{% alert color="primary" %}} 
If the processed text is very long, you may encounter an error when calling via cURL in a shell command. Use the `getconf ARG_MAX` command to check the maximum length of the command arguments (in bytes).
{{% /alert %}}

## Evaluation mode

To use GroupDocs.Rewriter Cloud REST API in [evaluation mode](/rewriter/evaluation/), send a **POST** request to the endpoint `https://api.groupdocs.cloud/v2.0/rewriter/{task}/text/trial`.

This endpoint does not use the **Authorization** header, so there is no need to generate an access token. All other parameters remain the same as in [regular](/rewriter/subscription/) text translation requests.

## Return value

If successful, this method returns JSON with a unique identifier (value of the `id` property) of the request in the [queue](/rewriter/workflow/):

```json
{
    "status": 202,
    "message": "Starting",
    "id": "dae5390e-3658-4bff-85bf-4a77cc04eaa5_text"
}
```

Otherwise, it returns a HTTP status code corresponding to the error.

## What’s next

Processing will take a few seconds, depending on the size of the text and the current GroupDocs.Rewriter Cloud load. See the article [Fetching results](/rewriter/text/fetch/) for information on how to get results from the server.

## cURL example for paraphrasing

{{< tabs tabID="2" tabTotal="3" tabName1="Request (free tier/paid plan)" tabName2="Request (evaluation)" tabName3="Response" >}}
{{< tab tabNum="1" >}}

```bash
curl --request POST --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/text' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...LxLejtsVFwrZpHA' \
--data '{
  "language": "en",
  "text": "Hello, everyone! We will try to rephrase this text into something new.",
  "suggestions": "One",
  "diversityDegree": "Medium"
}'
```
{{< /tab >}}
{{< tab tabNum="2" >}}

```bash
curl --request POST --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/text/trial' \
--header 'Content-Type: application/json' \
--data '{
  "language": "en",
  "text": "Hello, everyone! We will try to rephrase this text into something new.",
  "suggestions": "One",
  "diversityDegree": "Medium"
}'
```
{{< /tab >}}
{{< tab tabNum="3" >}}

```json
{
    "status": 202,
    "message": "Starting",
    "id": "dae5390e-3658-4bff-85bf-4a77cc04eaa5_text"
}
```
{{< /tab >}}
{{< /tabs >}}
