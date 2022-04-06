---
id: "json-request-details"
url: "rewriter/json-request-details"
title: "JSON Request Details"
productName: "GroupDocs.Rewriter Cloud"
weight: 5
description: ""
keywords: ""
---

User should put in the requests body following information to paraphrase a document:

* **format** — format of file for paraphrasing (ex: docx)
* **outformat** — format of paraphrased file (ex: pdf)
* **language** — language of source file (ex: en)
* **name** — name of file to paraphrase (ex: test.docx)
* **folder** — folder of file to paraphrase (ex: texts) 
* **savepath** — folder for paraphrased file (ex: paraphrased)
* **savefile** — name of paraphrased file (ex: paraphrased.docx)
* **storage** — name of storage

To paraphrase plain text the following information should be put in the requests body:

* **language** — language of source text (ex: en)
* **text** — text to paraphrase (ex: hello world)
