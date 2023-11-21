---
title: Meeting Requirements by Journals -- Some Tips
date: 2023-11-21
permalink: /posts/2023/MRBJST
excerpt_separator: <!--more-->
toc: true
tags:
  - web-dev
---
In publication of scientific papers, different journals have various requirements. Here I list some tips regarding the problem I have encountered.
<!--more-->
## Introduction
The following tips can be programmed. For example, I have written a script file `publicationTools.py` to incorporate the utilities to tackle the problems.

## Tex file should not contain private macro
Journals such as *Annales Geophysicae* require the submitted tex file only contain macros defined by the journal. The program `de-macro`, which is a part of texlive, come in handy. To use it, follow

1. dump all private macros in a file named as `<defs-file>-private` where `<defs-file>` represents a string you can choose as you wish. Remember to put `\usepackage{<defs-file>-private}` in the preamble of tex file.

2. run
        
        de-macro with_private_macro.tex


## Typing abstract and figure and table captions into some submission portal
In submission, journals usually require this while tex code should be replaced
with some form of code defined by the journal. For example, Nature series journals represent italic text with `<i>text<\i>` and subscript with `R<sub>E<\sub>`.

To transform systematically tex code into these journal-specific code, one can
use pandoc. In the case of Nature journals, we can use

    pandoc --from latex --to html4 --no-highlight input.tex

followed by some additional translations such as from `<em>` to `<i>`.

