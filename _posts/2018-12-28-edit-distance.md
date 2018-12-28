---
layout: post
title: Levenshtein distance
mathjax: true
---

Levenshtein distance between two strings
=====================

Levenshtein distance is a kind of edit distance, that is a way of quantifying of how dissimilar two strings are. It measure the minimum number of edits needed to transform the first string into the second string.

We suppose that strings are indexed from 0. Let $s$ be a string, then $s[a, b)$ or $s[a, b-1]$ is a substring of a string that contains characters from $a$ to $b-1$ (including).

$$
  a +b = c
$$
