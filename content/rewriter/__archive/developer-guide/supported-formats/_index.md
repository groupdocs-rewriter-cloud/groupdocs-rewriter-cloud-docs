---
id: "supported-formats"
url: "rewriter/supported-formats"
title: "Supported Formats"
productName: "GroupDocs.Rewriter Cloud"
weight: 3
description: ""
keywords: ""
---

GroupDocs.Rewriter Cloud can rephrase documents in the most popular formats. User should specify the format of the document to
be paraphrased putting it in the request’s body:
* **extension of word file (docx / docm / doc / rtf)** — to paraphrase Microsoft Word document
* **extension of PDF file (pdf)** — to paraphrase Adobe PDF document
* **extension of OpenDocument files (odt)** — to paraphrase files of OpenDocument format
* **extension of Markdown file (md)** - to paraphrase Markdown file
* **extension of HTML file (html)** - to paraphrase HTML file
* **plain text (txt)** - to paraphrase plain text files or text in the form of lines

In addition to rephrasing, GroupDocs.Rewriter Cloud can save the resulting document in various file formats other than
the original, with formatting preserved (where applicable). Just specify the output format of the paraphrased document putting
the file extension in the request’s body:

* **doc, docx, odt, rtf** — docx, rtf, html, odt, txt, md, pdf, tiff, svg, xps
* **pdf** — pdf, docx, pptx, html, xps, svg
* **md** — md
* **html** — html, pdf, docx, tiff, xps

Remarks:

1. Conversion from doc to docx is supported but not vice versa
2. Document with macros could be saved only using the same format, i.e. docm
3. If format is not supported or there is a mistake, paraphrased file would be saved using the same format under specified name in request, i.e. paraphrased.png.docx
4. Default options are used for file conversion, if result is unsatisfactory, convert it with custom options using corresponding Aspose product