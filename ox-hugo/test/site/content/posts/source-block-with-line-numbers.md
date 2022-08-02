+++
title = "Source blocks with line number annotation"
tags = ["src-block", "highlight", "shortcode"]
draft = false
+++

-   [Org reference](https://orgmode.org/manual/Literal-examples.html)
-   [Hugo `highlight` shortcode with line numbers](https://gohugo.io/content-management/syntax-highlighting/)


## Cases {#source-block-line-number-cases}


### Default new line number start {#default-new-line-number-start}


#### Org source {#org-source}

```org
#+BEGIN_SRC emacs-lisp -n
;; this will export with line number 1 (default)
(message "This is line 2")
#+END_SRC
```


#### Output {#output}

{{< highlight emacs-lisp "linenos=table, linenostart=1">}}
;; this will export with line number 1 (default)
(message "This is line 2")
{{< /highlight >}}


### Specify new line number start {#specify-new-line-number-start}


#### Org source {#org-source}

```org
#+BEGIN_SRC emacs-lisp -n 20
;; this will export with line number 20
(message "This is line 21")
#+END_SRC
```


#### Output {#output}

{{< highlight emacs-lisp "linenos=table, linenostart=20">}}
;; this will export with line number 20
(message "This is line 21")
{{< /highlight >}}


### Default continued line numbers {#default-continued-line-numbers}


#### Org source {#org-source}

```org
#+BEGIN_SRC emacs-lisp +n
;; This will be listed as line 22
(message "This is line 23")
#+END_SRC
```


#### Output {#output}

{{< highlight emacs-lisp "linenos=table, linenostart=22">}}
;; This will be listed as line 22
(message "This is line 23")
{{< /highlight >}}


### Specify continued line numbers jump {#specify-continued-line-numbers-jump}


#### Org source {#org-source}

```org
#+BEGIN_SRC emacs-lisp +n 10
;; This will be listed as line 33
(message "This is line 34")
#+END_SRC
```


#### Output {#output}

{{< highlight emacs-lisp "linenos=table, linenostart=33">}}
;; This will be listed as line 33
(message "This is line 34")
{{< /highlight >}}
