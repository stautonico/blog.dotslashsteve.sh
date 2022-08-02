+++
title = "Overriding Org-style tags"
tags = ["overriding", "underscore_is_retained", "hyphenated-works"]
categories = ["cat3", "3 word cat"]
draft = false
+++

By using `EXPORT_HUGO_TAGS` in the property drawer, Org tags in the
current headline ("this\_tag\_wont\_apply") **and** the inherited one
("alpha", "beta", "hyphenated-tag", "super") will get overridden.

When setting categories via the keyword `#+HUGO+CATEGORIES` or the
subtree property `EXPORT_HUGO_CATEGORIES`, do **not** add the "@" prefix.
