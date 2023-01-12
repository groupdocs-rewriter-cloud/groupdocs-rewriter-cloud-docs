---
id: "groupdocs-rewriter-for-cloud-22-12-release-notes"
url: "rewriter/groupdocs-rewriter-for-cloud-22-12-release-notes"
title: "GroupDocs.Rewriter for Cloud 22.12 Release Notes"
productName: "GroupDocs.Rewriter Cloud"
weight: 9
description: ""
keywords: ""
---

Release features:

* Added support for paraphrasing Markdown and HTML files
* Added an option to select the degree of diversity of the paraphrased text. It allows one to choose how much the source
text will change and supports three modes:

    **off** (default) - fewer changes, but potentially more accurate text \
    **medium** - moderately diverse and plausible text in terms of language \
    **high** - more changes, but potentially less accurate text

    Diversity when paraphrasing in **medium** and **high** modes is achieved by:
    - parameters that restrict copying of long phrases from the original text
    - a wider search for a suitable word/phrase in order to replace a word/phrase from the original text carried out by a neural network
* Added an option to receive 1, 2 or 3 paraphrasing variants for each sentence at the user’s choice