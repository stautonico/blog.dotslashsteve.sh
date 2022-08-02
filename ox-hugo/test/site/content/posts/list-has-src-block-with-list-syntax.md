+++
title = "Source block with list syntax in a list"
date = 2017-08-01
tags = ["src-block"]
categories = ["upstream"]
draft = false
+++

An upstream bug in _Blackfriday_ ([Issue #239](https://github.com/russross/blackfriday/issues/239)) caused fenced code
blocks in lists to not render correctly if they contain Markdown
syntax lists. `ox-hugo` provides a hack to get around that bug.

Below is an example of such a case:

-   List item 1

    ```md
    ​- List item 1.1 in code block
    ​- List item 1.2 in code block
    ```
-   List item 2

    ```md
    ​+ List item 2.1 in code block
    ​+ List item 2.2 in code block
    ```
-   List item 3
