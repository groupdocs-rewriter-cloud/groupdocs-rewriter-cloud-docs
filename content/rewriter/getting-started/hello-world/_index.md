---
id: "hello-world"
weight: 40
date: "2023-12-15"
author: "Vladimir Lapin"
type: docs
url: rewriter/hello-world
aliases:
- rewriter/quickstart
productName: "GroupDocs.Rewriter Cloud"
title: Hello, world!
description: Get familiar with GroupDocs.Rewriter Cloud by running a bare minimum example.
keywords:
- hello world
- evaluation
- example
- sample
- dummies
- code
---

In this article, you will learn how to paraphrase a short fragment of text from English to German using GroupDocs.Rewriter Cloud REST API.

{{% alert color="primary" %}} 
We assume that you have already [signed up](/rewriter/sign-up/) to the service and have not yet exceeded your [free subscription plan](/rewriter/subscription/) limits.
{{% /alert %}} 

## You will need

- [Any system](/rewriter/system-requirements/) with Internet connection.
- A web browser.
- Any tool that allows you to make REST API calls, such as [cURL](https://curl.se/) or [Postman](https://www.postman.com/). The article provides cURL examples.
- **10 minutes** of spare time.

## Getting an access token

The GroupDocs.Rewriter Cloud API is fully compliant with industry security standards and best practices. Data transfer is carried out using JWT authentication, which eliminates all possibilities of data theft or disclosure.

To obtain a JWT token, get the _Client ID_ and _Client Secret_ credentials:

1. Sign in to [GroupDocs Cloud API Dashboard](https://dashboard.groupdocs.cloud/).
2. Go to [**Applications**](https://dashboard.groupdocs.cloud/applications) page.
3. Create the `samples` storage for exchanging files by clicking the _plus_ icon and following the required steps. _Internal storage_ with _24-hour_ retention will suffice.
4. Provide the application name, for example, _HelloWorld_.
5. Click **Save** button.
6. Click the newly created **HelloWorld** application and copy the values from **Client Id** and **Client Secret** fields.

Now request an access token with the following API call:

```bash
curl --request POST --location 'https://id.groupdocs.cloud/connect/token' \
     --header 'Content-Type: application/x-www-form-urlencoded' \
     --data-urlencode 'grant_type=client_credentials' \
     --data-urlencode 'client_id=CLIENT-ID-VALUE' \
     --data-urlencode 'client_secret=CLIENT-SECRET-VALUE'
```

You should get a response that looks something like this:

```json
{
	"access_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...LxLejtsVFwrZpHA",
	"expires_in": 3600,
	"token_type": "Bearer"
}
```

{{% alert color="primary" %}} 
The access token will be valid for the number of seconds specified in the `expires_in` property. If it has expired, request a new one using the same credentials.
{{% /alert %}} 

## Sending text for rephrasing

Let's rephrase the following simple text:

```
Hello, everyone! We will try to rephrase this text into something new.
```

The rephrasing is carried out in 2 stages. First we need to POST a request to the GroupDocs.Rewriter Cloud API with parameters in JSON format in the body:

```bash
curl --request POST --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/text' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...LxLejtsVFwrZpHA' \
--data '{
  "language": "en",
  "text": "Hello, everyone! We will try to rephrase this text into something new.",
  "suggestions": "one",
  "diversityDegree": "medium"
}'
```

The authorization header must contain the access token obtained [earlier](#getting-an-access-token).

Wait a moment. The request will be placed in the queue and you will get its unique identifier. For example:

```json
{
	"status": 202,
	"message": "Starting",
	"id": "dae5390e-3658-4bff-85bf-4a77cc04eaa5_text"
}
```

## Getting paraphrased text

The text processing will take a second or two, depending on the length of the text and the current GroupDocs.Rewriter Cloud load. After the rephrasing is completed, the paraphrased text can be obtained by sending the unique identifier of the request obtained on the previous step to `https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/text/` endpoint:

```bash
curl --location 'https://api.groupdocs.cloud/v2.0/rewriter/paraphrase/text/dae5390e-3658-4bff-85bf-4a77cc04eaa5_text' \
--header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...LxLejtsVFwrZpHA'
```

The authorization header must contain the access token obtained [earlier](#getting-an-access-token).

You will get the following response:

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

You can fetch the paraphrased texts from the `paraphraseReult` property.

## What’s next?

Congratulations! You have successfully paraphrased the text using GroupDocs.Rewriter Cloud API.

Read the [Developer's Guide](/rewriter/developer-guide/) and [API Reference](https://api.groupdocs.cloud/v2.0/rewriter/swagger/index.html) for details on creating advanced content processing solutions with GroupDocs.Rewriter Cloud.
