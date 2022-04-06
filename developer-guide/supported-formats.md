---
id: "supported-formats"
url: "rewriter/supported-formats"
title: "Supported Formats"
productName: "GroupDocs.Rewriter Cloud"
weight: 3
description: ""
keywords: ""
---

GroupDocs.Rewriter Cloud allows to paraphrase Microsoft Word documents. User should specify format of document to paraphrase putting in the request’s body:

* **extension of word file (docx / docm / doc)** — to paraphrase Microsoft Word document
* **extension of PDF file (pdf)** — to paraphrase Adobe PDF document

Additionally, user could obtain paraphrased file in any other format available for conversion. Just specify output format of paraphrased document putting file extension in the request's body:

* **doc, docx** — docx, rtf, html, odt, txt, md, pdf, tiff, svg, xps
* **pdf** — docx, pptx, html, xps, svg

Remarks:

1. Conversion from doc to docx is supported but not vice versa
2. Document with macros could be saved only using the same format, i.e. docm
3. If format is not supported or there is a mistake, paraphrased file would be saved using the same format under specified name in request, i.e. paraphrased.png.docx
4. Default options are used for file conversion, if result is unsatisfactory, convert it with custom options using corresponding Aspose product 