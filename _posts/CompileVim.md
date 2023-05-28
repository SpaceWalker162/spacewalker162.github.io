---
title: Compile VIM on MacOS with Python3 Dynamic Support
date: 2023-05-27
permalink: /posts/2023/CVMPDS
excerpt_separator: <!--more-->
toc: true
tags:
  - test
---
1. Move to the home directory

        cd

2. Get VIM source from github

        git clone https://github.com/vim/vim.git

3. Enter the source directory

        cd vim

4. Set the Python configuration e.g.

        python3-config --configdir

5. Add configuration

        ./configure --with-features=huge \
        --enable-python3interp=dynamic \
        --with-python3-command=python3.9 \
        --with-python3-config-dir=$(python3-config --configdir) \
        --prefix=/usr/local

5. Configure .vimrc to point to the python interpreter you wish to use

        " on OSX
        set pyxversion=3
        set pythonthreedll=/Library/Frameworks/Python.framework/Versions/3.6/Python
