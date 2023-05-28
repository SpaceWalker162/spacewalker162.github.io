---
title: Automatically Posting My Publications on This Site
date: 2023-05-28
permalink: /posts/2021/07-test
excerpt_separator: <!--more-->
toc: true
tags:
  - web-dev
---
This post presents the process of automatically posting my publications.

1. I use Jabref to manage my library. The data of my publications are saved in a bib file.

2. Run a python script `../utilities/publications/makeMyPublicationsMDFile.py` to generate markdown files under `_publications` and copy pdf files to `files/papers`
