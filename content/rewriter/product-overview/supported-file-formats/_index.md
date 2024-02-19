---
id: "supported-file-formats"
weight: 20
date: "2023-12-15"
author: "Vladimir Lapin"
type: docs
url: rewriter/supported-file-formats
aliases:
- rewriter/supported-document-formats
productName: "GroupDocs.Rewriter Cloud"
title: Supported file formats
description: A complete list of file formats that can be processed by GroupDocs.Rewriter Cloud.
keywords:
- format
- extension
- conversion
- source
- target
---

GroupDocs.Rewriter Cloud can process files in all popular formats while accurately preserving layout, structure, and formatting.

Document | Extensions | Description
-------- | ---------- | -----------
Plain text | .TXT | Plain text files or text in the form of lines.
Portable Document Format | .PDF | An open standard cross-platform format for documents that include formatted text, images, multimedia elements, and more.
HTML page | .HTML, .HTM | The standard markup language for Web pages.
Microsoft Word | .DOCX<br />.DOCM<br />.DOC | Microsoft Word 97-2021 and Microsoft 365 documents, including macro-enabled documents.
Rich Text Format | .RTF | Popular rich text format supported by many word processors in different OS'es.
OpenDocument Text | .ODT | Documents created with a number of open source word processing applications, such as _Writer_ from Apache OpenOffice and LibreOffice.
Microsoft PowerPoint | .PPTX<br />.PPTM<br />.PPT | Microsoft PowerPoint 97-2021 and Microsoft 365 PowerPoint presentations, including macro-enabled presentations.
Markdown | .MD | Plain text files formatted using one of the dialects of the Markdown language (including Markdown with Hugo syntax).

**Note:** We cannot guarantee that processed documents will be fully compatible with applications other than those in which the original document was created. For example, if the original document was created in Microsoft Office 2016, we recommend that you open the rewritten document in the same or newer version of Office applications.

## Conversion

In addition to content processing, GroupDocs.Rewriter Cloud can save the paraphrased document in various file formats other than the original, with formatting preserved (where applicable).

Source file format | Converted file format
------------------ | ---------------------
.PDF               | .DOCX<br />.PPTX<br />.HTML<br />.SVG<br />.XPS
.DOCX              | .PDF<br />.RTF<br />.HTML<br />.ODT<br />.TXT<br />.MD<br />.TIFF<br />.SVG<br />.XPS
.DOC               | .DOCX<br />.RTF<br />.HTML<br />.ODT<br />.TXT<br />.MD<br />.PDF<br />.TIFF<br />.SVG<br />.XPS
.ODT               | .DOCX<br />.RTF<br />.HTML<br />.ODT<br />.TXT<br />.MD<br />.PDF<br />.TIFF<br />.SVG<br />.XPS
.RTF               | .DOCX<br />.RTF<br />.HTML<br />.ODT<br />.TXT<br />.MD<br />.PDF<br />.TIFF<br />.SVG<br />.XPS
.PPTX              | .PPTX<br />.PDF<br />.TIFF<br />.HTML<br />.XPS<br />.ODP
.PPT               | .PPT<br />.PPTX<br />.PDF<br />.TIFF<br />.HTML<br />.XPS<br />.ODP
.HTML              | .PDF<br />.DOCX<br />.TIFF<br />.XPS
.MD                | .HTML<br />.PDF<br />.DOCX<br />.TIFF<br />.XPS
