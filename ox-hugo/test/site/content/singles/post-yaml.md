---
title : "Single Post with YAML front matter"
date : 2017-07-20
publishDate : 2017-07-22
expiryDate : 2017-07-23
tags : ["single", "yaml"]
categories : ["cat1", "cat2"]
draft : false
menu :
  foo:
    parent : "main"
    weight : 10
    identifier : "single-yaml"
---

This is a single post. You do not need to set the `EXPORT_FILE_NAME`
property in here. But then you also lose the tag and property
inheritance, TODO state, etc. Org awesomeness.


## First heading in this post {#first-heading-in-this-post}

This is a under first heading.


## Second heading in this post {#second-heading-in-this-post}

This is a under second heading.
