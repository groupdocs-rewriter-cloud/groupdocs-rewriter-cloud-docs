---
id: "languages"
weight: 30
date: "2023-12-15"
author: "Vladimir Lapin"
type: docs
url: /rewriter/languages/
productName: "GroupDocs.Rewriter Cloud"
title: Setting content language
description: How to specify a language of the processed text.
keywords:
- content
- languages
- source
---

Automated content processing, such as rephrasing, involves a large number of language-specific nuances, idioms, and expressions that can significantly impact the way sentences are structured and meanings are conveyed. Different languages have unique grammatical rules, word choices, and cultural contexts that influence the appropriate content processing techniques.

Thus, you must explicitly specify the correct content language in `language` parameter when making GroupDocs.Rewriter API calls. It will ensure that the rephrased content is grammatically correct and accurately captures the intended meaning. The following languages are supported:

Language | Configuration value
-------- | -------------------
Arabic | `ar`
English | `en`
French | `fr`
German | `de`
Hindi | `hi`
Indonesian | `id`
Italian | `it`
Portuguese | `pt`
Russian | `ru`
Slovak | `sk`
Spanish | `es`
Thai | `th`
Ukrainian | `uk`

## Example

```json
{
  "language": "en",
  "text": "Hello, everyone! We will try to rephrase this text into something new.",
  "suggestions": "One",
  "diversityDegree": "Off"
}
```
