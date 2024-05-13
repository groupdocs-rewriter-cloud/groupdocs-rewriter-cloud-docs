---
id: "file-request"
weight: 10
date: "2023-10-20"
author: "Vladimir Lapin"
type: docs
url: /rewriter/file/request/
productName: "GroupDocs.Rewriter Cloud"
title: Sending files for processing
description: How to send files for processing to the selected language.
keywords:
- paraphrase
- summarize
- send
- input
- request
- file
- content
---

To process file, send a **POST** request to the `https://api.groupdocs.cloud/v2.0/rewriter/{task}/document` GroupDocs.Rewriter Cloud REST API endpoint, where **task** means what you want to do: detect, paraphrase, simpllify or summarize. To authorize the request, pass the [access token](/rewriter/authorization/) in **Authorization** header (_Bearer_ authentication).

The link to file and processing parameters are provided in JSON format in the request body. 

{{< tabs "example1">}}
{{< tab "Detect" >}}

```json
{
  "language": string,
  "url": string,
  "minLength": int,
  "format": string
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source file.
`url ` | Link to file.
`minLength ` | Minimal length of files textual content to apply paraphrasing detection.
`format ` | File format.
{{< /tab >}}
{{< tab "Paraphrase" >}}

```json
{
  "language": string,
  "url": string,
  "savingMode": string,
  "outputFormat": string,
  "diversityDegree": string,
  "format": string
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source file.
`url` | Link to file.
`savingMode ` | How the result shoud be saved, as file, as archive or both.
`outputFormat ` | Format of the paraphrased file.
`diversityDegree` | Degree of paraphrasing, accepted values Off, Medium and High.
`format` | File format.
{{< /tab >}}
{{< tab "Simplify" >}}

```json
{
  "language": string,
  "url": string,
  "savingMode": string,
  "outputFormat": string,
  "format": string
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source file.
`url` | Link to file.
`savingMode ` | How the result shoud be saved, as file, as archive or both.
`outputFormat ` | Format of the simplified file.
`format` | File format.{{< /tab >}}
{{< tab "Summarize" >}}

```json
{
  "language": string,
  "url": string,
  "savingMode": string,
  "outputFormat": string,
  "summarization": string,
  "format": string,
  "minLength": int
}
```
Property | Description
-------- | -----------
`language` | [Language code](/rewriter/languages/) of the source file.
`url` | Link to file.
`savingMode ` | How the result shoud be saved, as file, as archive or both.
`outputFormat ` | Format of the paraphrased file.
`summarizationDegree` | Summarization degree, accepted values Off, Medium and High.
`format` | File format.
`minLength ` | Minimal length of files textual content to apply summarization.
{{< /tab >}}
{{< /tabs >}}

{{% alert color="primary" %}} 
If the processed file is very long, you may encounter an error when calling via cURL in a shell command. Use the `getconf ARG_MAX` command to check the maximum length of the command arguments (in bytes).
{{% /alert %}}

## Evaluation mode

To use GroupDocs.Rewriter Cloud REST API in [evaluation mode](/rewriter/evaluation/), send a **POST** request to the endpoint `https://api.groupdocs.cloud/v2.0/rewriter/{task}/document/trial`.

This endpoint does not use the **Authorization** header, so there is no need to generate an access token. All other parameters remain the same as in [regular](/rewriter/subscription/) text requests.

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
curl --request POST --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/document' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...LxLejtsVFwrZpHA' \
--data '{
  "language": "en",
  "url": "https://rewriter-groupdocs-app.s3.us-west-2.amazonaws.com/0cd7b09d-4d63-4bcd-a9a5-dfd72897aa17.pdf...ff474526313a24821e98",
  "savingMode": "Files",
  "outputFormat": "Pdf",
  "diversityDegree": "Off",
  "format": "Pdf"
}'
```
{{< /tab >}}
{{< tab tabNum="2" >}}

```bash
curl --request POST --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/document/trial' \
--header 'Content-Type: application/json' \
--data '{
  "language": "en",
  "url": "https://rewriter-groupdocs-app.s3.us-west-2.amazonaws.com/0cd7b09d-4d63-4bcd-a9a5-dfd72897aa17.pdf...ff474526313a24821e98",
  "savingMode": "Files",
  "outputFormat": "Pdf",
  "diversityDegree": "Off",
  "format": "Pdf"
}'
```
{{< /tab >}}
{{< tab tabNum="3" >}}

```json
{
    "status": 202,
    "message": "Starting",
    "id": "dae5390e-3658-4bff-85bf-4a77cc04eaa5"
}
```
{{< /tab >}}
{{< /tabs >}}
