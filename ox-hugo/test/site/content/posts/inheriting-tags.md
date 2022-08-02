+++
title = "Inheriting tags"
tags = ["tag with lot of words", "hyphened-tag", "alpha", "beta", "super", "gamma", "delta", "two words"]
categories = ["cat1", "cat2"]
draft = false
+++

If user specifies tags to the post subtree headline, those tags get
added to the set of default tags set in `#+FILETAGS` (and the ones
inherited). For the inheritance of tags from parent headlines and
`#+FILETAGS` to work, `org-use-tag-inheritance` needs to be set
appropriately if changed from the default value of `t`. These tags are
collected together and assigned to the Hugo `tags` front matter
variable for this post.

When setting categories via Org-style tags, prefix the tags with
"@". That "@" is used as a special character for `ox-hugo` to identify
those tags to be used as Hugo categories. This applies to categories
added as Org tags to headlines as well as `#+FILETAGS`.
